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
1,200 patient visits across 4 states (Abuja, Anambra, Lagos, Rivers) and 6 departments, Jan–Dec 2025. Also includes State_Targets and a Date dimension table.

## Tools Used
Power BI Desktop, Power Query, DAX

## Data Cleaning Process
I cleaned the data, performed clean and trim on text columns, and ensured data formats were correctly set (date for the dates, whole number for visits and age, decimal for the ratings column). I then created a new table to store the measures so they would be organised and easy to access. 

## Data Model
My data model was a one-to-many model aimed at the Fact_Visits table from both the Dim_Dates and Dim_State_Targets tables.

## DAX Measures
1. Total Patients        = DISTINCTCOUNT(Fact_Visits[Patient_ID])
2. Total Visits          = SUM(Fact_Visits[Visit_Count])
3. Total Revenue         = SUM(Fact_Visits[Revenue_NGN])
4. Total Cost            = SUM(Fact_Visits[Cost_NGN])
5. Total Profit          = [Total Revenue] - [Total Cost]
6. Profit Margin %       = DIVIDE([Total Profit], [Total Revenue])
7. Avg Revenue Per Patient = DIVIDE([Total Revenue], [Total Patients])
8. Avg Waiting Time      = AVERAGE(Fact_Visits[Waiting_Time_Min])
9. Avg Satisfaction      = AVERAGE(Fact_Visits[Satisfaction_Score])
10. Previous Month Revenue = CALCULATE([Total Revenue], DATEADD(Dim_Date[Date], -1, MONTH))
11. MoM Revenue Growth %   = DIVIDE([Total Revenue] - [Previous Month Revenue], [Previous Month Revenue])
12. Previous Year Revenue  = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR(Dim_Date[Date]))
13. YoY Revenue Growth %   = DIVIDE([Total Revenue] - [Previous Year Revenue], [Previous Year Revenue])
14. Revenue Target   = SUM(Dim_State_Targets[Annual_Revenue_Target_NGN])
15. Revenue Variance = [Total Revenue] - [Revenue Target]
16. Achievement %    = DIVIDE([Total Revenue], [Revenue Target])

## Key Insights
1. No state is close to its revenue target. Achievement ranges from 20.6% (Anambra) to 27.5% (Abuja) of annual targets.
2. Patient volume is fairly even across departments, so no single bottleneck department exists. Pediatrics (221 patients) and Outpatient (211) lead, but the spread across all 6 departments is narrow (189–221).
3. Waiting time shows almost no relationship with satisfaction (correlation ≈ 0.002). This contradicts the common assumption that longer waits drive dissatisfaction.
4. Three in four patients (74%) are returning patients (Visit_Count > 1), suggesting strong patient retention.
5. Malaria, Typhoid and Hypertension together account for ~58% of all diagnoses.

## Recommendations
1. Management should review revenue targets that were set; all states margins are similar and low, which suggests that the targets set might be unrealistic. Implement a mid-year target recalibration benchmarked against actual patient volume and service, rather than a flat annual number.
2. A follow-up analysis on staff-to-patient ratios per branch to confirm the theory that a particular branch is responsible for the service problem experienced as opposed to the department initially thought to be contributing.
3. Management should not prioritize wait-time-reduction initiatives as a satisfaction lever; the data doesn't support that assumption, and resources aimed there may not move the needle. A patient survey should assess staff interaction quality, clarity of diagnosis/communication, and payment/insurance friction as satisfaction drivers.
4. Since recurring visits drive the dominant demand, shift operational planning investment from new-patient acquisition toward retention-servicing infrastructure (appointment systems, recall reminders, chronic-case management), and flag this to finance/strategy—a retention-heavy patient base requires fundamentally different revenue forecasting and growth assumptions than acquisition-led models.
5. Pilot a outreach program targeting these three conditions specifically (seasonal malaria prevention campaigns, water/sanitation-linked typhoid awareness, hypertension screening drives) to reduce the recurrence in the highest-volume diagnoses. Also, track diagnosis-recurrence rate per patient as a new metric going forward, since it is not currently in the dataset but would directly measure whether such a program works.

## Conclusion
This project transformed 1,200 raw patient visit records into a five-page interactive Power BI dashboard covering executive performance, patient demographics, operational efficiency, financial results, and patient experience. Beyond visualization, the analysis surfaced findings that do not align with default assumptions, most notably that waiting time shows no measurable relationship with patient satisfaction, and that every state in the organization is tracking well below its annual revenue target, pointing to a target-setting issue rather than isolated underperformance.

The goal throughout was a dashboard management can actually act on: KPIs tied to specific recommendations, conditional formatting that flags what needs attention rather than just displaying numbers, and cross-page interactivity (drill-through, synced slicers, field parameters) that lets a decision-maker move from a high-level number to the branch or department behind it in a few clicks. The data modelling (star schema, dedicated measures table, marked date table) and 15+ DAX measures underpinning it were built to support that goal, not just to satisfy a technical checklist.
