---
title: "The Function gen_dynamic"
collection: open access
type: "R-based"
permalink: /open access/2024-spring-open access-1.md
venue: "Dynamic network game"
date: 2024-02-24
---

The function `gen_dynamic` serves the purpose of generating a dynamic evolving network model and simulating the interaction and evolution of strategies among nodes within the network.
  
- It achieves this by first defining an internal function, `payoff_sug`, which calculates the payoff between nodes specifically for the SUG game (Spatial Ultimatum Game).

- Input parameter validation ensures that essential parameters such as network size `N`, time steps `L`, average degree `aver_k` are all positive numeric values, and that the specified game type and network type are valid.

- Another internal function, `payoff`, is defined to compute node payoffs based on their strategies and payoff matrices, allowing for flexibility across different game types.

- The function also includes an internal function, `generate_network`, responsible for generating the network structure based on the specified network type (BA, ER, SW).

- Initialization of payoff matrices corresponding to different game types ensures that the simulation can accommodate various types of games.

- The strategy matrix `S` for nodes is initialized based on the game type, which could involve either random initialization or initialization within a specific range.

- Recording of the initial adjacency matrix `initial_adj` provides a reference point for tracking network changes throughout the simulation.

- Initialization of matrices `X` and `Y` enables the storage of node payoffs and the process of strategy changes, respectively, facilitating analysis and visualization of simulation results.

- The simulation process iterates through each time step, computing node payoffs and updating strategies based on the Fermi updating mechanism, which incorporates randomness and differences in payoffs between nodes.

- At each step of the simulation, the node payoffs and strategy changes are recorded, providing insights into the dynamics of the network.

- Finally, the function records the final adjacency matrix `final_adj` and returns a list object containing stored payoff and strategy change processes, encapsulating the outcome of the dynamic network evolution simulation.
