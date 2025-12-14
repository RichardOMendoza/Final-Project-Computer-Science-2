Problem Statement :

Many schools struggle to effectively monitor and analyze student academic performances across different sections and subjects because sometimes there is just too much to be able to compute. Without clear insights, many teachers and staff dont know who to help so they can recognize trends and adjust their teaching method.
This problem is important because getting to improve the student performance and providing targetted support can impact significantly on educational success and even a students well-being. Identifying the learning gaps helps school use resources more efficiently and imrpove the curriculum.
The dataset of student grades across various subjects and sections provides valuable information that, when properly analyzed, can address this problem. By analyzing these grades, the project aims to uncover meaningful patterns and trends that educators can use to enhance student learning experiences.

Problem Objectives :

- Calculate each student’s average grade.
- Calculate the average grade for each subject.
- List all students in a given section.
- Find the highest and lowest grade in a specific subject.
- Compute the average grade of a section.
- Identify students above or below a given grade limit.
- Display all students with their full set of grades.

Planned Features :

1.	It keeps all the students’ names and classes.
2.	It adds up the grades and finds who did good.
3.	It  separates students in their right sections.
4.	It lists down the subjects where the student got a final grade lower than 2.50.
5.	Computes the general average of one student.

Planned Inputs and Outputs :

Inputs:
- student id or name
- Section
- Subject
- Grade minimum and maximum (for filtering)

Outputs:
- Avg grade of each student
- Avg grade for each subject
- List of students in a specific section
- Highest and lowest grade found in a subject
- Section average
- Students who are above or below the grade limit
- Full list of students grade in all subjects.

Logic Plan :

The system keeps a record of all students, including their names, sections, and grades in each subject. When the program starts, it shows a menu where the user can choose what they want to do.The system can calculate a student’s average grade by adding all their subject grades and dividing by the number of subjects. It can also find the average grade for each subject by combining the grades of all students.The system can show a list of students in a specific section and find the highest and lowest grades in a subject by comparing all the scores.It can compute the average grade of a section and identify students whose grades are above or below a set limit. The system also displays all students with their complete grades and points out subjects where the grade is below 2.50.The program keeps running until the user chooses to exit.

PSEUDOCODE :

BEGIN
    DECLARE studentList AS ARRAY OF RECORD
        studentID AS STRING
        studentName AS STRING
        section AS STRING
        subject AS STRING
        grade AS INTEGER
    END RECORD

  DECLARE inputStudentID AS STRING
  DECLARE inputSection AS STRING
  DECLARE inputSubject AS STRING
  DECLARE minGrade AS INTEGER
  DECLARE maxGrade AS INTEGER

  DECLARE avgGradePerStudent AS DICTIONARY
  DECLARE avgGradePerSubject AS DICTIONARY
  DECLARE studentsInSection AS ARRAY OF STRING
  DECLARE highestGrade AS INTEGER
  DECLARE lowestGrade AS INTEGER
  DECLARE sectionAverage AS FLOAT
  DECLARE aboveGradeLimit AS ARRAY OF STRING
  DECLARE belowGradeLimit AS ARRAY OF STRING
  DECLARE fullListOfGrades AS DICTIONARY

  // Calculate average grade of each student
  FOR EACH student IN studentList DO
        IF student.studentID NOT IN avgGradePerStudent THEN
            avgGradePerStudent[student.studentID] = 0
        END IF
        avgGradePerStudent[student.studentID] += student.grade
    END FOR

    // Calculate average grade for each subject
  FOR EACH student IN studentList DO
        IF student.subject NOT IN avgGradePerSubject THEN
            avgGradePerSubject[student.subject] = 0
        END IF
        avgGradePerSubject[student.subject] += student.grade
    END FOR

    // List of students in a specific section
  FOR EACH student IN studentList DO
        IF student.section = inputSection THEN
            studentsInSection.APPEND(student.studentName)
        END IF
    END FOR

   // Find highest and lowest grade in a subject
   highestGrade = -1
    lowestGrade = 101
    FOR EACH student IN studentList DO
        IF student.subject = inputSubject THEN
            IF student.grade > highestGrade THEN
                highestGrade = student.grade
            END IF
            IF student.grade < lowestGrade THEN
                lowestGrade = student.grade
            END IF
        END IF
    END FOR

  // Calculate section average
  DECLARE totalGrades AS INTEGER
    DECLARE count AS INTEGER
    totalGrades = 0
    count = 0
    FOR EACH student IN studentList DO
        IF student.section = inputSection THEN
            totalGrades += student.grade
            count += 1
        END IF
    END FOR
    sectionAverage = totalGrades / count

  // Students above or below the grade limit
  FOR EACH student IN studentList DO
        IF student.grade > maxGrade THEN
            aboveGradeLimit.APPEND(student.studentName)
        ELSE IF student.grade < minGrade THEN
            belowGradeLimit.APPEND(student.studentName)
        END IF
    END FOR

  // Full list of students' grades in all subjects
    FOR EACH student IN studentList DO
        IF student.studentID NOT IN fullListOfGrades THEN
            fullListOfGrades[student.studentID] = ARRAY OF INTEGER
        END IF
        fullListOfGrades[student.studentID].APPEND(student.grade)
    END FOR
END

FLOWCHART :

https://docs.google.com/document/d/1R11unnYOjb47hMSE5nlJyVzE_owlowsQGrxzULbnjCY/edit?usp=sharing (GOOGLE DOCS PO MAAM)

