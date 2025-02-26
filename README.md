# **🌍 Earthquake Data Analysis Project using MICROSOFT FABRIC 📊**

This project focuses on **Earthquake Data Analysis**, leveraging **Data Factory (ADF)** and **Databricks** for seamless data ingestion, transformation, and reporting.

## 📥 **Data Ingestion**  

- 🚨 The earthquake data is fetched from the **USGS API**: [USGS Earthquake API](https://earthquake.usgs.gov/fdsnws/event/1/#parameters).  

- 💻 The JSON data is ingested into **Data Factory** via a **notebook** using Python’s `requests` library.  

- 🌍 The dataset contains an object called **"features"**, where each **feature** represents an individual earthquake event.  

- 📝 The extracted data is loaded into a **DataFrame**, with columns derived from `features` (geometry, id, properties, and type).  

- 💾 This **Bronze Layer** data is stored as a table in **Lakehouse**.

## 🔄 **Data Transformation (Silver Layer)**  

- 🔧 A separate **notebook** processes the **Bronze Layer** data.  

- 🧑‍🔬 The `geometry` and `properties` columns are split to extract **important metrics** for analysis.  

- ⏱️ The **timestamp**, originally in milliseconds, is converted to **seconds** and further into **TimestampType**.  

- 💡 The transformed data is saved as a table to serve the **Gold Layer**.

## 🏅 **Data Enrichment & Aggregation (Gold Layer)**  

- 🕰️ The **Gold Layer** notebook applies a filter to extract only data **after the pipeline-defined start time**.  

- 🌍 A new **"country"** column is derived using **latitude & longitude** via the `reverse_geocoder` library.  

- ⚙️ Since `reverse_geocoder` is not available by default in **Microsoft Fabric**, a custom environment is created, and the library is installed.  

- 🌐 The `search()` method of `reverse_geocoder` extracts **geographical properties**, specifically the **country code (cc)**.  

- ✂️ Additional transformations:  

  - 🔴 Classification of earthquakes based on **significance**.  

  - 🌎 Splitting the **place_description** column to separate **country** and **place description**.  

- 🏆 The final aggregated dataset is stored as a **reporting table**.

## 🧑‍💻 **Orchestration of Notebooks**  

- 🔄 The entire pipeline of notebooks is orchestrated to automate the process, with **start_date** and **end_date** added as base parameters.  

- ⏳ These base parameters ensure that earthquake events are extracted for a **specified time period**, making the process **flexible** and **efficient**.

## 📊 **Power BI Reporting**  

- 📈 A **Power BI report** is generated using the **final dataset**, allowing:  

  - 🌍 **Country-wise classification** of earthquake events based on significance.  

  - 🗓️ **Filtering within a date range** for better insights.  

---

### 🚀 **Technologies Used**  

- **Data Factory (DF)** 🏭  

- **Notebooks for ETL Processing** 📝  

- **Python (requests, pandas, reverse_geocoder)** 🐍  

- **Microsoft Fabric (Lakehouse & Custom Environments)** 🏙️  

- **Power BI (Visualization & Reporting)** 📊

📌 *This project enables efficient earthquake data processing, transformation, and visualization for meaningful insights!* 🌍📊  

---
