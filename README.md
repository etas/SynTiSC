# SynTiSC Dataset

## Abstract

The SynTiSC dataset (Synthetic Traffic in Smart City) represents vehicle journeys within a smart city.
The city is represented by an abstract graph where nodes indicate crossings and edges indicate road segments between them.
It is similar to a Manhattan-style grid, but with a number of irregularities and choke points to enhance realism.
The vehicle journeys are presented in discrete time steps and follow the road segments between defined entry/exist points.
SynTiSC has been created to evaluate and benchmark resource offloading algorithms.
It is supplementary material to the paper "Differentiable Optimization for Orchestration: Resource Offloading for Vehicles in Smart Cities" ([DOI: 10.1109/ACCESS.2024.3363426](https://doi.org/10.1109/ACCESS.2024.3363426)).
If you use this dataset, please provide a citation to the aforementioned paper.

## Data Description

### File Contents

The dataset, which can be downloaded as single zip file, consists of one gml file and four csv files named as follows.

- SmartCity_Graph.gml
- SmartCity_Traffic_Vehicles_200.csv
- SmartCity_Traffic_Vehicles_400.csv
- SmartCity_Traffic_Vehicles_800.csv
- SmartCity_Traffic_Vehicles_1600.csv

### City Graph

The gml file contains a description in Graph Modeling Language (GML) of the abstract graph modeling road segments and crossings that represent the city's road network.
The graph is undirected, planar, and consists of 50 nodes (labeled `0` to `49`), and 57 edges between them.
They form a single connected component such that there are paths from any node to any other node.
In the original paper each node was considered to feature a Road-Side Unit (RSU).
Furthermore, RSUs were expected to feature wired interconnections between them at every edge.

### Traffic Journeys

The traffic is presented in the csv files as a sequence of 200 discrete time steps (labeled `Time_0` to `Time_199`).
Each row then represents one vehicle and begins with a unique alphanumerical identifier followed by the sequence of time steps.
Each time step may contain either the value `None` or an integer corresponding to a node label of the graph.
The former indicates that the vehicle is currently not located within the graph.
The latter means that the vehicle is currently closest to the node of the given label.

Each vehicle performs exactly one journey during the 200 time steps.
All journeys follow one of the 20 shortest paths between uniformly chosen entry and exit node.
Vehicles may only enter or exit the graph at one of the following nodes

```text
0, 3, 5, 6, 11, 20, 22, 28, 33, 39, 42, 48, 49
```

Therefore, all journeys begin and end with one of these node labels.
The filenames of the csv files contain the total number of vehicles / journeys, i.e., 200, 400, 800 and 1600.
The first vehicle always starts its journey at `Time_0` while all others are subject to a random process.
After the first vehicle, there is a short period where the number of vehicles increases.
The steady state is at about 10% of their total number.
Shortly before the end, the number decreases again.

## License

The SynTiSC dataset is distributed under the terms of the Creative Commons BY-SA 4.0 license. (See accompanying file LICENSE or <https://creativecommons.org/licenses/by-sa/4.0/>)
