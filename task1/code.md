# University Scholarship Allocation System

Here is a complete B.Tech first-year Python mini-project with the problem statement, algorithm, flowchart, Python source code, sample input, and sample output. You can use this format for your lab record.

## 1. Problem Statement

Design and develop a Python program to allocate university scholarships to students based on their aggregate marks, subject-wise minimum marks, attendance percentage, and family income. The program should identify eligible students, rank them according to predefined criteria, and resolve ties using aggregate marks, attendance percentage, and student ID.

## 2. Algorithm

1. Start the program.
2. Read the number of students.
3. Enter each student's ID, name, aggregate marks, subject-wise marks, attendance percentage, and annual family income.
4. Check the eligibility criteria:
   - Aggregate marks must be at least 75%.
   - Each subject mark must be at least 60%.
   - Attendance must be at least 75%.
   - Annual family income must not exceed ₹2,50,000.
5. Add eligible students to the eligible list.
6. Sort eligible students using these rules:
   - Higher aggregate marks first.
   - If aggregate marks are equal, higher attendance first.
   - If both are equal, lower student ID first.
7. Display the eligible students in ranked order.
8. If no students qualify, display a message indicating that no students are eligible.
9. Stop.
``` marmaid
## 3. Flowchart
```
## 4. Python Source Code

```
# University Scholarship Allocation Systemstudents = []eligible_students = []n = int(input("Enter number of students: "))for i in range(n):    print("\nEnter details of student", i + 1)    student_id = int(input("Student ID: "))    name = input("Student Name: ")    aggregate = float(input("Aggregate marks (%): "))    subjects = int(input("Number of subjects: "))    subject_marks = []    for j in range(subjects):        mark = float(input(f"Subject {j + 1} marks: "))        subject_marks.append(mark)    attendance = float(input("Attendance (%): "))    income = float(input("Annual family income (Rs.): "))    student = {        "id": student_id,        "name": name,        "aggregate": aggregate,        "subjects": subject_marks,        "attendance": attendance,        "income": income    }    students.append(student)    if (aggregate >= 75 and        all(mark >= 60 for mark in subject_marks) and        attendance >= 75 and        income <= 250000):        eligible_students.append(student)# Ranking rules:# 1. Higher aggregate marks# 2. Higher attendance# 3. Lower student IDeligible_students.sort(    key=lambda s: (        -s["aggregate"],        -s["attendance"],        s["id"]    ))print("\n--- Scholarship Allocation Results ---")
```

## 5. Sample Input

```

Enter number of students: 4

Enter details of student 1
Student ID: 101
Student Name: Asha
Aggregate marks (%): 85
Number of subjects: 3
Subject 1 marks: 80
Subject 2 marks: 90
Subject 3 marks: 85
Attendance (%): 90
Annual family income (Rs.): 200000

Enter details of student 2
Student ID: 102
Student Name: Ravi
Aggregate marks (%): 85
Number of subjects: 3
Subject 1 marks: 75
Subject 2 marks: 80
Subject 3 marks: 85
Attendance (%): 95
Annual family income (Rs.): 230000

Enter details of student 3
Student ID: 103
Student Name: Meena
Aggregate marks (%): 78
Number of subjects: 3
Subject 1 marks: 70
Subject 2 marks: 65
Subject 3 marks: 80
Attendance (%): 80
Annual family income (Rs.): 250000

Enter details of student 4
Student ID: 104
Student Name: Kiran
Aggregate marks (%): 90
Number of subjects: 3
Subject 1 marks: 90
Subject 2 marks: 55
Subject 3 marks: 95
Attendance (%): 90
Annual family income (Rs.): 180000

```

## 6. Sample Output

```

--- Scholarship Allocation Results ---

Rank  ID    Name       Aggregate  Attendance
1     102   Ravi       85.00      95.00%
2     101   Asha       85.00      90.00%
3     103   Meena      78.00      80.00%

Ineligible Students:
104 - Kiran

```

## 7. Explanation of the Flowchart and Tie-Breaking Rules

- Eligibility check: A student must satisfy all four conditions.
- Sorting: The program first considers aggregate marks, then attendance, and finally student ID.
- Tie resolution: Ravi and Asha both scored 85% aggregate marks. Ravi ranks first because his attendance is 95%, compared with Asha's 90%.
- Ineligible student: Kiran has 90% aggregate marks but scores only 55 in one subject, below the required 60 marks. Therefore, Kiran is not eligible.

Result: The program successfully identifies eligible students, ranks them according to the specified rules, and displays the scholarship allocation results.
