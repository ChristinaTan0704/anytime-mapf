# Anytime Multi-Agent Path Finding

This repository is directly modified based on [official bandit repo](https://github.com/thomyphan/anytime-mapf) and supports using JSON file as input to initialize the solution. This modified repository is for obtaining result for project [Benchmarking Large Neighborhood Search for Multi-Agent Path Finding](https://github.com/ChristinaTan0704/mapf-lns-benchmark/tree/main).


## Installation
The code requires the external libraries [`BOOST 1.81.0`](https://www.boost.org/) and [`Eigen 3.3`](https://eigen.tuxfamily.org/), and [`CMake`](https://cmake.org) for building the code. 
    
After installing all libraries go to the root folder of this repository and run the following commands: 
```shell script
cmake -DCMAKE_BUILD_TYPE=RELEASE .
make
```

## Usage

```shell
./balance \
--map random-32-32-20.map \
--agents random-32-32-20-random-1.scen \
--state map-random-32-32-20-scene-1-agent-150.json \
--neighborCandidateSizes 5 \
--uniform_neighbor 3 \
--agentNum 150 \
--cutoffTime 300
```
- agents (required): the .scen file downloaded from the MAPF benchmark
- map (required): the .map file downloaded from the MAPF benchmark
- agentNum (required): number of agents in the current map
- state (required): path to the current state JSON file, key: agent id, value: list of agent location in 2D x, y coordinate, check [map-random-32-32-20-scene-1-agent-150.json](map-random-32-32-20-scene-1-agent-150.json) as an example
- cutoffTime (optional): runtime limit for running the removal and replan of LNS

You can find more details and explanations for all parameters with:
```
./balance --help
```



## References 

- [1] J. Li et al. *"MAPF-LNS2: Fast Repairing for Multi-Agent Path Finding via Large Neighborhood Search"*. AAAI 2022.
- [2] T. Phan et al. *"Adaptive Anytime Multi-Agent Path Finding using Bandit-Based Large Neighborhood Search"*. AAAI 2024.