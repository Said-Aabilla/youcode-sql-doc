## 2. SQL Basics

### Setting Up Your Environment
1. **Install a Database System**:  
   Choose your weapon 🗡️:  
   - **MySQL**: [Download and Install](https://dev.mysql.com/downloads/) (popular and reliable).  
   - **PostgreSQL**: [Download and Install](https://www.postgresql.org/download/) (smart and a little fancy). 🧐  

2. **Tools**:  
   - **Local Management**: Use MySQL Workbench or pgAdmin (think of these as the friendly butler for your database).  
   - **Online Practice**: Platforms like SQLBolt or SQLZoo (perfect for when you’re stuck in a coffee shop with Wi-Fi and no SQL editor ☕).  

---

### SQL Data Types
Did you know that databases are picky eaters? They love data but insist on knowing exactly what kind of data you're feeding them! Here's the menu 🍽️:

#### **Common Data Types**
1. **Numeric**:  
   - `INT`, `SMALLINT`, `BIGINT`: Whole numbers. Perfect for things like counting inventory or tracking your coffee intake. ☕  
   - `DECIMAL(p, s)`, `NUMERIC(p, s)`: For precise decimal values, like your salary (down to the last cent 💸).  
   - `FLOAT`, `REAL`: Approximate values for when precision isn’t critical, like measuring how long your coworker spends "working" on Instagram. 📱  

2. **String/Text**:  
   - `CHAR(n)`: Fixed-length strings. For people who like their strings as disciplined as they are.  
   - `VARCHAR(n)`: Variable-length strings. Perfect for unpredictable data, like usernames.  
   - `TEXT`: Long text fields, because sometimes people *just won’t stop typing*... 🤣  

3. **Date/Time**:  
   - `DATE`: Store dates, like when your next project is *allegedly* due. 🗓️  
   - `TIME`: Record time. Useful for things like "When did I actually start this task?" ⏰  
   - `DATETIME`: Combines date and time for that detailed timestamp.  

4. **Boolean**:  
   - `BOOLEAN`: Stores `TRUE` or `FALSE`, like "Have I finished my work today?" (Spoiler: it’s probably `FALSE` 😅).  

---

### Types of SQL Commands
Think of SQL commands as tools in your developer toolbox 🧰. Each type has its job:

1. **DDL (Data Definition Language)**:  
   - The architect's tools for building and remodeling your database. 🏗️  
   - Examples: `CREATE`, `ALTER`, `DROP`.  

2. **DML (Data Manipulation Language)**:  
   - The movers and shakers for adding, changing, or removing data. 💪  
   - Examples: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.  

3. **DCL (Data Control Language)**:  
   - The bouncer of the database world, controlling who gets in. 🚷  
   - Examples: `GRANT`, `REVOKE`.  

4. **TCL (Transaction Control Language)**:  
   - The database referee for managing transactions. 🏅  
   - Examples: `COMMIT`, `ROLLBACK`.  

5. **DQL (Data Query Language)**:  
   - The detective for finding the data you need. 🕵️  
   - Example: `SELECT`.  

---

### Creating a Database
Imagine you’re opening a new café, and the first thing you need is a name beacause it will be the coolest virtual café in town! 🍵. Let’s name it **"The SQL Café"** (yes, it’s nerdy and amazing 😎).  

#### Create a Database
```sql
CREATE DATABASE sql_cafe;
```  

#### Use the Database
```sql
USE sql_cafe;
```  

Congrats, you’re now the proud owner of an empty database café! 🎉 Time to add some tables (think of these as your café’s menu).

---

### Creating a Table
Let’s create a table to track your café employees. 👩‍💻👨‍🍳  

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,  
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10, 2)
);
```  

Now you’ve got a table, but it’s empty! Kind of like a café with no customers. Let’s fix that!

---

### Testing Commands

#### **Inserting Data**
Add your employees (don’t forget to pay them! 💰).  
```sql
INSERT INTO employees (id, name, department, salary)
VALUES
    (1, 'Alice', 'Barista', 30000),
    (2, 'Bob', 'Manager', 50000),
    (3, 'Charlie', 'Chef', 40000);
```  

---

#### **Selecting Data**
Ask the database, “Who’s working here?”  
```sql
SELECT name, department
FROM employees;
```  

| id | name       | department | salary |
|----|------------|------------|--------|
| 1  | Alice      | Barista    | 30000  |
| 2  | Bob        | Manager    | 50000  |
| 3  | Charlie    | Chef       | 40000  |


#### **Filtering Data**
You decide to give a raise to employees making less than 40k. But first, find out who they are:  

```sql
SELECT *
FROM employees
WHERE salary < 40000;
```  

| id | name       | department | salary |
|----|------------|------------|--------|
| 1  | Alice      | Barista    | 30000  |


It seems there is only poor Alice with less than 40k 😭, let's make her happy and give her a raise:  

```sql
UPDATE employees
SET salary = 40000
WHERE id = 1;
``` 

---

#### **Updating Data**
Sometimes, you’ll need to correct a mistake (like when you realize you accidentally paid Bob $50,000 instead of $5,000 💸). Let’s fix it!  

```sql
UPDATE employees
SET salary = 5000
WHERE name = 'Bob';
``` 

Now, Bob’s salary is corrected! 🙌

---

#### **Deleting Data**
Let’s say Charlie decided to leave the café to open his own restaurant (the nerve!). We’ll need to remove him from the employee list. 😭  

```sql
DELETE FROM employees
WHERE name = 'Charlie';
``` 

And just like that, Charlie is out! 👋 May god help him, opening your own business can be frustrating sometimes!

---
### Grouping and Aggregating Data – Let’s Crunch Some Numbers! 📊  
SQL is great at helping you summarize data, and you’ll often need to use `GROUP BY` with aggregation functions. It’s like trying to figure out how much tip your team made after a long day of service.  
But first let us clean the employees table and insert new data:

```sql
DELETE FROM employees
WHERE 1 = 1;  -- A nice way to delete all records from the employees table.

-- insert new records
INSERT INTO employees (id, name, department, salary)
VALUES
    (1, 'Alice', 'Barista', 30000),
    (2, 'Bob', 'Manager', 50000),
    (3, 'Charlie', 'Chef', 40000);
    (4, 'Amine', 'Sous-Chef', 38000);

```


#### **COUNT**  
Let’s count how many employees we have in the café (spoiler: more than enough 🍽️).  

```sql
SELECT COUNT(*) AS number_of_employees
FROM employees;
```  

**Result:**

| number_of_employees |
|---------------------|
| 5                   |

#### **SUM**  
Let’s calculate the total salary your café is paying. Hopefully, it’s not too shocking! 💰  

```sql
SELECT SUM(salary) AS total_salary
FROM employees;
```  

**Result:**

| total_salary |
|--------------|
| 158000       |

#### **AVG**  
Let’s find out the average salary in your café. Spoiler alert: Alice might be earning a lot less than Bob! 😅  

```sql
SELECT AVG(salary) AS average_salary
FROM employees;
```  

**Result:**

| average_salary |
|----------------|
| 39500          |

#### **MAX and MIN**  
Let’s figure out who’s earning the most (Bob, duh 😏), and who’s earning the least (poor Alice 😢).  

```sql
SELECT MAX(salary) AS max_salary, MIN(salary) AS min_salary
FROM employees;
```  

**Result:**

| max_salary | min_salary |
|------------|------------|
| 50000      | 30000      |

---

### Sorting Data – Time to Organize! 📋  
Now that you’ve got all the data, let’s organize it properly, so you can actually make sense of it. 🧠

#### **ORDER BY**  
Let’s sort employees by their salary, from the highest to the lowest. Who’s the boss in this café? 💼  

```sql
SELECT name, salary
FROM employees
ORDER BY salary DESC;
```  

**Result:**

| name    | salary |
|---------|--------|
| Bob     | 50000  |
| Charlie | 40000  |
| Aminenn | 38000  |
| Alice   | 30000  |
