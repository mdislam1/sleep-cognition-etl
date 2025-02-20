# ETL Pipeline: Analyzing Sleep Deprivation and Cognitive Performance

## Overview
This project implements an **ETL (Extract, Transform, Load) pipeline** to process a dataset exploring the impact of sleep deprivation on cognitive performance and emotional regulation. The dataset includes metrics such as sleep duration, sleep quality, reaction times, memory accuracy, and emotional stability, along with demographic and lifestyle factors.

The ETL pipeline:
1. **Extracts** the raw dataset.
2. **Transforms** the data by cleaning, normalizing, and engineering new features.
3. **Loads** the processed data into an SQLite database for further analysis.

---

## Analysis Repository
The **analysis** part of this project, which includes data exploration, statistical analysis, and visualizations, is located in a separate GitHub repository. You can access the analysis code and documentation here:  
[**Analysis Repository: sleep-cognition-analysis**](https://github.com/mdislam1/sleep-cognition-analysis.git)

This repository contains the complete implementation of the analysis, including data visualizations, correlation analysis, and insights derived from the dataset.

---

## Dataset Description
The dataset contains the following key columns:
- **Sleep Metrics**: `Sleep_Hours`, `Sleep_Quality_Score`, `Daytime_Sleepiness`
- **Cognitive Performance**: `Stroop_Reaction_Time`, `N_Back_Accuracy`, `PVT_Time`
- **Emotional Regulation**: `Emotion_Regulation_Score`
- **Demographics**: `Age`, `Gender`, `BMI`
- **Lifestyle Factors**: `Caffeine_Intake`, `Physical_Activity_Level`, `Stress_Level`

---

## ETL Pipeline Steps

### 1. **Extract**
- The raw dataset is loaded from a CSV file (`sleep_deprivation_dataset_detailed.csv`) into a pandas DataFrame using the Kaggle API.

### 2. **Transform**
- **Data Cleaning**:
  - Check for and handle missing values (none found in this dataset).
  - Convert categorical variables (e.g., `Gender`) to appropriate data types.
- **Feature Engineering**:
  - Create new features such as `Sleep_Efficiency` (Sleep Quality Score / Sleep Hours).
- **Normalization**:
  - Normalize numerical columns (e.g., `Sleep_Hours`) to a 0-1 scale for consistency.
- **Encoding**:
  - One-hot encode categorical variables (e.g., `Gender`) for machine learning compatibility.
- **Rounding**:
  - Round numerical columns to 2 decimal places for readability.
- **Renaming**:
  - Rename columns for better readability (e.g., `Stroop_Task_Reaction_Time` → `Stroop_Reaction_Time`).

### 3. **Load**
- The transformed data is saved to a new CSV file (`transformed_sleep_data.csv`).
- The data is loaded into an SQLite database (`sleep_study.db`) for efficient storage and querying.

---

## Tools and Libraries
- **Python**: Primary programming language.
- **Pandas**: Data manipulation and transformation.
- **NumPy**: Numerical operations.
- **SQLite3**: Database management.
- **Kaggle API**: Dataset extraction.

---

## File Structure
```
project/
├── data/
│   ├── sleep_deprivation_dataset_detailed.csv  # Raw dataset
│   └── transformed_sleep_data.csv              # Transformed dataset
├── database/
│   └── sleep_study.db                          # SQLite database
├── scripts/
│   └── sleep_study_etl_pipeline.ipynb          # ETL pipeline script
└── README.md                                   # Project documentation
```

---

## How to Run the ETL Pipeline
1. Clone the repository:
   ```bash
   git clone https://github.com/mdislam1/sleep-cognition-etl.git
   cd project
   ```
2. Install the required libraries:
   ```bash
   pip install pandas numpy sqlite3 kagglehub
   ```
3. Run the ETL pipeline script:
   ```bash
   python scripts/sleep_study_etl_pipeline.ipynb
   ```
4. Check the output:
   - Transformed data: `data/transformed_sleep_data.csv`
   - Database: `database/sleep_study.db`

---

## Key Insights from Data Exploration
- **Sleep Hours**: Normalized to a 0-1 scale for consistent analysis.
- **Sleep Efficiency**: A new feature created to measure sleep quality relative to sleep duration.
- **Gender Encoding**: Converted to binary (`Gender_Male`: 1 for Male, 0 for Female).
- **Correlation Analysis**: Explored relationships between sleep metrics and cognitive/emotional performance.

---

## Future Enhancements
- Add logging for better tracking of the ETL process.
- Integrate with cloud storage (e.g., AWS S3) for scalability.
- Automate the pipeline using workflow management tools like Apache Airflow.

---

## Author
Md Islam  
GitHub: https://github.com/mdislam1
