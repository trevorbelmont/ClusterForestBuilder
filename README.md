# Biconnectivity Analysis and Cluster Forest Construction

This project implements a program that analyzes a network's **biconnectivity** properties and constructs a **cluster-border forest** based on its structure. The implementation is based on **Tarjan's algorithm**, which efficiently finds articulation points and bridges in a graph using **a single depth-first search (DFS) traversal**.

To facilitate input generation, a **graph conversion utility** is provided to transform adjacency matrices from the [GraphOnline](https://graphonline.ru/pt/) tool into the required adjacency list format.

## Features

- **Identifies bridge edges (border links)**: Finds the links whose removal would increase the number of connected components in the network.
- **Detects clusters**: Groups links that remain connected even if any single link is removed.
- **Constructs the cluster-border forest**: Builds a forest where clusters and border links are represented as nodes, with edges indicating their connections.
- **High efficiency**: The use of Tarjan's algorithm ensures an optimal runtime of **O(N + M)**, making it suitable for large graphs.

## Input Format

The program expects input representing a network as an **undirected graph**, where:

1. The first line contains two integers, **N** (number of links) and **M** (number of connections between links).
2. The next **M** lines each contain two integers, **xᵢ** and **yᵢ**, representing a connection between two links.

### Example Input

```
9 11
1 2
2 3
3 4
3 8
4 1
4 6
4 7
5 6
5 7
6 7
8 9
```

## Output Format

The program generates:

1. **A list of border links** (one per line, sorted by ID).
2. **A list of clusters** (with cluster IDs and their contained links, sorted lexicographically).
3. **The cluster-border forest**, represented as a list of edges between clusters and border links.

### Example Output

```
3
3
4
8
4
10 4 1 2 3 4
11 2 3 8
12 4 4 5 6 7
13 2 8 9
7 6
3 10
3 11
4 10
4 12
8 11
8 13
```

## Utility for Graph Conversion

The repository includes **matrixToGraphInput.cpp**, a utility that converts adjacency matrices from the [GraphOnline](https://graphonline.ru/pt/) tool into adjacency lists, making it easier to generate valid input files.

- **matrixToGraphInput.cpp** is compiled into the executable **util**.
- **main.cpp**, the primary program, is compiled into the executable **exe**.

This allows users to create custom graph inputs visually and quickly transform them into the format required by the main program.

## Preloaded Graphs for Testing

The repository includes two sample graph files, **orion.in** and **gravata.in**, located in the root directory for quick testing. Additionally:

- More pre-prepared graph files can be found in the **Graphs** folder.
- New graphs can be created using [GraphOnline](https://graphonline.ru/pt/) and converted into adjacency list format using the **util** executable.

