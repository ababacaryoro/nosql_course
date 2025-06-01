
# 🧪 HBase Introduction Assignment
 
## 🎯 Objective:
Set up a minimal HBase environment using Docker and practice basic operations in both HBase Shell and Python.

---

## 📦 Part 1: Environment Setup with Docker

1. Create a `docker-compose.yml` file with a minimal HBase service. Example:

```yaml
version: '3'
services:
  hbase:
    image: harisekhon/hbase
    container_name: hbase
    ports:
      - "16010:16010"
      - "9090:9090"
      - "2181:2181"
    environment:
      - HBASE_MANAGES_ZK=true
```

2. Start the container:
```bash
docker-compose up -d
```

3. Access the HBase Shell:
```bash
docker exec -it hbase /bin/bash
hbase shell
```

---

## 🧱 Part 2: Create and Explore a Table

1. Create a namespace and table in HBase Shell:
```bash
create_namespace 'practice'
create 'practice:students', 'info'
```

2. Insert sample data:
```bash
put 'practice:students', '1001', 'info:name', 'Alice'
put 'practice:students', '1001', 'info:age', '21'
put 'practice:students', '1002', 'info:name', 'Bob'
put 'practice:students', '1002', 'info:age', '23'
```

3. Retrieve all data:
```bash
scan 'practice:students'
```

---

## 🐍 Part 3: Access HBase with Python

1. Install Python HBase client:
```bash
pip install happybase
```

2. Connect and scan the table:
```python
import happybase

connection = happybase.Connection('localhost')
table = connection.table('practice:students')

for key, data in table.scan():
    print(key, data)
```

3. Add a new row:
```python
table.put(b'1003', {
    b'info:name': b'Charlie',
    b'info:age': b'22'
})
```

4. Read a row:
```python
row = table.row(b'1003')
print(row)
```

---

## 📤 Deliverables

- Screenshot of `scan 'practice:students'` output from HBase Shell
- Python code in a `.py` file
- (Optional) Link to GitHub repository
