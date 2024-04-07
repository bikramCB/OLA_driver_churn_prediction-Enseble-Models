# OLA_driver_churn_prediction-Enseble-Models

## Problem Statement:
Recruiting and retaining drivers is seen by industry watchers as a tough battle for Ola. Churn among drivers is high and it’s very easy for drivers to stop working for the service on the fly or jump to Uber depending on the rates.
As the companies get bigger, the high churn could become a bigger problem. To find new drivers, Ola is casting a wide net, including people who don’t have cars for jobs. But this acquisition is really costly. Losing drivers frequently impacts the morale of the organization and acquiring new drivers is more expensive than retaining existing ones.
You are working as a data scientist with the Analytics Department of Ola, focused on driver team attrition. You are provided with the monthly information for a segment of drivers for 2019 and 2020 and tasked to predict whether a driver will be leaving the company or not .

## Data
Demographics (city, age, gender etc.)
Tenure information (joining date, Last Date)
Historical data regarding the performance of the driver (Quarterly rating, Monthly business acquired, grade, Income)

MMMM-YY: Reporting Date (Monthly)
Driver_ID: Unique id for drivers
Age: Age of the driver
Gender: Gender of the driver – Male : 0, Female: 1
City: City Code of the driver
Education_Level : Education level – 0 for 10+ ,1 for 12+ ,2 for graduate
Income: Monthly average Income of the driver
Date Of Joining: Joining date for the driver
LastWorkingDate: Last date of working for the driver
Joining Designation: Designation of the driver at the time of joining
Grade: Grade of the driver at the time of reporting
Total Business Value: The total business value acquired by the driver in a month (negative business indicates cancellation/refund or car EMI adjustments)
Quarterly Rating: Quarterly rating of the driver: 1,2,3,4,5 (higher is better)

## Tech Used:
Random Forest, Decision Tree, XGboost

## Tools Used:
Numpy, Pandas, matplotlib,Sklearn

## Solutions:
1. About 20k datasets were collected from the OLA website considering drivers' reporting dates for the months of 2019 and 2020 year.
2. Age and gender column nulls value filled up by KNN (neighbor = 5) because if we use mean value distribution of the datasets might be changed.
3. driver leaves or not target variable based on last reporting date or last working date (1,0) null or has a date.
4. 'Age':'max', 'Gender':'first','City':'first',
 'Education_Level':'last', 'Income':'last',
 'Joining Designation':'last','Grade':'last',
 'Dateofjoining':'last','LastWorkingDate':'last',
 'Total Business Value':'sum','Quarterly Rating':'last'
Create a new data frame based on the above data structure.
5. Create new features quarterly rating increased, monthly income increased based on the first and last reporting date.
6.  findings :
There are 2381 employees in the dataset. The minimum age of the employee in the data is 21 years and the maximum age is 58 years. 75% of the employees have a monthly income less than or equal to 75,986 units. 50% of the employees have acquired 8,17,680 as their total business value.
7. The proportion of gender and education is more or less the same for both the employees who left the organization and those who did not leave.70% people leave and 30% people stay.
8. The employees who have their grade as 3 or 4 at the time of reporting are less likely to leave the organization.
9. The employees who have their last quarterly rating as 3 or 4 at the time of reporting are less likely to leave the organization.
10. The employees whose quarterly rating has increased are less likely to leave the organization.
11. The employees whose age is in the 20-35 or 50-65 groups are more likely to leave the organization.
12. Drivers whose monthly income 160000 - 190000 are less likely to leave the organization.
13. The employees who have acquired total business value greater than 68,00,000 are less likely to leave the organization.
14. Applied Random Forest after grid search with best depth:2, n_estimators:100 and got Presision, recall and F1 score 0.82,0.85 and 0.89 respectively.
15. Applied XGBoost classifier and  got Presision, recall and F1 score 0.81,0.86 and 0.83 respectively.
16. Received the best important business features for random forest models accordingly.

## Business Impact:
A high F1 score indicates that the model has both high precision and high recall, meaning it effectively identifies churn cases while minimizing false positives (incorrectly predicting churn) and false negatives (missed churn cases).
With a high-performing churn prediction model, Ola can effectively identify drivers who are likely to churn (leave the platform). By pinpointing these drivers early on, Ola can take proactive measures to prevent churn, such as offering incentives, bonuses, or support to retain them. This helps maintain a stable pool of drivers, ensuring consistent service availability for customers, which in turn leads to higher revenue
almost by 8% in the next year.






