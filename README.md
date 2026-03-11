# Data Porfolio: HR Analytics Dashboard

---

## Table of Contents
- [Objective](#objective)
- [Tools Used](#tools-used)
- [Dataset](#dataset)
- [Dashboard Pages](#dashboard-pages)
- [Key Insights](#key-insights)
- [DAX Measures](#dax-measures)

---

## Objective

Help HR teams and management quickly understand:
- Overall workforce composition
- Attrition trends and root causes
- Individual employee details for deeper investigation

---

## Tools Used

| Tool | Purpose |
|---|---|
| Power BI | Dashboard & Visualization |
| Excel / CSV | Data Source |
| DAX | Calculated Measures |

---

## Dataset

**Source:** HRDataset_v14.csv

| Column | Description |
|---|---|
| EmpID | Unique employee identifier |
| Sex | Gender (M/F) |
| Department | Department name |
| Salary | Annual salary |
| DateofHire | Hire date |
| DateofTermination | Termination date (if applicable) |
| TermReason | Reason for leaving |
| CitizenDesc | Citizenship status |
| MaritalDesc | Marital status |
| RaceDesc | Race/ethnicity |
| EmploymentStatus | Active or Terminated |

---

## Dashboard Pages

### 1. Overview
Provides a high-level snapshot of the entire workforce.

<img width="893" height="499" alt="page 1" src="https://github.com/user-attachments/assets/7b152446-ce98-4740-91e6-df742c490f51" />


**Visuals included:**
- **KPI Cards:** Total Employees (311), AVG Salary ($69K), Attrition Rate (50.24%)
- **Donut Charts:** Employee distribution by Sex, Citizenship, Marital Status
- **Bar Charts:** Employee count by Department, Race, and Age Band

---

### 2. Attrition
Focuses on employee turnover — who left, when, and why.

<img width="893" height="497" alt="page 2" src="https://github.com/user-attachments/assets/4255407c-7056-426c-8b85-ddffba81d50a" />


**Visuals included:**
- **KPI Cards:** Terminated Employees (104), Active Employees (207), Attrition Rate (50.24%)
- **Donut Chart:** Terminated employees by Sex
- **Line Chart:** Attrition Rate trend by Year (2010–2018)
- **Bar Chart:** Termination reasons ranked (top reason: *Another position*)

---

### 3. Employee Details
A detailed, filterable table for individual employee records.

<img width="892" height="499" alt="page 3" src="https://github.com/user-attachments/assets/65554627-2027-4854-bd4a-e8914ed7c1c6" />


**Filters available:** Position, Department, Year

**Columns shown:** EmpID, Employee Name, Sex, CitizenDesc, Year, Quarter, Month, Day, Department, Date of Hire, Date of Termination, Age Band

---

## Key Insights

- **56.59%** of the workforce is male; **43.41%** female
- **94.86%** of employees are US Citizens
- **Production** is the largest department by headcount
- The **40–49** age band has the most employees
- Top reason employees leave: **found another position elsewhere**
- Attrition spiked sharply from **2016 to 2018**, signaling potential internal issues in that period
- Despite having more male employees overall, terminated employees skew **57.69% male**

---

## DAX Measures

```dax
-- Total Employees
Total Employees = COUNT(HRDataset[EmpID])

-- Terminated Employees
Terminated Employees = 
    CALCULATE(COUNT(HRDataset[EmpID]), HRDataset[Termd] = 1)

-- Active Employees
Active Employees = 
    CALCULATE(COUNT(HRDataset[EmpID]), HRDataset[Termd] = 0)

-- Attrition Rate
Attrition Rate = 
    DIVIDE([Terminated Employees], [Total Employees], 0)

-- Average Salary
AVG Salary = AVERAGE(HRDataset[Salary])
```

---

## Repository Structure

```
 hr-analytics-dashboard
 ┣  assets
 ┃ ┣  images        ← Dashboard screenshots
 ┃ ┗  dataset       ← HRDataset_v14.csv
 ┣  README.md
 ┗  _config.yml
```

---

*Built as a portfolio project to demonstrate end-to-end data analysis skills using real-world HR data.*
