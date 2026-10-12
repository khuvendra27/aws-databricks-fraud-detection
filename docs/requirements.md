# Fraud Detection Platform — Project Requirements

## 1. Project Overview

Build an end-to-end fraud detection data platform using Python, PySpark, Databricks, Delta Lake, and cloud storage. The platform will process synthetic financial transactions, prepare reliable analytical datasets, train fraud detection models, and produce risk scores for transactions.

The initial implementation will prioritize batch processing. Near-real-time streaming will be introduced after the batch pipeline is tested and validated.

## 2. Business Problem

Financial institutions need to identify potentially fraudulent transactions among legitimate transactions. Fraud is typically rare, and missing fraudulent transactions can be costly. However, flagging too many legitimate transactions also creates unnecessary investigation work.

This project will demonstrate how reliable data engineering and machine learning can support fraud investigation.

This is a portfolio project using synthetic data, not a production banking system.

## 3. Project Objectives

- Build a reproducible transaction data pipeline.
- Implement Bronze, Silver, and Gold data layers using Delta Lake where supported.
- Validate, clean, and transform transaction data with PySpark.
- Engineer transaction and customer behavioral features.
- Train and compare multiple fraud classification models.
- Track experiments and metrics with MLflow where available.
- Produce fraud predictions and analytical summaries.
- Add automated tests, documentation, and version control.
- Introduce streaming after the batch implementation is validated.
- Keep cloud expenditure within an explicitly reviewed budget.

## 4. Technology Stack

- Language: Python
- Data processing: PySpark
- Lakehouse storage: Delta Lake
- Development platform: Databricks Free Edition, subject to feature limits
- Cloud: AWS, subject to account eligibility and cost review
- Machine learning: scikit-learn and XGBoost, subject to environment compatibility
- Experiment tracking: MLflow
- Version control: Git and GitHub
- Project tracking: Jira
- Testing: pytest
- Documentation: Markdown

The implementation may use local alternatives when a cloud service or Databricks feature is unavailable without paid resources.

## 5. Functional Requirements

### FR-01: Synthetic Transaction Data

Generate reproducible synthetic transaction data containing transaction identifiers, customer identifiers, timestamps, amounts, merchant categories, payment methods, and fraud labels.

### FR-02: Data Validation

Validate required fields, data types, transaction identifiers, timestamps, amounts, and duplicate records. Record rejected or invalid records for investigation.

### FR-03: Bronze Layer

Store raw transaction records with sufficient metadata to support traceability and replay.

### FR-04: Silver Layer

Clean and standardize transaction records, handle invalid data according to documented rules, and enforce data quality checks.

### FR-05: Gold Layer

Produce analytical tables and model-ready datasets for fraud analysis.

### FR-06: Feature Engineering

Create useful transaction-level and customer-behavior features without using information that would not have been available at prediction time.

### FR-07: Model Training

Train a baseline Logistic Regression model and compare it with Random Forest and XGBoost where feasible.

### FR-08: Model Evaluation

Report precision, recall, F1-score, PR-AUC, ROC-AUC, and a confusion matrix. Use a time-aware train/test split where appropriate and avoid data leakage.

### FR-09: Fraud Predictions

Produce a fraud probability or risk score and a configurable alert flag for each scored transaction.

### FR-10: Experiment Tracking

Record model parameters, evaluation metrics, and relevant artifacts in MLflow where supported.

### FR-11: Batch Execution

Make the initial pipeline repeatable and capable of processing a defined batch of transactions.

### FR-12: Streaming Extension

After the batch pipeline is validated, implement near-real-time ingestion and scoring if the selected platform supports it within the cost constraints.

### FR-13: Testing

Create automated tests for data validation, transformation logic, feature generation, and model evaluation.

### FR-14: Documentation

Document setup instructions, architecture, data definitions, model methodology, limitations, and execution procedures.

## 6. Non-Functional Requirements

- Reproducibility: use fixed random seeds where applicable.
- Maintainability: organize code into logical modules with clear responsibilities.
- Data quality: report validation failures and preserve traceability.
- Security: never commit credentials, tokens, or sensitive data.
- Cost control: review cloud pricing before provisioning resources.
- Testability: separate transformation and model logic so it can be tested independently.
- Observability: record execution status, processed record counts, errors, and model metrics.
- Responsible interpretation: model scores indicate risk, not proof of fraud.

## 7. Initial Success Criteria

The following are targets to verify, not claims of achieved results.

- The batch pipeline runs reproducibly from documented instructions.
- Bronze, Silver, and Gold outputs are created and validated.
- Duplicate transaction identifiers and invalid required fields are detected and handled according to documented rules.
- Data splitting and feature engineering avoid target leakage.
- At least two feasible models are compared using the same evaluation approach.
- Precision, recall, F1, PR-AUC, ROC-AUC, and a confusion matrix are reported where applicable.
- Tests cover key transformation and validation rules.
- Model parameters and evaluation results are documented or tracked.
- The repository contains setup instructions and architecture documentation.
- Streaming is attempted only after batch processing is validated and its cost and feature requirements have been reviewed.

No fixed accuracy or recall target is guaranteed before the dataset and class distribution are examined.

## 8. Delivery Phases

### Phase 1 — Foundation
Requirements, architecture, Git workflow, Jira backlog, and cost safeguards.

### Phase 2 — Data Generation
Create a reproducible synthetic transaction dataset and data dictionary.

### Phase 3 — Batch Lakehouse
Implement Bronze, Silver, and Gold processing with Delta Lake.

### Phase 4 — Feature Engineering
Create leakage-safe model features.

### Phase 5 — Machine Learning
Train, compare, evaluate, and track fraud detection models.

### Phase 6 — Testing and Analytics
Add automated tests, analytical outputs, and monitoring.

### Phase 7 — Streaming Extension
Add event ingestion and near-real-time scoring if feasible.

### Phase 8 — Production Practices
Improve orchestration, CI/CD, documentation, and resource cleanup.

## 9. Scope Exclusions

The initial project will not process real customer or payment-card data, connect to a real banking system, execute transactions, or automatically block payments. Fraud predictions are for demonstration and investigation workflows only.

## 10. Cost and Security Constraints

- Prefer local development and Databricks Free Edition when practical.
- Do not assume AWS promotional credits cover every service.
- Do not provision resources until pricing and cleanup requirements are understood.
- Maintain billing alerts, while recognizing that alerts are not hard spending caps.
- Keep secrets out of source control and use synthetic data only.