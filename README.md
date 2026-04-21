#  NovaCart Lakehouse Data Engineering Project

##  Overview

This project demonstrates an end-to-end **data engineering pipeline** for a fictional e-commerce platform, **NovaCart**. It showcases how to transform raw operational data into meaningful business insights using a modern **Lakehouse architecture**.

The pipeline is built using **Azure Databricks**, **Delta Lake**, and **Azure SQL Database**, following real-world best practices like incremental processing, orchestration, and monitoring.

---

## Case Study

The system generates data across:
* Products
* Orders
* Payments

This data is continuously evolving:
* New records are inserted
* Existing records are updated

### Objective

Design a pipeline that:

* Processes only **new or updated data**
* Avoids **duplicate ingestion**
* Maintains **state across runs**

---

##  Architecture Diagram

![Architecture](assets/architecture.png)

This architecture illustrates:

* Data ingestion from Azure SQL
* Processing in Azure Databricks
* Storage using Delta Lake
* BI dashboards and alerting

---

##  Pipeline Flow

![Pipeline](assets/pipeline.png)

This flow highlights:

* Medallion Architecture (Bronze → Silver → Gold)
* Data transformations and enrichment
* Workflow orchestration and automation

---

##  Data Ingestion (Lakehouse Federation)

* Source: **Azure SQL Database**
* Access via **Databricks Lakehouse Federation (Unity Catalog)**
* No traditional ETL connectors required
* Incremental data loading into Delta tables

---

##  Data Model

* Products, Orders, and Payments are interconnected
* Changes in one entity impact downstream outputs
* Multiple datasets are joined for analytics

---

## Pipeline Design (Medallion Architecture)

### 🥉 Bronze Layer — Raw

* Incremental ingestion using **watermark logic**
* Control table to track processed data
* Raw Delta tables with ingestion metadata

---

### 🥈 Silver Layer — Clean

* Data cleaning and standardization
* Deduplication and validation
* Incremental upserts using **Delta MERGE**

---

### 🥇 Gold Layer — Business

* Data enrichment and aggregation
* Combines multiple entities
* Implements **SCD Type 2** for history tracking

---

## ⚙️ Tech Stack

* **Cloud:** Azure
* **Processing:** Azure Databricks
* **Storage:** Delta Lake
* **Database:** Azure SQL Database
* **Governance:** Unity Catalog
* **Version Control:** GitHub + Databricks Repos
* **Orchestration:** Databricks Workflows

---

## Code Management

* Version-controlled using GitHub
* Integrated with Databricks Repos

### Benefits:

* Collaboration
* Version tracking
* Environment separation
* Organized notebook management

---

## ⚙️ Jobs & Workflows

* Orchestrated using **Databricks Workflows**
* Notebook execution in sequence:

  * Bronze → Silver → Gold
* Dashboard refresh after pipeline completion
* Alerts triggered automatically


## 📊 BI Dashboards

The Gold layer enables:
*  Sales analytics
*  Payment monitoring
*  Category insights

---

##  Alerts & Monitoring

* Alerts on pipeline failures
* Workflow-based triggers
* Ensures reliability and observability

---

##  Key Concepts Demonstrated

* Incremental loading (no full reloads)
* Watermark logic (timestamp + primary key)
* Delta Lake MERGE (upsert)
* Control tables for state tracking
* Idempotent pipeline design
* Slowly Changing Dimension (SCD Type 2)

---

## Project Structure

📦 NovaCart-Lakehouse
 ┣ 📂 Alert
 ┣ 📂 Assets
 ┃ ┣ 📜 architecture.png
 ┃ ┗ 📜 pipeline.png
 ┣ 📂 Dashboards
 ┣ 📂 NoteBooks
 ┃ ┣ 📜 bronze_ingestion
 ┃ ┣ 📜 silver_transformation
 ┃ ┗ 📜 gold_aggregation
 ┣ 📂 Work_flows
 ┣ 📂 raw_data
 ┣ 📜 README.md


*  Incremental processing
* Version-controlled pipelines
* Automated workflows
* Built-in monitoring and alerts

---

## 🔮 Future Improvements

* Real-time streaming (Kafka / Event Hub)
* CI/CD integration
* Data quality frameworks (e.g., Great Expectations)
* Advanced dashboards

---

## 👤 Author

**Krishna Teja**


## ⭐ Acknowledgement

This project is built for learning purposes using a fictional company, **NovaCart**, to simulate real-world data engineering scenarios.

---

