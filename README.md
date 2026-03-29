# 📦 E-Commerce Supply Chain & Customer Sentiment Architecture 
![Python](https://img.shields.io/badge/Python-3.9+-blue.svg) ![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-yellow.svg) ![NLP](https://img.shields.io/badge/NLP-Text_Analysis-green.svg) ![Tableau/PowerBI](https://img.shields.io/badge/Dashboard-Tableau%2FPowerBI-orange.svg)

> **Transforming 100,000+ fragmented e-commerce records into a unified Data Warehouse and Business Intelligence Dashboard to optimize last-mile logistics and customer retention.**

## 📊 Executive Summary & The Business Problem
In the highly competitive e-commerce sector, the **"Last Mile"** of delivery is where customer trust is either solidified or permanently destroyed. A leading Brazilian e-commerce platform (Olist) provided a fragmented, raw database of over 100,000 orders across 9 relational tables. 

**The objective of this project is to answer a critical executive question:** 
*How much is poor logistics costing the business in customer lifetime value, and are bad reviews driven by product quality or delivery failures?*

Instead of simply creating charts, this project acts as an end-to-end **Data Engineering and Analytics Pipeline**. It ingests raw relational data, cleanses and engineers new KPIs, applies Natural Language Processing (NLP) to unstructured text, and feeds a clean dataset into a BI dashboard for executive decision-making.

---

## 🏗️ System Architecture & Data Strategy

To prevent system crashes and massive data redundancy, the raw `.csv` files were not blindly merged. Instead, the data was modeled using a **Star Schema** architecture, mimicking a true enterprise Data Warehouse environment.

```mermaid
flowchart TD
    subgraph Raw Data [Layer 1: Raw Data Ingestion]
        A[(Orders Table)]
        B[(Customers Table)]
        C[(Order Items)]
        D[(Product Catalog)]
        E[(Customer Reviews)]
    end

    subgraph ETL Pipeline [Layer 2: Python ETL & NLP]
        F[Date Standardization & Cleansing]
        G[KPI Engineering: Delivery Delays]
        H[NLP: Portuguese Text Categorization]
    end

    subgraph Data Warehouse [Layer 3: Processed Output]
        I[(Master_Analytical_Table.csv)]
        J[(Final_Dashboard_Data.csv)]
    end

    subgraph BI Presentation [Layer 4: Executive Dashboard]
        K[Logistics Bottleneck Map]
        L[Root Cause Sentiment Analysis]
    end

    A --> F
    B --> F
    C --> F
    D --> F
    E --> H
    
    F --> G
    G --> I
    H --> I
    I --> J
    J --> K
    J --> L
