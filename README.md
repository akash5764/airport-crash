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
```

---

# 📂 Dataset

The dataset contains historical aircraft crash records with fields such as:

| Column | Description |
|------|-------------|
| ID | Unique crash identifier |
| Date | Date of crash |
| Location | Crash location |
| Operator | Airline/operator |
| Type | Aircraft type |
| Aboard | Number of people onboard |
| Fatalities | Number of deaths |
| Survivors | Number of survivors |
| Ground | Ground casualties |
| SurvivalRate | Survival percentage |

---

# 🔎 Analysis Performed

## 1️⃣ Highest Ground Casualties

Identify the crash with the **maximum ground fatalities**.

```python
highest_ground = df.loc[df["Ground"].idxmax()]
```

---

## 2️⃣ Crash Distribution by Operator

Find which airline/operator appears most frequently in crash records.

```python
crash_counts = df["Operator"].value_counts()
```

---

## 3️⃣ Most Frequent Aircraft Type

Determine which aircraft type appears most often.

```python
df["Type"].value_counts()
```

---

## 4️⃣ Decade With Highest Fatalities

Create a **Decade column** to analyze crash trends.

```python
df["decade"] = pd.to_datetime(df["Date"]).dt.year // 10 * 10
df.groupby("decade")["Fatalities"].sum()
```

---

## 5️⃣ Lowest Survival Rate

Find crashes with the **lowest survival rate (excluding zero)**.

```python
filtered_df = df[df["SurvivalRate"] > 0]
```

---

## 6️⃣ Median Passengers Aboard

Calculate the **median number of passengers onboard**.

```python
df["Aboard"].median()
```

---

## 7️⃣ Survival Rate Statistics

Basic statistical summary of survival rates.

```python
df["SurvivalRate"].agg(["mean", "min", "max"])
```

---

## 8️⃣ Crashes with Fatalities > 90%

Identify severe crashes where **more than 90% of passengers died**.

```python
df[df["Fatalities"] > df["Aboard"] * 0.9]
```

---

## 9️⃣ Top 5 Operators With Most Crashes

```python
df["Operator"].value_counts().head(5)
```

---

# 🛠️ Technologies Used

## Programming
- Python

## Libraries
- Pandas
- PyODBC
- python-dotenv

## Database
- Microsoft SQL Server

## Environment
- Jupyter Notebook

---

# 📁 Project Structure

```
plane-crash-analysis/

Project.ipynb          # Main analysis notebook
cleaned_dataset.csv    # Dataset used for analysis
.env                   # Database credentials
output.csv             # Processed dataset output
README.md
.gitignore
```

---

# ⚙️ Setup Instructions

## 1️⃣ Install dependencies

```bash
pip install pandas pyodbc python-dotenv
```

---

## 2️⃣ Configure environment variables

Create a `.env` file:

```
DB_SERVER=YOUR_SERVER_NAME
DB_DATABASE=YOUR_DATABASE_NAME
```

---

## 3️⃣ Run the notebook

Open Jupyter Notebook and run:

```
Project.ipynb
```

---

# 📈 Example Insights

Some key findings from the analysis include:

- Certain **operators appear more frequently in crash records**
- Some decades have **significantly higher fatality counts**
- Aircraft crashes with **>90% fatality rates** are rare but extremely severe
- Survival rates vary widely depending on **crash conditions and aircraft type**

---

# 🎯 Learning Outcomes

This project demonstrates:

- SQL database connectivity using Python
- Data extraction from relational databases
- Data analysis using Pandas
- Exploratory data analysis techniques
- Practical data science workflow

---

# 👨‍💻 Author

**Akashchand Rajput**  
AI & Data Science Engineer

Projects:

- Agentic Annual Report Analyzer
- Retail Demand Forecasting System
- Plane Crash Data Analysis
