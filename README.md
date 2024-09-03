# School Database System

This SQL project creates a simple school database with tables for Students, Courses, and Grades. It also inserts sample data and runs three queries to obtain relevant information about students and their performance in courses.

## Database Structure

- **Students**: Stores information about the students, including their name, date of birth, and address.
- **Courses**: Stores information about the courses offered, including the course name and a description.
- **Grades**: Records the grades of students in various courses, linking students to courses.

## Created Tables

1. **Students**
    - `id_student` (INT, PK, Auto Increment)
    - `name` (VARCHAR(100), NOT NULL)
    - `date_of_birth` (DATE, NOT NULL)
    - `address` (VARCHAR(255), NOT NULL)

2. **Courses**
    - `id_course` (INT, PK, Auto Increment)
    - `course_name` (VARCHAR(100), NOT NULL)
    - `description` (TEXT)

3. **Grades**
    - `id_grade` (INT, PK, Auto Increment)
    - `id_student` (INT, FK, REFERENCES Students)
    - `id_course` (INT, FK, REFERENCES Courses)
    - `grade` (DECIMAL(5,2), NOT NULL)

## Data Insertion

- Students: Includes 3 students with their names, birth dates, and addresses.
- Courses: Includes 3 courses with names and descriptions.
- Grades: Records 5 grades for students across different courses.

## Queries

1. **List all students and their grades in each course**:
   ```sql
   SELECT
       S.name AS student,
       C.course_name AS course,
       G.grade
   FROM
       Grades G
   JOIN
       Students S ON G.id_student = S.id_student
   JOIN
       Courses C ON G.id_course = C.id_course;
