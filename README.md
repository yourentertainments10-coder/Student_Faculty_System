# Student Faculty Management System (Flask + SQLite)

A web-based Student Faculty Management System built using Flask and SQLAlchemy that provides role-based access for students and faculty. The system allows faculty members to manage assignments and attendance, while students can view their academic records through dedicated dashboards.

## Features

### User Authentication

* Secure Signup and Login System
* Password Hashing using Werkzeug
* Session-Based Authentication
* Role-Based Access Control

### Faculty Module

* Faculty Dashboard
* Add Assignments
* Manage Student Attendance
* View Academic Records

### Student Module

* Student Dashboard
* View Assignments
* View Personal Attendance Records
* Access Academic Information

### Admin Module

* View Students
* View Faculty Members
* View Assignments
* View Attendance Records
* Dashboard Summary Statistics

## Technology Stack

* Python
* Flask
* Flask-SQLAlchemy
* SQLite
* HTML
* CSS
* Jinja2 Templates

## Project Structure

```text
.
├── ap.py
│
├── static/
│   └── style.css
│
├── templates/
│   ├── base.html
│   ├── login.html
│   ├── signup.html
│   ├── admin_dashboard.html
│   ├── admin_students.html
│   ├── admin_faculty.html
│   ├── admin_assignments.html
│   ├── admin_attendance.html
│   ├── faculty_dashboard.html
│   ├── faculty_add_assignment.html
│   ├── faculty_mark_attendance.html
│   ├── student_dashboard.html
│   ├── student_assignments.html
│   └── student_attendance.html
│
└── database/
    └── db.sql
```

## How It Works

### 1) User Authentication

* Users register as either Student or Faculty.
* Passwords are securely hashed before storage.
* Login credentials are validated.
* Role-based access is provided after successful authentication.

### 2) Faculty Management

Faculty members can:

* Create and manage assignments
* Mark attendance for students
* Access faculty dashboard
* Monitor academic activities

### 3) Student Portal

Students can:

* View assigned coursework
* Check attendance records
* Access student dashboard
* Track academic progress

### 4) Administration

Administrators can:

* Manage students and faculty records
* View attendance information
* Monitor assignments
* Access system-wide statistics

## Database

The application uses SQLite as the primary database.

### Models

#### User

Stores:

* User ID
* Username
* Password (Hashed)
* Role (Student / Faculty)

#### Assignment

Stores:

* Assignment Title
* Description
* Faculty Information

#### Attendance

Stores:

* Student Information
* Attendance Date
* Attendance Status
* Faculty Information

## Setup & Run

### 1) Create Virtual Environment

```bash
python -m venv venv
venv\Scripts\activate
```

### 2) Install Dependencies

```bash
pip install flask flask_sqlalchemy werkzeug
```

### 3) Run the Application

```bash
python ap.py
```

### 4) Open in Browser

```text
http://127.0.0.1:5000
```

## Available Routes

### Authentication

* `/login`
* `/signup`
* `/logout`

### Faculty

* `/faculty`
* `/faculty/add-assignment`
* `/faculty/mark-attendance`

### Student

* `/student`
* `/student/assignments`
* `/student/attendance`

### Admin

* `/admin`
* `/admin/students`
* `/admin/faculty`
* `/admin/assignments`
* `/admin/attendance`

## Screenshots

### Login Page

![Login](screenshots/login.png)

### Faculty Dashboard

![Faculty Dashboard](screenshots/faculty-dashboard.png)

### Student Dashboard

![Student Dashboard](screenshots/student-dashboard.png)

### Attendance Management

![Attendance](screenshots/attendance.png)

## Security Notes

* Passwords are stored as hashed values.
* Session management is implemented using Flask sessions.
* Replace the default secret key before production deployment.
* Disable debug mode in production environments.

## Future Improvements

* Email Notifications
* Role-Based Admin Authentication
* Assignment Submission Module
* Attendance Analytics
* Student Performance Tracking
* MySQL Integration

## Author

**Anuj Srivastava**

Aspiring Full-Stack Developer | Python | Flask | SQL | Web Development

