### SQL Joins – Let’s Connect! 🔗  
Sometimes, you need to connect tables to get the full picture (kind of like finding out how your café employees' tips 🍽️ compare to their salaries 💸 knowing that the tip is stored in another table). SQL JOINs are here for that!

#### Table Structures and Foreign Keys
Let’s create the structure of our two tables to do some joins:
 - **Step 1: Creating the `departments` table**:
    ```sql
    CREATE TABLE departments (
        id INT PRIMARY KEY,
        name VARCHAR(100)
    );
    ```

 - **Step 2: Drop the department_name column from employees table**
    ``` sql
    ALTER TABLE employees
    DROP COLUMN department_name;
    ```
 - **Step 3: Add the foreign key to link employees to departments**
    ```sql
    ALTER TABLE employees
    ADD department_id INT,
    ADD CONSTRAINT fk_department
    FOREIGN KEY (department_id) REFERENCES departments(id);
    ```
#### Foreign Key Explanation
 Adding a **foreign key** to the `employees` table links each employee to a department. A **foreign key** is like a reference or a link that ties data from one table to data in another. In this case, the `department_id` in the `employees` table is a foreign key that refers to the `id` in the `departments` table. It ensures that every employee is assigned to a valid department.


#### Visualizing Joins with Images

To understand how each type of join works, let’s take a look at some images! Visualizing joins can really help clarify how they behave:

1. **INNER JOIN**  
   - An `INNER JOIN` returns only the rows where there’s a match in both tables.

   ![INNER JOIN](https://www.sqlservertutorial.net/wp-content/uploads/2018/03/inner-join.png)

2. **LEFT JOIN**  
   - A `LEFT JOIN` returns all rows from the left table, and the matched rows from the right table. If there’s no match, it returns `NULL` for the right table.

   ![LEFT JOIN](https://www.sqlservertutorial.net/wp-content/uploads/2018/03/left-join.png)

3. **RIGHT JOIN**  
   - A `RIGHT JOIN` returns all rows from the right table, and the matched rows from the left table. If there’s no match, it returns `NULL` for the left table.

   ![RIGHT JOIN](https://www.sqlservertutorial.net/wp-content/uploads/2018/03/right-join.png)

4. **FULL OUTER JOIN**  
   - A `FULL OUTER JOIN` returns all rows from both tables, with `NULL` where there’s no match.

   ![FULL OUTER JOIN](https://www.sqlservertutorial.net/wp-content/uploads/2018/03/full-outer-join.png)

#### Performing SQL Joins
Now that you have a better understanding of the table structures and how foreign keys work, let’s try performing some SQL joins!

##### **INNER JOIN**  
An `INNER JOIN` returns only the rows where there’s a match between the tables. Think of it like connecting two sets of friends who *actually know each other*.  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
end of sql script  

**Result:**

| name    | department_name |
|---------|-----------------|
| Alice   | Barista         |
| Charlie | Barista         |
| Bob     | Manager         |
| David   | Chef            |

##### **LEFT JOIN**  
A `LEFT JOIN` returns all the rows from the left table (employees) and the matched rows from the right table (departments). If there’s no match, it’ll still show the employee, but with a `NULL` value for the department (just like when your café staff works without a manager on shift 😂).  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.id;
end of sql script  

**Result:**

| name    | department_name |
|---------|-----------------|
| Alice   | Barista         |
| Bob     | Manager         |
| Charlie | Barista         |
| David   | Chef            |

##### **RIGHT JOIN**  
A `RIGHT JOIN` is the opposite: it returns all the rows from the right table (departments) and the matching rows from the left table (employees). When departments have no employees assigned, it shows `NULL` values for employee names.  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.id;
end of sql script  

**Result:**

| name    | department_name |
|---------|-----------------|
| Alice   | Barista         |
| Bob     | Manager         |
| Charlie | Barista         |
| David   | Chef            |

##### **FULL OUTER JOIN**  
A `FULL OUTER JOIN` returns rows when there’s a match in one of the tables. It’s like inviting both sets of friends who may or may not know each other to the same party. 🥳  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
FULL OUTER JOIN departments ON employees.department_id = departments.id;
end of sql script  

**Result:**

| name    | department_name |
|---------|-----------------|
| Alice   | Barista         |
| Bob     | Manager         |
| Charlie | Barista         |
| David   | Chef            |

---

### Conclusion – SQL Can Be Fun! 🎉  
You’ve learned the basics of SQL in a fun and interactive way! 🎈 By now, you should be able to create a database, add tables, insert data, filter, update, delete, and even join tables like a pro. You’re well on your way to becoming an SQL wizard! 🧙‍♂️

Remember, SQL is like a superpower—you can do a lot with it, but you need to practice! So keep experimenting, and soon enough, you’ll be flexing those SQL muscles like a champion 💪.

Now go forth and conquer the world of databases, one query at a time! 🚀


### Grouping and Aggregating Data – Let’s Crunch Some Numbers! 📊  
SQL is great at helping you summarize data, and you’ll often need to use `GROUP BY` with aggregation functions. It’s like trying to figure out how much tip your team made after a long day of service.  

#### **COUNT**  
Let’s count how many employees we have in the café (spoiler: more than enough 🍽️).  

```sql
SELECT COUNT(*) AS number_of_employees
FROM employees;
```  

**Result:**

| number_of_employees |
|---------------------|
| 4                   |

#### **SUM**  
Let’s calculate the total salary your café is paying. Hopefully, it’s not too shocking! 💰  

```sql
SELECT SUM(salary) AS total_salary
FROM employees;
```  

**Result:**

| total_salary |
|--------------|
| 195000       |

#### **AVG**  
Let’s find out the average salary in your café. Spoiler alert: Alice might be earning a lot less than Bob! 😅  

```sql
SELECT AVG(salary) AS average_salary
FROM employees;
```  

**Result:**

| average_salary |
|----------------|
| 48750          |

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
| David   | 45000  |
| Charlie | 40000  |
| Alice   | 30000  |

---

### Conclusion – SQL Can Be Fun! 🎉  
You’ve learned the basics of SQL in a fun and interactive way! 🎈 By now, you should be able to create a database, add tables, insert data, filter, update, delete, and even join tables like a pro. You’re well on your way to becoming an SQL wizard! 🧙‍♂️

Remember, SQL is like a superpower—you can do a lot with it, but you need to practice! So keep experimenting, and soon enough, you’ll be flexing those SQL muscles like a champion 💪.

Now go forth and conquer the world of databases, one query at a time! 🚀