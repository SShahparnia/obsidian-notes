# In-Class: DB Queries in SQL
## Problem 1 - Find the names of all the instructors from Biology department

```
SELECT name
FROM instructor
WHERE dept_name = 'Biology';
```
## Problem 2 - Find the names of courses in Computer science department which have 3 credits
```
SELECT title
FROM course
WHERE dept_name = 'Comp. Sci.' AND credits = 3;
```
## Problem 3 - For the student with ID 12345 (or any other value), show all course_id and title of all courses registered for by the student.
```
SELECT c.title, c.course_id
FROM course c
JOIN takes t ON c.course_id = t.course_id
WHERE t.id = '1232';
```
## Problem 4 - As above, but show the total number of credits for such courses (taken by that student). Don't display the tot_creds value from the student table, you should use SQL aggregation on courses taken by the student.
```
SELECT SUM(c.credits) AS total_credits
FROM course c
JOIN takes t ON c.course_id = t.course_id
WHERE t.id = '1232'
```
## Problem 5 - As above, but display the total credits for each of the students, along with the ID of the student; don't bother about the name of the student. (Don't bother about students who have not registered for any course, they can be omitted)
```
SELECT t.id, SUM(c.credits) AS total_credits
FROM course c
JOIN takes t ON c.course_id = t.course_id
GROUP BY t.id;
```
## Problem 6 - Find the names of all students who have taken any Comp. Sci. course ever (there should be no duplicate names)
```
SELECT DISTINCT s.name
FROM student s
JOIN takes t ON s.id = t.id
JOIN course c ON t.course_id = c.course_id
WHERE c.dept_name = 'Comp. Sci.';
```

