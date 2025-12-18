QL Data Cleaning Project – Global Layoffs
📌 Project Overview

This project focuses on cleaning and preparing a global layoffs dataset using SQL to make it reliable and ready for analysis.
The goal is to apply real-world data cleaning techniques such as removing duplicates, standardizing values, handling nulls, and refining the dataset structure while preserving the original raw data.

This project demonstrates practical SQL data cleaning skills commonly used by data analysts.

🗂 Dataset

Dataset: Global layoffs data

Content includes:

Company name

Location

Industry

Total laid off

Percentage laid off

Date

Company stage

Country

Funds raised (in millions)

🛠 Tools & Technologies

SQL

MySQL

Window Functions (ROW_NUMBER)

Data Cleaning Techniques

🔄 Data Cleaning Steps
1️⃣ Data Staging

Created a staging table to preserve the raw dataset.

All cleaning operations were performed on the staging table to ensure data integrity.

CREATE TABLE layoffs_staging LIKE layoffs;
INSERT INTO layoffs_staging SELECT * FROM layoffs;

2️⃣ Identifying & Removing Duplicates

Used ROW_NUMBER() with PARTITION BY to detect duplicate records.

Removed duplicate rows while keeping only unique entries.

3️⃣ Standardizing & Correcting Data

Standardized inconsistent industry names (e.g., Crypto variations).

Cleaned country names by removing extra spaces or punctuation.

Converted date columns into a proper DATE format.

4️⃣ Handling Null & Empty Values

Converted blank strings to NULL for consistency.

Imputed missing industry values by referencing records from the same company.

Carefully evaluated columns where null values were meaningful and left them unchanged.

5️⃣ Removing Useless Rows & Columns

Identified rows that added no analytical value (e.g., no layoff data).

Removed unnecessary columns and refined the dataset for analysis readiness.

✅ Final Outcome

Cleaned, standardized, and well-structured dataset

Duplicate-free records

Consistent formatting across all fields

Dataset ready for EDA, visualization, and business analysis

🎯 Key Learnings

Importance of staging data before cleaning

Practical use of SQL window functions

Making context-based decisions while handling null values

Real-world data cleaning workflow used by data analysts

📌 How to Use This Project

Import the dataset into MySQL

Run the SQL scripts step by step

Review the cleaned staging table

Use the cleaned data for analysis or dashboards
