# Student Performance Analysis

A data cleaning and analysis project built in Databricks, using pandas for data preparation and Spark SQL for aggregation and querying. The project takes a raw student performance dataset, cleans it, engineers new features, and surfaces insights about academic performance and attendance risk.

> **Note:** This notebook was built and run in Databricks. Cells prefixed with `%sql` and the `spark.createDataFrame()` call rely on a Databricks Spark session and will not execute standalone in a plain Jupyter/local environment.

## What it does

- Loads a raw student dataset (`school_student_performance.csv`) into a pandas DataFrame
- Cleans and standardizes the data:
  - Normalizes column names to lowercase
  - Fills missing city values with `"Unknown"`
  - Fills missing score values with the column mean
- Engineers new features:
  - **`score`** — an average of math, English, and science scores
  - **`result`** — `Pass`/`Fail` based on a 50-point threshold
  - **`attendance_category`** — classifies students as `High Attendance`, `Low Attendance`, or `At Risk` based on attendance rate
- Registers the cleaned DataFrame as a Spark SQL temp view (`school_performance_updated`)
- Runs SQL queries to answer questions like:
  - How many students fall into each attendance category?
  - What's the average score per grade?
  - Which students are flagged as `Low Attendance` or `At Risk`?
- Exports the cleaned dataset back out as CSV and Parquet

## Tools & tech

- **Databricks** (notebook environment, Spark runtime)
- **PySpark / Spark SQL** — DataFrame-to-SQL view registration and aggregation queries
- **pandas** — data cleaning, feature engineering
- **Python** (`.apply()`, boolean filtering, custom functions)

## Key insights surfaced

- Count of students by attendance category (High / Low / At Risk)
- Average score by grade, ranked
- List of specific students flagged as low-attendance or at-risk, for targeted follow-up

## File structure

```
student-performance-analysis/
├── Students.ipynb
└── README.md
```

