# IncidentTicketAnalysis
Analyze the duration of Incident tickets

## Installation
Python:
matplotlib.pyplot
sklearn.linear_model
sklearn.model_selection
sklearn.metrics
scipy
seaborn

## Project motivation
Business Questions:
1. What are the factors that influence the time to resolve incident tickets?
2. Is there a difference in ticket resolution time between vendors?
3. Can customer satisfaction be related to the resolution time?

While incident ticket resolution timelines are generally available through various dashboards,
the factors can not always be compared given the difference in context.
Therefore looked for a way to standardize the data in a way to enable comparisons.

## File Descriptions
Code:
IncidentTicketAnalysis.ipynb (Jupyter notebook / Python code)

Input:
Incidents.xlsx (subset of fields extracted from EDL through a SQL query and manually anonymized)

Output:
ttr_days.png (histogram of the actual time to resolve)
diff.png (histogram of the time difference: actual - predicted)
assignment_group_company.png (boxplot of the time difference, showing the different vendors)
cstat_score.png (boxplot of the time difference, showing the different customer satisfaction scores)
IncidentDuration_coef.xlsx (coefficients for the factors that influence the time to resolve incidents as determined through the Linear model)
Factors influencing TTR.xlsx (2 tabs: one for the increases, one for the decreases; shows values for all combination of categorical field / values: mean, t and p value)

## Technical details
Step 1: Predict the resolution times based on a set of factors using sklearn linear model
Step 2: Calculate the difference between the actual and predicted resolution time (this serves as a standardized set which is independent of the known factors)
Step 3: For each of the remaining factors - variable combinations: determine if the 'mean' of the difference is different from 0 (by means of the 1 Sample T test)

First attempted to use all of the factors as input to the linear model.
This resulted in significant overfitting and very high coefficient values.
Therefore opted for a 2 step approach using a combination of a linear model and Ttest statistics.

## Licensing, Authors, Acknowledgements
Made use of Udacity course materials
Bart Leplae

