# Barclays Bank Customer Churn Analysis

An end-to-end data science project that analyses customer churn at Barclays Bank, identifies the factors behind customers leaving, and prepares the data for machine learning models that can **predict future churn** so management can act early.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/152VVV7rd-_2HQxgw38mEX8xwUF_pZps1)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Status](https://img.shields.io/badge/status-in%20progress-orange)

---

## 📌 Problem Statement

Barclays is facing a high customer churn rate: customers stop using the bank's services. Previously, the bank did not get timely insights and decisions were delayed, and the methods in use were outdated. This increased churn.

The bank now needs **live analysis and corrective measures** to:

- Understand *why* customers are leaving
- Give management timely, data-backed insights for decision making
- Predict future churn so retention actions can be taken in advance

##  Objectives

1. Combine the bank's customer, account, geography and gender data into one analysis-ready dataset.
2. Explore churn patterns across time, geography, gender and tenure.
3. Engineer features suitable for machine learning.
4. Build and compare classification models to predict churn.
5. Turn findings into insights and recommendations for management.

## Dataset

The data is loaded directly from a public GitHub repository ([`ankitmisk/PowerBI-Dataset`](https://github.com/ankitmisk/PowerBI-Dataset), folder *Barclays Customer Churn Analysis PowerBI Report*), so no manual download is needed.

| File | Description |
|------|-------------|
| `Bank_Churn.csv` | Core account/churn data (~10,000 rows, 14 columns), including the `Exited` target |
| `CustomerInfo.csv` | Customer details (surname, geography and gender IDs, bank joining date) |
| `Geography.xlsx` | Lookup table for geography (France, Spain, Germany) |
| `Gender.xlsx` | Lookup table for gender |
| `ActiveCustomer.xlsx` | Active customer lookup |
| `CreditCard.xlsx` | Credit card lookup |
| `ExitCustomer.xlsx` | Exit customer lookup |

The main tables are merged on `CustomerId`, `GeographyID` and `GenderID` to build a single `final_df`.

> **Note:** Please check the license/terms of the source repository before reusing or redistributing the data.

##  Tech Stack

- **Language:** Python
- **Data handling:** `pandas`, `numpy`
- **Visualisation:** `matplotlib`, `seaborn`
- **Machine learning:** `scikit-learn` (Logistic Regression, SVM, Decision Tree, Random Forest, KNN, Gradient Boosting, AdaBoost)
- **Environment:** Google Colab / Jupyter Notebook

##  Workflow

### Step 1: Load modules
Import all required libraries.

### Step 2: Load datasets
Read the 7 source files (CSV and Excel) from GitHub into DataFrames.

### Step 3: Exploratory Data Analysis (EDA)
- Shape, info and descriptive statistics (numerical and categorical)
- Missing value handling
- Correlation matrix and heatmap
- Convert `Bank DOJ` (date of joining) to datetime
- Drop unneeded columns (`RowNumber`)
- **Univariate analysis** of categorical columns
- **Bivariate analysis** of churn by:
  - Bank date of joining (trend over time)
  - Month
  - Day of week
  - Gender
  - Geography
  - Tenure

### Step 4: Feature engineering
Convert text columns to numbers so models can use them:
- `Month` → 0–11
- `GenderCategory` → Male = 0, Female = 1
- `GeographyLocation` → France = 0, Spain = 1, Germany = 2
- Check correlation of each feature with the target (`Exited`)

### Step 5: Features vs target
Split into `X` (features) and `y` (`Exited`).

### Step 6: Train/test split
80/20 split with `random_state=42`.

## Current Status & Roadmap

- [x] Data loading and merging
- [x] EDA and visualisation
- [x] Feature engineering
- [x] Train/test split
- [ ] Train and compare classification models
- [ ] Evaluate with accuracy, recall, confusion matrix and classification report
- [ ] Save the best model (`pickle`)
- [ ] What-if and root-cause analysis
- [ ] Final report and recommendations for management

## How to Run

**Option 1: Google Colab (easiest)**
Click the **Open in Colab** badge at the top and run all cells.

**Option 2: Locally**

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

# 2. (Optional) create a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter

# 4. Launch the notebook
jupyter notebook
```

An internet connection is required because the datasets are read from GitHub URLs.

> The script uses `display()` and `IPython`, which work best in Colab or Jupyter. If running as a plain `.py` file, replace `display(...)` with `print(...)`.

## Repository Structure

```
├── barclays_bank_churn_analysis.py   # Main analysis script (Colab export)
├── images/                           # Project images (optional)
└── README.md
```

## Contributing

Suggestions and improvements are welcome. Feel free to open an issue or submit a pull request.
# Acknowledgement 

- Datasets from [`ankitmisk/PowerBI-Dataset`](https://github.com/ankitmisk/PowerBI-Dataset)

##  Author

**Your Name**
[LinkedIn](https://www.linkedin.com/in/your-profile) · [GitHub](https://github.com/your-username)
