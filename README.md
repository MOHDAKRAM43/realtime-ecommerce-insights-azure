# 🛒 Real-Time E-Commerce Order Intelligence & Sales Monitoring (Azure)

An **end-to-end real-time data engineering project** built on **Azure**, designed to simulate, process, and visualize **live U.S.-based e-commerce orders** using a **Modern Data Stack** and **Medallion Architecture (Bronze → Silver → Gold)**.

This project demonstrates how streaming data can be transformed into **minute-level business insights** using cloud-native tools.

---

## 🚀 Project Overview

This project simulates **real-time e-commerce transactions** across U.S. states (CA, TX, NY, etc.) and processes them through a scalable Azure-based pipeline.

The pipeline:
- Ingests live events using **Azure Event Hub**
- Processes streams using **PySpark on Azure Databricks**
- Stores data using **Delta Lake on Azure Blob Storage**
- Visualizes insights using **Power BI**
- Tracks all changes using **Git**

The final output is an **interactive Power BI dashboard** providing **real-time sales intelligence**.

---

## 🔧 Tech Stack

### 📥 Data Ingestion
- Azure Event Hub
- Python (Azure Event Hub SDK)

### ⚙️ Processing
- Azure Databricks
- PySpark (Structured Streaming)

### 🗄️ Storage
- Azure Blob Storage
- Delta Lake (Bronze / Silver / Gold)

### 📊 Visualization
- Power BI (Databricks SQL Connector)

### 🔄 Version Control
- Git (CLI-based workflow)

---

## 🏗️ Architecture

This project follows a **real-time streaming architecture** built on Azure services and the **Medallion (Bronze → Silver → Gold) design pattern**, enabling scalable ingestion, transformation, and analytics.

### 🏛️ System Architecture

The architecture below illustrates how real-time e-commerce order events flow from ingestion to visualization:

![Real-Time E-Commerce Architecture](https://github.com/MOHDAKRAM43/realtime-ecommerce-insights-azure/blob/main/Architecture/Architecture.png)

### 🔗 Architecture Flow (Connected View)

- A **Python-based simulator** generates U.S. e-commerce order events in real time.
- These events are streamed into **Azure Event Hub**, acting as the central ingestion layer.
- **Azure Databricks Structured Streaming** consumes Event Hub data and processes it through:
  - **Bronze Layer** – raw JSON ingestion
  - **Silver Layer** – cleaned and validated records
  - **Gold Layer** – 1-minute aggregated sales metrics
- All layers are stored in **Delta Lake format on Azure Blob Storage**.
- The **Gold Delta tables** are exposed via **Databricks SQL Warehouse**.
- **Power BI** connects to the SQL endpoint to deliver real-time dashboards for business users.

---

## 📁 Project Structure

real-time-ecommerce-insights-azure/
├──Architecture/
│   └── architecture.png           # Renamed for web-standard lowercase
├── databricks_notebooks/          # Standard naming for Databricks repos
│   ├── 01_bronze_ingestion.py     # Renamed for clarity on the Medallion step
│   ├── 02_silver_transformation.py
│   └── 03_gold_aggregation.py
├── simulator/                           # "Source" - for the data simulator
│   └── order_simulator.py         
├── power BI/                       # More professional than "Power BI"
│   └── sales_dashboard.pbix
├── CICD/                       # For utility/CLI scripts
│   └── git_setup.sh
└── README.md


## 🧪 Step 1: Data Simulation & Event Streaming

A Python-based simulator continuously generates **fake U.S. e-commerce orders** and streams them to **Azure Event Hub**.

### 📦 Event Fields
- `order_id`
- `state`
- `city`
- `product`
- `quantity`
- `price`
- `timestamp`

### ⚙️ Simulator Highlights
- Uses `uuid`, `random`, `json`, `time`
- Sends events every second
- Uses `send_batch()` for efficient streaming
- Built using `azure-eventhub` SDK
```
### 🪛 Setup Commands
```bash
pip install azure-eventhub
git add Simulator/
git commit -m "Added real-time U.S. e-commerce order simulator"
---
```
🔁 Step 2: Real-Time Processing in Databricks
Structured Streaming is used to build a three-layer Delta Lake pipeline.

🍂 Bronze Layer – Raw Streaming Data
File: 01_stream_orders_to_bronze.py

Reads streaming data from Event Hub

Parses and flattens JSON payloads

Writes raw data to Azure Blob Storage in Delta format

git commit -m "Bronze layer streaming for U.S. order data"
🪛 Silver Layer – Cleaned & Enriched Data
File: 02_cleaned_values_silver.py

Removes nulls and invalid records

Casts data types correctly

Stores refined data as Delta tables

git commit -m "Cleaned and enriched Bronze data into Silver layer"
🪙 Gold Layer – Aggregated Analytics Data
File: 03_aggregated_to_gold.py

Aggregates data using 1-minute windows

Groups by state, product, and timestamp

Stores business-ready metrics

git commit -m "Aggregated Silver data to Gold layer (minute-level)"
```
---
🗃️ Step 3: Azure Blob Storage (Delta Lake)
All layers are stored in Delta format inside Azure Blob Storage:

abfss://ecommerce@ecommercestoragema.dfs.core.windows.net/bronze/
abfss://ecommerce@ecommercestoragema.dfs.core.windows.net/silver/
abfss://ecommerce@ecommercestoragema.dfs.core.windows.net/gold/
Streaming writes continuously update Delta tables

Gold layer acts as the single source of truth for analytics

---
```
### 📊Step 4: Power BI Dashboard

Here’s a screenshot of the final **Power BI dashboard**, visualizing U.S. e-commerce sales analytics:

![Power BI Dashboard](https://github.com/MOHDAKRAM43/realtime-ecommerce-insights-azure/blob/main/Architecture/Dashboard.png)

📌 **Dashboard Highlights**
📈 Dashboard Visuals
Visual Type	Description
🗺️ Map Chart	State-wise total sales
📉 Line Chart	Sales trend over time (1-minute window)
🍩 Donut Chart	Total sales per state
🍩 Donut Chart	Total items sold per state
📄 Table	Raw aggregated data sorted by highest sales

---
```
Power BI connects directly to the Gold Delta table via Databricks SQL Warehouse.

🔌 Connection Steps
Created Databricks SQL Warehouse

Connected Power BI using Azure Databricks Connector

Authenticated using access token

Loaded Gold Delta table

git commit -m "Power BI dashboard with real-time U.S. sales insights"
---
```
🔗 Git Version Control Strategy
Used Git CLI throughout the project

Maintained clean, logical commits

Tracked changes layer-by-layer

Folder-level version control

git init
git add .
git commit -m "Initial project setup"
git push origin main
```
---
✅ Final Outcome
✔️ End-to-end real-time analytics pipeline
✔️ Azure-native & scalable architecture
✔️ Streaming + Delta Lake + BI integration
✔️ Minute-level insights for business teams
---
This project demonstrates real-world data engineering skills including streaming ingestion, distributed processing, data modeling, and analytics delivery.
---
⭐ If you found this project helpful, feel free to star the repository and connect!

🔗 Linkedin: (https://www.linkedin.com/in/mohd-akram-6a210a259/)
📧 Gmail: (imakram7860@gmail.com)


