📦 E-Commerce Supply Chain & Customer Sentiment Architecture
Python Pandas NLP Tableau/PowerBI

Transforming 100,000+ fragmented e-commerce records into a unified Data Warehouse and Business Intelligence Dashboard to optimize last-mile logistics and customer retention.

📊 Executive Summary & The Business Problem
In the highly competitive e-commerce sector, the "Last Mile" of delivery is where customer trust is either solidified or permanently destroyed. A leading Brazilian e-commerce platform (Olist) provided a fragmented, raw database of over 100k orders across 9 relational tables.

The objective of this project is to answer a critical executive question: How much is poor logistics costing the business in customer lifetime value, and are bad reviews driven by product quality or delivery failures?

Instead of simply creating charts, this project acts as an end-to-end Data Engineering and Analytics Pipeline. It ingests raw relational data, cleanses and engineers new KPIs, applies Natural Language Processing (NLP) to unstructured text, and feeds a clean dataset into a BI dashboard for executive decision-making.

🏗️ System Architecture & Data Strategy
To prevent system crashes and massive data redundancy, the raw .csv files were not blindly merged. Instead, the data was modeled using a Star Schema architecture, mimicking a true enterprise Data Warehouse environment.

mermaid






Layer 4: Executive Dashboard
Layer 3: Processed Output
Layer 2: Python ETL & NLP
Layer 1: Raw Data Ingestion
Orders Table
Customers Table
Order Items
Product Catalog
Customer Reviews
Date Standardization &Cleansing
KPI Engineering:Delivery Delays
NLP: Portuguese TextCategorization
Master_Analytical_Table.csv
Final_Dashboard_Data.csv
Logistics BottleneckMap
Root Cause SentimentAnalysis
1. The ETL Pipeline (Extract, Transform, Load)
Temporal Cleansing: Converted disjointed string timestamps into operational datetime objects.
Custom KPI Engineering: Engineered the delivery_delay_days metric by calculating the exact variance between the Estimated Delivery Date and the Actual Delivery Date.
Dimensional Modeling: Placed the Orders table at the center (Fact Table) and merged Customers, Items, and Geospatial data as branches (Dimension Tables) to optimize query performance.
2. Natural Language Processing (NLP) & Sentiment Engineering
To categorize qualitative customer feedback, I engineered an NLP script to analyze the raw, unstructured Portuguese review text.

Instead of relying solely on the 1-5 star numerical score, the Python script scans for contextual keywords (e.g., atraso [delay], quebrado [broken]).
It automatically tags the review into categorical buckets: "Logistics & Delivery Issue" vs. "Product Quality Issue". This allows the business to isolate supply chain failures from bad product manufacturing.
💡 Key Business Insights
(Note: These are sample insights derived from the dashboard. Update these based on your specific visual findings.)

The Delay Threshold: Customers who receive their order even 1 day past the expected date are 3x more likely to leave a 1-star review.
Logistics vs. Product: Unstructured text analysis revealed that 65% of negative reviews are explicitly due to freight/delivery issues, not the quality of the product itself.
Geospatial Profit Drain: The Northern region accounts for the highest freight costs but yields the lowest average delivery speeds, indicating a need to renegotiate carrier Service Level Agreements (SLAs) in those states.
📂 Repository Structure
text


Olist_ECommerce_Project/
│
├── data/
│   ├── raw/                  # Original 9 CSV files (Ignored in Git)
│   └── processed/            # Cleaned, merged, and NLP-processed CSVs
│
├── notebooks/
│   ├── 01_ETL_Data_Pipeline.ipynb     # Data cleaning, schema merging, KPI creation
│   └── 02_NLP_Review_Analysis.ipynb   # Text categorization and sentiment extraction
│
├── dashboards/
│   └── Executive_Summary.twbx         # Tableau/PowerBI Dashboard File
│
├── .gitignore                # Ensures heavy data files are not pushed to GitHub
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation
⚙️ Setup & Installation Guide
Follow these steps to replicate the environment and run the data pipeline on your local machine.

Prerequisites
Python 3.8+ installed.
Jupyter Notebook or VS Code.
A BI Tool (Tableau Desktop/Public or Power BI).
Step-by-Step Instructions
1. Clone the Repository Open your terminal and run:

bash


git clone https://github.com/YourUsername/Olist_ECommerce_Project.git
cd Olist_ECommerce_Project
2. Install Dependencies Install the required Python libraries using pip:

bash


pip install pandas numpy jupyter
(Or run pip install -r requirements.txt if you have generated the file).

3. Download the Raw Data Due to file size limits, the raw data is not hosted on GitHub.

Download the dataset from Kaggle: Brazilian E-Commerce Public Dataset by Olist
Extract the .csv files and place them exactly inside the data/raw/ folder.
4. Execute the ETL & NLP Pipeline

Launch Jupyter Notebook (jupyter notebook in your terminal).
Navigate to the notebooks/ directory.
Run 01_ETL_Data_Pipeline.ipynb cell-by-cell to clean and merge the data.
Run 02_NLP_Review_Analysis.ipynb cell-by-cell to apply the text categorization algorithm.
5. Connect the Dashboard

Open your BI tool.
Connect to the newly generated data/processed/Final_Dashboard_Data.csv.
Build or view the visualizations.
🚀 Future Scope
To scale this architecture for a live production environment, the following upgrades are recommended:

Cloud Migration: Transition the .csv pipeline into an AWS S3 data lake, queried via Amazon Athena or Snowflake.
LLM Integration: Replace the keyword-based NLP script with an OpenAI or LangChain API connection to perform nuanced, automated summarization of customer reviews as they stream in.
Predictive Modeling: Train a Machine Learning model (XGBoost) on the delivery_delay_days metric to predict which active shipments are highly likely to be delayed before they fail.
Author: [Your Name/LinkedIn Profile]
Date: [Current Month, Year]
Data provided by Olist via Kaggle.
