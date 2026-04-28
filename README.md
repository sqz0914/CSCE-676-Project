# Next-Basket Recommendation from Retail Purchase History

🎥 **Project Video:** [Youtube Link](https://www.youtube.com/watch?v=IxA1DNQq5LU)

👉 **Main deliverable:** `notebooks/main_notebook.ipynb`

## Overview

This project studied whether time-ordered purchase patterns improved next-basket recommendation beyond simpler basket-based methods. Using the Online Retail dataset, we compared four recommenders with increasing levels of structure: a popularity baseline, an association-rule recommender, a sequential recommender, and a hybrid sequential-plus-embedding recommender. The main finding was that time order improved recommendation beyond global popularity and basket rules, and a small embedding-based reranking step improved the sequential recommender slightly further.

## Research Questions

- **Main question:** Can time-ordered purchase patterns improve next-basket recommendation beyond popularity-based and basket-based methods?
- **Extension question:** Can item embeddings improve a sequential recommender by reranking its candidate next items?

## Results Summary
The main result was a clear progression across methods: popularity performed worst, association rules improved on popularity, sequential recommendation improved further, and the hybrid sequential-plus-embedding model performed best overall. This means basket structure helped, but time order helped more, and embeddings were most useful when they supported the sequential model rather than replaced it.

## Data

### Dataset
- **Online Retail dataset**
- File used in this project: `data/Online Retail.xlsx`

### What the data contains
The dataset records retail transactions at the line-item level. Each row includes fields such as:
- `InvoiceNo`
- `StockCode`
- `Description`
- `Quantity`
- `InvoiceDate`
- `UnitPrice`
- `CustomerID`
- `Country`

### Preprocessing
The notebook created a purchase-only dataset by:
- removing cancellations, identified by `InvoiceNo` starting with `C`
- keeping only rows with `Quantity > 0`
- keeping only rows with `UnitPrice > 0`
- dropping rows with missing key fields such as `InvoiceNo`, `StockCode`, or `InvoiceDate`
- converting invoice-level rows into basket-based transactions
- building customer-level purchase histories for the sequential methods

## How to Reproduce This Work

This project was built in **Google Colab**.

### Steps
1. Open `main_notebook.ipynb`
2. Make sure `Online Retail.xlsx` is available in the same working directory, or upload it to Colab
3. Run the notebook from top to bottom

### Notes
- The notebook is the main curated deliverable and contains the full workflow:
  - data loading
  - preprocessing
  - train-test split
  - popularity recommender
  - association-rule recommender
  - sequential recommender
  - hybrid sequential-plus-embedding recommender
  - comparison and final conclusions

## Key Dependencies and Versions

Main packages used in this project:

- `python 3.12.13`
- `pandas 2.2.2`
- `numpy 2.0.2`
- `matplotlib 3.10.0`
- `gensim 4.4.0`

The full dependency list is in `requirements.txt`.

## Repo Structure

```text
project-root/
├── README.md
├── requirements.txt
├── main_notebook.ipynb
├── Online Retail.xlsx
├── notebooks/
    ├── main_notebook.ipynb
    ├── checkpoint1_notebook.ipynb
    └── checkpoint2_notebook.ipynb

