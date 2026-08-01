# 💳 Customer Segmentation — Credit Card

> Segmenting 850 credit card customers into distinct behavioral profiles using KMeans clustering to help a credit card company tailor its marketing strategy.

---

## 📋 Project Overview

This project applies **unsupervised machine learning** (KMeans clustering) to segment credit card customers based on demographic and financial behavior. The goal is to identify distinct customer groups that a credit card company can target with tailored marketing strategies.

The project covers the full clustering pipeline: data cleaning, feature scaling, optimal K selection via Elbow Plot and Silhouette Score, cluster profiling, PCA visualization, and actionable business recommendations per segment.

---

## 📊 Dataset

| Property | Value |
|---|---|
| Records | 850 customers |
| Features | 8 (after dropping ID columns) |
| Missing Values | 150 in `Defaulted` → filled with median |
| Target | None (unsupervised) |

**Features:**

| Feature | Description |
|---|---|
| `Age` | Customer age |
| `Edu` | Education level (encoded) |
| `Years Employed` | Years of employment history |
| `Income` | Annual income (thousands) |
| `Card Debt` | Credit card debt (thousands) |
| `Other Debt` | Other debt obligations (thousands) |
| `Defaulted` | Whether the customer has defaulted (0/1) |
| `DebtIncomeRatio` | Debt-to-income ratio |

---

## 🔧 Pipeline

### 1. Data Cleaning
- Dropped non-informative columns: `Unnamed: 0`, `Customer Id`
- Imputed 150 missing values in `Defaulted` with **median** (0.0)
- Confirmed: **0 null values** after cleaning

### 2. Feature Scaling
- Applied `StandardScaler` to all 8 features before clustering
- Essential for KMeans — prevents features with larger ranges from dominating distance calculations

### 3. Optimal K Selection
- Tested K = 2 to 10 using:
  - **Elbow Plot** (Inertia) — sharp drop from K=2 to K=3, then flattens
  - **Silhouette Score** — measures cluster separation quality

**Chosen K = 3** because:
- The Elbow Plot shows the classic "elbow" at K=3
- K=2 produces only two broad groups with limited business value
- K=3 creates three distinct, actionable customer profiles ideal for marketing strategy

### 4. Final Model
- `KMeans(n_clusters=3, random_state=42)`
- Cluster labels assigned to each customer

---

## 👥 Cluster Profiles

| Feature | Cluster 0 | Cluster 1 | Cluster 2 |
|---|---|---|---|
| **Count** | 304 customers | 393 customers | 153 customers |
| **Age** | 33.83 | 31.89 | 43.09 |
| **Years Employed** | 7.65 | 3.96 | 17.22 |
| **Income** | $36.18K | $31.79K | $102.72K |
| **Card Debt** | $0.86K | $1.58K | $4.23K |
| **Other Debt** | $1.82K | $2.84K | $8.02K |
| **Default Rate** | **0%** | **99%** | **13%** |
| **DebtIncomeRatio** | 7.99 | 13.99 | 13.92 |

---

## 🔍 Cluster Descriptions

### 🟢 Cluster 0 — "Young & Cautious" (n=304)
The **largest segment** — younger to middle-aged customers (avg age 33.83) with moderate employment (7.65 years) and mid-range income ($36.18K). They carry **very low debt** and have a **0% default rate**. These customers are financially responsible and conservative with credit — representing untapped potential.

**Key Insight:** This group is reliable but currently underusing credit products. They have room to safely grow their credit usage — making them ideal candidates for upgrades and new product offerings.

---

### 🔴 Cluster 1 — "Young & High-Risk" (n=393)
The **largest by count** — young customers (avg age 31.89) with very short employment histories (3.96 years) and the lowest income ($31.79K). Their debt-to-income ratio is high (~14) and nearly **99% have defaulted**. These customers are early in their careers and have taken on more credit than their income can support.

**Key Insight:** This group is not necessarily irresponsible — they are simply young and financially overwhelmed. They need structured support, not rejection.

---

### 🔵 Cluster 2 — "Established & Stable" (n=153)
**Mature, financially established** customers — oldest group (avg age 43.09), longest employment (17.22 years), and by far the **highest income ($102.72K)**. They carry the most debt ($4.23K card, $8.02K other), but their income absorbs it. Default rate is only **13%**.

**Key Insight:** Despite the highest debt levels, this group manages it well. They likely hold multiple credit products and are high spenders — the premium customer segment.

---

## 💡 Recommendations for the Credit Card Company

### Recommendation 1: Differentiate Product Offerings by Cluster
- **Cluster 2 (Established & Stable):** Offer **premium rewards cards** with high credit limits, travel perks, and exclusive benefits. These customers have the income and stability to support premium products.
- **Cluster 0 (Young & Cautious):** Target with **credit-limit upgrade offers** and **cash-back or entry-level rewards cards**. Zero defaults and low debt make them low-risk candidates to expand.

### Recommendation 2: Build a Risk-Aware Recovery Strategy for Cluster 1
**Cluster 1** should not be offered new high-limit cards — but they should not be abandoned either. The company should proactively offer **debt restructuring plans, financial literacy resources, and lower-APR options** to help these customers recover. Retaining a recovering customer is far cheaper than acquiring a new one.

---

## 🛠 Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| Pandas & NumPy | Data manipulation |
| Matplotlib & Seaborn | Visualizations |
| Scikit-learn | KMeans, StandardScaler, Silhouette Score |
| Google Colab | Development environment |

---

## 📁 Project Structure

```
Customer-Segmentation-Credit-Card/
│
├── KMeans_Customer_Segmentation.ipynb    # Main notebook
└── README.md
```

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/Dounia-Nassar/Customer-Segmentation-Credit-Card
cd Customer-Segmentation-Credit-Card

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# Open the notebook
jupyter notebook KMeans_Customer_Segmentation.ipynb
```

---

## 👩‍💻 Author

**Dounia Nassar**
- 📧 dounia.nassar@outlook.com
