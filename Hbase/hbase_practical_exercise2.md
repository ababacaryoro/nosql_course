
# HBase Assignment – Los Angeles Crime Data

## 🎯 Objective

In this assignment, you will practice loading and querying a large dataset using **HBase**, interact with it via the **HBase Shell** and **Python**, and deploy everything using **Docker**. You will analyze a sample of crime reports in Los Angeles. You should download first this dataset using this [link](https://catalog.data.gov/dataset/crime-data-from-2020-to-present/resource/5eb6507e-fa82-4595-a604-023f8a326099).

## 🧱 Technologies

- Docker / Docker Compose
- HBase
- Python (with `happybase`, `pandas`)
- GitHub (for submission)

---

## 🔧 Setup Instructions

1. **Clone the starter repository**
2. **Launch your environment** using Docker Compose:
   - Create `docker-compose.yml` with HBase and optional HBase UI.

3. **Start Docker services**:
   ```bash
   docker-compose up -d
   ```

4. **Enter the HBase Shell using a terminal**:
   ```bash
   docker exec -it hbase /bin/bash
   hbase shell
   ```

5. **Create a document to report finding**
This document should be saved in PDF format at the end.

6. **Create a notebook for Python tasks**

---

## 📊 Part 1: Data Understanding in Python

1. Load the downloaded dataset (can be named `sample_crimes_data.csv`) using `pandas`.
2. Explore it:
   - Show number of rows & columns
   - Show missing values
   - Describe crimes & areas categories
   - Make a temporal description of the data (number of crimes by month, year, etc.)
Create charts as much as possible for your analysis.
This analysis will help you in the design of the database (rowkey an column families).

---

## 🧱 Part 2: HBase Data Modeling

1. In the HBase shell, create a namespace called:
   ```bash
   create_namespace 'practice'
   ```

2. Design a table: `practice:crimes` with at least **two column families** (we can go up to 4 column families):
   - `location`
   - `crime_info`
Explain your design choice in the report.
3. Design a rowkey containing `DR_NO` and other informations (a salt, the day...) to optimize scanning. Choose an optimal prefix (based on your EDA) to help speed up queries. Ex : "Prefix_OtherInformations"

---

## 🧪 Part 3: Data Insertion in Python

1. Connect to HBase from Python using `happybase`.
2. Create the table in Python (optional if not done via shell).
3. Clean data:
   - Rename columns with efficient names (replace spaces with `_`, lowercase characters)
   - Prepare a catalog to map every column with a column family
   - Implement the efficient rowkey you designed (e.g. `12_190326475`)
   - Convert date/time to strings
   - Prepare a function to push data into hbase. To efficiently manage the memory, do not push a cell when the value is `NA`.
4. **Push at least the 500 000 first rows** to HBase.

---

## 🔍 Part 4: Queries in HBase Shell

Using `hbase shell`, answer the following:

- Count the number of rows of our crimes table
- Count & show the first 10 rows of : 
    - All crimes in `Hollywood` in 2020
    - All `SHOPLIFTING` and `VANDALISM` crimes (if the label of the crime contains it) in February 2020 
    - Victim age and sex for crimes of `INTIMATE PARTNER - SIMPLE ASSAULT` (exact match) in April 2020 
    - Crimes reported in `03/12/2020 12:00:00 AM`
    - Crimes occuring between `02/01/2020 12:00:00 AM` and `02/02/2020 12:00:00 AM`, in `Wilshire` on female victims.
- Check number of regions and region servers

The code & screenshot of results for these queries should be included in the report.
---

## 🧠 Part 5: Retrieve data from Hbase and Analyze in Python

1. From Python, retrieve:
   - All `SHOPLIFTING` and `VANDALISM` crimes (if the label of the crime contains it)
   - Crimes occuring in `Hollywood`
   - Victim age and sex for crimes of `INTIMATE PARTNER - SIMPLE ASSAULT` (exact match)

2. Compare these queries with original CSV

---

## 🚀 Submission

1. Push the following to GitHub:
   - All code: Docker setup, Python notebooks or scripts
   - A document report summarizing:
     - Modeling choices
     - Screenshots of HBase Shell queries
     - Sample retrieved data
     - EDA results

2. Send an email to: `yoroba93@gmail.com`  
   **Subject**: `HBase Assignment - [Your Name]`  
   Include the GitHub repo link.

---

## ✅ Evaluation Criteria

| Criteria                        | Points |
|---------------------------------|--------|
| Data exploration in Python      | 10     |
| HBase table modeling            | 15     |
| Clean data & efficient rowkeys  | 10     |
| Data load with filtering        | 15     |
| Querying in HBase Shell         | 15     |
| Python retrieval & comparison   | 20     |
| Documents & GitHub structure    | 15     |
| **Total**                       | **100**|

---

Good luck! 🚀