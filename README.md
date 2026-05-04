📘 Databricks Data Engineering Project

End-to-End Data Pipeline using Databricks, AWS S3 & PySpark

📖 Overview

This repository contains a Databricks notebook-based data engineering project for FMCG analytics. The notebooks are organized by setup, dimension processing, and fact processing.

🏗️ Architecture

Flow:
Landing (S3) → Raw Layer → Transform (Databricks) → Refined Layer → Outbound

Landing Layer: Raw files ingested from source systems
Raw Layer: Immutable storage of source data
Refined Layer: Cleaned and transformed data
Outbound Layer: Business-ready data for reporting

⚙️ Tech Stack

- Databricks
- Apache Spark / PySpark
- AWS S3
- Delta Lake
- SQL

📂 Project Structure
project/
├── dashboarding/
│ └── denormalise_table_query_fmcg.txt
├── notebooks/
│ ├── 1_setup/
│ │ ├── dim_date_table_creation.ipynb
│ │ ├── setup_catalog.ipynb
│ │ └── utilities.ipynb
│ ├── 2_dimension_data_processing/
│ │ ├── 1_customers_data_processing.ipynb
│ │ ├── 2_products_data_processing.ipynb
│ │ └── 3_pricing_data_processing.ipynb
│ └── 3_fact_data_processing/
│ ├── 1_full_load_fact.ipynb
│ └── 2_incremental_load_fact.ipynb
└── resource/
└── databricks_project.excalidraw

🔄 Notebook Deployment
The GitHub Actions workflow deploys notebook changes in `project/notebooks/` to your Databricks workspace when changes are pushed to `main`.

Required repository secrets:

- `DATABRICKS_HOST` — Your Databricks workspace URL, e.g. `https://adb-123456789012345.10.azuredatabricks.net`
- `DATABRICKS_TOKEN` — A Databricks personal access token with workspace import permissions
- `DATABRICKS_WORKSPACE_PATH` — Destination path in Databricks, e.g. `/Users/<your-user>/databricks-de-fmcg-atlikon-project`

📁 Workflow file:
`.github/workflows/deploy-notebooks-to-databricks.yml`

🚀 How it works

1. `actions/checkout` checks out the repo.
2. Python and `databricks-cli` are installed.
3. All files under `project/notebooks/` are imported into the target Databricks workspace path.
4. Existing notebooks are overwritten.

🛠️ Usage

- Add the required GitHub secrets in your repository settings.
- Push notebook changes to the `main` branch.
- The workflow runs automatically and uploads the updated notebooks.

📌 Notes

- This workflow is optimized for Databricks notebook deployment and current `.ipynb` files.
- If your workspace path or notebook format changes, update `DATABRICKS_WORKSPACE_PATH` or the workflow accordingly.
