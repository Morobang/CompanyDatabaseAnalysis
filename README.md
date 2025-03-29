# Company Database Analysis

This project delves into the company's database to extract meaningful insights regarding employee demographics, salaries, sales performance, and branch distributions. Utilizing SQL queries and data visualization tools, we aim to provide a clear understanding of the company's operational metrics.

## Table of Contents

- [Project Overview](#project-overview)
- [Database Schema](#database-schema)
- [Data Analysis Objectives](#data-analysis-objectives)
- [Tools and Technologies Used](#tools-and-technologies-used)
- [Installation and Setup](#installation-and-setup)
- [Analysis and Findings](#analysis-and-findings)
  - [Employee Salary Analysis](#employee-salary-analysis)
  - [Gender-Based Salary Comparison](#gender-based-salary-comparison)
  - [Sales Performance by Employee](#sales-performance-by-employee)
  - [Employee Distribution Across Branches](#employee-distribution-across-branches)
- [Dashboard](#dashboard)
- [Visualizations](#visualizations)
- [Conclusion](#conclusion)
- [References](#references)

## Project Overview

The objective of this project is to perform an in-depth analysis of the company's internal database to uncover insights related to employee compensation, sales achievements, and organizational structure. By leveraging SQL queries and data visualization tools, we aim to provide actionable insights that can inform strategic decisions.

## Database Schema

The analysis is based on a relational database comprising the following tables:

- `employee`: Contains information about employees, including their IDs, names, birth dates, gender, salary, supervisor ID, and branch ID.
- `branch`: Details about company branches, including branch ID, name, manager ID, and manager start date.
- `client`: Information on clients associated with each branch.
- `works_with`: Records of interactions between employees and clients, including total sales.
- `branch_supplier`: Details of suppliers associated with each branch and the types of supplies provided.

## Data Analysis Objectives

The analysis focuses on the following key areas:

1. **Employee Salary Analysis**: Identifying employees with the minimum, maximum, and average salaries.
2. **Gender-Based Salary Comparison**: Analyzing salary disparities between male and female employees.
3. **Sales Performance by Employee**: Determining which employees have achieved the highest total sales.
4. **Employee Distribution Across Branches**: Counting the number of employees working in each branch.

## Tools and Technologies Used

- **SQL Server Management Studio (SSMS)**: For querying and managing the SQL database.
- **Power BI**: For creating interactive data visualizations and dashboards.
- **DAX (Data Analysis Expressions)**: Utilized within Power BI for advanced data calculations.
- **Data Analysis Techniques**: Applied various statistical methods to interpret the data effectively.

## Installation and Setup

To replicate or build upon this analysis, follow these steps:

1. **Database Setup**:
   - Install a SQL Server instance.
   - Use the provided SQL scripts to create the database schema and populate it with data.

2. **Tools Installation**:
   - **SSMS**: Download and install from the official Microsoft website.
   - **Power BI**: Download and install from the official Power BI website.

3. **Repository Structure**:
   - Clone the `DevToolKit` repository from [https://github.com/Morobang/DevToolkit](https://github.com/Morobang/DevToolkit).
   - Navigate to the respective directories for detailed guides on each tool:
     - [Microsoft SQL Server](https://github.com/Morobang/DevToolkit/tree/main/Microsoft%20SQL%20Server)
     - [SQL](https://github.com/Morobang/DevToolkit/tree/main/SQL)
     - [Power BI](https://github.com/Morobang/DevToolkit/tree/main/Power%20Bi)
     - [DAX](https://github.com/Morobang/DevToolkit/tree/main/DAX)
     - [Data Analysis](https://github.com/Morobang/DevToolkit/tree/main/Data%20Analysis)

## Analysis and Findings

### Employee Salary Analysis

To identify employees with the minimum, maximum, and average salaries, the following SQL query was utilized:

```sql
SELECT 
    MIN(salary) AS Min_Salary,
    MAX(salary) AS Max_Salary,
    AVG(salary) AS Avg_Salary
FROM 
    employee;
```

### Gender-Based Salary Comparison

Analyzing salary differences between male and female employees:

```sql
SELECT 
    sex,
    AVG(salary) AS Avg_Salary
FROM 
    employee
GROUP BY 
    sex;
```

### Sales Performance by Employee

To determine which employees have generated the highest total sales:

```sql
SELECT 
    e.emp_id,
    e.first_name,
    e.last_name,
    SUM(ww.total_sales) AS Total_Sales
FROM 
    employee e
JOIN 
    works_with ww ON e.emp_id = ww.emp_id
GROUP BY 
    e.emp_id, e.first_name, e.last_name
ORDER BY 
    Total_Sales DESC;
```

### Employee Distribution Across Branches

To count the number of employees in each branch:

```sql
SELECT 
    b.branch_name,
    COUNT(e.emp_id) AS Employee_Count
FROM 
    branch b
LEFT JOIN 
    employee e ON b.branch_id = e.branch_id
GROUP BY 
    b.branch_name;
```

## Dashboard

The dashboard presents key insights derived from the analysis. It includes:

- Employee salary distribution (min, max, avg).
- Gender-based salary comparisons.
- Sales performance by employee.
- Employee distribution across branches.

![Company Database Dashboard](https://github.com/Morobang/CompanyDatabaseAnalysis/blob/main/Company%20Database%20Dashboard.png)

## Visualizations

To provide a more intuitive understanding of the data, visualizations were created using Power BI:

- **Salary Distribution**: A histogram depicting the distribution of employee salaries across different ranges.
- **Gender Salary Comparison**: A bar chart comparing average salaries between male and female employees.
- **Top Sales Performers**: A ranked list or bar chart showcasing employees with the highest total sales.
- **Employee Distribution by Branch**: A pie chart illustrating the proportion of employees in each branch.

## Conclusion

This analysis offers valuable insights into the company's workforce and operational metrics. Key takeaways include:

- Identification of salary ranges and potential disparities.
- Understanding of sales performance across employees.
- Overview of employee distribution among branches.

These insights can inform strategic decisions to improve overall business efficiency.

---

