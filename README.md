# TASK-7-Get-Basic-Sales-Summary-from-a-Tiny-SQLite-Database-using-Python


# 📊 Simple SQLite Sales Dashboard in Python

---

## 🎯 Project Goal

Build a lightweight **sales analysis tool** using only built-in Python libraries and `matplotlib` to:

✅ Connect to a SQLite database  
✅ Run SQL queries from Python  
✅ Display a clean table summary of total sales  
✅ Visualize revenue with an interactive and animated bar chart

---

## 📦 Features

- 🛠️ Uses only built-in libraries (`sqlite3`, `matplotlib`, `pandas`)
- 📈 Creates a bar chart of revenue per product
- 🧠 Demonstrates basic SQL skills in Python
- 💡 Perfect starter project for data beginners

---

---

## 🧪 How It Works

```python
import sqlite3
import pandas as pd
import matplotlib.pyplot as plt

# Connect to SQLite database
conn = sqlite3.connect("sales_data.db")

# SQL query to summarize sales
query = """
SELECT product, 
       SUM(quantity) AS total_qty, 
       SUM(quantity * price) AS revenue 
FROM sales 
GROUP BY product
"""

# Load into pandas
df = pd.read_sql_query(query, conn)
conn.close()

# Plot bar chart
df.plot(kind='bar', x='product', y='revenue', color='skyblue')
plt.title("Revenue by Product")
plt.show()
