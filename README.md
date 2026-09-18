# Student Management System - Java

## Overview
A command-line Student Management System developed in Java. It demonstrates object-oriented programming, collections, file handling, exception handling, validation, sorting, streams, and modular class design.

## Features
- Add student records
- List all students
- Search by student ID
- Delete a student
- Generate a performance report
- Calculate average marks and identify the top student
- Save/load data using a CSV file
- Input validation and exception handling

## Technologies
- Java 17 or later
- Java Collections Framework
- Java I/O
- Java Streams
- Git/GitHub

## Project Structure
```text
StudentManagementSystem/
├── README.md
├── statement.md
├── .gitignore
├── src/
│   ├── Main.java
│   ├── Student.java
│   ├── StudentManager.java
│   ├── FileStorage.java
│   ├── Validator.java
│   └── ReportService.java
└── tests/
    └── StudentManagerTest.java
```

## Requirements
Install JDK 17 or newer. Verify:
```bash
java -version
javac -version
```

## Compile
From the project root:
```bash
mkdir -p out
javac -d out src/*.java
```

On Windows Command Prompt:
```bat
mkdir out
javac -d out src\*.java
```

## Run
```bash
java -cp out Main
```

The program is fully terminal based. On first use, no GUI or external dependency is required.

## Test
Compile the test:
```bash
javac -cp out -d out tests/StudentManagerTest.java
```

Run assertions:
```bash
java -ea -cp out StudentManagerTest
```

Expected:
```text
All tests passed.
```

## Data
When the user selects `Save & Exit`, the program creates `students.csv` in the project root. It is automatically loaded when the program starts.

## Example
```text
=== Student Management System ===

1. Add Student
2. List Students
3. Search Student
4. Delete Student
5. Performance Report
6. Save & Exit
Choose an option: 1
Enter ID: 101
Enter name: Shayan
Enter course: CSE AI-ML
Enter marks (0-100): 88
Student added successfully.
