
# 🍽️ MongoDB Practical Exercise: Restaurant Dataset

## 🎯 Objective

In this exercise, you'll manipulate a MongoDB database containing restaurant information. You'll use CRUD operations and basic queries to practice interacting with a real-world JSON dataset.

You must work in a **Dockerized environment**.

---

## 📦 Step 1: Docker Setup

Create a `docker-compose.yml` file that includes the following services:

- `mongodb`: A MongoDB service (expose port 27017)
- `jupyter`: A Jupyter notebook (e.g. `jupyter/scipy-notebook`) that you’ll use for Python scripting

Mount a volume to share your notebook and JSON dataset into the container.
You can install the GUI client `MongoDB Compass` to better manipulate the data.

Example structure:

```
.
├── docker-compose.yml
├── data/
│   └── restaurants.json
├── notebooks/
│   └── mongo_queries.ipynb
```

---

## 🧩 Step 2: Load Data into MongoDB

- Use the Mongo shell or a script in the Jupyter notebook or MongoDB Compass to load `restaurants.json` into a collection named `restaurants` in the `nyc` database.

---

## 🛠️ Step 3: CRUD & Query Practice

In your notebook, complete the following tasks using the Python `pymongo` client:

### 🟢 Create

- Insert a new restaurant document (can be a mock one).

### 🟡 Read

- Count the total number of restaurants.
- List all restaurants in the borough "Bronx".
- Find all restaurants serving "Bakery" cuisine with an "A" grade.

### 🟠 Update

- Update the grade of a restaurant with name `"Morris Park Bake Shop"` to `grade: "A+"`.

### 🔴 Delete

- Delete all restaurants with grade `"C"`.

---

## ✅ Deliverables

- Push your work into a github repository.