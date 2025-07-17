

# 🎧 Music Listening Analysis – ADB Dataviz Project

This project presents an end-to-end pipeline to analyze music listening behavior using an interactive Tableau dashboard connected to a PostgreSQL database hosted on Supabase. The project leverages automated ETL with Apache Airflow, data cleaning, and advanced KPI visualizations.

## 📁 Project Structure

```
.
├── ETL-airflow_dag.zip            # Airflow DAGs for ETL pipeline
├── doc-APP-dataviz-CO-DELLAL-ALMEIDA-HORD.pdf                           # Documentation in .pdf format
├── Music-listen-analysis-CO_DELLAL_ALMEIDA_HORD.twbx   # Tableau dashboard (tracked via Git LFS)
├── README.md                      # Project description
├── .gitattributes                 # Git LFS configuration
```



---

## 🚀 What It Is

This is a data visualization project focused on analyzing music listening behavior through calculated KPIs. It transforms raw CSV data into valuable insights using automated ETL, database views, and a user-friendly Tableau interface.

---

## 🔧 What It Does

- **ETL with Airflow**: Loads raw `.csv` files into Supabase after cleaning (standardizes dates, handles `NaT`, formats strings).
- **PostgreSQL View**: A SQL view `music_data` was created to pre-clean the data for Tableau.
- **KPI Calculation** (in SQL):
  - Most listened track of all time
  - Most listened album of all time
  - Most listened artist of all time
  - Weekly top tracks, albums, and artists
  - Top 10 biggest listeners (global + weekly)
  - Cross-tabulation listener × artist
- **Tableau Dashboard**:
  - Shows trends, rankings, and listener behaviors.
  - Interactive filters for year and week selection.
  - Extracted `.twbx` version uploaded with loaded data.

---

## ⚙️ How It Works

### ETL with Apache Airflow

A DAG (`flow_in_supabase_music_data`) handles:

1. Iterating over all `.csv` files in a directory
2. Converting and cleaning the data using `pandas`
3. Formatting dates with `pd.to_datetime`
4. Inserting data into the `flow_in_music_data` table in Supabase


Connection to Supabase is configured using Airflow’s **Connections UI** (`supabase_music_viz`).

---

## Tableau Dashboard

### Features
- KPIs displayed with key stats and evolution charts
- Cross-tab of listeners and artists
- Contribution of top listeners to total plays
- Weekly breakdown with drill-down capabilities

> Data was extracted in `.twbx` format to ensure the dashboard works without live connection.

## How to Install and Run

### Requirements

- Apache Airflow
- Python 3.8+
- Supabase account (PostgreSQL)
- Git + Git LFS
- Tableau Desktop

### Setup Steps

```bash
# 1. Clone the repo
git clone https://github.com/thuy29/ADB-dataviz-project.git
cd ADB-dataviz-project

# 2. Install Git LFS and pull large files (if not yet)
git lfs install
git lfs pull

# 3. Launch Airflow and trigger the DAG manually (or schedule it)
```

DAG file in ETL-airflow_dag : `airflow_dag.py`  
CSV folder path used in DAG: `/home/[name of your user folder]/airflow/dags/Lastfm`

You can import the `.twbx` file in Tableau Desktop to view and interact with the dashboard.

---

## Bonus Features

- Additional KPIs via filters
- Use of **Dataviz Catalogue** to inspire layout and design consistency
- Git LFS integration to manage large dashboard files
- Airflow used for reproducibility

---

## License

This project is for academic purposes only.  
All data was provided as part of the ADB course.
