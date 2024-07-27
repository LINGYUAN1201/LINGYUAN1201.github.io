---
title: "The genDynamic Package "
collection: open access
type: "R-based"
permalink: /open access/2024-spring-open access-1
venue: "Dynamic network game"
date: 2024-02-24
---

The function `gen_dynamic` serves the purpose of generating a dynamic evolving network model and simulating the interaction and evolution of strategies among nodes within the network.


  
1. It achieves this by first defining an internal function, `payoff_sug`, which calculates the payoff between nodes specifically for the SUG game (Spatial Ultimatum Game).

2. Input parameter validation ensures that essential parameters such as network size `N`, time steps `L`, average degree `aver_k` are all positive numeric values, and that the specified game type and network type are valid.

3. Another internal function, `payoff`, is defined to compute node payoffs based on their strategies and payoff matrices, allowing for flexibility across different game types.

4. The function also includes an internal function, `generate_network`, responsible for generating the network structure based on the specified network type (BA, ER, SW).

5. Initialization of payoff matrices corresponding to different game types ensures that the simulation can accommodate various types of games.

6. The strategy matrix `S` for nodes is initialized based on the game type, which could involve either random initialization or initialization within a specific range.

7. Recording of the initial adjacency matrix `initial_adj` provides a reference point for tracking network changes throughout the simulation.

8. Initialization of matrices `X` and `Y` enables the storage of node payoffs and the process of strategy changes, respectively, facilitating analysis and visualization of simulation results.

9. The simulation process iterates through each time step, computing node payoffs and updating strategies based on the Fermi updating mechanism, which incorporates randomness and differences in payoffs between nodes.

10. At each step of the simulation, the node payoffs and strategy changes are recorded, providing insights into the dynamics of the network.

11. Finally, the function records the final adjacency matrix `final_adj` and returns a list object containing stored payoff and strategy change processes, encapsulating the outcome of the dynamic network evolution simulation.

Information about this R package can be found [here](https://github.com/LINGYUAN1201/genDynamic).
