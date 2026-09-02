### 1. Actors

In software engineering, an **actor is an entity that interacts with the system** to achieve a goal. 

Actors in this system include:

- Administrator
- Teacher
- Faculty
- HR
- Student
- Employee

### 2. Organization Types and Roles

The platform supports three organization types: School, College, and Company. Each organization type has roles with different responsibilities and permissions. There are three types of Organization:

1. School
2. College
3. Company

Every types has their own roles which help us t understand their work.

1. School: 
    
    School Organization has three roles of their actors:
    
    1. Admin: So the responsibility of admin is to manage the system very well, because of too much responsibility like
        - Admin should be able to view an organizational dashboard containing user counts and attendance summaries such as total users, present users, and absent users.
        - Should able to add/deactivate/update the students and teachers.
        - View every students and teachers personal information (not password)
    2. Teacher: So the responsibility of teachers are:
        - In every school, each class usually has a class teacher who is assigned to manage the class and teach the students, so that teacher should able to add students. Adding students responsibility is assign on to class teacher not every teacher.
        - Teachers should be able to mark attendance only for students/classes they are authorized to manage. Students can report an incorrect attendance record to an administrator for review and correction.
        - Can view the student info.
        - Can’t able to see the other teacher personal info
    3. Student: Responsibility of student is:
        - Should able to see their own Attendance and personal info.
2. College: 
    
    College Organization has three roles of their actors:
    
    1. Admin: So the responsibility of admin is to manage the system very well, because of too much responsibility like
        - Admin should be able to view an organizational dashboard containing user counts and attendance summaries such as total users, present users, and absent users.
        - Should able to add/deactivate/update the students and faculties.
        - View every students and faculties personal information (not password).
    2. Faculty: So the responsibility of Faculties are:
        - Should able to mark attendance of students
        - Can view the student info.
        - Faculty members cannot view other faculty members' personal information.
        - Some faculty will be HOD of their department, so are responsible for adding students. HOD is not a seprate role, it is additional responsibility.
        - Students can report an incorrect attendance record to an administrator for review and correction.
        - An HOD can manage students within their assigned department.
    3. Student: Responsibility of studetn is:
        - Should able to see their own Attendance and personal info.
3. Company: 
    
    Company Organization has three roles of their actors:
    
    1. Admin: So the responsibility of admin is to manage the system very well, because of too much responsibility like
        - Admin should be able to view an organizational dashboard containing user counts and attendance summaries such as total users, present users, and absent users.
        - Should able to add/deactivate/update the employees/HR users.
        - View every employees personal information (not password).
    2. HR: So the responsibility of HR are:
        - Should able to give permission of leaves, and able reject the leaves
        - Can view the employees info.
        - Should able to view attendance history.
        - Should able to generate attendance reports.
        - HR can correct employee attendance records after reviewing the request.
    3. Employee: Responsibility of employees is:
        - Should able to see their own Attendance and personal info.
        - Employee should able to mark their attendance.

### 3. Actors Goals

**Admin**

> Manage organization users and monitor overall attendance.
> 

**Teacher**

> Record and monitor attendance for assigned students.
> 

**Faculty**

> Record and monitor attendance for assigned students and, when assigned as HOD, manage students within their department.
> 

**Student**

> View personal attendance records and attendance percentage.
> 

**HR**

> Manage employee attendance and leave requests.
> 

**Employee**

> View personal attendance and leave information.
>
