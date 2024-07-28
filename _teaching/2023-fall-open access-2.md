---
title: "Dynamic Network Generation and Analysis"
collection: open access
type: "MATLAB-based"
permalink: /open access/2023-fall-open access-2
venue: "Dynamic Network"
date: 2023-11-27
---

This MATLAB code generates and analyzes a growing network graph. The main functionalities include:

1. *Network Growth* :It starts with an initial set of nodes (m0) and progressively adds new nodes (up to N) along with edges. The edges are added based on specified conditions, such as isolated nodes, a complete graph, or random connections.

2. *Visualization* :The code generates coordinates for nodes and plots the evolving network graph. Initial nodes are marked in red, and edges are drawn with green lines.

3. *Degree Calculation* :It calculates the degree of each node in the network, representing the number of edges connected to each node.

4. *Degree Distribution* :It analyzes and plots the distribution of node degrees in the network.

5. *Pajek Data Generation* :It includes a call to a function (assuming `Matlab_to_Pajek`) to generate Pajek data from the generated network. Pajek is a software tool used for the analysis and visualization of large networks.

Please note that the specific details of network growth and visualization depend on user input (initial conditions and parameters) and the random generation of nodes and edges. The code is designed to provide insights into the evolving network structure and its properties.

```matlab
clc, clear
m0 = input('Enter the initial number of network nodes m0: ');
m = input('Enter the number of edges generated when introducing a new node m: ');
N = input('Enter the total number of network nodes after growth N: ');
disp('Initial network conditions: 1 for isolated nodes, 2 for a complete graph, 3 for random connections');
se = input('Select initial network condition 1, 2, or 3: ');

if m > m0
    disp('Invalid input for parameter m');
    return;
end

x = 100 * rand(1, m0);
y = 100 * rand(1, m0);  % Create initial coordinates for plotting with m0 nodes

if se == 1
    A = zeros(m0);
elseif se == 2
    A = ones(m0);
    A(1:m0 + 1:m0^2) = 0; % Set diagonal elements to 0
else
    A = zeros(m0);
    B = rand(m0);
    B = tril(B); % Extract lower triangular elements
    A(B <= 0.1) = 1; % Connect edges with a probability of 0.1
    A = A + A';  % Build a complete adjacency matrix
end

for k = m0 + 1:N
    x(k) = 100 * rand;
    y(k) = 100 * rand; % Generate coordinates for the current node for plotting
    p = (sum(A) + 1) / sum(sum(A) + 1); % Calculate connection probabilities for all nodes
    pp = cumsum(p); % Compute cumulative distribution
    A(k, k) = 0;   % Expand the dimension of the adjacency matrix before adding new edges
    ind = []; % Initial set of nodes connected to the new node
    
    while length(ind) < m
        jj = find(pp > rand);
        jj = jj(1); % Use roulette wheel selection to choose the node number to connect
        ind = union(ind, jj); % Use union to ensure the selected nodes are unique
    end
    
    A(k, ind) = 1;
    A(ind, k) = 1; % Build the new adjacency matrix after adding edges
end

plot(x, y, 'ro', 'MarkerEdgeColor', 'g', 'MarkerFaceColor', 'r', 'markersize', 8);
hold on;
A2 = tril(A);
[i, j] = find(A2); % Find non-zero elements in the lower triangular part of the adjacency matrix

for k = 1:length(i)
    plot([x(i(k)), x(j(k))], [y(i(k)), y(j(k))], 'linewidth', 1.2);
end

deg = sum(A);  % Calculate the column sum of the adjacency matrix, i.e., the degree of each node
ave_degree = sum(deg) / N;  % Calculate the average degree

subplot(2, 1, 1);
plot([1:N], deg); % Plot a bar graph of the degree of each node
title('Node Degree in the Network');
xlabel('$v_{i}$', 'Interpreter', 'Latex');
ylabel('$k$', 'Interpreter', 'Latex');

degrange = minmax(deg); % Find the range of degree values
pinshu = hist(deg, [degrange(1): degrange(2)]); % Find the frequency of degree values
df = pinshu / N; % Find the frequency distribution of degrees

subplot(2, 1, 2);
scatter([degrange(1):degrange(2)], df, 'r');  % Plot a bar graph of the degree distribution
title('Degree Distribution in the Network');
xlabel('$k$', 'Interpreter', 'Latex');
ylabel('$P$', 'Interpreter', 'Latex');

% Assuming Matlab_to_Pajek is a valid function, uncomment the line below
% Matlab_to_Pajek(A, 2)  % Generate Pajek data, filename is Pajek_data2.net
```




