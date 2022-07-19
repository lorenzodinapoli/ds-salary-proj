# ds-salary-proj
repo for end-to-end data scientist salary prediction

	- Created a tool to estimate data scientist salaries (MAE = 25.52k)to help data scientist negotiate their salary
	- Engineered features from text of each job description to quantify the value companies put on skills such as python, R, spark, and excel
	- Optimized linear, Lasso, and Random Forest Regressor using Random Search CV (preferred over Grid Search CV for running time optimization)
		to reach the best model
	- Built a client facing API using Flask.

## Code and Resources Used
**Python Version:** 3.9

**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, flask, json, pickle

**Data:** for the project are from Kaggle: https://www.kaggle.com/datasets/andrewmvd/data-scientist-jobs

**Flask Productionization:** https://towardsdatascience.com/productionize-a-machine-learning-model-with-flask-and-heroku-8201260503d2

## Data

This dataset contains more than 3900 job listing for data scientist positions, with the following features:

	- ID
	- Job Title
	- Salary Estimate
	- Job Description
	- Rating
	- Company Name
	- Location
	- Headquarters
	- Size
	- Founded
	- Type of ownership
	- Industry
	- Sector
	- Revenue
	- Competitors

## Data Cleaning

The dataset from Kaggle was filled with raw data scraped from Glassdoor so a lot of data cleaning was needed. The following variables were either changed or created:

	- Extracted numeric data from salary
	- Created columns for employer provided salary and hourly wages
	- Removed all the rows that didn't have a salary
	- Parsed rating out of company text
	- Created a new column for company state
	- Created a new column if the job listed was at company's HQ
	- Transformed founded date into age of the company
	- Made columns if different list were listed in job description:
		- Python
		- R
		- Excel
		- AWS
		- Spark
	- Column for simplified job title and seniority
	- Column for description length

## EDA

In the exploration phase I looked at the distribution of the data and the value counts for the categorical variables as well as to the correlation matrix of the main variables.

Value counts of categorical variables:
![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/location.png "Location")
![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/revenues.png "Revenues")
![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/sector.png "Sector")
![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/size.png "Company Size")
![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/company_name.png "Company Name")


![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/avg_salary.png "Average Salary by Role")
![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/avg_salary_seniority.png "Average Salary by Role and Seniority")
![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/avg_salary_state.png "Average Salary by State")


![alt text](https://github.com/lorenzodinapoli/ds-salary-proj/blob/main/images/word_cloud.png "World Cloud")



## Model Building

The first step has been to transform all categorical variables into dummy variables. Then split the data into train and test set with a test size of 20%.


I then decided to use three models and evaluate them by using the Mean Absolute Error, because of it is relative simple to interpret and because it doesn't suffer excessively from potential outliers.

The three different models used are:

		**Multiple Linear Regression:** Baseline for the model
	 	**Lasso Regression:** Since we have a lot of dummy variables that make the data very sparse having a regularization system might make sense
		**Random Forest:** This could be a good fit also because of the sparsity of the data

## Model Performance

After developing our models and applied RandomSearchCV (in order to save time when optimizing, GridSearchCV was taking too long for my hardware) the best performing models based on MAE are:

	**Random Forest:** 25.52
	**Lasso Regression:** 25.67
	**Linear Regression:** 25.92






















