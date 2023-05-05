# JOINs


```python
import pandas as pd

```


```sql
SLECT * FROM MY_TABLE
ORDER BY COLUMN 1, DESC COLUMN 2

```

Select the distinct values of order_id in order_items. Count the distinct values

```sql
SELECT COUNT(*)
FROM(
    SELECT DISTINCT order_id 
    FROM CO.order_items
)
```

COUNT DISTINCT VALUES OF ORDER ID 
Note: In SQL you cannot run a query without slec. YOu have to START with select. 
```sql
SELECT DISTINCT order_id
FROM CO.order_item
```

COUNTS ALL THE ROWS IN THE TABLE 
```sql
SELECT COUNT(*)
FROM CO.order_item

```


COUNTS ALL THE ROWS WHERE ORDER ID IN NOT NULL 


```sql
SELECT COUNT(order_id)
FROM CO.order_item

```

```sql
SELECT COUNT (DISTINCT (order_id)
FROM CO.order_items
```

COMBINATION OF TWO ROWS: 
GET COUNT OF THE UNIQUE COMBINATION OF TWO ROWS order_id, product_id

```sql
SELECT COUNT (*)
FROM (
      SELECT DISTINCT order_id, product_id
      FROM CO.order_items
) 


```

6. find all employees whose last name doe not start with Sm

```sql

SELECT employee_id, last_name
FROM hr_employees
WHERE last_name NOT LIKE sm%

```

5. Find all employees whose last name starts with Sm

```sql
SELECT employee_id, last_name
FROM hr_employees
WHERE last_name LIKE 'sm%'
```


AGGREGATE FUNCTIONS WITH GROUPBY 
```sql
SELECT department_id, SUM(salary) as total_salary
FROM hr.employees
GROUP BY department_id;
```

Count the numbre of employees with a commission_pctvalue different from 0 for each department 
This counts every employee in each Group!: 

```sql

This counts every employee in each Group!: 
SELECT department_id, Count(*)
FROM hr.employees
WHERE commission_pct IS NOT NULL 
GROUP BY department_id

```
FIND THE AVG SALARY FOR EACH DEPARTMENT WHERE THERE ARE MORE THAN TWO EMPLOYEES AND ORDER THE RESULTS BY AVERAGE SALARY 

```sql
SLECT department_id, AVG(salary) as avg_salary, COUNT(*) n_employees 
FROM hr.employees
GROUP BY department_id
WHERE COUNT(department_id)
HAVING COUNT(*) > 2
