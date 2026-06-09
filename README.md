# Weather & Traffic Data Analysis Pipeline

An end-to-end data engineering and business intelligence project that extracts historical and current weather data and combines it with readily available traffic data, orchestrates a pipeline using Apache Airflow for current weather data, loads historical weather and traffic data into Google Cloud Platform (GCP), and visualizes insights to analyze weather impacts on traffic patterns.

## System Architecture

The pipeline follows a modern data stack architecture to extract, load, transform, and analyze the data:

![Data Engineering Lifecycle](DE%20Lifecycle.jpg)

1. **Source Data & Extraction:** Automated Python scripts query the Visual Crossing Weather API and extract flat-file traffic data from the Utah Department of Transportation (UDOT).
2. **Orchestration:** Apache Airflow schedules and manages the part of workflow tasks.
3. **Data Storage:** Raw `json` and `csv` extractions are securely pushed into a Google Cloud Storage (GCS) bucket.
4. **Transformation:** Data is transformed using Python/SQL in Google Colab to prepare clean analytical tables.
5. **Analytics & BI:** Final reporting layer built in Power BI to showcase actionable insights.

---

## Tech Stack & Tools
* **Languages:** Python, SQL
* **Orchestration:** Apache Airflow
* **Cloud Platform:** Google Cloud Platform
* **Environment:** Google Colab / Jupyter Notebooks
* **BI Tool:** Power BI

---

## Repository Structure

* [/Batch Weather Data Download](./Batch%20Weather%20Data%20Download) - Contains the Airflow DAG scripts, environment windows, execution pipeline screenshots, and DAG script
* [/Historical Weather Data Download](./Historical%20Weather%20Data%20Download) - Contains the script for historical weather data pull for the user input
* [/Traffic Data Download and Transform](./Traffic%20Data%20Download%20and%20Transform) - Contains script used to transform the traffic data
* [/Visualization](./Visualization) - Contains basic visualization showing weather impacts on traffic patterns.

---

## Steps of Analysis

### 1. Automated Weather API Ingestion
Using a robust Python script ([DAG Script](./Batch%20Weather%20Data%20Download/api_call.py)), the pipeline interacts with the Visual Crossing Weather API.
* Handles batch downloads smoothly.
* Saves structured outputs directly to cloud buckets.

Alongside this, a direct extraction was completed using a Google Colab script ([Colab Script 1](./Historical%20Weather%20Data%20Download/Historical%20Weather%20Data%20API%20Call.ipynb)) prior to implementing the Apache Airflow batch extraction. The purpose was to gain hands-on experience using various data engineering tools.

![Airflow Main Window](./Batch%20Weather%20Data%20Download/Airflow%20Main%20Window.jpg)
![Airflow Run Window](./Batch%20Weather%20Data%20Download/Run%20Window.jpg)
![Airflow DAG Response Window](./Batch%20Weather%20Data%20Download/DAG%20Response.jpg)
![Batch File Saved in GCP Bucket](./Batch%20Weather%20Data%20Download/Files%20Saved.jpg)

### 2. Cloud Storage & Transformation
The UDOT traffic data was downloaded and saved in Google buckets, including the weather data. The traffic data was transformed to ease visualization using [Colab Script 2](./Traffic%20Data%20Download%20and%20Transform/fetch_traffic1.ipynb).

The screenshot below shows all the data stored in Google Buckets.
![GCP Bucket](GCP%20Bucket.jpg)

### 3. Analytics
Initial visualizations highlighting weather impacts on traffic patterns are detailed below. Notably, vehicle speeds were observed to decrease significantly during periods of low temperatures and high precipitation. The primary objective of this project was to gain hands-on experience utilizing a variety of modern data engineering tools.

![Visualization 1](./Visualization/Visual%201.jpg)
![Visualization 2](./Visualization/Visual%202.jpg)
