
# 🧪 Practical Exercise: Redis with Actors and Movies Dataset

## 🗂️ Overview
You are provided with two files containing Redis `HSET` commands to insert data into a Redis database:

- `actors.redis`: contains ~1300 actors
- `movies.redis`: contains ~900 movies

Each file uses the following structure:
```
HSET "actor:1" first_name "AA" last_name "B" date_of_birth 1979
HSET "movie:5" title "AAA" genre "BB" votes 489175 rating 8.1 release_year 2014
```

## 🛠️ Objective
You'll:
1. Load data into Redis using Docker.
2. Interact with Redis using Python.
3. Write queries to analyze data.

---

## 🚀 Setup

### 1. Run Redis and RedisInsight using Docker Compose

Create a `docker-compose.yml` with this minimal configuration and add a Jupyter notebook image with a mounted folder for your notebooks :
```yaml
version: '3'
services:
  redis:
    image: redis:latest
    container_name: redis-server
    ports:
      - "6379:6379"
    volumes:
      - ./data:/data

  redisinsight:
    image: redis/redisinsight:latest
    container_name: redis-insight
    ports:
      - "5540:5540"
    depends_on:
      - redis

volumes:
  redis_data:
```
The data folder should contain the files `actors.redis` and `movies.redis`.

Start it:
```bash
docker-compose up -d
```

---

## 📥 Load the Data

In a terminal, run:
```bash
docker exec -i redis-server redis-cli < data/actors.redis
docker exec -i redis-server redis-cli < data/movies.redis
```

---

## 🧪 Part 1 – Data Exploration (RedisInsight or Python)

Jupyter notebook page and install the client:

```python
!pip install redis
import redis

# Connect
r = redis.Redis(host='redis', port=6379, decode_responses=True)
```

Answer to the following questions : 

1. How many actors and movies are stored in Redis?
2. List 5 actors born before 1980.
3. Retrieve the genre and rating of the movie "The Imitation Game".
4. List the top 5 highest-rated movies.
5. How many movies have a rating above 7.5?
6. Update the rating of the movie "The Imitation Game" to 8.5.
7. Add a new actor: "Zendaya", born in 1996.
8. Delete the movie with title "The Room".

---

## 📌 Part 2 – Python Interaction

Write a Python script that does the following:

1. Connects to Redis.
2. Loads all actor hashes and counts how many actors have a last name starting with “P”.
3. Gets all movies released after 2010 with more than 100,000 votes.
4. Creates a new hash: `top_movies_by_genre:<genre>` with the highest-rated movie per genre.

---

## 🧼 Cleanup

To stop everything:
```bash
docker-compose down
```

## ✅ Deliverables

You must push your work into a Github repository that includes:

- `docker-compose.yml` + `REDME.md` file that explains your application
- `data/` folder with the original dataset
- Python script for interaction with Redis database
- A PDF with the results of the queries

📧 Send the link to your Github repository to: **yoroba93@gmail.com**
