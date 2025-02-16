# SQL

## Learn SQL by Building a Student Database

### Part 1 

### Set-up

This course runs in a virtual Linux machine using Gitpod. Follow these instructions to start the course:

- Create a GitHub account if you don't have one
- Click the start button below
- Login to Gitpod with your GitHub account if you aren't already
- Once the virtual Linux machine is finished loading, start the CodeRoad extension by:
- Clicking the "hamburger" menu near the top left of the VSCode window,
- Going to the "View" menu,
- Clicking on the "Command Palette" option,
- and running the "CodeRoad: Start" command
- Follow the instructions in CodeRoad to complete the course

Clicking the button below will start a new project. If you have previously started the Build a Student Database: Part 1 course, go to your Gitpod dashboard to continue.

#### Part One

echo - command to print text to terminal

we start with .csv files, or commma separated values.
  - top row has titles, and the rest are values for those titles.
  - We will add all this info to a PostgreSQL database
  - What is a psql Database?
A psql database refers to a PostgreSQL database that you interact with using the psql interactive terminal.

PostgreSQL (psql) is an open-source SQL database used to store and manage data.
psql is the command-line tool for interacting with a PostgreSQL database.
It lets you run SQL commands to create tables, insert data, query results, and more.
  - Log into the psql interactive terminal with psql --username=freecodecamp --dbname=postgres to get started.
  - View the existing databases with the \l shortcut command to see what's here.
  
Create a new database
  - use the CREATE DATABASE keywords
  - check using \l command

Connect to the new database
- Use the \c shortcut command

The CSV files have a bunch of students with info about them, and some courses and majors. You will have four tables. One for the students and their info, one for each major, another for each course, and a final one for showing what courses are included in each major.
  - Create the students table
  - Use the CREATE TABLE keywords
  - there should be parenthesis after the table name.
    - CREATE TABLE students();
  - SQL commands end in ;

The final table will be a junction table for the majors and courses. Create it with the name majors_courses.
  - What is a Junction Table?
A junction table (also called a join table or bridge table) is used in many-to-many relationships between two tables. It connects two other tables by storing references (foreign keys) to their primary keys.

How Is This Different from a Regular Table?

  - A regular table (like students) holds data about a specific entity.
A junction table does not hold unique data; it only stores relationships between two other tables.
It has only foreign keys (pointing to two different tables), instead of its own unique data.

Use the display  shortcut command to view your tables
  - \d

Onto the columns. The students.csv file has four fields, you will make a column for each of those as well as an ID column. Add a column to your students table named student_id. Give it a type of SERIAL so it automatically increments and make it a PRIMARY KEY

  - Use the ALTER TABLE, ADD COLUMN, SERIAL and PRIMARY KEY keywords
  - Here's an example: ALTER TABLE <table_name> ADD COLUMN <column_name> <TYPE> <CONSTRAINTS>;
  - Type ALTER TABLE students ADD COLUMN student_id SERIAL PRIMARY KEY

The first column in students.csv is first_name. Add a column to the students table with that name. Make it a type of VARCHAR(50) and give it the NOT NULL constraint.
  -  Use the ALTER TABLE, ADD COLUMN, VARCHAR() and NOT NULL keywords

2. Here's an example: ALTER TABLE <table_name> ADD COLUMN <column_name> <DATA_TYPE> <CONSTRAINTS>;

3. Type ALTER TABLE students ADD COLUMN first_name VARCHAR(50) NOT NULL; into the psql prompt.

The next column in the data is last_name. Add it to the students table. Give it the same data type and max-length as first_name and make sure it has the NOT NULL constraint.
  -  Use the ALTER TABLE, ADD COLUMN, VARCHAR() and NOT NULL keywords

#### Question?
  
What is VARCHAR(50)?
  - VARCHAR(50) is a variable-length character string data type in SQL.

🔹 Breakdown:
  - VAR = Variable
  - CHAR = Character (text)
  - (50) = Maximum number of characters (up to 50)
🔹 Key Features:
   - Stores text values (e.g., names, emails).
  -  Only takes up as much space as needed (unlike CHAR(50), which always uses 50 characters).
  - Ideal for columns with text that varies in length (e.g., names, descriptions).
  
  ```sql
  CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE
);
```
  - name can store up to 50 characters
  - email can store up to 100 charachters and must be unique

#### Lesson Continued
The next column is for the major. Since you will have each major in another table this column will be a foreign key that references it. Create a column in the students table named major_id, give it a data type of INT for now. You will come back and set the foreign key later.
  - ALTER TABLE students ADD COLUMN major_id INT;

Create the last column, gpa. The data in the CSV shows that they are decimals with a length of 2 and 1 number is to the right of the decimal. So give it a data type of NUMERIC(2,1).
  - ALTER TABLE students ADD COLUMN gpa NUMERIC(2,1);
  
Use the shortcut command to display the details of the students table to make sure you like it.
  - \d
  - Add the table name after the command
  - \d students

The foreign key is still missing. Let's fill in the majors table next. Add a major_id column to it. Make it a type of SERIAL and the PRIMARY KEY for this table.
  - The foreign key is still missing. Let's fill in the majors table next. Add a major_id column to it. Make it a type of SERIAL and the PRIMARY KEY for this table.

This table will only have one other column for the name of the major. Add a column to it named major. Make it a VARCHAR with a max-length of 50 and give it the NOT NULL constraint.
  - ALTER TABLE majors ADD COLUMN major VARCHAR(50) NOT NULL;

View the details of the majors table to make sure you like it.
  - Use the display shortcut command

  - Add the table name after the command

  - It's the \d command
    -  Here's an example: \d <table_name>
    -  Type \d majors into the psql prompt

This table looks good. Now, set the major_id column from the students table as a foreign key that references the major_id column from the majors table. 
  - Here's an example of how to do that: ALTER TABLE <table_name> ADD FOREIGN KEY(<column_name>) REFERENCES <referenced_table_name>(<referenced_column_name>);
  - This table looks good. Now, set the major_id column from the students table as a foreign key that references the major_id column from the majors table. Here's an example of how to do that: ALTER TABLE <table_name> ADD FOREIGN KEY(<column_name>) REFERENCES <referenced_table_name>(<referenced_column_name>);

  - Type ALTER TABLE students ADD FOREIGN KEY(major_id) REFERENCES majors(major_id); in the psql prompt

#### To Continue after a session has ended
  - open up the lesson
  - view command pallete > start 
  - psql --username=freecodecamp --dbname=postgres
  - postgres=> \c students;
  - students=> \dt
  - should be good to go 

// we are 15% complete on Sat Feb 15 2025

#### Question

What is the difference between saying SQL, psql, and PostgresSQL?
  - The terms SQL, psql, and PostgreSQL are related but have distinct meanings:

SQL (Structured Query Language)
  - SQL is a language used to manage and query databases.
  - It’s not specific to PostgreSQL—it works with many database systems (MySQL, SQLite, SQL Server, etc.).
   - SQL is not a tool or a program—it’s just the language used to interact with databases.

PostgreSQL (Postgres)
  - PostgreSQL (or Postgres for short) is a database management system (DBMS).
  - It is an advanced, open-source relational database system.
  - You use SQL to interact with PostgreSQL databases.
  - Example: When you run a PostgreSQL server, it manages databases like students, employees, etc.

psql (PostgreSQL Shell)
  - psql is the command-line tool (interactive shell) used to interact with PostgreSQL.
  - It allows you to run SQL queries directly from the terminal.
  - You can also use special psql commands (which aren’t part of standard SQL), like:
  ```sql
  \l   -- List databases
\c students  -- Connect to a database
\dt  -- Show tables
```






