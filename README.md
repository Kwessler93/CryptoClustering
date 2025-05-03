# Cryptocurrency Clustering with K-Means and PCA

## Overview

This project explores clustering techniques using K-Means and Principal Component Analysis (PCA) to identify groupings among cryptocurrencies based on their performance metrics. The project follows a full machine learning pipeline, from preprocessing and feature scaling to clustering analysis and visualization, using Python and `hvPlot`.

## Technologies Used

- Python
- pandas
- scikit-learn
- hvPlot
- Jupyter Notebook

## Methodology

### 1. **Scaling the Data**
- Used `StandardScaler` to normalize the cryptocurrency price change percentages across multiple time frames.
- Constructed a scaled DataFrame with `coin_id` set as the index.

### 2. **Finding the Optimal k with the Elbow Method**
- Implemented the elbow method to determine the best number of clusters (`k`) by plotting inertia values for `k` from 1 to 11.
- Visualized the elbow curve to identify the inflection point.

> **Best k using original scaled data:** `k = 4`

### 3. **K-Means Clustering with Scaled Data**
- Initialized and trained a `KMeans` model with the optimal `k`.
- Predicted clusters and appended them to the scaled DataFrame.
- Created a scatter plot using `hvPlot` (x: 24h change, y: 7d change) to visualize clusters.

### 4. **Dimensionality Reduction with PCA**
- Applied PCA to reduce the dataset to 3 principal components.
- Evaluated explained variance to assess how much information was preserved.

> **Total explained variance by 3 components:** `90%`

- Built a new DataFrame from the PCA-transformed data while retaining `coin_id` as the index.

### 5. **Finding the Optimal k with PCA Data**
- Repeated the elbow method using the PCA-reduced dataset.

> **Best k using PCA data:** `k = 4`  
> **Comparison:** This did not differ from the original k value.

### 6. **K-Means Clustering with PCA Data**
- Fitted a new `KMeans` model using the PCA data.
- Visualized the clusters in a scatter plot using PC1 and PC2.

### 7. **Visual Comparisons**
- Created composite plots comparing:
  - Elbow curves (original vs PCA).
  - Found that using fewer features through PCA simplifies the dataset but slightly reduces clustering effectiveness. The Elbow Curve shows that PCA-reduced data consistently yields lower inertia, indicating tighter clusters, but possibly at the cost of capturing less of the original variance. In the scatter plots, the clusters from the standard scaled data appear more distinct and better separated, while the PCA-based clusters are more compressed and tend to overlap, particularly near the center. This suggests that while dimensionality reduction can improve performance and reduce complexity, it may also obscure some natural groupings in the data.

