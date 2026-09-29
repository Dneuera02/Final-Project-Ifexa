# Final-Project-Ifexa
Final project dashboard build for IFEXA data analysis class
# IFEXA Healthcare Performance & Patient Analytics Dashboard

## Project Overview
The project is a business analysis for a hospital, aimed at aiding management decision-making processes. It shows the performance of a healthcare organisation in terms of quality of care across different departments and states. 

## Business Problem
1. Which age group represents the largest number of patients?
2. Which diagnoses are most common?
3. Which states have the highest patient volume?
4. How many patients are returning?
5. What are the most common patient outcomes?
6. Which department receives the most patients?
7. Which department has the longest waiting time?
8. Which branch handles the most visits?
9. Which departments have lower satisfaction scores?
10. Are there operational areas management should investigate?
11. Which state generates the most revenue?
12. Which department generates the most profit?
13. Which services generate the most revenue?
14. Are states meeting their revenue targets?
15. Which areas require further financial investigation?
16. Which department has the highest satisfaction?
17. Which branch has the lowest satisfaction?
18. What is the relationship between waiting time and satisfaction?
19. Which patient outcomes occur most frequently?

## Dataset Description
1,200 patient visits across 4 states (Abuja, Anambra, Lagos, Rivers) and
6 departments, Jan–Dec 2025. Also includes State_Targets and a Date dimension table.

## Tools Used
Power BI Desktop, Power Query, DAX

## Data Cleaning Process
I cleaned the data, performed clean and trim on text columns, and ensured data formats were correctly set (date for the dates, whole number for visits and age, decimal for the ratings column)
I then created a new table to store the measures so they will be organised and easy to access. 

## Data Model
My data model was a one-to-many model aimed at the Fact_Visits table from both the Dim_Dates and Dim_State_Targets tables.

## DAX Measures
[List all 15+ with one-line explanations, or link to docs/dax_measures.md]

## Dashboard Screenshots
![Executive Overview](screenshots/page1_executive_overview.png)
![Patient Analysis](screenshots/page2_patient_analysis.png)
[...etc for all 5 pages]

## Key Insights
[Your 5 insights — the revenue-target gap, department volume spread,
wait-time/satisfaction non-relationship, returning-patient share,
top-3 diagnoses]

## Recommendations
[What management should investigate, tied to each insight]

## Conclusion
[2-3 sentences wrapping it up]
