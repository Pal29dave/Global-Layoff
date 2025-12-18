SQL Data Cleaning Project – Global Layoffs
End‑to‑end SQL data‑cleaning project on a global layoffs dataset, showcasing a production‑style workflow: staging, deduplication, standardization, and null handling for analytics‑ready data.​

Project Overview
Built a complete SQL pipeline to clean and prepare a raw global layoffs table for analysis and reporting.​

Focused on data integrity: never modifying the raw source, only transforming data in controlled staging layers.​

Designed with real‑world scenarios in mind, where messy, incomplete, and inconsistent data must be made reliable for business decisions.​

Tech Stack & Skills
Language: SQL (MySQL‑style syntax: DDL, DML, window functions, joins).​

Concepts: Data quality, null strategy, standardization, dataset refinement, data modeling for analytics.​

Workflow: Staging tables, temporary tables, controlled deletes, iterative cleaning passes.​

Data Cleaning Blueprint
Staging the data

Goal: Protect the raw layoffs table and isolate all transformations.​

Highlights: Used CREATE TABLE ... LIKE and INSERT ... SELECT to build a safe staging layer.​

Removing duplicates

Goal: Eliminate duplicate company‑level layoff records that could inflate counts or distort insights.​

Highlights: Applied ROW_NUMBER() OVER (PARTITION BY ...) and deleted rows with row numbers greater than 1.​

Standardizing formats

Goal: Make industries, countries, and dates consistent across all rows.​

Highlights: Consolidated similar industry labels, trimmed extra spaces or punctuation in country fields, and converted date strings to a proper DATE type.​

Handling nulls

Goal: Treat missing values intelligently instead of blindly dropping or filling them.​

Highlights: Converted blanks to NULL, imputed missing values when reliable information existed, and preserved meaningful nulls in key numeric fields.​

Refining the dataset

Goal: Remove non‑informative rows and columns to streamline analysis.​

Highlights: Dropped records with no analytical value and pruned unnecessary columns to improve performance and clarity.​

Core SQL Logic
Staging strategy

Created a staging table mirroring the raw layoffs table to perform all cleaning without touching the original source.​

Ensured traceability and rollback capability by separating raw and transformed layers.​

Duplicate detection and removal

Used ROW_NUMBER() OVER (PARTITION BY company, location, industry, totallaidoff, percentagelaidoff, date, stage, country, fundsraisedmillions) to flag duplicate records.​

Loaded these results into a secondary staging table with a rownum column and removed rows where rownum > 1 to retain only unique entries.​

Standardization of categories and dates

Consolidated fragmented industries (for example “Crypto Currency” and “CryptoCurrency”) into a single standardized label such as Crypto.​

Cleaned country fields by trimming extra spaces and punctuation, and converted date strings into a consistent DATE type for accurate time‑series analysis.​

Null and blank handling

Converted empty strings to NULL for categorical columns like industry to simplify downstream logic.​

Imputed missing industry values by self‑joining on company when other rows for the same company had valid data.​

Evaluated nulls in numeric fields such as totallaidoff, percentagelaidoff, and fundsraisedmillions as potentially meaningful signals (for example no layoffs or undisclosed funding) rather than always filling or dropping them.​

Dataset refinement

Removed records that added no analytical value, such as rows where both totallaidoff and percentagelaidoff were null and no other useful attributes were present.​

Dropped unnecessary columns to create a lean, analytics‑ready table optimized for BI tools and reportin
