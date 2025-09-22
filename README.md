# Weather ETL & Dashboard Project

## Project Overview
This project demonstrates a complete ETL pipeline using **Databricks** to fetch, process, and visualize weather data. 

The pipeline extracts hourly weather data from the **Open-Meteo API**, cleans and transforms it, aggregates daily statistics, and stores results in **Delta tables**. The final dashboard visualizes daily weather trends, including temperature, humidity, and precipitation.

---

## ETL Pipeline Structure
The ETL workflow is organized into three layers:

1. **Bronze Layer**: Raw data ingestion from Open-Meteo API, stored as a Delta table with extraction timestamp and unique IDs.  
2. **Silver Layer**: Cleaned and transformed data with proper data types, deduplicated records, and source metadata.  
3. **Gold Layer**: Aggregated analytics-ready data, including daily average temperature, humidity, and total precipitation.

All notebooks are scheduled as a **Databricks job** to run daily at 8 AM, automatically updating the Gold layer and the dashboard.

---

## Notebooks
- `Bronze_ETL.ipynb` – Extract and store raw weather data from the API  
- `Silver_ETL.ipynb` – Clean, transform, and deduplicate Bronze data  
- `Gold_ETL.ipynb` – Aggregate Silver data and prepare for analytics  

---

## Dashboard
The Databricks dashboard visualizes:

- Daily average temperature (line chart)  
- Total precipitation per day (bar chart)  
- Humidity trends (area chart)  
- Min and max temperature per day (optional)

The dashboard **automatically refreshes** after the ETL job completes.

 <img width="1470" height="830" alt="Screenshot 2025-09-22 at 5 38 25 PM" src="https://github.com/user-attachments/assets/9906fbdf-6a5b-4c9e-b262-c839cc690e04" />


---

## ETL Job
The ETL pipeline is orchestrated using a Databricks job:

- **Job Name:** `Weather_ETL_Pipeline`  
- **Tasks:** Bronze → Silver → Gold → Dashboard refresh  
- **Schedule:** Runs daily at 8 AM  
- **Behavior:** Appends new daily data to Delta tables, keeping past records and updating visualizations automatically  
<img width="1636" height="1230" alt="image" src="https://github.com/user-attachments/assets/7142e142-314e-4d22-ac09-f50935264d10" />
<img width="1636" height="1534" alt="image" src="https://github.com/user-attachments/assets/e7d2c5a9-5d1e-49c7-8982-f0c16c26c87c" />


---

## License
This project is licensed under the MIT License.  

---

