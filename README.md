# Student Faculty System (Flask + SQLite)

A simple Student–Faculty management system built using **Flask** and **SQLAlchemy**.

## Features

- **User authentication** (Signup/Login)
  - Users can register as either **student** or **faculty**
  - Passwords are stored as **hashed** values
- **Role-based dashboards**
  - **Faculty dashboard**
    - Add assignments
    - Mark attendance for all students
  - **Student dashboard**
    - View assignments
    - View personal attendance records
- **Admin routes (templates exist)**
  - Admin pages are present as templates and backend query functions in the code:
    - View students
    - View faculty
    - View assignments
    - View attendance
    - Admin dashboard summary counts

## Technology Stack

- Flask
- Flask-SQLAlchemy
- SQLite (database file: `college.db`)
- Jinja2 templates
- CSS for UI styling

## Project Structure

```text
.
├── ap.py
├── static/
│   └── style.css
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

### 1) Authentication
- **Signup**: `POST /signup`
  - Stores a new user with:
    - `username`
    - `password` (hashed)
    - `role` (`student` or `faculty`)
- **Login**: `POST /login`
  - Validates username/password
  - Saves `user_id` and `role` into Flask `session`
  - Redirects:
    - `faculty` -> `/faculty`
    - `student` -> `/student`

### 2) Faculty
- **Faculty dashboard**: `GET /faculty`
- **Add assignment**: `GET/POST /faculty/add-assignment`
  - Creates an `Assignment` linked to the logged-in faculty user.
- **Mark attendance**: `GET/POST /faculty/mark-attendance`
  - Faculty selects a date and sets Present/Absent for every student.
  - Attendance records are created for all students.

### 3) Student
- **Student dashboard**: `GET /student`
- **View assignments**: `GET /student/assignments`
  - Displays all assignments.
- **View attendance**: `GET /student/attendance`
  - Displays attendance records for the logged-in student.

### 4) Admin (Templates + query routes exist)
Routes implemented in `ap.py` include:
- `/admin/students`
- `/admin/faculty`
- `/admin/assignments`
- `/admin/attendance`
- `/admin`

> Note: Admin UI/access control is not shown in the provided session logic; these routes are defined primarily to render the templates.

## Database

The app uses **SQLite** with this configuration:

- `SQLALCHEMY_DATABASE_URI = 'sqlite:///college.db'`

### Models (from `ap.py`)
- `User`
  - `id`, `username` (unique), `password` (hashed), `role` (`student` / `faculty`)
- `Assignment`
  - `id`, `title`, `description`, `faculty_id` -> `User.id`
- `Attendance`
  - `id`, `student_id` -> `User.id`, `date`, `status` (`Present`/`Absent`), `faculty_id` -> `User.id`

On startup (within app context):
- `db.create_all()` is called to create tables automatically.

### SQL File (`database/db.sql`)
A MySQL-style schema is included in `database/db.sql` (shown in the repo).
The running app itself uses SQLite via SQLAlchemy.

## Setup & Run

### 1) Create a Python virtual environment

```bash
python -m venv venv
venv\Scripts\activate
```

### 2) Install dependencies

```bash
pip install flask flask_sqlalchemy werkzeug
```

### 3) Start the app

```bash
python ap.py
```

Open the displayed local URL (typically):

- `http://127.0.0.1:5000`

## Default Pages / Routes

- `/` -> redirects to `/login`
- `/login` -> login page
- `/signup` -> signup page
- `/faculty` -> faculty dashboard
- `/faculty/add-assignment`
- `/faculty/mark-attendance`
- `/student` -> student dashboard
- `/student/assignments`
- `/student/attendance`
- `/logout` -> clears session

## Notes / Important Implementation Details

- The Flask app uses a hardcoded `secret_key = "secret123"`.
  - Replace it with an environment variable for production.
- Debug mode is enabled:
  - `app.run(debug=True)`
- Attendance is stored per student with:
  - `date` and `status` (Present/Absent)

## License

Add your license information here (MIT/Apache/etc.) if required.

