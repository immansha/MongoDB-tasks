
# 🗂️ ORG123 SQL Database Project

## 📚 Project Overview
This project demonstrates the creation and manipulation of a database named **`ORG123`** that contains a table called **`Worker`**. The table stores details about employees, including their personal information, salary, joining date, and department.

The SQL queries showcase various operations such as:
- Database and table creation
- Data insertion
- Filtering and retrieval of data using `SELECT`
- Use of `BETWEEN`, `IN`, and `CASE` statements
- Aggregations with `COUNT()` and `MIN()`
- Combining results with `UNION` and `UNION ALL`
- Sorting and limiting results
- Grouping and counting records by department

---

## 📑 Table of Contents
1. [Database and Table Creation](#-database-and-table-creation)
2. [Data Insertion](#-data-insertion)
3. [Data Retrieval and Queries](#-data-retrieval-and-queries)
4. [Conditional Statements and Filtering](#-conditional-statements-and-filtering)
5. [Union and Alias Usage](#-union-and-alias-usage)
6. [Categorizing Employees Based on Salary](#-categorizing-employees-based-on-salary)
7. [Top 3 Highest Salaries in Admin Department](#-top-3-highest-salaries-in-admin-department)
8. [Employee Count by Department](#-employee-count-by-department)

---

## 🛠️ 1. Database and Table Creation
```sql
CREATE DATABASE ORG123;
SHOW DATABASES;
USE ORG123;

CREATE TABLE Worker (
    WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    FIRST_NAME CHAR(25),
    LAST_NAME CHAR(25),
    SALARY INT(15),
    JOINING_DATE DATETIME,
    DEPARTMENT CHAR(25)
);
```
✅ Purpose:
- Create a new database `ORG123` and use it.  
- Define the `Worker` table with appropriate fields.

---

## 📥 2. Data Insertion
```sql
INSERT INTO Worker 
    (WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
    (001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),
    (002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),
    (003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),
    (004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),
    (005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),
    (006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),
    (007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),
    (008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');
```
✅ Purpose:  
- Insert 8 records into the `Worker` table.

---

## 🔍 3. Data Retrieval and Queries
```sql
SELECT * FROM worker;
SELECT DISTINCT (department) FROM worker;
SELECT worker_id AS emp_code FROM worker;
```
✅ Purpose: 
- Retrieve all records.  
- Get unique departments.  
- Use an alias to rename `worker_id` as `emp_code`.

---

## 📊 4. Conditional Statements and Filtering
### Employees with Salary NOT between 100,000 and 200,000
```sql
SELECT * FROM worker
WHERE salary NOT BETWEEN 100000 AND 200000;
```

### Employees with Salary BETWEEN 200,000 and 400,000 and Limited by `worker_id`
```sql
SELECT * FROM worker
WHERE salary BETWEEN 200000 AND 400000
AND worker_id IN (1, 2, 3, 4, 5);
```

### Minimum Salary in the Table
```sql
SELECT MIN(salary)
FROM worker;
```

---

## 🔗 5. Union and Alias Usage
### Union of `worker_id` and `first_name`
```sql
SELECT worker_id FROM worker
UNION ALL
SELECT first_name FROM worker;
```

### Union of Departments and `worker_id` for HR and Account
```sql
SELECT department, worker_id FROM worker
WHERE department='HR'
UNION ALL
SELECT department, worker_id FROM worker
WHERE department='Account'
ORDER BY worker_id;
```

---

## 💸 6. Categorizing Employees Based on Salary
```sql
SELECT worker_id, first_name, department,
CASE
    WHEN salary > 300000 THEN 'Rich people'
    WHEN salary <= 300000 AND salary >= 100000 THEN 'Middle stage'
    ELSE 'Poor people'
END AS People_stage_wise
FROM worker;
```
✅ Purpose: 
- Categorize employees based on their salary into:
    - Rich people
    - Middle stage
    - Poor people

---

## 🏆 7. Top 3 Highest Salaries in Admin Department
```sql
SELECT * FROM worker
WHERE department='Admin'
ORDER BY salary DESC
LIMIT 3;
```
✅ Purpose:
- Get the top 3 highest-paid employees in the `Admin` department.

---

## 📈 8. Employee Count by Department
```sql
SELECT department, COUNT(department) AS total_employees
FROM worker
WHERE department = 'HR' OR department='Account'
GROUP BY department;
```
✅ Purpose:
- Count the number of employees in the `HR` and `Account` departments.

---

## 📝 Conclusion
This project demonstrates a complete workflow of SQL operations, starting from:
- Database and table creation
- Inserting data
- Filtering, grouping, and aggregating information
- Using conditional logic (`CASE` statements) for categorization
- Union, aliasing, and limit-based filtering for refined queries

This knowledge can be leveraged for larger database systems and advanced SQL applications.

---

