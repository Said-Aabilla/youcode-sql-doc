## 4. Advanced Topics
### Subqueries
**Queries within queries**.

Example:

```sql
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Window Functions
Window functions are advanced SQL operations that allow you to perform calculations across a "window" of rows that are related to the current row. Unlike aggregate functions (e.g., SUM, AVG), which collapse data into a single row, window functions maintain individual rows while adding calculated values.

#### Ranking Query Example:

```sql 
SELECT name, salary, RANK() OVER (ORDER BY salary DESC) AS rank
FROM employees;
```
#### Explanation:
- `RANK()`: A ranking function that assigns a rank to each row.
- `OVER (ORDER BY salary DESC)`: Specifies the "window" as all rows ordered by `salary` in descending order.
- `AS rank`: Assigns a name to the resulting column.

#### Input Table (`employees`):
| name    | salary |
|---------|--------|
| Alice   | 9000   |
| Bob     | 8500   |
| Charlie | 9000   |
| Diana   | 8000   |

#### Output:
| name    | salary | rank |
|---------|--------|------|
| Alice   | 9000   | 1    |
| Charlie | 9000   | 1    |
| Bob     | 8500   | 3    |
| Diana   | 8000   | 4    |

#### Key Points:
1. **Ties**: `RANK()` assigns the same rank to tied rows (e.g., Alice and Charlie both have rank 1).
2. **Gaps**: The rank skips numbers after ties (e.g., rank 2 is missing).


### Indexing for Performance
Indexes improve query performance by reducing data retrieval time.

**Create an Index**

```sql
CREATE INDEX idx_department
ON employees(department);
```