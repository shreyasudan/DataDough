# DataDough 💸🤑

DataDough is a comprehensive analysis of publicly available data sourced from [kaggle](https://www.kaggle.com/datasets/arnabchaki/data-science-salaries-2023), conducted by Shreya Sudan. It encompasses a series of rigorous analytical procedures, including data cleansing, exploratory data analysis, data visualizations, hypothesis testing, and predictive analysis.

## Introduction 🤓
Welcome to DataDough, a data science project focused on exploring the fascinating realm of data and uncovering insights related to salaries of data scientists. In today's data-driven world, understanding the factors that influence data scientists' salaries is crucial for both professionals and organizations alike. This project aims to shed light on the various factors that contribute to the salaries of data scientists and provide valuable insights into this ever-evolving field.

The dataset `salary` contains data on not only the salaries of data scientists, but also their experience, salary in USD, residence, company's location, and company's size. 

This project not only seeks to answer questions about salary trends but also aims to explore the relationships between different variables and their impact on compensation. By examining the interplay between factors like work experience, employment type, and company size, we aim to uncover valuable insights that can aid professionals in negotiating salaries and assist organizations in formulating competitive compensation packages.

To accomplish these objectives, we employ a range of analytical techniques and tools, including data preprocessing, exploratory data analysis, feature engineering, and machine learning algorithms. The project utilizes popular libraries like pandas, scikit-learn, and plotly to perform data manipulation, modeling, and visualization.

Here are the components of our project:
- Part I : Inferential Analysis

    - Data Cleaning
    
    - Exploratory Data Analysis (EDA)
    
    - Hypothesis Testing
    
- Part II : Predictive Analysis

    - Linear Regression Model
    
        - Framing the Problem
        
        - Baseline Model
        
        - Final Model
        
    - Multiclass Classification
    
        - Random Forest Classifier
        
        - Decision Trees

By the end of DataDough, we aim to provide a comprehensive understanding of the salary landscape for data scientists, empowering both individuals and organizations with actionable insights. Whether you are a data scientist seeking to benchmark your salary or an organization looking to attract and retain top talent, this project strives to offer valuable information and assist in data-driven decision-making.

Here is a preview of the `salary` dataset:
|   work_year | experience_level   | employment_type   | job_title                |   salary | salary_currency   |   salary_in_usd | employee_residence   |   remote_ratio | company_location   | company_size   |
|------------:|:-------------------|:------------------|:-------------------------|---------:|:------------------|----------------:|:---------------------|---------------:|:-------------------|:---------------|
|        2023 | SE                 | FT                | Principal Data Scientist |    80000 | EUR               |           85847 | ES                   |            100 | ES                 | L              |
|        2023 | MI                 | CT                | ML Engineer              |    30000 | USD               |           30000 | US                   |            100 | US                 | S              |
|        2023 | MI                 | CT                | ML Engineer              |    25500 | USD               |           25500 | US                   |            100 | US                 | S              |
|        2023 | SE                 | FT                | Data Scientist           |   175000 | USD               |          175000 | CA                   |            100 | CA                 | M              |
|        2023 | SE                 | FT                | Data Scientist           |   120000 | USD               |          120000 | CA                   |            100 | CA                 | M              |

