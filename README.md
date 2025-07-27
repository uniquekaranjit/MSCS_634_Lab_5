# MSCS 634 – Lab 6: Association Rule Mining and Clustering (Apriori, FP-Growth, Hierarchical & DBSCAN)

## **Purpose**
The goal of this lab is to explore association rule mining techniques (Apriori & FP-Growth) and clustering methods (Hierarchical Clustering & DBSCAN). We analyze transactional data to uncover frequent itemsets and association rules, and we apply clustering techniques to identify meaningful data groupings. Visualizations using Seaborn and PCA are used for interpretation.

---

## **Dataset**
- **Name:** Online Retail II Dataset (UCI/Kaggle)
- **Source:** [Kaggle – mashlyn/online-retail-ii-uci](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci)
- **Data Description:** Invoice-level retail transactions with fields such as InvoiceNo, Description, Quantity, and Country.
- **Preprocessing Steps:**
  - Removed canceled transactions (InvoiceNo starting with `C`).
  - Kept only positive quantities.
  - Filtered to the **top 100 most frequent items** for computational efficiency.
  - Sampled **50,000 rows** for faster execution.

---

## **Steps Implemented**
### **1. Association Rule Mining**
- **Apriori:** Extracted frequent itemsets using a minimum support of 2%.
- **FP-Growth:** Applied with the same threshold for comparison.
- **Association Rules:** Generated rules with support, confidence, and lift, then visualized confidence vs. lift.

### **2. Clustering**
- **Hierarchical Clustering:**
  - Created dendrograms to identify natural breaks (suggesting ~3 clusters).
  - Used Agglomerative Clustering with `n_clusters=3`.
  - Visualized clusters using PCA for dimensionality reduction.
- **DBSCAN:**
  - Performed density-based clustering with tuned `eps` and `min_samples`.
  - Detected noise and arbitrarily shaped clusters.

---

## **Analysis and Insights**

### **1. Hierarchical Clustering**
- The dendrogram suggests a natural break around **3 clusters**.
- Agglomerative clustering provided interpretable groupings when `n_clusters=3`.
- PCA visualization showed well-separated clusters.

### **2. DBSCAN**
- DBSCAN identified **noise points** and formed clusters based on density.
- Performance was sensitive to **`eps` and `min_samples`** parameters.
- Certain parameter values led to a single cluster or excessive noise, lowering metrics.

### **3. Comparison**

| **Method**                     | **Silhouette** | **Homogeneity** | **Completeness** |
|--------------------------------|----------------|-----------------|------------------|
| Hierarchical (n=3)             | ~0.28          | ~0.85           | ~0.88            |
| DBSCAN (eps=1.0, min_samples=5)| ~0.24          | ~0.65           | ~0.60            |

- **Strengths:**
  - **Hierarchical:** Clear hierarchical structure and visual dendrogram.
  - **DBSCAN:** Handles noise and non-linear cluster shapes.
- **Weaknesses:**
  - **Hierarchical:** Sensitive to scaling of features.
  - **DBSCAN:** Requires careful tuning of parameters (`eps`, `min_samples`).

---

## **Key Results**
- **Apriori vs FP-Growth:** FP-Growth was faster, producing similar frequent itemsets with less runtime.
- **Top Rules:** Example – `{GIFT BAG}` → `{GREETING CARD}` (support=0.03, confidence=0.62, lift=2.1).
- **Clustering:** Hierarchical clustering yielded better Silhouette, homogeneity, and completeness metrics compared to DBSCAN.

---

## **Challenges**
- Large dataset size caused memory issues; resolved by:
  - Sampling 50,000 rows.
  - Limiting to the top 100 items for one-hot encoding.
- DBSCAN parameter tuning required trial and error.
- Scaling was necessary for hierarchical clustering to achieve better performance.

---

## **Technologies Used**
- **Python 3.x**
- **Jupyter Notebook**
- **Libraries:** pandas, numpy, seaborn, matplotlib, scikit-learn, mlxtend

