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

## Part I : Inferential Analysis 🔬🔬
### Data Cleaning 🧹 🧽
After looking at some preliminary statistics for `salary`, we decided to undertake the following steps to clean our data and prepare it for use:

1. `remote_ratio` column was divided by 100 to ensure scalability and correctness if the column were to be used as a numeric feature in a model.
2. `work_year` was converted to string type as it is a categorical feature here and the interpretation of the 'mean' of the `work_year` in the descriptive statistics is meaningless.

Here are the premliminary descriptive statistics of `salary`:

|       |   work_year |        salary |   salary_in_usd |   remote_ratio |
|:------|------------:|--------------:|----------------:|---------------:|
| count | 3755        |   3755        |          3755   |      3755      |
| mean  | 2022.37     | 190696        |        137570   |        46.2716 |
| std   |    0.691448 | 671677        |         63055.6 |        48.5891 |
| min   | 2020        |   6000        |          5132   |         0      |
| 25%   | 2022        | 100000        |         95000   |         0      |
| 50%   | 2022        | 138000        |        135000   |         0      |
| 75%   | 2023        | 180000        |        175000   |       100      |
| max   | 2023        |      3.04e+07 |        450000   |       100      | 

And the first few rows of the cleaned dataset `salary`

|   work_year | experience_level   | employment_type   | job_title                |   salary | salary_currency   |   salary_in_usd | employee_residence   |   remote_ratio | company_location   | company_size   |
|------------:|:-------------------|:------------------|:-------------------------|---------:|:------------------|----------------:|:---------------------|---------------:|:-------------------|:---------------|
|        2023 | SE                 | FT                | Principal Data Scientist |    80000 | EUR               |           85847 | ES                   |              1 | ES                 | L              |
|        2023 | MI                 | CT                | ML Engineer              |    30000 | USD               |           30000 | US                   |              1 | US                 | S              |
|        2023 | MI                 | CT                | ML Engineer              |    25500 | USD               |           25500 | US                   |              1 | US                 | S              |
|        2023 | SE                 | FT                | Data Scientist           |   175000 | USD               |          175000 | CA                   |              1 | CA                 | M              |
|        2023 | SE                 | FT                | Data Scientist           |   120000 | USD               |          120000 | CA                   |              1 | CA                 | M              |

### EDA 📊
As part of our EDA we explored the relationship and the distribution of the following variables:
1. The Distribution of `salary_in_usd`
    - **Observations**: The distribution of salaries (USD) is fairly normal, and slightly right-skewed. It's a unimodal histogram with its peak at `$150,000-$155,000`
    
      <iframe src="assets/edaFirst.html" width=800 height=600 frameBorder=0></iframe>
    
2. The Distribution of `salary_in_usd` with respect to `company_size`
    - **Observations**: We can derive from the overlaid histogram that the medium companies are generally taller than the smaller and the larger companies. This is because the dataset contains more data-points for medium-sized companies. The boxplots accompanying the histograms confirm that the medium sized companies have more outliers and a higher median than the other two groups.
  
      <iframe src="assets/edaSecond.html" width=800 height=600 frameBorder=0></iframe>

3. The average `salary` and `salary_in_usd` as `work_year` increases
    - **Observations**: There is a steady increase in the mean `salary_in_usd` as the years increase. This could be explained by the usual rise in the general price level or inflation. However, the growth of the mean `salary` is quite peculiar. The `salary` column has a very high standard deviation, because of the disparities in the foreign ecxchange values of the different currencies. Thus, `salary_in_usd` provides a more standardized distribution of salaries.
    
      <iframe src="assets/edaThird.html" width=800 height=600 frameBorder=0></iframe>

### Hypothesis Testing 👩🏻‍🔬

**Null Hypothesis**: The distribution of salaries of different company sizes is drawn from the same population, and any differences in the distribution are purely conincidental.

**Alternative Hypothesis**: The differences in salaries are not purely coincidental

**Test Statistic**: Means

**p-value**: 0.0

**Conclusion**: It is highly unlikely that the difference in means are purely coincidental. Thus, we reject the null hypothesis.

<iframe src="assets/hypothesis.html" width=800 height=600 frameBorder=0></iframe>

## Part II : Predictive Analysis 🔮🔮
### Linear Regression 📈📈
#### Framing the Problem 🧮 🤔

**Prediction Problem**: Predict the salaries of data scientists in USD

**Response Variable**: `salary_in_usd`

**Regressors**: `work_year`, `employee_type`

**Evaluation Metric**: R²

#### Baseline Model 🧩

<iframe src="assets/baseline.html" width=800 height=600 frameBorder=0></iframe>
