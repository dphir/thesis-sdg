# Thesis Project: Synthetic Data Generation for GRC Audit

This repository contains the **as-is GRC data views, ETL preprocessing notebooks, and generated outputs** used to simulate fragmented data flows across the **Three Lines of Defense (3LOD). ****
These datasets represent the baseline condition **before** applying the synthetic data architecture proposed in the thesis.

## **1. Overview**

Large organizations often suffer from **data silos, restricted access, and fragmented reporting** across the Business (1st Line), risk and compliance (2nd Line), and Internal Audit (3rd Line).

This repository illustrates:

- How operational, risk, and audit data are **separated** in the AS-IS environment

- How each line receives a different **view** of the same organizational dataset

- How audits become slow, incomplete, and costly due to **limited data flows**

- The **baseline dataset** used to build the upcoming **Synthetic Data Twin**

This repository, therefore, serves as the foundation for evaluating a more efficient and privacy-preserving audit approach using synthetic data generation.

## **2. Repository Structure**
```
thesis-sdg/
│
├── data/
│   ├── raw/                         # Public or external raw input datasets
│   ├── processed/                   # ETL outputs and master tables
│   │   └── TRANSACTION_MASTER_FULL.csv
│   └── asis_views/                  # AS-IS GRC views & reports for 3 Lines of Defense
│       ├── ASIS_1ST_LINE_REPORT.csv
│       ├── ASIS_2ND_LINE_REPORT.csv
│       ├── ASIS_3RD_LINE_REPORT.csv
│       ├── ASIS_FIRST_LINE_VIEW.csv
│       ├── ASIS_SECOND_LINE_VIEW.csv
│       └── ASIS_THIRD_LINE_VIEW.csv
│
├── notebooks/
│   ├── 01_customer_data_upload.ipynb
│   ├── 02_transaction_data_upload.ipynb
│   └── 03_the_process_upload.ipynb
│
├── src/
│   ├── etl/                         # ETL scripts (optional future refactor)
│   ├── sdg/                         # Synthetic data generation modules (future)
│   └── utils/                       # Helper functions
│
├── docs/
│   ├── diagrams/                    # Architecture diagrams & thesis figures
│   └── thesis-outline.md            # Notes related to thesis structure
│
├── .gitignore
├── requirements.txt
└── README.md
```

## **3. File Descriptions**

These CSV files represent the AS-IS fragmented GRC environment.

| File Name                       | Description                                                                          |
| ------------------------------- | ------------------------------------------------------------------------------------ |
| **ASIS_1ST_LINE_REPORT.csv**    | Operational-level report used by Business / Operations / IT (1st Line).              |
| **ASIS_2ND_LINE_REPORT.csv**    | Risk & Compliance report containing alerts, scoring, and monitoring data (2nd Line). |
| **ASIS_3RD_LINE_REPORT.csv**    | Internal Audit report summarizing anomalies, gaps, and audit findings (3rd Line).    |
| **ASIS_FIRST_LINE_VIEW.csv**    | Data view accessible to the First Line (operational subset).                         |
| **ASIS_SECOND_LINE_VIEW.csv**   | Data view accessible to the Second Line (risk/compliance enriched subset).           |
| **ASIS_THIRD_LINE_VIEW.csv**    | Restricted data view accessible only to Internal Audit.                              |
| **TRANSACTION_MASTER_FULL.csv** | Full transaction master table generated from ETL preprocessing (baseline for SDG).   |


## **4. Jupyter Notebooks (ETL + Simulation Code)**

These notebooks generate and preprocess all datasets above.

| Notebook                          | Purpose                                                                                                  |
| --------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Customer_Data_upload.ipynb**    | Preprocessing of customer master data, cleaning, merging, formatting, and attribute engineering.         |
| **Transaction_Data_upload.ipynb** | ETL pipeline for transaction data, integration with customer profiles, and creation of the master table. |
| **The_Process_upload.ipynb**      | Simulation of AS-IS GRC data flows. Generates First/Second/Third Line *views* and *reports*.             |

## **5. Purpose of These Outputs**
The AS-IS datasets are essential for:
- Demonstrating data fragmentation in traditional GRC processes
- Showing how limited access impacts risk visibility and audit quality
- Providing a baseline scenario for comparison with the proposed synthetic data solution
- Feeding the next steps of the thesis:
  - Synthetic Data Generation (SDG)
  - Synthetic Twin Architecture
  - Privacy-Preserving Audit Simulation
 
## **6. Workflow Summary**

**Step 1 — Customer ETL**

- Parse customer data
- Clean & standardize fields
- Derive new attributes
- Save processed master

**Step 2 — Transaction ETL**

- Load transaction logs
- Merge with customer tables
- Add AML/risk-related derived features
- Export TRANSACTION_MASTER_FULL.csv

**Step 3 — AS-IS GRC Simulation**

- Split the master dataset by 3LOD roles
- Generate line-specific views & reports
- Demonstrate siloed information flow

## **7. Privacy Notes**

- All datasets in this repository are **synthetically generated or derived from public sources.**
- No real customer or transaction information is included.
- These files are intended exclusively for academic research and demonstration purposes.
