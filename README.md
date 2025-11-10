# DBSCAN-PCA-Projection-On-Wine-Dataset

🍷 DBSCAN (From Scratch) on Wine Dataset — with PCA Projection

📘 Density-Based Spatial Clustering of Applications with Noise (DBSCAN)

An unsupervised machine learning algorithm that discovers clusters based on data density rather than predefined shapes.


---

🧠 Overview

Goal: Identify natural clusters and outliers in the Wine dataset without using labels.

Unlike K-Means or Hierarchical Clustering, DBSCAN:

Does not require the number of clusters in advance.

Can find arbitrarily shaped clusters.

Automatically detects noise/outliers.

Works well when clusters have different densities.



---

🧮 Mathematical Foundation

1. Distance Metric

The Euclidean distance between two points  and :

$$\D(x_i, x_j)$$ = $$\sqrt{\sum_{k=1}^{n}(x_{ik} - x_{jk})^2}$$


---

2. Neighborhood Concept

For each data point $$\x_i$$:

$$N_\varepsilon(x_i)$$ = $$\{x_j \mid D(x_i, x_j) \leq \varepsilon\}$$

where:

$$\varepsilon$$ → radius defining the neighborhood boundary.

 $$N_\varepsilon(x_i)$$ → set of neighbors of .



---

3. Core, Border, and Noise Points

Type	                  Definition

Core Point	:            Has ≥ minPts neighbors within ε
Border Point	:          Fewer than minPts neighbors but reachable from a core point
Noise Point	  :          Not reachable from any core point



---

4. Algorithmic Steps

1. For each unvisited point:

Find all neighbors within ε.



2. If the number of neighbors ≥ minPts → form a new cluster.


3. Expand the cluster by recursively including all reachable points.


4. Points not belonging to any cluster are labeled -1 (noise).




---

⚙️ Implementation Details

Step	                                             Description

🧹 Data Preprocessing	:                          Standardized all features using StandardScaler.
🧩 Dimensionality Reduction	:                    Applied PCA (2 components) for 2D visualization.
🧮 Clustering	:                                  Implemented DBSCAN from scratch (recursive cluster expansion).
🔬 Evaluation	:                                   Compared with sklearn.DBSCAN implementation.
📈 Validation:                                  	Used Silhouette Score for cluster quality.



---

📊 Visualization

After clustering, we visualize both Scratch and Sklearn versions side-by-side using PCA-projected features.

Scratch Implementation	sklearn.DBSCAN

	


Black dots represent noise points, while colored regions represent dense clusters.


---

🧩 Code Summary

🔹 1. Core Functions

def region_query(X, point_idx, eps):
    # Finds all neighbors within epsilon distance

def expand_cluster(X, labels, point_idx, neighbors, cluster_id, eps, minPts):
    # Recursively expands clusters by adding reachable points

def dbscan(X, eps, minPts):
    # Main DBSCAN algorithm to assign cluster labels


---

🔹 2. Evaluation Metric

Silhouette Score:

S = $$\frac{b - a}{\max(a, b)}$$

a = average intra-cluster distance

b = average nearest-cluster distance


A higher  S (close to 1) means better separation and cohesion.


---

📈 Results

Version           	ε	            minPts	   Clusters Found	              Silhouette Score

Scratch DBSCAN	   0.6	   ,        6	,         ~3	 ,                          0.013.
sklearn.DBSCAN	   0.6	    ,       6	 ,        ~3	  ,                         0.013.


✅ The scratch implementation performs comparably to the sklearn version, proving correctness and robustness.


---

🧭 Key Learnings

No need for train-test split → DBSCAN is unsupervised (no labels to predict).

Density-based clustering works well for non-linear cluster shapes.

Outliers can be automatically identified.

PCA projection enables visualization in 2D for high-dimensional datasets.

Silhouette Score quantitatively evaluates cluster quality.



---

🌍 Real-World Applications

Domain	                                          Use Case

🏦 Banking	:                                 Fraud and anomaly detection,
🧬 Bioinformatics:                           	Gene expression pattern analysis,
🧭 Geospatial Data	:                         Grouping nearby locations or signals,
🛍️ Marketing	:                               Customer segmentation,
🚗 Autonomous Systems:                       	Sensor-based anomaly detection,



---

🧠 Note on Learning Progress

"This project is part of my Unsupervised Machine Learning Scratch Implementation Series, where each algorithm is implemented from mathematical foundations to visualization — ensuring both conceptual clarity and coding depth".




---

📚 Concepts Covered

Density-based clustering

Recursive expansion algorithms

PCA visualization

Silhouette score evaluation

Noise/outlier detection



---

🏁 Next in the Series

Next algorithm: t-Distributed stochastic Neighbour Embedding (t-SNE) —  from scratch and visualization in PCA space.
