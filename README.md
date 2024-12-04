# Optimizing Call Center Performance: A Monthly KPI Dashboard

Author: Charlene D’Costa <br />
Date: December 3, 2024 <br />
Final Project for the Analyst Builder: Tableau for Data Visualization course. <br />

[Tableau Dashboard](https://public.tableau.com/app/profile/charlene.d.costa/viz/CallCenterKPIDashboard_17332652973680/CallCenterKPIDashboard) <br />
[Call Center Dataset]

# Project Overview

<details>
<summary>Defining the business problem.</summary>

<br />

For this project, I built a monthly KPI dashboard for a call center's help desk to provide actionable insights for a manager. **The objective was to track employee performance metrics and gain a high-level understanding of call center operations.**

Using an Excel dataset containing 3 months of call center data, I focused on the most recent month to align with the manager's priorities. The dataset included variables such as call ID, agent name, call date and time, call topic, calls answered and resolved, speed of answer, average talk duration, and customer satisfaction ratings. To build the dashboard, I cleaned and transformed the data directly in Tableau to standardize metrics, ensure data accuracy and create meaningful visualizations.

The resulting dashboard showcases key performance indicators like resolution rates, answer speed, call volume trends, customer satisfaction distributions, and agent-level performance comparisons. These insights enable the manager to:

 - Monitor employee efficiency in real time. 
 - Identify top-performing agents and areas for improvement. 
 - Optimize staffing and resource allocation. 
 - Enhance customer satisfaction and call center efficiency.

</details>

# Data Cleaning in Tableau

<details>
<summary>Cleaning the data for analysis.</summary>

## Checking Data Types
After uploading the dataset into Tableau, my first step is to verify that the data has been imported correctly by reviewing the data types. I observed that the `Date` column was imported as a string, so it needs to be converted to a date datatype. All other data types were correct, allowing me to proceed with the analysis.

<div align="center">
<img width="404" alt="1" src="https://github.com/user-attachments/assets/20604b99-397a-4d0e-948e-0c1d602228da">
</div>

<br />

<div align="center">
<img width="411" alt="2" src="https://github.com/user-attachments/assets/71109568-c201-4fe9-9310-1968b312c0e5">
</div>

## Fixing Incorrect Data Types
Since Tableau does not have a dedicated time datatype, it automatically converts time-related data into a datetime datatype, populating the date portion with placeholder values. This condition impacted the `Time` and `AvgTalkDuration` coloumns and needs to be corrected before I proceed with building my visualizations. 

<div align="center">
<img width="468" alt="3" src="https://github.com/user-attachments/assets/06734f7a-02e3-4b67-be35-449faf7fc092">
</div>

<br />

<div align="center">
<img width="468" alt="4" src="https://github.com/user-attachments/assets/7af09b41-9945-4868-a604-e666fa3809d3">
</div>

To address this:
 - I used the `DATEPART` function to extract the hour of the call from the `Time` column. 
 - I also used the `DATEPART` function to extract the minutes and seconds from the `AvgTalkDuration` column. 

<div align="center">
<img width="351" alt="5" src="https://github.com/user-attachments/assets/c3ac53ff-ef1d-4c5c-ba71-896bfed5c419">
</div>

<br />

<div align="center">
<img width="344" alt="6" src="https://github.com/user-attachments/assets/8818c753-6549-4582-9049-76b293ad0f9b">
</div>

</details>

# Data Transformations in Tableau

<details>
<summary>Transforming the data for analysis.</summary>

## Filtering for the Most Recent Month
To focus on the most recent month of data, I created a calculated field that dynamically identifies the latest month in the dataset. 

- I used the `DATEPART` function to extract the month and year from the `Date` column. 
- I used the `MAX` function to ensure only the most recent month is included. 
- I combined the month and year for accuracy, adhering to best practices even though the dataset is limited to 2021.

The result is a Boolean field that evaluates whether each row belongs to the most recent month. I'll use this calculated field as a filter in all the visualizations I create for this dashboard.

<div align="center">
<img width="327" alt="7" src="https://github.com/user-attachments/assets/0da94c3d-86aa-4ec5-8231-b6f4c3292bea">
</div>

## Converting the ‘Resolved’ Column for Analysis
Next I transformed the `Resolved` column, which initially contains string values (‘Y’ or ‘N’) into numeric data so that I could calculate the percentage of resolved vs. unresolved calls instead of just counting them, allowing for a deeper analysis.

To address this:
- I created a calculated field using the `COUNT` and `IF` functions to:
  - Assign a value of 1 if the column equals ‘Y’ and 0 otherwise.
- I used the `SUM` function to total resolved calls and divided it by the count of all calls. 
- I converted the result into a percentage.

<div align="center">
<img width="330" alt="8" src="https://github.com/user-attachments/assets/aa033d83-cc77-4a1d-a324-dc74a217e95d">
</div>

<br />

Now that the data has been cleaned and transformed, I can proceed with building the visualizations + dashboard.

</details>
