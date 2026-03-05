# ✈️ Plane Crash Data Analysis (SQL + Python)

This project performs **exploratory data analysis on historical plane crash data** using **Python, Pandas, and SQL Server**.  
The dataset is queried from a **Microsoft SQL Server database** and analyzed in a **Jupyter Notebook** to extract meaningful insights about aviation accidents.

The goal of this project is to demonstrate **data extraction, transformation, and analytical querying using Python and SQL**.

---

# 📊 Project Overview

The analysis explores various questions about aircraft crashes such as:

- Which crash had the **highest ground casualties**
- Which **aircraft operator** had the most crashes
- Most common **aircraft types**
- Which **decade recorded the highest fatalities**
- Crashes with the **lowest survival rates**
- Statistical analysis of **survival rates and passengers aboard**

The results help understand patterns and trends in aviation accident data.

---

# 🧠 Key Concepts Used

## Database Connection

The dataset is stored in **SQL Server** and accessed using:

- `pyodbc`
- `python-dotenv`

Example connection:

```python
conn_str = (
    f'DRIVER={{ODBC Driver 17 for SQL Server}};'
    f'SERVER={server};'
    f'DATABASE={database};'
    'Trusted_Connection=yes;'
)