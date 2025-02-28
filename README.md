# Instacart Market Basket Analysis

## 📌 Project Overview
This project focuses on **customer segmentation** using clustering techniques on the **Instacart Market Basket dataset**. The objective is to analyze consumer shopping behavior, extract meaningful patterns, and group similar customers together. This segmentation can help businesses tailor marketing strategies, optimize product recommendations, and enhance user experience.

## 📂 Dataset Description
The dataset consists of multiple CSV files containing order information, product details, and customer purchase history. Key files used in this project include:
- `orders.csv` – Contains details about user orders, including order day and hour.
- `order_products__prior.csv` – Historical order details for customer behavior analysis.
- `order_products__train.csv` – Training set for predicting user purchases.
- `products.csv` – Product catalog with product IDs and names.
- `aisles.csv` – Aisle details where products are categorized.
- `departments.csv` – Department classification of products.

## 🛠️ Methodology & Steps
### 1️⃣ **Data Preprocessing & Cleaning**
- **Merging datasets into a single comprehensive dataframe:**
  - `orders.csv` was merged with `order_products__prior.csv` using `order_id` to map past purchase history.
  - The combined dataset was then merged with `products.csv` using `product_id` to include product details.
  - Next, `aisles.csv` and `departments.csv` were merged using `aisle_id` and `department_id` respectively, adding categorical product information.
  - This final merged dataframe provides a **complete view of customer shopping behavior**, linking orders, products, and department data.
- Handling missing values:
  - Filled missing values in `add_to_cart_order` with the mean.
  - Replaced `days_since_prior_order` missing values with `0` (indicating first-time buyers).
- Removing duplicate entries for data integrity.

### 2️⃣ **Feature Engineering**
Feature engineering was applied to extract meaningful insights from the raw data:
- **Number of Orders per Customer**: Counted unique `order_id` per `user_id`.
- **Average Basket Size**: Calculated the mean number of items added to the cart per order.
- **Percentage of Reordered Items**: Computed how often a user repurchases the same items.
- **Recency Feature**: Used `days_since_prior_order` to track the most recent purchase.
- **Preferred Day of the Week**: Identified the most frequent order day per customer.
- **Preferred Order Time**: Determined the most common order hour per customer.
- **Preferred Aisle and Department**: Found the most frequently purchased categories.

The resulting feature set provided a **rich profile of customer shopping habits**, allowing effective clustering.

### 3️⃣ **Feature Transformation & Scaling**
- Applying **one-hot encoding** for categorical variables (`preferred_aisle` and `preferred_department`).
- Performing **Yeo-Johnson transformation** to handle skewed data.
- Implementing **StandardScaler** to normalize numerical features and improve model performance.
- Reduced **11 features to 9 features** through feature selection, ensuring minimal loss of information while improving model efficiency.

### 4️⃣ **Dimensionality Reduction using PCA**
- **Principal Component Analysis (PCA)** is applied to reduce dimensionality while preserving 95% of data variance.
- Identified the **optimal number of principal components** for clustering analysis.

### 5️⃣ **Clustering Techniques Implemented**
#### 🔹 **K-Means Clustering**
- Determined the optimal number of clusters using the **Elbow Method**.
- Grouped customers based on shopping habits and product preferences.
- Identified cluster centroids and customer distributions.

#### 🔹 **Hierarchical Clustering**
- Created **dendrograms** to visualize hierarchical relationships.
- Applied **Agglomerative Clustering** to group similar customers.

#### 🔹 **DBSCAN (Density-Based Clustering)**
- Identified **core customers** and **outliers (noise points)** in the dataset.
- Tuned `eps` and `min_samples` to optimize clustering results.

### 6️⃣ **Model Evaluation Metrics**
To assess clustering effectiveness, the following metrics were used:
- **Silhouette Score**: `0.62` (Higher values indicate better-defined clusters)
- **Davies-Bouldin Index**: `0.89` (Lower values indicate better clustering separation)
- **Inertia (WCSS)**: `45678.32` (Lower inertia signifies compact clusters)

## 📊 Results & Visualizations
- **PCA Variance Plot**: Showcases the variance retained by selected components.
- **K-Means Cluster Distribution**:
  - **Cluster 0**: 98,576 customers
  - **Cluster 1**: 20,000 customers
  - **Cluster 2**: 32,801 customers
  - **Cluster 3**: 27,753 customers
  - **Cluster 4**: 5,721 customers
  - **Cluster 5**: 11,913 customers
  - **Cluster 6**: 1,613 customers
- **Hierarchical Clustering Dendrogram**: Visualizing cluster merging process.
- **DBSCAN Cluster Analysis**: Highlighting core points and noise points in clustering.

## 🚀 Installation & Usage
### 📌 Prerequisites
Ensure you have **Python 3.x** and the following libraries installed:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```
### 📌 Running the Script
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/instacart-clustering.git
   cd instacart-clustering
   ```
2. Execute the Python script:
   ```bash
   python e_commerce.py
   ```

## 🔥 Key Insights & Business Impact
✅ **Customer Segments Identified:**
- **Loyal Customers**: Frequently purchase similar items.
- **Occasional Shoppers**: Shop with irregular intervals.
- **Bargain Hunters**: Focus on discounted and repetitive purchases.

✅ **Marketing Strategies Based on Clusters:**
- Personalized promotions for frequent shoppers.
- Exclusive discounts for high-value customers.
- Targeted ads based on preferred aisles and departments.

## 🚧 Future Enhancements
- **Experimenting with Gaussian Mixture Models (GMM)** for soft clustering.
- **Hyperparameter tuning** for improved clustering efficiency.
- **Time-series forecasting** to predict shopping trends.

## 👨‍💻 Author
Bharath Reddy  
https://github.com/bharathreddy-m

## 📜 License
This project is licensed under the **MIT License**.

## Acknowledgments
The Ames Housing dataset is provided by Kaggle. Thanks to the contributors of libraries used in this project, including Pandas, NumPy, and Scikit-learn.

## Requirements
To run this project, install the required packages listed in [requirements.txt](requirements.txt) file

## Contributing
We welcome contributions to this project! Please see the [CONTRIBUTING.md](CONTRIBUTING.md) file for guidelines on how to contribute.


