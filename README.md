# Telco-Customer-Churn-Analysis-SQL-Powered-Insights-for-Retention
Comprehensive Telco customer churn analysis project, showcasing end-to-end data pipeline skills. Leveraged SQL for MySQL database management &amp; data extraction, and Python (Pandas, Matplotlib, Seaborn) for robust cleaning and Exploratory Data Analysis. 
# Project 2: Telco Customer Churn Analysis - Technical Deep Dive

## Table of Contents
1.  [Project Overview](#project-overview)
2.  [Business Objective](#business-objective)
3.  [Dataset](#dataset)
4.  [Methodology / Roadmap](#methodology--roadmap)
5.  [Technical Stack](#technical-stack)
6.  [Setup and Execution](#setup-and-execution)
7.  [Key Findings & Recommendations](#key-findings--recommendations)
8.  [Deliverables](#deliverables)
9.  [Future Work](#future-work)
10. [Contact](#contact)

---

## 1. Project Overview

This project demonstrates a comprehensive data analysis pipeline, from database management and data extraction to cleaning, exploratory data analysis (EDA), and deriving actionable business insights. Using a real-world Telco customer churn dataset, the goal is to identify key factors contributing to customer attrition and propose strategies to improve retention.

**Skills Showcased:** Python (Pandas, Matplotlib, Seaborn), SQL, MySQL Database Management, Jupyter Notebook, Data Cleaning, Data Visualization, Problem Solving, Analytical Thinking, Business Communication.

## 2. Business Objective

The primary objective is to understand why customers are leaving a telecommunications company (churning) and to identify the main predictive factors of churn. By analyzing customer demographics, services, and billing information, we aim to provide data-driven insights and actionable recommendations to reduce churn and improve customer lifetime value.

## 3. Dataset

The dataset used is the **"Telco Customer Churn"** dataset, publicly available on Kaggle.
*   **Source:** [Kaggle - Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
*   **Description:** Contains information about a fictional telecommunications company's customers, including services signed up for, contract type, payment method, monthly charges, total charges, and whether they churned.
*   **Size:** 7043 rows (after initial load), 21 columns.

## 4. Methodology / Roadmap

The project followed a structured approach:

1.  **Database Management (MySQL):**
    *   Set up a local MySQL database.
    *   Created a table (`telco_data`) and imported the `Telco Customer Churn.csv` dataset into it.
2.  **Data Extraction & Cleaning (SQL & Python):**
    *   Connected a Jupyter Notebook to the MySQL database.
    *   Extracted data using SQL queries into a Pandas DataFrame.
    *   Cleaned the data: handled missing values (especially in `TotalCharges`), converted categorical 'Yes'/'No' and 'gender' columns to numerical (1/0), and dropped redundant identifiers (`customerID`).
3.  **Exploratory Data Analysis (EDA) (Python):**
    *   Utilized Matplotlib and Seaborn for data visualization.
    *   Analyzed key aspects such as overall churn rate, churn by contract type, relationship between monthly charges/tenure and churn, and impact of various services (e.g., Internet Service, Online Security, Tech Support).
4.  **Insights & Recommendations:**
    *   Summarized key findings supported by data visualizations.
    *   Proposed actionable business recommendations to mitigate customer churn.

## 5. Technical Stack

*   **Programming Language:** Python 3.x
*   **Development Environment:** Jupyter Notebook
*   **Database:** MySQL (local server)
*   **Key Libraries:**
    *   `pandas`: For data manipulation and analysis.
    *   `numpy`: For numerical operations (e.g., NaN handling).
    *   `matplotlib`: For static data visualizations.
    *   `seaborn`: For enhanced statistical data visualizations.
    *   `sqlalchemy`: Python SQL toolkit and ORM, used for connecting to MySQL.
    *   `mysql-connector-python`: MySQL driver for Python.
    *   `urllib.parse`: For URL encoding database credentials.
*   **Database Management Tool:** MySQL Workbench (for setting up the database and importing CSV).

## 6. Setup and Execution

To run this project on your local machine:

### Prerequisites
*   Python 3.x installed.
*   MySQL Server installed and running locally.
*   MySQL Workbench (recommended for database setup).
*   Jupyter Notebook installed.

### Installation
1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/YourGitHubUsername/Telco-Churn-Analysis.git
    cd Telco-Churn-Analysis
    ```
    *(If not using Git, just download the project folder.)*
2.  **Install Python Libraries:**
    ```bash
    pip install pandas numpy matplotlib seaborn sqlalchemy mysql-connector-python notebook
    ```
    *(If using Anaconda, consider `conda install ...` instead.)*

### Database Setup (MySQL)
1.  **Download the Dataset:** Download `WA_Fn-UseC_-Telco-Customer-Churn.csv` from the [Kaggle link](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) provided above and place it in your project directory.
2.  **Create Database:**
    *   Open MySQL Workbench and connect to your local MySQL server.
    *   Execute the following SQL command to create a new database:
        ```sql
        CREATE DATABASE IF NOT EXISTS telecom_churn;
        USE telecom_churn;
        ```
3.  **Create Table and Import Data:**
    *   Right-click on the `telecom_churn` database in MySQL Workbench and select "Table Data Import Wizard".
    *   Browse to your downloaded `WA_Fn-UseC_-Telco-Customer-Churn.csv` file.
    *   Follow the wizard. It will guide you through creating a new table (e.g., named `telco_data`) and importing the CSV data. Ensure column types are correctly inferred (e.g., `VARCHAR` for text, `INT` for numbers, `DECIMAL` or `FLOAT` for charges).
    *   *Alternatively, you can manually create the table schema and then use `LOAD DATA INFILE`.*
        ```sql
        -- Example table creation script if not using wizard:
        CREATE TABLE telco_data (
            customerID VARCHAR(20),
            gender VARCHAR(10),
            SeniorCitizen INT,
            Partner VARCHAR(5),
            Dependents VARCHAR(5),
            tenure INT,
            PhoneService VARCHAR(5),
            MultipleLines VARCHAR(20),
            InternetService VARCHAR(20),
            OnlineSecurity VARCHAR(20),
            OnlineBackup VARCHAR(20),
            DeviceProtection VARCHAR(20),
            TechSupport VARCHAR(20),
            StreamingTV VARCHAR(20),
            StreamingMovies VARCHAR(20),
            Contract VARCHAR(20),
            PaperlessBilling VARCHAR(5),
            PaymentMethod VARCHAR(30),
            MonthlyCharges DECIMAL(10,2),
            TotalCharges VARCHAR(20), -- Import as VARCHAR first due to potential empty strings
            Churn VARCHAR(5)
        );
        -- Then use LOAD DATA INFILE 'path/to/WA_Fn-UseC_-Telco-Customer-Churn.csv' INTO TABLE telco_data ...
        -- However, the wizard is generally easier.
        ```
4.  **Update Database Credentials:**
    *   Open the `Telco_Churn_Analysis.ipynb` notebook.
    *   Locate the `DB_CONFIG` dictionary in **Phase 2: Data Extraction & Cleaning**.
    *   Update `'user'` and `'password'` with your MySQL credentials. Ensure your password handles special characters correctly as discussed in the notebook (using `urllib.parse.quote_plus`).

### Running the Jupyter Notebook
1.  **Start Jupyter Lab/Notebook:**
    ```bash
    jupyter notebook
    ```
    or
    ```bash
    jupyter lab
    ```
2.  **Open the Notebook:** Navigate to and open `Telco_Churn_Analysis.ipynb`.
3.  **Run All Cells:** Go to `Kernel -> Restart & Run All` to execute the entire analysis pipeline.

## 7. Key Findings & Recommendations

The detailed analysis, visualizations, and a comprehensive final report with specific churn rates and actionable recommendations are provided within the Jupyter Notebook under the "Final Report" section.

**Summary of Key Findings:**
*   A significant portion of customers churned, indicating a critical retention issue.
*   Month-to-month contracts exhibit drastically higher churn rates compared to longer-term contracts.
*   Customers with Fiber Optic internet and higher monthly charges show a notable propensity to churn.
*   The absence of crucial services like Online Security and Tech Support is strongly correlated with higher churn.

**Summary of Recommendations:**
*   Implement targeted marketing campaigns to encourage month-to-month customers to switch to longer-term contracts with incentives.
*   Offer bundled Online Security and Tech Support services, especially to high-risk groups like Fiber Optic users, to increase perceived value and reduce churn.
*   Develop enhanced onboarding and early retention programs for new customers to address initial pain points and build loyalty.

## 8. Deliverables

*   `Telco_Churn_Analysis.ipynb`: The main Jupyter Notebook containing all code, analysis, visualizations, and the final report.
*   `README.md`: This documentation file.
*   `WA_Fn-UseC_-Telco-Customer-Churn.csv`: The raw dataset used for analysis.

## 9. Future Work

*   **Machine Learning Model:** Build and evaluate classification models (e.g., Logistic Regression, Random Forest, XGBoost) to predict customer churn with higher accuracy.
*   **Feature Engineering:** Create new features from existing ones (e.g., 'TotalServices', 'ServiceRatio') to potentially improve model performance.
*   **Customer Segmentation:** Perform advanced clustering to identify distinct customer segments and tailor retention strategies further.
*   **Cost-Benefit Analysis:** Quantify the potential impact of recommendations by estimating the cost of churn versus the cost of retention initiatives.

## 10. Contact

*   **Name:** Your Name
*   **LinkedIn:** [Your LinkedIn Profile URL]
*   **GitHub:** [Your GitHub Profile URL]
