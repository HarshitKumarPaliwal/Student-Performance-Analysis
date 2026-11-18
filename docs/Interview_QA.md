# Interview Questions & Answers - Student Performance Analysis

**Q1. Explain this project in 30 seconds.**
I analysed marks, attendance and results of 50 students in Excel. I calculated total, percentage, result, grade and rank with formulas, built summary tables and a dashboard, and found that Math was the weakest subject and that low attendance was linked to low marks (correlation 0.70).

**Q2. What was the business problem?**
A college wants to identify weak students and subjects early so it can support them before exams.

**Q3. Where did the data come from?**
It is a fictional dataset I created for practice with realistic marks and attendance. In a real job it would come from the college ERP or exam system exported as CSV/Excel.

**Q4. What formula decides Pass/Fail?**
`=IF(MIN(E2:I2)>=35,"Pass","Fail")` - the student passes only if the lowest subject mark is at least 35.

**Q5. How did you calculate Rank, and how did you handle ties?**
`=RANK(L2,$L$2:$L$51,0)+COUNTIF($L$2:L2,L2)-1`. The COUNTIF part gives tied students different ranks so that INDEX/MATCH can find every student in the Top 10 list.

**Q6. Why use LOOKUP for grades instead of nested IFs?**
The grade bands sit in a table on the Assumptions sheet. If the college changes a cut-off, I edit one cell and nothing else breaks.

**Q7. What is the difference between COUNTIF and COUNTIFS? AVERAGEIF?**
COUNTIF counts with one condition; COUNTIFS with several. AVERAGEIF averages a column for rows that meet a condition (e.g. average percentage for Section A).

**Q8. What is a PivotTable and how is it different from your summary tables?**
A PivotTable summarises data by dragging fields into Rows/Columns/Values. My Analysis sheet builds the same tables with formulas; the Pivot_Guide sheet explains how to create the PivotTables, and I verified both give the same numbers.

**Q9. Which insight was most important?**
Attendance: students below 75% attendance averaged 54.5% compared with 76.0% for the 85-94% group, and all 2 failures had attendance under 75%.

**Q10. What is correlation? What does 0.70 mean?**
Correlation (-1 to +1) shows how two numbers move together. 0.70 means a strong positive relationship - higher attendance goes with higher marks. It does not prove attendance *causes* higher marks.

**Q11. Which subject is weakest and what would you recommend?**
Math (average 64.5). I would recommend extra classes and practice tests, starting with Section C.

**Q12. How do you make sure your numbers are correct?**
I cross-checked totals, percentages, pass counts and averages with an independent calculation; section counts add up to 50 and the grade counts add up to 50.

**Q13. What would you improve with more time?**
Use data from several terms, add trend charts, add subject-wise pass/fail by section, and connect the file to Power BI.

**Q14. Why a dashboard?**
Managers do not read 50 rows. A dashboard shows the KPIs and charts on one screen so decisions are quick.

**Q15. What were the challenges?**
Handling ties in the ranking, avoiding hard-coded numbers, and making every chart read from formula tables so it updates automatically.
