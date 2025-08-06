# 📊 Decoding hidden patterns

This project explores unsupervised clustering techniques applied to [challenge dataset]([آدرس لینک](https://github.com/zall-e/ML_rahnemacollege/blob/main/challenge.txt)). The analysis includes data preprocessing, dimensionality reduction, cluster evaluation, and outlier detection.

---

## 📌 Overview

The goal of this project is to identify meaningful clusters in the data using unsupervised learning methods and analyze the stability and characteristics of these clusters.

---

## ⚙️ Preprocessing

- Initial clustering was performed on **raw data**, but later it was found that **standardizing the features** significantly improves performance and fairness in clustering.
- File `college_register_old` contains the version without standardization.

---

## 📉 Dimensionality Reduction (PCA)

- **PCA** was used to reduce dimensionality and visualize clusters.
- On standardized data, the first 2 components explained ~**70%** of the total variance.
- On non-standardized data, this value was over **90%**, but misleading due to scale imbalance.

---

## 📊 Feature Distribution Analysis

- Among the 10 features:
  - The **first 3 features** had **non-normal and dispersed distributions**.
  - The **remaining 7 features** showed **normal and concentrated** distributions.

---

## 🔗 Correlation Matrix

- The **first 4 features** showed **low correlation** with others — possibly containing **unique or complementary information**.
- The **remaining 8 features** had **high inter-correlation** (close to 1), suggesting **redundancy** — and many of them were sparsely filled (mostly zeros).

---

## 🧩 Clustering Results

Clustering was performed using three algorithms:

- **KMeans**
- **DBSCAN**
- **Agglomerative Clustering**

📈 The optimal number of clusters determined was **3**, using **Silhouette Score** as the evaluation metric.

| Algorithm       | Silhouette Score |
|----------------|------------------|
| KMeans          | 0.566            |
| DBSCAN          | 0.566            |
| Agglomerative   | 0.566            |

📝 Since all three algorithms performed similarly, none could be distinctly preferred over the others based solely on silhouette score.

---

## 🚨 Outlier Detection

- Applied **Isolation Forest** to detect and remove outliers prior to final clustering.
- Helped reduce noise and improved clustering reliability.

---

## ✅ Cluster Stability Analysis

- Conducted **bootstrapping** to assess clustering stability.
- Used **Adjusted Rand Index (ARI)** to measure consistency across different bootstrap samples.

```text
Mean ARI:      0.840
ARI Std Dev:   0.271
