
---

# 🚀 NASA APOD ETL Pipeline (Airflow + Postgres)

This project is a fully automated **ETL data pipeline** built using **Apache Airflow 2.9+**, **PostgreSQL**, and the public **NASA Astronomy Picture of the Day (APOD) API**.

The pipeline fetches NASA’s daily image metadata, processes it, and stores it in a Postgres database for analytics and downstream use.

---

## 📌 **Project Overview**

The goal of this pipeline is simple:

1. **Extract**
   Fetch latest APOD data using NASA API.

2. **Transform**
   Parse JSON response and clean required fields.

3. **Load**
   Store final dataset into a PostgreSQL table.

The pipeline runs **every day** using Airflow’s modern scheduling system (`schedule="@daily"`).

---

## 🏗 **Tech Stack**

* **Apache Airflow 2.9+**
* **PostgreSQL**
* **Docker / Docker Compose**
* **Airflow Providers**

  * `apache-airflow-providers-http`
  * `apache-airflow-providers-postgres`
* **Python 3.12**
* **Requests library**

---

## 📂 **Project Structure**

```
.
├── dags/
│   └── etl.py
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

## ⚙️ **Airflow DAG Summary**

### **DAG ID:** `nasa_apod_postgres`

### **Schedule:** Daily (`@daily`)

### **Catchup:** Disabled

### **Tasks:**

| Task               | Description                       |
| ------------------ | --------------------------------- |
| **extract_apod**   | Calls NASA API (HTTP GET)         |
| **transform_apod** | Cleans and prepares JSON fields   |
| **load_apod**      | Inserts cleaned row into Postgres |

---

## 🔌 **Environment Variables Required**

Add these in `.env` or Airflow UI → Variables:

```
NASA_API_KEY=your_api_key_here
POSTGRES_CONN_ID=postgres_default
```

---

## 📦 **Installation & Setup**

### 1️⃣ Clone repository

```bash
git clone https://github.com/your-username/nasa-apod-airflow.git
cd nasa-apod-airflow
```

### 2️⃣ Install dependencies

```
pip install -r requirements.txt
```

### 3️⃣ Start Airflow (Docker)

```bash
docker compose up -d
```

### 4️⃣ Access Airflow UI

Go to:
**[http://localhost:8080](http://localhost:8080)**

Enable the DAG → watch the ETL pipeline run.

---

## 🗄 **PostgreSQL Table Schema**

```
CREATE TABLE nasa_apod (
    date DATE PRIMARY KEY,
    title TEXT,
    explanation TEXT,
    media_type TEXT,
    url TEXT
);
```

---

## 📊 Output Example

| date       | title       | media_type | url                                                 |
| ---------- | ----------- | ---------- | --------------------------------------------------- |
| 2025-01-02 | Galaxy View | image      | [https://apod.nasa.gov/](https://apod.nasa.gov/)... |

---

## 🎯 **Why This Project Is Valuable**

✔ Real ETL workflow
✔ Scheduling + automation
✔ API → Airflow → Postgres pipeline
✔ Industry-standard stack
✔ Recruiter-friendly, perfect for Data Engineer intern roles

---

## 🤝 **Contributions**

Feel free to fork this project and improve the transformations, add logging, or build Dash/Streamlit dashboards on top of the dataset.

---

## 📜 License

MIT License

---


Just tell me and I’ll add it!
