# Anime Industry Trends & Market Analytics Dashboard 

##  Project Overview
This project is an end-to-end Business Intelligence dashboard designed to track the historical production trends, user engagement, and categorical dominance of the global anime industry. 

Rather than relying on pre-cleaned data, this project showcases heavy **Data Engineering** and **ETL (Extract, Transform, Load)** methodologies to convert wildly inconsistent, multi-valued string data into a strict relational data model ready for enterprise-level analytics.

Dashboard Preview <img width="1321" height="746" alt="Dashboard_Screenshot" src="https://github.com/user-attachments/assets/0f852e67-7f09-4722-8291-63dcfb99a63f" />


## The Tech Stack
* **Tool:** Power BI Desktop
* **Data Transformation:** Power Query Editor (M Code)
* **Calculations:** DAX (Data Analysis Expressions)
* **Concepts:** Relational Data Modeling, Unpivoting, Text Parsing, Data Normalization

## Data Engineering & ETL Pipeline
Real-world data is messy. The raw dataset contained over 50,000 rows of inconsistent strings, merged arrays, and broken date formats. I built a robust pipeline in Power Query to normalize the data without losing relational integrity:

* **Handling Multi-Valued Cells (Unpivoting):** The original `genre` column contained comma-separated arrays (e.g., "Action, Comedy, Sci-Fi"). I split this column by delimiter and expanded it into new rows to allow for accurate categorical filtering.
* **String Trimming & Normalization:** Implemented formatting scripts to eradicate invisible rogue spaces caused by the delimiter split, preventing duplicate categorical variables.
* **Custom Text Parsing (Bypassing AI Limits):** The `aired_string` date column contained a mix of full dates, single years, ranges, and "Not available" text. Because the variance broke standard automated extraction, I engineered a manual brute-force text-parsing pipeline (using Custom Delimiter Splits and Right-Character Extractions) to isolate a pure 4-digit `Release Year` integer.
* **DAX Optimization:** Because unpivoting the genres duplicated the total row count, standard implicit counting would have inflated the metrics. I authored custom explicit DAX measures utilizing `DISTINCTCOUNT` to ensure all KPI cards and charts reflected the true, unique entity counts.

## Key Visualizations & Market Insights
1. **Historical Anime Production Volume (Line Chart):** Tracks the explosive growth of the industry from 1917 to 2019, filtered by clean numeric integers.
2. **Anime Score vs. Total Voters Distribution (Scatter Plot):** Analyzes the correlation between critical reception and sheer popularity, identifying true "masterpieces" (high score + massive user base) versus niche highly-rated shows.
3. **Number of Animes Per Genre (Conditionally Formatted Bar Chart):** Displays the dominance of specific genres (like Comedy and Action) using sorted descending logic and conditional gradient formatting for immediate visual hierarchy.

## Repository Contents
* `Anime_Analytics_Dashboard.pbix`: The complete, interactive Power BI project file.
* `Raw_Data.csv`: The initial, uncleaned dataset to demonstrate the starting point of the ETL pipeline.
* `Dashboard_Screenshot.png`: High-resolution preview of the final UI.
