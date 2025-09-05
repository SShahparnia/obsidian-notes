# In-Class: More SQL

1. Question: What SQL statement would you use to create a new table called employees with columns id (integer), name (varchar), and hire_date (date)?

 I would use “CREATE TABLE” as the SQL statement to perform this operation. The syntax you could use would be as follows:

CREATE TABLE employees (

    id INTEGER,

    name VARCHAR,

    hire_date DATE

);

2. Question: Write a basic SQL query to retrieve all columns from a table called students where the age is greater than 20.

 SELECT * FROM students WHERE age > 20;

3. Question: How would you update the salary of all employees in the employees table by 10%?

 UPDATE employees SET salary = salary * 1.10;

4. Question: Describe the difference between the UNION and INTERSECTset operations in SQL.

 UNION combines the results from 2 queries (removes duplicates) & INTERSECT reuters only the rows that are present from both queries.

5. Question: How do you check for NULL values in a column called email in the contacts table?

 SELECT * FROM contacts WHERE email IS NULL;

6. Question: Write a SQL query to find the average salary of employees in the employees table.

I would use the “AVG” function upon the “salary” column.

 SELECT AVG(salary) FROM employees;

7. Question: What is a subquery in SQL, and give an example of a query that uses a subquery.

 A subquery is a query nested within another query

Example:

SELECT name FROM employees WHERE salary > (SELECT AVG(salary) FROM employees);

8. Question: How would you delete all records from a table called orders where the order_date is before '2023-01-01'?

 DELETE FROM orders WHERE order_date < '2023-01-01';

### Bonus Question

Question: Explain how the EXISTS clause works in SQL with an example.

The EXISTS clause in SQL checks if a subquery returns any rows from the DB

Example:

  

SELECT * FROM employees WHERE EXISTS (

    SELECT 1 FROM departments WHERE departments.manager_id = employees.id

);

  

This query returns all employees who are managers of any department if they exist.

  

```
erDiagram

DEPARTMENT ||--o{ INSTRUCTOR : "has"

DEPARTMENT ||--o{ COURSE : "offers"

DEPARTMENT ||--o{ STUDENT : "is major for"

  

INSTRUCTOR }o--o{ COURSE : "teaches"

STUDENT }o--o{ COURSE : "enrolls in"

  

DEPARTMENT {

int dept_id PK

string name

string building

numeric budget

}

  

INSTRUCTOR {

int instructor_id PK

string name

numeric salary

int dept_id FK

}

  

COURSE {

string course_id PK

string title

int dept_id FK

}

  

STUDENT {

int student_id PK

string name

int major_dept_id FK

}

  

TEACHES {

int instructor_id FK

string course_id FK

PK (instructor_id, course_id)

}

  

ENROLLMENT {

int student_id FK

string course_id FK

string grade "A,B,C,D,F,I,W"

PK (student_id, course_id)

}
```

```