DBMS Queries
 
Lab 1: Data Definition Language (DDL) and Constraints
 
Objective: To learn how to create and manage database schema using SQL's Data Definition Language.
Database Schema: A simple student management system with three tables: Students, Courses, and Enrollments.
 
Tasks:
 
Database Creation:
Create a new database named StudentDB.
Table Creation:
Write CREATE TABLE statements for the Students, Courses, and Enrollments tables as defined below.
Define Primary Key (PK) constraints for each table's unique identifier.
Define Foreign Key (FK) constraints to establish relationships between tables.
Use appropriate data types (INT, VARCHAR, DATE, DECIMAL) and constraints (NOT NULL, UNIQUE).
Students (student_id PK, first_name, last_name, major, email UNIQUE)
Courses (course_id PK, course_name, credits)
Enrollments (enrollment_id PK, student_id FK, course_id FK, grade DECIMAL)
Schema Modification:
Use an ALTER TABLE statement to add a new column start_date of type DATE to the Students table.
Use an ALTER TABLE statement to add a NOT NULL constraint to the first_name column in the Students table.
Table Deletion:
Use the DROP TABLE command to delete the Enrollments table.
Recreate the Enrollments table from Task 2.
 
Lab 2: Data Manipulation Language (DML)
 
Objective: To practice adding, modifying, and deleting data using SQL's Data Manipulation Language.
Pre-requisite: Complete Lab 1 and ensure all three tables (Students, Courses, Enrollments) exist.
 
Tasks:
 
Inserting Data:
Use INSERT INTO statements to add at least three records into each of the Students and Courses tables.
Add at least five enrollment records into the Enrollments table, ensuring the student_id and course_id values match existing records.
Updating Data:
Use the UPDATE statement to change the major of a student from 'Computer Science' to 'Data Science'.
Use UPDATE to change the grade of a specific enrollment record.
Deleting Data:
Use the DELETE statement to remove a single student record from the Students table. Note the impact this may have on related records in the Enrollments table due to foreign key constraints (cascading actions).
Use DELETE to remove a specific course from the Courses table.
 
Lab 3: Basic Data Retrieval (SELECT)
 
Objective: To retrieve data from single and multiple tables using various SELECT clauses and operators.
 
Tasks:
 
Simple SELECT:
Retrieve all columns and all rows from the Students table.
Retrieve only the first_name and email columns from the Students table.
Filtering with WHERE:
Retrieve all students whose major is 'Computer Science'.
Retrieve all courses with more than 3 credits.
Retrieve students who have a student_id greater than 102 and a major of 'Physics'.
Sorting and Limiting:
Retrieve all students, ordered by their last_name in ascending order.
Retrieve the top 3 students based on their student_id.
Aggregate Functions:
Count the total number of students in the Students table.
Calculate the average grade for all students in the Enrollments table.
Find the highest grade recorded.
Grouping and Filtering Groups:
Find the number of students in each major.
Find the average grade for each course_id.
Find majors that have more than 1 student, using HAVING.
 
Lab 4: Joins
 
Objective: To combine data from multiple tables using different types of JOINs.
 
Tasks:
 
INNER JOIN:
List the names of all students and the names of the courses they are enrolled in.
Find all students who have a grade of 90 or higher, and display their name, course name, and grade.
LEFT JOIN:
List all students and the courses they are enrolled in. Include students who are not enrolled in any courses.
RIGHT JOIN:
List all courses and the students enrolled in them. Include courses that have no students enrolled.
Multiple Joins:
Retrieve the student's full name, the course name, and the grade for every enrollment.
 
Lab 5: Subqueries and Views
 
Objective: To use subqueries for complex filtering and to create reusable queries with views.
 
Tasks:
 
Subqueries:
Find the names of students who are enrolled in the course with course_id = 'CS101'.
Find the names of students who have a grade higher than the average grade of all students.
Views:
Create a VIEW named StudentGrades that shows the student's full name, course name, and their grade.
Query the StudentGrades view to find all students with a grade higher than 90.
Use the DROP VIEW command to remove the StudentGrades view.




```CREATE TABLE IF NOT EXISTS Students(
Student_ID int primary key,
First_Name varchar(225),
Last_Name varchar(225),
Major varchar(225),
Email varchar(225) unique
);```
-----Schema Modification
---Alter Table to add a new column start_date type Date to student table
```ALTER TABLE Students 
ADD Start_Date DATE;```
---Alter Table to add a Not Null constraint to First_Name in Student table 
```Alter Table Students 
Alter Column First_Name set NOT NULL;```
```select * from Students```
 -- Insert 10 Students
```INSERT INTO Students (Student_ID, First_Name, Last_Name, Major, Email, Start_Date) VALUES
(1, 'John', 'Doe', 'Physics', 'john.doe@mail.com', '2023-08-01'),
(2, 'Emily', 'Clark', 'Math', 'emily.clark@mail.com', '2023-08-05'),
(3, 'Michael', 'Smith', 'Chemistry', 'michael.smith@mail.com', '2023-08-10'),
(4, 'Sophia', 'Brown', 'Biology', 'sophia.brown@mail.com', '2023-09-01'),
(5, 'Daniel', 'Wilson', 'History', 'daniel.wilson@mail.com', '2023-09-05'),
(6, 'Olivia', 'Johnson', 'English', 'olivia.johnson@mail.com', '2023-09-10'),
(7, 'Ethan', 'Taylor', 'Math', 'ethan.taylor@mail.com', '2024-01-15'),
(8, 'Ava', 'Martinez', 'Physics', 'ava.martinez@mail.com', '2024-01-20'),
(9, 'Liam', 'Garcia', 'Biology', 'liam.garcia@mail.com', '2024-02-01'),
(10, 'Isabella', 'Lee', 'Chemistry', 'isabella.lee@mail.com', '2024-02-05');```
```SELECT * FROM Students;```
--create course Table 
```CREATE TABLE Courses(
    Course_ID INT PRIMARY KEY,
    Course_Name VARCHAR(15),
    Credits INT
);```

-- Insert 10 Courses
```INSERT INTO Courses (Course_ID, Course_Name, Credits) VALUES
(101, 'Algebra', 3),
(102, 'Biology', 4),
(103, 'Physics', 4),
(104, 'Chemistry', 3),
(105, 'History', 2),
(106, 'Literature', 3),
(107, 'Statistics', 3),
(108, 'Astronomy', 4),
(109, 'Philosophy', 2),
(110, 'Economics', 3);

SELECT * FROM Courses;```

-- Create Enrollment table
```DROP TABLE IF EXISTS Enrollment;
CREATE TABLE Enrollment(
    Enrollment_Id INT PRIMARY KEY,
    Student_ID INT REFERENCES Students(Student_ID),
    Course_ID INT REFERENCES Courses(Course_ID),
    Grade DECIMAL
);
```
-- Insert 10 Enrollments
```INSERT INTO Enrollment (Enrollment_Id, Student_ID, Course_ID, Grade) VALUES
(1, 1, 103, 85.5),
(2, 2, 101, 90.0),
(3, 3, 104, 78.0),
(4, 4, 102, 88.0),
(5, 5, 105, 92.0),
(6, 6, 106, 84.0),
(7, 7, 107, 76.5),
(8, 8, 108, 89.0),
(9, 9, 102, 80.0),
(10, 10, 104, 91.0);

SELECT * FROM Enrollment;```
----Table Deletion 
----Use Drop table to delete Enrollment table
```DROP TABLE IF EXISTS Enrollment;```
---Recreate the Enrollment table 

```UPDATE Students
SET Major = 'Data Science'
WHERE Major = 'English';
SELECT * FROM Students;```

--Retrieve all columns and all rows from the Students table.
```SELECT * FROM Students;```
--Retrieve only the first_name and email columns from the Students table.
```select first_name,last_name from Students```
--Retrieve all students whose major is 'Chemistry'.
```select * from students
where major='Chemistry';```
--Retrieve all courses with more than 3 credits.
```select * from Courses 
where credits >=3;```
--Retrieve students who have a student_id greater than 6 and a major of 'Physics'.
```SELECT *
FROM Students
WHERE Student_ID > 6 
  AND Major = 'Physics';```
              -----Sorting and Limiting:
--Retrieve all students, ordered by their last_name in Descending order.
```select * from Students
order by last_name desc;```
--Retrieve the top 3 students based on their student_id.
```select * from Students
order by Student_ID desc
limit 3;```
          ---Aggregate Functions:
--Count the total number of students in the Students table.
```select 
count(student_id) as total_number_student
from Students;```
--Calculate the average grade for all students in the Enrollments table.
```select 
Round(Avg(grade),2) as Avg_grade 
from Enrollment;```
--Find the highest grade recorded.
```select max(grade) from Enrollment;
SELECT *
FROM (
    SELECT *,
           DENSE_RANK() OVER (ORDER BY Grade DESC) AS rnk
    FROM Enrollment
) ranked
WHERE rnk <= 5;```
         ---Grouping and Filtering Groups:
--Find the number of students in each major.
```select major,
count(student_id) as number_of_student
from Students
Group by 1;```
--Find the average grade for each course_id.
```select * from Enrollment;
select course_id,
Round(Avg(grade),2)as avg_grade
from Enrollment
group by 1;```

--Find majors that have more than 1 student, using HAVING.
```select major,
count(*) as student_count
from Students
group by 1
 having count(*)> 1;```
        --Joins
--INNER JOIN:
--List the names of all students and the names of the courses they are enrolled in.
```select 
s.first_name,
s.last_name,
c.course_name 
from students s
INNER JOIN Enrollment e 
    ON s.Student_ID = e.Student_ID
INNER JOIN Courses c 
    ON e.Course_ID = c.Course_ID;```
--Find all students who have a grade of 90 or higher, and display their name, course name, and grade.
```select s.first_name,
s.last_name,
c.course_name,
e.grade
from Students s
Inner join Enrollment e
ON s.student_id=e.student_id
Inner join Courses c
ON e.course_id=c.course_id
where grade >=90;```

------------------------LEFT JOIN:
--List all students and the courses they are enrolled in. Include students who are not enrolled in any courses.

```SELECT 
    s.first_name, 
    s.last_name, 
    COALESCE(c.course_name, 'Not Enrolled') AS course_name
FROM Students s
LEFT JOIN Enrollment e 
    ON s.Student_ID = e.Student_ID
LEFT JOIN Courses c 
    ON e.Course_ID = c.Course_ID;```
--List all courses and the students enrolled in them. Include courses that have no students enrolled.
```SELECT 
    c.course_name, 
    s.first_name, 
    s.last_name
FROM Students s
RIGHT JOIN Enrollment e 
    ON s.Student_ID = e.Student_ID
RIGHT JOIN Courses c 
    ON e.Course_ID = c.Course_ID;```


--Multiple Joins:
--Retrieve the student's full name, the course name, and the grade for every enrollment.

```SELECT 
    s.first_name || ' ' || s.last_name AS full_name,
    c.course_name,
    e.grade
FROM Students s
INNER JOIN Enrollment e 
    ON s.student_id = e.student_id
INNER JOIN Courses c
    ON e.course_id = c.course_id;```
             --Subqueries and Views
--Find the names of students who are enrolled in the course with course_id = 'CS101'.
--joins
```SELECT s.first_name, 
       s.last_name
FROM Students s
INNER JOIN Enrollment e 
    ON s.Student_ID = e.Student_ID
WHERE e.Course_ID = '101';```
--subqury
```SELECT first_name, last_name
FROM Students
WHERE Student_ID IN (
    SELECT Student_ID
    FROM Enrollment
    WHERE Course_ID = '101'
);```
--Find the names of students who have a grade higher than the average grade of all students.
```SELECT first_name, last_name
FROM Students
WHERE Student_ID IN (
    SELECT Student_ID
    FROM Enrollment
    WHERE Grade > (SELECT AVG(Grade) as avfg FROM Enrollment)
);```

------Views:
--Create a VIEW named StudentGrades that shows the student's full name, course name, and their grade.
```CREATE VIEW StudentGrades AS
SELECT 
    s.first_name || ' ' || s.last_name AS full_name,
    c.course_name,
    e.grade
FROM Students s
JOIN Enrollment e 
    ON s.Student_ID = e.Student_ID
JOIN Courses c 
    ON e.Course_ID = c.Course_ID;```
--Query the StudentGrades view to find all students with a grade higher than 90.
```SELECT *
FROM StudentGrades
WHERE grade > 90;```
--Use the DROP VIEW command to remove the StudentGrades view.

```DROP VIEW StudentGrades;```

