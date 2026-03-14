# BLENDED LEARNING
# Implementation of Customer Segmentation Using K-Means Clustering

## AIM:
To implement customer segmentation using K-Means clustering on the Mall Customers dataset to group customers based on purchasing habits.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorith:
1. Import Libraries: Bring in the necessary libraries such as NumPy, Pandas, Matplotlib, and Scikit-learn.
2. Load the Dataset: Load the customer dataset containing information such as age, annual income, spending score, or purchase history.
3. Data Preprocessing: Check for missing values, clean the dataset if necessary, and normalize or scale the data to ensure all features are in the same range.
4. Select Features: Choose the relevant features (X) such as income and spending score that will be used for customer segmentation.
5. Determine Number of Clusters: Use methods such as the Elbow Method to determine the optimal number of clusters (K).
6. Build K-Means Model: Initialize the K-Means clustering algorithm with the selected number of clusters.
7. Train the Model: Fit the K-Means model to the dataset so that customers are grouped into clusters based on similarity.
8. Assign Clusters: Assign each customer to a cluster based on the nearest centroid.
9. Visualize the Clusters: Plot the clusters using graphs to clearly show the different customer segments.
10. Analyze the Segments: Interpret the clusters to understand different types of customers and their behavior.

## Program:
```
/*
Program to implement customer segmentation using K-Means clustering on the Mall Customers dataset.
Developed by: Harish Kumar P 
RegisterNumber:  25006070

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score

data=pd.read_csv("CustomerData.csv")
print(data.head())
print(data.columns)

features = ['Age', 'Annual Income (k$)', 'Spending Score (1-100)']
X = data[features]

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

wcss = [] 
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, random_state=42)
    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)

plt.figure(figsize=(8, 4))
plt.plot(range(1, 11), wcss, marker='o', linestyle='--')
plt.xlabel('Number of Clusters')
plt.ylabel('WCSS')
plt.title('Elbow Method for Optimal Number of Clusters')
plt.show()

optimal_clusters = 4
kmeans = KMeans(n_clusters=optimal_clusters, random_state=42)
kmeans.fit(X_scaled)

data['Cluster'] = kmeans.labels_
sil_score = silhouette_score(X_scaled, kmeans.labels_)
print(f"Silhouette Score: {sil_score}")

plt.figure(figsize=(10, 6))
sns.scatterplot(data=data, x='Annual Income (k$)', y='Spending Score (1-100)', hue='Cluster', palette='viridis', s=100, alpha=0.7)
plt.title('Customer Segmentation based on Annual Income and Spending Score')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.legend(title='Cluster')
plt.show()
*/
```

## Output:
![alt text](<Screenshot 2026-03-14 092728.png>)
![alt text](<Screenshot 2026-03-14 092747.png>)
![alt text](<Screenshot 2026-03-14 092752.png>)
![alt text](<Screenshot 2026-03-14 092821.png>)
![alt text](<Screenshot 2026-03-14 092843.png>)


## Result:
Thus, customer segmentation was successfully implemented using K-Means clustering, grouping customers into distinct segments based on their annual income and spending score. 
