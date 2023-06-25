# NAP v2.0

## Overview
[NAP v2.0](https://github.com/PavlopoulosLab/NAP) is a powerful network analysis platform implemented in R and Shiny. It supports various types of networks, 
including weighted, unweighted, directed, undirected simple, and bipartite networks. NAP utilizes the igraph library for its backend calculations. 
Users can upload tab-delimited files as input, where the first two columns represent the node connections and the third column indicates the edge weight. 
NAP v2.0 offers four main functions: Basic Visualization, Topological Analysis, Node/Edge Ranking, and Intersection Network.

### Basic 2D/3D Visualization
Once a network is uploaded and named, NAP provides a visual representation using the visNetwork library. This visualization offers full interactivity, 
allowing users to zoom, drag, and pan the network. Nodes can be selected and freely placed on the plane, and selecting a node highlights its first neighbors. 
The network view displays one network at a time and automatically updates when a different network is selected. NAP supports the following igraph layouts for the 2D visualization:

Fruchterman-Reingold: Places nodes using a force-directed layout.
Random: Uniformly places vertices on a 2D plane using random coordinates.
Circle: Places vertices on a circle, ordered by name.
Kamada-Kawai: Places vertices on a 2D plane by simulating a physical model of springs.
Reingold-Tilford: Suitable for trees, ontologies, and hierarchies, providing a tree-like layout.
LGL: Force-directed layout suitable for larger graphs.
Grid: Places vertices on a rectangular 2D grid.
Sphere: Places vertices on a rectangular 3D-like sphere.
In addition to the 2D visualization, NAP offers an interactive 3D network visualization using a force-directed layout. Users can zoom in/out and interactively drag and drop nodes or the entire network to any position in space. This visualization, based on the D3.js library, is particularly useful for larger graphs when the 2D view becomes overcrowded. Refer to Figure 1 for an example of a Yeast PPI visualized in NAP.

### Topological Features
NAP provides several topological features based on the igraph library for network analysis:

Number of nodes: Displays the total number of vertices in the network.
Diameter: Represents the length of the longest geodesic, which is calculated using a breadth-first search method. The geodesic distance is the length of the shortest path between two points.
Radius: Indicates the eccentricity of a vertex, which is the shortest path distance from the farthest node in the graph. The smallest eccentricity in a graph is called its radius.
Density: Calculates the ratio of the number of edges to the number of possible edges, representing the graph's density.
Average path length: Gives the average number of steps required to reach any other node from a given node.
Clustering Coefficient: Measures the tendency of the network to form clusters.
Modularity: Evaluates the modularity of a graph division into subgraphs.
Number of self-loops: Determines the number of nodes connected to themselves.
Average Eccentricity: Provides the average eccentricity of the vertices, representing their shortest path distance from the farthest node.
Average Eigenvector Centrality: Measures the influence of a node in a network.
Assortativity Degree: The assortativity coefficient indicates whether similar vertices, based on an external property, tend to connect or not.
Directed Acyclic Graph: Indicates whether a graph contains cycles.
Average Number of Neighbors: Gives the average number of neighbors for each node in the network.
Centralization Betweenness: Quantifies a node's centrality by counting the shortest paths from all vertices to all others that pass through the node. Betweenness centrality identifies how often a node acts as a bridge along the shortest path between two other nodes.
Centralization Closeness: Measures the speed at which randomly walking messages reach a vertex from elsewhere in the graph.
Centralization Degree: Defined as the number of links incident upon a node.
Graph Mincut: Calculates the minimum st-cut between two vertices in a graph. It represents the minimum total weight of edges needed to be removed to eliminate all paths from the source to the target.
Motifs-3: Searches the graph for motifs of size 3.
Motifs-4: Searches the graph for motifs of size 4.

### Topological Feature Pairwise Comparison and Node/Edge Ranking
Nodes in NAP can be ranked using various topological features, including centralization degree, centralization betweenness, clustering coefficient, 
page rank, eccentricity, eigenvector, and subgraph centrality. On the other hand, edges can be ranked based on betweenness centrality. 
NAP allows users to generate an all-versus-all scatterplot matrix, showcasing the pairwise correlations between the selected topological 
features.

### Network Intersection
NAP enables users to automatically extract, export, and visualize the common edges and nodes between any pair of selected networks. 
Common node and edge names are initially presented in interactive tables as text, while Venn diagrams are employed to illustrate the node/edge 
union and intersection between the two networks. Venndiagrams library is used to generate Venn diagrams, while VisNetwork library provides an interactive 
2D view of the network's intersection. Apart from the 2D view, NAP offers the option to visualize the common parts of two selected networks using a 3D multi-layer 
graph implemented in D3.js. In this representation, nodes from the first network are placed on one layer and colored blue, nodes from the second network are placed 
on a different layer and colored red, and nodes belonging to both networks with the same name are considered common and colored yellow. Edges are drawn to connect 
these common nodes across the two layers. Optionally, users can employ a 3-layer representation, positioning the common nodes on a third middle layer for a more 
comprehensive view, although it may not always be superior. To minimize line crossovers between layers, an initial layout can be applied to the entire network, 
and nodes can be separated onto their respective layers by adjusting their height coordinate upon completion. NAP currently supports several layouts for this view, 
including random, circular, fruchterman-reingold, fruchterman-reingold grid, kamada-kawai, spring, and LGL force-directed algorithms.

The multi-layer 3D graph is fully interactive, allowing users to zoom in/out, drag, and rotate nodes or the entire network in 3D space for easier exploration. 
Additionally, users can export the network as a text file for further processing by advanced third-party 3D visualizers such as Arena3D.
