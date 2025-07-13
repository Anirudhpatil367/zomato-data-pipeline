# 🍽️ Zomato Data Pipeline: Extract, Transform, Load with AWS Glue (PySpark) & Snowflake 📊

🚗 **Project Overview**

The **Zomato Data Pipeline** project automates the extraction, transformation, and loading of restaurant data using **AWS services**, **AWS Glue (PySpark)**, and **Snowflake**. The pipeline processes a public **Kaggle Zomato dataset**, filtering it specifically for **restaurants located in Bangalore**. With integration into **Power BI** and **QuickSight**, it enables interactive dashboards and real-time analytics for food trends and business performance.

### Key Features:
- 📥 **Data Extraction from Kaggle**: Use the publicly available Zomato dataset from **Kaggle** as the primary data source.
- 🏙️ **Bangalore-Focused Insights**: Filter the data to include only **restaurants in Bangalore** for targeted analytics.
- 🔄 **Data Transformation**: Clean, standardize, and enrich the raw data using **PySpark scripts within AWS Glue**.
- 📊 **Seamless Data Analysis**: Query and analyze data using **Amazon Athena** and **Snowflake**.
- ⚙️ **Fully Automated Workflow**: Automate the entire pipeline using **Apache Airflow** and **Docker**.
- 📱 **Interactive Dashboards**: Visualize key insights with **Power BI** and **AWS QuickSight**.

This project brings Zomato’s Bangalore restaurant data to life through a scalable, automated cloud-native analytics pipeline.

---

🛠️ **Architecture & Services Used**

The pipeline integrates with a modern data stack combining AWS tools and Glue for scalable data processing:

### Services Involved:
- **Kaggle Dataset**: Public Zomato dataset used as the raw data source.
- **AWS S3**: Store raw and transformed data securely.
- **AWS Glue (PySpark)**: Perform transformations and filtering for Bangalore restaurants using PySpark scripts.
- **AWS Glue Crawler**: Automatically infer schemas and register tables in the Glue Data Catalog.
- **Snowflake**: Store analysis-ready data for scalable querying.
- **Snowpipe**: Enable continuous ingestion from S3 into Snowflake.
- **Amazon Athena**: Perform serverless SQL queries directly on S3.
- **Apache Airflow**: Orchestrate each stage of the pipeline.
- **Docker**: Containerize custom components for consistent deployments.
- **Power BI / AWS QuickSight**: Create dynamic dashboards for visual insights.

---

### Pipeline Flow:
1. **Extract**: Download Zomato data from **Kaggle**, upload to **S3**.
2. **Transform**: Use **AWS Glue (PySpark)** to clean and filter the dataset for **Bangalore**.
3. **Store**: Save transformed data to a new **S3** bucket.
4. **Catalog**: Use **Glue Crawler** to register schemas in Glue Data Catalog.
5. **Load**: Use **Snowpipe** to load data continuously into **Snowflake**.
6. **Analyze**: Query using **Athena** and **Snowflake**.
7. **Visualize**: Create dashboards with **Power BI** and **QuickSight**.

---

💻 **How It Works**

### 1. Data Extraction from Kaggle
- Download Zomato dataset from **Kaggle**.
- Upload raw CSV/JSON files to the `raw_data/` folder in **AWS S3**.
- Trigger an Airflow DAG to initiate the pipeline.

### 2. Data Transformation
- **AWS Glue** executes **PySpark scripts** to:
  - Filter the dataset to only include **restaurants in Bangalore**.
  - Perform cleaning, normalization, and enrichment.
- Transformed data is stored in `transformed_data/` on **S3**.

### 3. Cataloging with AWS Glue
- **AWS Glue Crawler** scans the transformed dataset.
- Glue creates metadata tables in the **Glue Data Catalog** for use by Athena and other services.

### 4. Loading into Snowflake
- **Snowpipe** continuously ingests new files from S3 into the **Snowflake** warehouse.
- Tables in Snowflake are optimized for restaurant-based analytics.

### 5. Querying with Athena & Snowflake
- Use **Amazon Athena** for ad-hoc queries directly on S3.
- Use **Snowflake** for performance-intensive queries and dashboard backends.

### 6. Visualization
- **Power BI** connects to Snowflake to create restaurant trend dashboards.
- **AWS QuickSight** provides serverless, scalable dashboards with role-based access.

---

🔧 **System Workflow**

![Workflow_Diagram](https://github.com/Anirudhpatil367/zomato-data-pipeline/blob/6e20ca6ae6e082e40654e632307706a557448361/AWS.jpg)

### 1. Data Collection:
- Zomato data is downloaded from **Kaggle** and uploaded to **AWS S3** using Airflow.

### 2. Data Transformation:
- Data is transformed in **AWS Glue using PySpark**.
- Glue jobs clean and filter the dataset for **Bangalore** city.

### 3. Data Storage:
- Raw and transformed datasets are stored in different folders in **S3**.
- Data is organized for efficient querying and loading.

### 4. Data Analysis:
- **Athena** queries the transformed data in **S3**.
- **Snowpipe** ingests data into **Snowflake** for low-latency analysis.

### 5. Data Visualization:
- Dashboards in **Power BI** and **QuickSight** show key metrics like top cuisines, ratings, and average cost by location.

---

🔄 **How to Set Up the Zomato Data Pipeline**

### Step 1: Download Dataset from Kaggle
- Download the restaurant dataset from Kaggle.

### Step 2: Upload to S3
- Create an S3 bucket with folders: `raw_data/` and `transformed_data/`.
- Upload the Kaggle dataset to `raw_data/`.

### Step 3: Set Up AWS Glue (PySpark)
- Create a Glue Job using **PySpark** for cleaning and filtering Bangalore-specific data.
- Output the result to `transformed_data/` on S3.

### Step 4: Configure AWS Glue Crawler
- Set up a Glue Crawler to catalog the `transformed_data/` in S3 and register it in the Glue Data Catalog.

### Step 5: Configure Snowflake & Snowpipe
- Create corresponding tables in Snowflake.
- Set up **Snowpipe** to auto-load files from `transformed_data/`.

### Step 6: Use Amazon Athena
- Configure Athena to read Glue Catalog tables for quick data exploration and validation.

### Step 7: Set Up Visualization
- Connect **Power BI** and **QuickSight** to Snowflake and Athena.
- Build dashboards showing restaurant ratings, cuisines, and location analytics for **Bangalore**.

---

🎯 **Demonstration**

The pipeline follows this flow:

1. **Data Extraction**: Zomato dataset from Kaggle is stored in S3.
2. **Data Transformation**: AWS Glue with PySpark cleans and filters data for Bangalore.
3. **Data Loading**: Transformed data is loaded into Snowflake via Snowpipe.
4. **Query & Analyze**: Athena and Snowflake enable deep SQL analysis.
5. **Visualization**: Power BI and QuickSight dashboards deliver insights.

---

🚀 **Future Enhancements**

- 🔍 **Sentiment Analysis**: Use NLP models on restaurant reviews.
- 📱 **Mobile Dashboards**: Deploy dashboards via mobile BI apps.
- 🛰️ **Real-Time Streaming**: Add live ingestion using **AWS Kinesis**.
- ⚡ **Kubernetes-Based Scaling**: Run Glue Spark on **EKS** for horizontal scalability.
- 🤖 **ML Recommendations**: Suggest restaurants based on trends and pricing.

---

## 🪪 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
