# Healthcare Analytics Dashboard

## Project Overview

This project involves the development of a dynamic Power BI dashboard designed to provide actionable insights into hospital operations, patient demographics, and service quality. By analyzing patient flow, wait times, and satisfaction levels, the dashboard enables healthcare administrators to identify bottlenecks, understand patient segmentation, and improve overall hospital efficiency.

## Business Problem

Hospital management often struggles to balance patient volume with quality of care. Key challenges addressed by this project include:

- **Operational Bottlenecks**: Identifying peak visit periods and excessive wait times. 
- **Service Quality Gaps**: Monitoring patient satisfaction and identifying groups (by age or race) that may be underserved.
- **Resource Allocation**: Understanding the ratio of administrative to clinical patients and departmental referral patterns.

## Dataset Description

The analysis is based on a patient dataset (CSV format) containing granular encounter details:

- **Patient Demographics**: Age, Race, and Gender.
- **Clinical Data**: Wait Time (minutes), Patient Satisfaction Score (1-10 scale), and Department Referral.
- **Administrative Data**: Patient Admin Flag (boolean indicator for administrative status).
- **Temporal Data**: Date and Time of visit, including AM/PM indicators.


## Data Preparation & Transformation

Data was cleaned and structured in Power Query to ensure analytical readiness:
- **Data Profiling**: Enabled "Column Quality" to identify missing values (e.g., 72% of satisfaction scores were empty, representing "No Rating").
- **Column Splitting**: Extracted "Moment" (AM/PM) from the Date/Time column and converted the remainder to a standard Date format. - **Custom Columns**: Created a "Full Name" column by merging first and last names for unique identification.

## Data Modeling
A  **Star Schema** approach was utilized:
- **Fact Table**: Patient Data Set containing all encounter metrics.
- **Dimension Table**: A custom Date Table generated via CALENDARAUTO with attributes for Year, Month, Weekday, and Weekend.
- **Measure Table**: A disconnected table named "Calculation" was created to house all DAX measures for better organization.

## Dashboard Features
- **Dynamic Measure Switching**: A field parameter allows users to toggle the entire heatmap between "Average Wait Time" and "Average Satisfaction."
- **Temporal Filtering**: Slicers for Year and "Moment" (AM/PM) to analyze shift-based performance.
- **Auto-Highlighting**: The trend line automatically highlights the months with the maximum and minimum patient visits using conditional formatting.

## Key KPIs
- **Total Patient Visits**: Volume of hospital encounters.
- **Average Wait Time**: Mean minutes spent waiting before being seen.
- **Average Satisfaction Score**: Rated quality of care (excluding non-responses).
- **Admin vs. Non-Admin %**: Proportion of patients with administrative status.
- **No Rating %**: Percentage of patients who opted out of the feedback survey.


## Visualizations Used
- **Heatmap**: Analyzes Wait Time/Satisfaction across Race and Age Buckets.
- **Line Chart**: Displays patient visit trends over time with max/min markers.
- **Bar/Column Charts**: Shows patient distribution by Age Group and Department Referral.
- **Donut/Card Visuals**: Highlighting referral percentages (Referred vs. Unreferred).


## Business Insights

- **Peak Demand**: Monthly and yearly trends reveal specific periods of high volume, allowing for better staff scheduling.
- **Demographic Wait Variance**: The heatmap identifies if specific ethnic groups or age ranges experience disproportionately longer wait times.
- **Feedback Gaps**: A high "No Rating" percentage (72%) suggests the hospital needs more proactive ways to collect patient feedback to ensure data reliability.
- **Referral Analysis**: A significant portion of patients are "Unreferred," indicating high walk-in volume versus scheduled departmental visits.


## Dashboard Screenshots

![Dashboard Overview](dashboard/Final_Dashboard.png)


## Technology Stack

- **Power BI Desktop**: Data modeling, DAX, and visualization.
- **Power Query**: ETL (Extract, Transform, Load) processes.
- **PowerPoint**: Custom UI background and layout design.