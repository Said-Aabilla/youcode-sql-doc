
### SQL Joins – Let’s Connect! 🔗
Sometimes, you need to connect tables to get the full picture (kind of like finding out how your café employees' tips (le pourboire) compare to their salaries). SQL JOINs are here for that!

#### **INNER JOIN**
An `INNER JOIN` returns only the rows where there’s a match between the tables. Think of it like connecting two sets of friends who *actually know each other*.  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
end of sql script  

#### **LEFT JOIN**
A `LEFT JOIN` returns all the rows from the left table (employees) and the matched rows from the right table (departments). If there’s no match, it’ll still show the employee, but with a `NULL` value for the department (just like when your café staff works without a manager on shift 😂).  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.id;
end of sql script  

#### **RIGHT JOIN**
A `RIGHT JOIN` is the opposite: it returns all the rows from the right table (departments) and the matching rows from the left table (employees). When departments have no employees assigned, it shows `NULL` values for employee names.  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.id;
end of sql script  

#### **FULL OUTER JOIN**
A `FULL OUTER JOIN` returns rows when there’s a match in one of the tables. It’s like inviting both sets of friends who may or may not know each other to the same party. 🥳  

start of sql script
SELECT employees.name, departments.name AS department_name
FROM employees
FULL OUTER JOIN departments ON employees.department_id = departments.id;
end of sql script  

---

### Grouping and Aggregating Data – Let’s Crunch Some Numbers! 📊
SQL is great at helping you summarize data, and you’ll often need to use `GROUP BY` with aggregation functions. It’s like trying to figure out how much tip your team made after a long day of service.  

#### **COUNT**
Let’s count how many employees we have in the café (spoiler: more than enough 🍽️).  

start of sql script
SELECT COUNT(*) AS number_of_employees
FROM employees;
end of sql script  

#### **SUM**
Let’s calculate the total salary your café is paying. Hopefully, it’s not too shocking! 💰  

start of sql script
SELECT SUM(salary) AS total_salary
FROM employees;
end of sql script  

#### **AVG**
Let’s find out the average salary in your café. Spoiler alert: Alice might be earning a lot less than Bob! 😅  

start of sql script
SELECT AVG(salary) AS average_salary
FROM employees;
end of sql script  

#### **MAX and MIN**
Let’s figure out who’s earning the most (Bob, duh 😏), and who’s earning the least (poor Alice 😢).  

start of sql script
SELECT MAX(salary) AS max_salary, MIN(salary) AS min_salary
FROM employees;
end of sql script  

---

### Sorting Data – Time to Organize! 📋
Now that you’ve got all the data, let’s organize it properly, so you can actually make sense of it. 🧠

#### **ORDER BY**
Let’s sort employees by their salary, from the highest to the lowest. Who’s the boss in this café? 💼  

start of sql script
SELECT name, salary
FROM employees
ORDER BY salary DESC;
end of sql script  

---

### Conclusion – SQL Can Be Fun! 🎉
You’ve learned the basics of SQL in a fun and interactive way! 🎈 By now, you should be able to create a database, add tables, insert data, filter, update, delete, and even join tables like a pro. You’re well on your way to becoming an SQL wizard! 🧙‍♂️

Remember, SQL is like a superpower—you can do a lot with it, but you need to practice! So keep experimenting, and soon enough, you’ll be flexing those SQL muscles like a champion 💪.

Now go forth and conquer the world of databases, one query at a time! 🚀

