# SQL Documentation for Students

## Table of Contents
1. [Introduction to SQL](#introduction-to-sql)
2. [SQL Basics](#sql-basics)
3. [Intermediate SQL](#intermediate-sql)
4. [Advanced Topics](#advanced-topics)

---

## 1. Introduction to SQL

### What is SQL?
SQL (Structured Query Language) is a standardized language used to manage and manipulate relational databases. It allows you to:
- Query and retrieve data.
- Insert, update, and delete records.
- Define and manage database structures.

### Why is SQL Important?
- SQL is essential for full-stack developers to interact with databases.
- It’s used across industries for data analysis, reporting, and backend development.

---

## 2. SQL Basics

### Setting Up Your Environment
1. **Install a Database System**:
(You can pick one of the 2)
   - MySQL: [Download and Install](https://dev.mysql.com/downloads/).
   - PostgreSQL: [Download and Install](https://www.postgresql.org/download/).

2. **Tools**:
   - **Database Management Tools (local machine)**: MySQL Workbench (for MySQL), pgAdmin (for PostgreSQL).
   - **Practice Platforms (online)**: SQLBolt, SQLZoo.

### Basic SQL Syntax
**Example Table: `employees`**

| id | name       | department | salary |
|----|------------|------------|--------|
| 1  | Alice      | HR         | 50000  |
| 2  | Bob        | IT         | 60000  |
| 3  | Charlie    | Finance    | 55000  |

#### Select Data
```sql
SELECT name, department
FROM employees;
```

#### Filter Data
```sql
SELECT *
FROM employees
WHERE salary > 55000;
```