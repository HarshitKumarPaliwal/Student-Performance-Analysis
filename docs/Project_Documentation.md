# Project Documentation - Student Performance Analysis

## 1. Objective
Analyse marks and attendance of 50 students to find top and low performers, weak subjects, and the effect of attendance, then present everything in a dashboard.

## 2. Dataset (fictional, 50 rows)
| Column | Meaning | Type |
|---|---|---|
| Student ID | S001 - S050 | Input |
| Student Name, Gender, Section | Student details (Section A / B / C) | Input |
| Math, Science, English, Computer, Social | Marks out of 100 | Input |
| Attendance % | Share of classes attended | Input |
| Total Marks | Sum of 5 subjects (out of 500) | **Formula** `=SUM(E2:I2)` |
| Percentage | Total / 500 | **Formula** |
| Result | Pass only if every subject is at least 35 | **Formula** `=IF(MIN(E2:I2)>=35,"Pass","Fail")` |
| Grade | A+ / A / B / C / D / E, or F if failed | **Formula** (LOOKUP on the Assumptions grade table) |
| Performance Category | Top Performer / Good / Average / Low Performer | **Formula** |
| Rank | 1 = highest percentage (ties broken by row order) | **Formula** `RANK + COUNTIF` |
| Attendance Status | Good if 75% or more, else Low | **Formula** |

## 3. Business rules (Assumptions sheet)
- Pass mark: **35 in every subject**; minimum attendance **75%**.
- Grades: A+ 90%+, A 80%+, B 70%+, C 60%+, D 50%+, E below 50%; failed students get F.
- Categories: Top Performer 80%+, Good 65%+, Average 50%+, Low Performer below 50% or failed.

## 4. Step-by-step (simple language)
1. **Create the data** - 50 students with names, gender, section, 5 subject marks and attendance.
2. **Check the data** - all marks are between 0 and 100, no blanks, no duplicate Student IDs.
3. **Add calculated columns** - Total, Percentage, Result, Grade, Category, Rank using formulas (never typed by hand).
4. **Set rules in one place** - the Assumptions sheet, so a rule change needs no formula edits.
5. **Build summary tables** (Analysis sheet) with COUNTIF, AVERAGEIF, COUNTIFS - these work like PivotTables.
6. **Find Top 10 / Bottom 10** - using Rank with INDEX + MATCH.
7. **Check attendance vs marks** - attendance bands and CORREL.
8. **Create the dashboard** - KPI cards and 6 charts that read from the Analysis sheet.
9. **Practise real PivotTables** - follow the Pivot_Guide sheet and confirm numbers match.
10. **Write insights and recommendations** (below).

## 5. Results
**Overall:** 50 students | average 67.2% | highest 88.4% | lowest 44.0% | pass rate 96.0% | average attendance 81.0% | 10 students below 75% attendance.

**Grades:** A+: 0, A: 7, B: 17, C: 11, D: 12, E: 1, F: 2

**Subject analysis**
| Subject | Average | Highest | Lowest | Passed | Pass % |
|---|---|---|---|---|---|
| Math | 64.5 | 93 | 26 | 48 | 96% |
| Science | 67.9 | 94 | 46 | 50 | 100% |
| English | 67.5 | 98 | 42 | 50 | 100% |
| Computer | 69.6 | 91 | 42 | 50 | 100% |
| Social | 66.2 | 100 | 39 | 50 | 100% |

**By section**
| Section | Students | Avg % | Pass rate | Avg attendance |
|---|---|---|---|---|
| A | 17 | 67.5% | 100.0% | 81.6% |
| B | 17 | 69.6% | 100.0% | 81.6% |
| C | 16 | 64.3% | 87.5% | 79.6% |

**By gender**
| Gender | Students | Avg % | Pass rate | Avg attendance |
|---|---|---|---|---|
| Male | 25 | 64.9% | 92.0% | 81.2% |
| Female | 25 | 69.4% | 100.0% | 80.7% |

**Attendance vs performance** (correlation = 0.70)
| Attendance band | Students | Avg % | Pass rate |
|---|---|---|---|
| Below 75% | 10 | 54.5% | 80% |
| 75% - 84% | 25 | 66.7% | 100% |
| 85% - 94% | 14 | 76.0% | 100% |
| 95% and above | 1 | 82.8% | 100% |

**Top 10 students**
| Rank | ID | Name | Section | % | Attendance |
|---|---|---|---|---|---|
| 1 | S042 | Yash Malhotra | C | 88.4% | 94% |
| 2 | S023 | Kavya Reddy | B | 85.6% | 83% |
| 3 | S043 | Varun Tiwari | A | 83.6% | 88% |
| 4 | S013 | Anjali Reddy | A | 82.8% | 95% |
| 5 | S004 | Tanya Agarwal | A | 81.6% | 92% |
| 6 | S018 | Tanvi Mishra | C | 80.8% | 82% |
| 7 | S047 | Divya Pandey | B | 80.0% | 93% |
| 8 | S049 | Kunal Tiwari | A | 79.6% | 91% |
| 9 | S038 | Vikas Chauhan | B | 78.6% | 91% |
| 10 | S046 | Meera Bansal | A | 78.4% | 85% |

**Bottom 10 students**
| Rank | ID | Name | Section | % | Attendance | Result |
|---|---|---|---|---|---|---|
| 50 | S048 | Vivaan Saxena | C | 44.0% | 70% | Fail |
| 49 | S015 | Sahil Sharma | C | 47.2% | 72% | Fail |
| 48 | S009 | Khushi Singh | C | 47.2% | 68% | Pass |
| 47 | S022 | Manish Jain | A | 50.0% | 74% | Pass |
| 46 | S010 | Mohit Yadav | A | 50.0% | 76% | Pass |
| 45 | S034 | Nikhil Bansal | A | 50.6% | 70% | Pass |
| 44 | S014 | Naveen Yadav | B | 54.0% | 71% | Pass |
| 43 | S007 | Sakshi Yadav | A | 55.0% | 75% | Pass |
| 42 | S033 | Pooja Patel | C | 55.2% | 80% | Pass |
| 41 | S027 | Deepak Gupta | C | 56.0% | 75% | Pass |

## 6. Business insights
1. **Overall performance is healthy but not outstanding** - average 67.2%; most students sit in the Good (65-80%) and Average bands.
2. **Math is the weakest subject** (average 64.5); Computer is the strongest (69.6). All 2 failures (Sahil Sharma (S015), Vivaan Saxena (S048)) came from Math (below 35).
3. **Attendance matters.** Correlation is 0.70. Students under 75% attendance average 54.5%, about 22 points below the 85-94% group.
4. **Section C needs attention** - lowest average (64.3%) and the only section with failures; Section B is strongest (69.6%).
5. **Every failed student also had attendance under 75%**, so attendance is an early-warning signal.
6. Gender: female students average 69.4% vs male 64.9% in this sample (small sample - do not generalise).

## 7. Recommendations
- Run extra **Math support classes**, especially for Section C.
- Create an **attendance alert**: contact students and parents when attendance falls below 75%.
- Pair Top Performers with the Bottom 10 as study buddies.
- Track the dashboard every term to see whether interventions work.

## 8. Limitations
- Fictional dataset with 50 rows, one term only; correlation does not prove cause.
- Pass rule (35 per subject) and grade bands are assumptions and can be changed in the Assumptions sheet.
