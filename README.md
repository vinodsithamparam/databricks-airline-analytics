# US Airline Delay Analytics & Real-Time Data Pipeline

This repository hosts a data engineering pipeline and analytics built entirely on the **Databricks** platform. The project processes large-scale, transactional aviation flight data to extract key performance indicators regarding U.S. domestic flight delays, route optimization, on-ground taxi efficiency, and scheduling disruptions.

---
## Demonstration

https://github.com/user-attachments/assets/3fd9177e-4fd2-45c7-a480-bae079a4c3e3

---

## 🏗️ Architecture Overview

The pipeline leverages a cloud data lakehouse architecture designed for high scalability, unified analytics and business intelligent.

```
[ Amazon S3 Bucket ] ──> [ Databricks Pipeline Ingestion ] ──> [ Medallion Architecture ] ──> [ Databricks AI/BI Dashboard ]

```

* **Storage Layer:** Raw CSV data is stored and secured within an **Amazon S3 Bucket**.
* **Ingestion Engine:** Orchestrated using the **Databricks Pipeline**, automating the parsing of raw CSV data.
* **Data Processing Framework:** Structured around the **Medallion Architecture**, progressing raw CSV data through incremental stages of cleaning and business-level metric aggregation:
  * `Bronze` : Raw append-only ingestion of source records.
  * `Silver` : Type casting, schema enforcement and data deduplication
  * `Gold` : Aggregate business-level tables optimized for downstream analytics, performance tracking, and low-latency visualization.


* **Visualization:** Built using the **Databricks AI/BI Dashboards**, enabling interactive analytics for operational stakeholders without moving data out of the lakehouse environment.

---

## 📊 Dataset Information

* **Data Source:** Office of Airline Information, Bureau of Transportation Statistics (BTS).
* **Dataset Dimensions:** 3,429,840 rows $\times$ 110 columns.
* **Temporal Scope:** October 2025 – March 2026.
* **Scope Details:** Contains scheduled and actual departure/arrival metrics reported by certified U.S. air carriers accounting for at least 0.5% of domestic scheduled passenger revenues.

---

## 📈 Dashboard Insights & Visualizations

The native Databricks dashboard serves as an interactive operational tool to pinpoint inefficiencies and track monthly macro trends.

### 1. Carrier Performance Monitoring

The dashboard highlights carrier-specific vulnerabilities by tracking the percentage of total delayed flights across the top 10 worst-performing airlines. This allows fleet managers to benchmark specific carriers (e.g., B6, NK, F9) experiencing frequent  delays.

### 2. Delay Attribution & Corridor Bottlenecks

* **Delay Factor Breakdown:** Visualizes contributing factors (Weather, Departure Delay, Late Aircraft, Carrier Delay, NAS Delay, and Security Delay) categorized by individual airlines. This categorical granularity helps operational teams to separate infrastructure faults (NAS) from internal carrier faults, while pinpoint areas for improvement. 
* **High-Traffic Corridors:** A multi-dimensional scatter plot flags specific Origin-to-Destination city pairs (such as `BOS → FLL`, `FLL → LGA`, `ORD → SEA`) regularly suffering from low on-time performance by plotting Average Arrival Delay against overall Delay Rate.

### 3. Ground Taxi Efficiency & Macro Completion Factors

* **Ground Congestion Trends:** Correlates average weekly Taxi-In and Taxi-Out times against overall departure delays grouped by day of the week. Spikes in on-ground congestion provide a signal for airport staff schedule optimization.
* **Completion Factor Analysis:** Tracks the long-term monthly correlation between scheduled, diverted, and cancelled flights. It outlines critical operational periods where scheduled flights decreased while cancellations experienced sudden upward spikes.

---
