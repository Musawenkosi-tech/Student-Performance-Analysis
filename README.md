# Student Performance Analysis

A data cleaning and analysis project built in Databricks, using pandas for data preparation and Spark SQL for aggregation and querying. The project takes a raw student performance dataset, cleans it, engineers new features, and surfaces insights about academic performance and attendance risk.

> **Note:** This notebook was built and run in Databricks. The `%sql` cells and the `spark.createDataFrame()` call rely on Databricks' built-in environment and will not execute standalone in a plain Jupyter/local environment.

## What it does

- Loads a raw student dataset (`school_student_performance.csv`) into a pandas DataFrame
- Cleans and standardizes the data:
  - Normalizes column names to lowercase
  - Fills missing city values with `"Unknown"`
  - Fills missing score values with the column mean
- Engineers new features:
  - **`score`** : an average of math, English, and science scores
  - **`result`** : `Pass`/`Fail` based on a 50-point threshold
  - **`attendance_category`** : classifies students as `High Attendance`, `Low Attendance`, or `At Risk` based on attendance rate
- Registers the cleaned data as a temp view (`school_performance_updated`) so it can be queried with SQL
- Runs SQL queries to answer questions like:
  - How many students fall into each attendance category?
  - What's the average score per grade?
  - Which students are flagged as `Low Attendance` or `At Risk`?
- Exports the cleaned dataset back out as CSV and Parquet

## Tools & tech

- **Databricks** (notebook environment)
- **Python & pandas** - data cleaning, feature engineering (`.apply()`, boolean filtering, custom functions)
- **SQL** - querying the cleaned data using Databricks' built-in SQL support (`%sql` cells) to run aggregations directly on the dataset

## Key insights surfaced

- Count of students by attendance category (High / Low / At Risk)
- Average score by grade, ranked
- List of specific students flagged as low-attendance or at-risk, for targeted follow-up

## File structure

```
student-performance-analysis/
├── Students.ipynb
├── school_student_performance.csv
└── README.md
```

## Author

Musa  [LinkedIn](www.linkedin.com/in/musawenkosi-mhlambi-04b5ba310)
*(part of ongoing data engineering coursework at Witle Academy)*
