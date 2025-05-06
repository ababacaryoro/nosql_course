
# 🧪 Practical Exercise: Migrating Medical Data to MongoDB

## 🎯 Objective

In this exercise, you will:

- Design a MongoDB schema suitable for medical data.
- Build a Python application that automates the migration of CSV data to MongoDB.
- Set up a Dockerized multi-container environment to run the application.
- Execute queries to explore and extract insights from the dataset.

---

## 🗂️ Context

You are developing a system to ingest medical data provided in CSV format. The data arrives periodically and filenames are suffixed with the date of generation. All files share the same structure.

Your objective is to build a pipeline that watches a mounted folder for incoming files and automatically processes and loads them into MongoDB.

A sample file is provided in the `data` directory: `healthcare_dataset-20250506.csv`.

---

## 🧱 Step 1: Propose a MongoDB Data Model

- Examine the structure of the CSV file.
- Identify appropriate fields and propose a schema.
- Choose between embedding vs referencing if multiple collections are needed.
- Provide an example document in MongoDB JSON-like format.

---

## 🐳 Step 2: Setup Multi-container Application with Docker Compose

Create a `docker-compose.yml` that includes:

- A Python container with required libraries (e.g. `pymongo`, `pandas`)
- A MongoDB container (with credentials and persistence)
- A shared volume for the data (`./data`)

Ensure environment variables are handled securely (e.g. via `.env` file).

---

## 🐍 Step 3: Python ETL Script

Write a script that:

- Detects new CSV files in the `data` volume.
- Loads and validates the data (check nulls, parse dates, etc.).
- Cleans the data if needed.
- Inserts the data into MongoDB.
- Logs each major step of the pipeline.

---

## 🧪 Step 4: MongoDB Queries

Once the data is loaded, write and execute queries to answer the following:

1. 🧮 How many patients are in the collection?
2. 📆 List all patients admitted after **January 1, 2023**.
3. 🧓 How many patients:
   - Are older than 50?
   - Have the first name **"Thomas"**?
   - Per each distinct **Medical Condition**?
4. 💊 What is the frequency of usage for each **Medication**?
5. 🔍 Retrieve all patients currently taking `"Lipitor"`.

Include the code and output of each query in your final report.

---

## ✅ Deliverables

You must push your work into a Github repository that includes:

- `docker-compose.yml` + `README.md` file that explains your application
- `data/` folder with the original dataset
- Python script for data migration
- A PDF with the results of the queries and screenshots (e.g. `.count()` output in MongoDB shell or GUI)

📧 Send the link to your Github repository to: **yoroba93@gmail.com**
