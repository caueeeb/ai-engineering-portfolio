# AI Engineering Portfolio

A curated portfolio of my projects in **Machine Learning, data science, and AI engineering**.

I am a Systems Analysis and Development (ADS) student at Fatec Taquaritinga, interested in building practical ML solutions, evaluating model reliability, and developing software around machine learning models.

## Featured projects

### 1. Delivery Delay Prediction — Brazilian E-Commerce (Olist)

[**Repository: delivery-prediction-ml**](https://github.com/caueeeb/delivery-prediction-ml)

A supervised classification project using the Brazilian E-Commerce Public Dataset by Olist. The analysis base contains 96,470 delivered orders and 26 engineered predictors.

**Highlights**
- Integrated order, customer, product, seller, and payment data.
- Built order-level features and chronological training, validation, and test partitions.
- Compared classifiers and selected a Logistic Regression pipeline.
- Exposed predictions through a FastAPI service with `/health`, `/model-info`, and `/predict` endpoints.
- Added automated tests; the project test suite passed 13 tests.

**Final chronological test results**

| Metric | Result |
|---|---:|
| Accuracy | 84.50% |
| Precision | 6.73% |
| Recall | 26.71% |
| F1-score | 10.75% |
| Average Precision | 0.0716 |

The final evaluation exposed limitations under temporal distribution changes. The model is a retrospective educational experiment, not a validated production system.

**Research extension:** [Temporal Distribution Shift study](https://github.com/caueeeb/delivery-prediction-ml/tree/main/research)

**Technical article:** [When Machine Learning Models Meet Temporal Distribution Shift](https://github.com/caueeeb/delivery-prediction-ml/blob/main/research/ARTICLE_TEMPORAL_DISTRIBUTION_SHIFT.md.md)

### 2. Titanic Survival Prediction — Kaggle

[**Repository: kaggle-titanic**](https://github.com/caueeeb/kaggle-titanic)

A binary classification project for the Kaggle *Titanic — Machine Learning from Disaster* competition.

**Highlights**
- Exploratory data analysis and feature engineering.
- Engineered `FamilySize`, `IsAlone`, `HasCabin`, and `Title` features.
- Built a scikit-learn preprocessing and Logistic Regression pipeline.
- Compared four classifiers and generated a Kaggle submission.

**Results**
- Local validation accuracy: **83.24%**.
- Kaggle public leaderboard score: **0.77033**.
- Predictions submitted: **418 passengers**.

### 3. Published model — Hugging Face

[**Titanic Survival Logistic Regression**](https://huggingface.co/caueeb/titanic-survival-logistic-regression)

The trained scikit-learn pipeline is published on Hugging Face with a Model Card, dependencies, and an inference example. A local inference test successfully loaded the artifact and returned a prediction.

## Research and technical writing

### Temporal Distribution Shift in E-commerce Delivery Prediction

An empirical study of feature-distribution changes, target prevalence, monthly model performance, classification errors, and probability diagnostics in the Olist project.

The study distinguishes observed feature and target distribution changes from strict concept drift. The experiments do not establish a causal explanation or prove that the conditional relationship between features and target changed.

- [Research notebook, protocol, reports, and discussion](https://github.com/caueeeb/delivery-prediction-ml/tree/main/research)
- [Technical article](https://github.com/caueeeb/delivery-prediction-ml/blob/main/research/ARTICLE_TEMPORAL_DISTRIBUTION_SHIFT.md.md)

## Technical skills

| Area | Tools and concepts |
|---|---|
| Programming | Python, SQL, C |
| Data analysis | pandas, NumPy, Jupyter |
| Machine Learning | scikit-learn, classification, feature engineering, model evaluation |
| Model evaluation | Precision, recall, F1-score, Average Precision, confusion matrices, Brier score, temporal validation |
| APIs and testing | FastAPI, REST, pytest |
| Development tools | Git, GitHub, VS Code |
| Model sharing | Hugging Face Hub |

## Current learning goals

- Build and evaluate reliable machine learning systems.
- Improve model monitoring and evaluation under changing data distributions.
- Develop practical AI applications with clear documentation and reproducible workflows.

---

*This portfolio is continuously evolving as I build, test, document, and publish new projects.*
