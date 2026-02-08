# AI-Driven-Energy-Grid-Stress-Monitor
This project is an end-to-end data pipeline that predicts real-time grid instability. Using Machine Learning (Random Forest), it analyzes weather patterns and historical load data to calculate a "Grid Stress Rating"—giving grid operators a "Digital Council" of predictions to prevent blackouts before they happen.

<img width="1942" height="1087" alt="image" src="https://github.com/user-attachments/assets/f32488b6-1c1d-4878-8f0a-a9f392b47ecf" />


# The Architecture

The project is built on a Medallion Architecture using Databricks and Unity Catalog:

   - Bronze Layer: Raw data ingested from Open-Meteo API (Weather) and Historical Grid Load datasets.

   - Silver Layer: Data cleaned, time-zones normalized, and features engineered (Lagged temperatures, rolling averages).

   - Gold Layer: Business-ready tables containing consolidated "Truth" data and Model Predictions.

   - Power BI: The final visualization layer connected via Partner Connect.

# The "Digital Council" (Machine Learning)

We moved away from simple "Yes/No" predictions to a probabilistic model.

  - Model: Random Forest Classifier.

  - Intuition: The model consists of 100+ decision trees. If 15 trees detect a dangerous pattern, the Grid Stress Rating becomes 15%.

  - Features: Temperature (2m), Wind Speed (10m), Hour of Day, and Historical Load.

# Dashboard Features

The Power BI dashboard provides a "Control Room" view:

  - Grid Stress Score: A dynamic gauge that changes color (🟢 🟡 🔴) based on the "consensus" of the ML model.

  - Historical Context: Compare current usage against the last 7 days of "Gold" data.

  - Weather Correlation: Real-time tracking of temperature and wind to explain why stress is rising.

  - Interactive Map: Filter the entire suite of analytics by clicking on Paris, Berlin, Munich, etc.

# Tech Stack

  - Cloud: Databricks 

  - Language: PySpark (Spark SQL & MLlib)

  - Storage: Delta Lake 

  - Orchestration: Databricks Workflows

  - Visualization: Power BI

# How to Run

   - Clone the Repo: Import the .ipynb notebooks into your Databricks Workspace.

   - Run Pipeline: Execute Notebooks A through D in sequence or set up a Databricks Job.

   - Connect Power BI: Use the SQL Warehouse connection string to refresh the .pbix file.
