---
title: "Cluster Analysis and Visualisation"
collection: open access
type: "MATLAB-based"
permalink: /open access/2022-fall-open access-2
venue: "Cluster Analysis"
date: 2022-11-27
---

This MATLAB code performs several clustering analyses on a generated dataset.

1. *Generate Random Data*: A random dataset X is generated with three clusters using Gaussian distribution parameters (mu and sigma). The generated data is visualized in a scatter plot.

2. *Gaussian Mixture Clustering*: A Gaussian Mixture Model (GMM) is fit to the data using the gmdistribution. The code then visualizes the GMM results with a scatter plot, contour plot (ezcontour), and surface plot (ezsurf).

3. *Plotting GMM Cluster Information*: The code calculates cluster assignments and posterior probabilities for each data point. It visualizes the clusters in a 3D plot with posterior probabilities and a plot showing the distribution of cluster membership scores.

4. *K-Means Clustering*: The dataset is clustered using the k-means algorithm (kmeans). Silhouette analysis is performed (plot_silhouette), and the clusters are visualized in a 2D plot.
  
5. *Hierarchical Clustering*: Hierarchical clustering is performed using the linkage and cluster functions.   A dendrogram is plotted to visualize the hierarchical structure.

6. *Helper Functions*: Several helper functions (plot_clusters_3d, plot_posterior_distribution, plot_silhouette, and plot_clusters_2d) are defined to facilitate the visualization of different aspects of clustering.

Overall, the code provides a comprehensive analysis of clustering techniques (Gaussian Mixture, K-Means, and Hierarchical) on a synthetic dataset, along with visualizations for better understanding and interpretation of the results.

*[Cluster Analysis and Visualisation](../assets/Cluster.txt)
