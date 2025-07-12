# MSCS 634 Lab 5: Clustering with Hierarchical and DBSCAN (MSCS 634)

## Purpose
The purpose of this lab is to explore clustering techniques using the Wine dataset from sklearn. We implement and compare Hierarchical Clustering and DBSCAN to better understand their performance and use cases.

## Key Insights
- Hierarchical clustering works well when a clear number of clusters is visible via dendrograms.
- DBSCAN is effective at identifying noise and clusters of different shapes but requires tuning.
- Evaluation metrics (Silhouette, Homogeneity, Completeness) provide quantitative insights into cluster quality.

## Challenges
- Choosing the right parameters for DBSCAN (eps and min_samples) required experimentation.
- Visualizing high-dimensional data required PCA for interpretability.
