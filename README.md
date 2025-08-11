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
