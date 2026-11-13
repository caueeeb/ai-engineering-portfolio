# AI Engineering Portfolio

Index of my machine learning and AI engineering projects, with the problem, the stack, the key result and what each result does and does not show.

I am **Cauê Buzolin**, a second-semester Analysis and Systems Development student at Fatec Taquaritinga (Brazil), building practical ML projects with a focus on honest evaluation and clean engineering around the model.

[GitHub](https://github.com/caueeeb) · [LinkedIn](https://www.linkedin.com/in/cau%C3%AA-buzolin-76a4283b3/) · [Hugging Face](https://huggingface.co/caueeb)

> **Resumo (PT-BR):** portfólio de projetos de Machine Learning e AI Engineering. O projeto principal prevê atrasos de entrega no e-commerce (Olist) com avaliação cronológica, API FastAPI, testes, Docker e CI, além de um estudo sobre mudança de distribuição ao longo do tempo. Os resultados são sempre apresentados com a linha de base e as limitações.

## Projects at a glance

| Project | Problem | Stack | Headline result | Links |
|---|---|---|---|---|
| **Delivery Delay Prediction** | Predict whether an e-commerce order is delivered after the estimated date (96,470 orders, 26 features) | Python, pandas, scikit-learn, FastAPI, pytest, Docker, GitHub Actions | Test AP 0.072 vs. 0.035 chance level (about 2×); ROC-AUC 0.70; random splits would have doubled the apparent AP and F1 | [Code](https://github.com/caueeeb/delivery-prediction-ml) · [Research](https://github.com/caueeeb/delivery-prediction-ml/tree/main/research) · [Article](https://github.com/caueeeb/delivery-prediction-ml/blob/main/research/ARTICLE_TEMPORAL_DISTRIBUTION_SHIFT.md) |
| **Titanic Survival** | Kaggle binary classification with 891 labeled passengers | Python, pandas, scikit-learn, pytest | Kaggle public score 0.77033; holdout accuracy 83.24%; extra features and models gave no gain beyond noise | [Code](https://github.com/caueeeb/kaggle-titanic) · [Model on Hugging Face](https://huggingface.co/caueeb/titanic-survival-logistic-regression) |

## 1. Delivery Delay Prediction (Olist)

[**delivery-prediction-ml**](https://github.com/caueeeb/delivery-prediction-ml)

A supervised classification project on the Brazilian E-Commerce Public Dataset by Olist, covering the path from raw tables to a served model.

- Integrated orders, customers, items, products, payments and sellers into one row per delivered order, with chronological train / validation / test partitions.
- Selected a Logistic Regression pipeline, chose the threshold on validation only and evaluated the test set once.
- `python -m src.train` rebuilds the committed model from raw data; retraining reproduces its coefficients and metrics.
- FastAPI service (`/health`, `/model-info`, `/predict`) driven by the model and its metadata, with input validation.
- 22 automated tests (preprocessing, end-to-end training on synthetic tables, API, model/metadata consistency), Ruff, Dockerfile and a CI workflow.

**Test results (chronological split, threshold 0.15)**

| Metric | Result |
|---|---:|
| Average Precision | 0.0716 (chance level: 0.0349, lift 2.05×) |
| ROC-AUC | 0.699 |
| Precision / Recall | 6.7% / 26.7% |
| F1-score | 0.1075 |

An all-"on time" classifier would reach 96.5% accuracy on this test set, so accuracy is not the metric to read. The model has modest ranking signal and over-confident probabilities in later months. It is a retrospective educational experiment, not a validated production system.

## 2. Temporal distribution shift study

[**research/**](https://github.com/caueeeb/delivery-prediction-ml/tree/main/research) · [**Technical article**](https://github.com/caueeeb/delivery-prediction-ml/blob/main/research/ARTICLE_TEMPORAL_DISTRIBUTION_SHIFT.md)

Why did metrics fall between validation and test? The late-delivery rate dropped from 7.82% in training to 3.49% in test, and freight and delivery-window distributions changed. The study measures feature and target drift, monthly performance, false alerts, calibration and Brier score, and compares random with chronological evaluation.

Main takeaway: random splits would have reported about twice the absolute AP and F1, while ROC-AUC (about 0.70) and AP lift (about 2×) were similar. Much of the drop is consistent with the change in late-delivery prevalence rather than a clear loss of ranking ability. The study does not identify causes or prove strict concept drift.

## 3. Titanic survival prediction (Kaggle)

[**kaggle-titanic**](https://github.com/caueeeb/kaggle-titanic) · [**Hugging Face model**](https://huggingface.co/caueeb/titanic-survival-logistic-regression)

- Exploratory analysis, engineered features (`FamilySize`, `IsAlone`, `HasCabin`, `Title`) and a scikit-learn preprocessing + Logistic Regression pipeline.
- Compared four classifiers with stratified cross-validation; Kaggle public score **0.77033**, local holdout accuracy **83.24%**.
- Code organized in tested modules; `python -m src.train` regenerates the submission exactly.
- Extra features and models were tested with repeated cross-validation; differences were within noise, so the baseline was kept.
- The pipeline is published on Hugging Face with a model card and an inference script.

## Skills used in these projects

| Area | Tools and concepts |
|---|---|
| Programming | Python, SQL/MySQL, C |
| Data and ML | pandas, NumPy, scikit-learn, feature engineering, imbalanced classification, permutation importance |
| Evaluation | Temporal validation, Average Precision and lift over baseline, ROC-AUC, precision/recall/F1, calibration, Brier score, drift metrics (PSI, KS) |
| Software engineering | FastAPI, Pydantic, pytest, Ruff, Docker, GitHub Actions, Git and GitHub |
| Sharing | Hugging Face Hub, technical writing |

## What I am working on next

- Improving the delivery model with seller–customer distance and seller history computed only from past deliveries, plus validation-based probability calibration.
- Building a first LLM-based application with an evaluation set, to move from classical ML toward generative AI engineering.

## Principles

1. Compare every result with a simple baseline and report it next to the metric.
2. Choose thresholds and models on validation data; touch the test set once.
3. State limitations next to the results, not at the end.
4. Make the work reproducible: pinned dependencies, one command to retrain, tests that check the claims.
