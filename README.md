# ML Final Project – Seeds Clustering

## Introduction

This project is the final project for the Machine Learning course. It uses unsupervised learning to explore whether meaningful structure can be found in the Seeds dataset.

The aim is to group the samples into clusters without using the known variety labels during the clustering process, and then evaluate how well the discovered structure matches the true varieties.

## Dataset

The Seeds dataset contains 210 wheat kernel samples described by 7 geometric features:

- Area
- Perimeter
- Compactness
- Kernel length
- Kernel width
- Asymmetry coefficient
- Groove length

The true variety labels were kept aside and were only used later to evaluate the clustering results.

## Preprocessing

The dataset was standardized using `StandardScaler` so that all seven features could contribute to the clustering on a comparable scale.

## PCA Exploration

Principal Component Analysis (PCA) was used to project the standardized data into two dimensions for visualization.

The first two principal components explained approximately 88.98% of the total variance.

The PCA scatter plot showed about three broad groups of points, although there was some overlap between them.

### PCA Visualization

![PCA scatter plot](PCA%20scatter%20plot.png)

## K-Means Clustering

K-Means clustering was applied to the standardized data.

The number of clusters was investigated using:

- the Elbow method
- the Silhouette method
- the PCA scatter plot

Three clusters were selected because the PCA visualization suggested approximately three groups and the Elbow method also supported a choice around three clusters.

The Silhouette method supported two clusters, so the choice of three clusters involves some uncertainty.

### Cluster Selection

![Elbow method](Elbow%20method.png)

![Silhouette method](Silhouette%20method.png)

## Results

The final K-Means model used:

- Number of clusters: **3**
- Number of features: **7**
- Number of samples: **210**

The resulting clusters were compared with the true variety labels using a cross-tabulation.

The purity score was:

**91.9%**

This indicates that the discovered clusters matched the known varieties quite well, although the match was not perfect.

Variety 2 was separated most cleanly, with most of its samples concentrated in one cluster.

### True Varieties

![PCA scatter plot - True varieties](PCA%20scatter%20plot%20-%20True%20varieties.png)

## Cluster Profiles

The cluster centres were transformed back to the original feature scale in order to examine the characteristics of the three clusters.

This provides an interpretation of the typical feature values associated with each discovered cluster.

## Important Interpretation

The K-Means algorithm used all seven features, while the PCA visualization shows only two dimensions.

Therefore, points that appear close together or overlapping in the two-dimensional PCA plot may still be separated when information from the remaining dimensions is taken into account.

## Ethical Considerations

Clustering will always produce groups, but these groups may not always represent real categories.

Although the purity score of 91.9% shows that the three clusters matched the true varieties quite well, it is not perfect. Therefore, the clusters should not automatically be treated as definite varieties.

The choice of three clusters also involves some uncertainty because the Silhouette method supported two clusters.

## Reflection

This project showed how unsupervised learning can be used to discover structure in data without using labels during the clustering process.

The main challenge was deciding how many clusters to use, since different evaluation methods gave different indications. Combining the PCA visualization, Elbow method and Silhouette method helped provide a more complete view of the clustering structure.

## Files

- `Final_Project_Option3_Seeds_Clustering.ipynb` – completed project notebook with code, outputs and analysis.
