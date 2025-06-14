# stock-predicting-nlp-model

# 🧠 Stock Prediction Using News Headlines

This project explores whether natural language processing (NLP) can be applied to predict stock price movements using daily news headlines. Built as part of an MBA data science capstone, it combines NLP techniques, various machine learning models, and financial reasoning to simulate stock-picking strategies.

[📊 Project Report (Presentation)](./Stock_Picking_Model_Presentation.pdf)

---

## 📌 Project Overview

- **Objective:** Predict whether a stock will go UP or DOWN based on the previous day's headlines.

## 📦 Dataset

Headline and stock price data from Kaggle:

- [News Headlines Dataset for S&P 500 Stocks](https://www.kaggle.com/datasets/miguelaenlle/massive-stock-news-analysis-db-for-nlpbacktests)
- [S&P 500 Stock Data](https://www.kaggle.com/datasets/mosesmoncy/ny-stock-exchange-size-dataset)

Date Range: **Jan 1, 2010 – Dec 31, 2016**


---

## 🧮 Methodology

### 🗂️ Preprocessing
- Lowercasing, stopword removal, punctuation removal, lemmatization.
- Excluded rows with missing headlines.
- Focused on daily predictions (not weekly, due to pricing lag).

### 🔠 NLP & Feature Engineering
- Headlines vectorized using **TF-IDF**.
- Experimental inclusion of quantitative indicators (e.g., volatility) found to be non-predictive.

---

## 🤖 Models & Techniques

Explored a range of supervised ML models:
- **Random Forest**
- **Logistic Regression**
- **XGBoost**
- **Support Vector Machine**
- **Neural Networks**
- **Stacked Ensemble** (Random Forest + NN base, Logistic Regression meta)

Also tested **BERT** and **ChatGPT (gpt-3.5-turbo)** with prompts to assess headline sentiment as a proxy for directional movement.

---

## 📈 Evaluation Strategy

While initial models had low classification accuracy (~50%), I reframed the problem:

> The goal is not to predict every movement correctly but to **confidently identify a subset of likely "UP" stocks** and assess their **cumulative returns**.

This prioritizes **recall** (True Positive Rate for UP) over precision or overall accuracy.

---

## 📊 Results Summary

| Model          | Accuracy | Precision (UP) | Recall (UP) | Notes                              |
|----------------|----------|----------------|-------------|------------------------------------|
| Random Forest  | 50.4%    | 0.513          | 0.584       | Base model one                     |
| CNN-LSTM       | 50.5%    | 0.514          | 0.573       | Faster training vs RF base         |
| Stacked        | 50.1%    | 0.512          | 0.552       | Underperformed vs both base models |
| GPT-3.5 Turbo  | 50.5%    | 0.4968         | 0.8000      | Prompt-based, low confidence       |

**Despite modest accuracy, the base models' high-recall predictions achieved cumulative returns that outpaced the S&P 500 in backtests.**

---

## 🔍 Future Work

- Incorporate **more context-aware NLP**, e.g., event modeling, earnings calls, SEC filings.
- Sector-specific modeling.
- Add valuation-based metrics alongside NLP.
- Use **larger and more recent** datasets.

---

### 📁 File Structure

```
project-root/
├── notebook/                             # Jupyter notebooks for EDA, modeling, evaluation
├── Stock_Picking_Model_Presentation.pdf  # 📊 Presentation with visuals & findings
├── README.md                             # You're here!
└── requirements.txt                      # Python dependencies
```
