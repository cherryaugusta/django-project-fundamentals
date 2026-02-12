# Django Project Setup and Fundamentals Showcase

A clean, professional, and well-structured Django project demonstrating best practices in Python, Django, virtual environments, Git, and GitHub. This repository is intentionally designed to showcase core backend development skills, project organization, and workflow discipline expected from entry-level to mid-level Django developers.

---

## 📌 Project Overview

This project walks through the complete lifecycle of setting up a Django project from scratch, including:

- Python virtual environment isolation
- Django installation and verification
- Project and app creation
- URL routing and views
- Database modeling with Django ORM
- Migrations and database inspection
- Development server execution

The repository emphasizes clarity, correctness, reproducibility, and adherence to Django conventions.

---

## 🧰 Technologies Used

- **Python 3.x**
- **Django (latest stable version at setup time)**
- **SQLite (default Django database)**
- **Git & GitHub**
- **Visual Studio Code**

---

## 📁 Project Structure

project-root/
│
├── demoproject/
│ ├── init.py
│ ├── asgi.py
│ ├── settings.py
│ ├── urls.py
│ └── wsgi.py
│
├── firstapp/
│ ├── init.py
│ ├── admin.py
│ ├── apps.py
│ ├── migrations/
│ │ └── init.py
│ ├── models.py
│ ├── tests.py
│ └── views.py
│
├── manage.py
├── db.sqlite3
└── myvenv/

---

## ⚙️ Environment Setup

### 1. Create Project Workspace
```
mkdir project-root
cd project-root
```
Open the folder in Visual Studio Code, then open the integrated terminal.
________________________________________
### 2. Create Virtual Environment
python -m venv myvenv
________________________________________
### 3. Activate Virtual Environment
Windows
```
myvenv\Scripts\activate
```
macOS / Linux
```
source myvenv/bin/activate
```
Successful activation displays:
```
(myvenv)
```
________________________________________
### 4. Install Django
```
pip install Django
```
Verify installation:
```
django-admin --version
```
________________________________________
### 🚀 Django Project Initialization
### 5. Create Django Project
```
django-admin startproject demoproject .
```
The dot (.) ensures the project is created in the root directory without nesting.
________________________________________
### 6. Run Development Server (Verification)
```
python manage.py runserver
```
Access:
```
http://127.0.0.1:8000/
```
Stop the server with:
```
Ctrl + C
```
________________________________________
### 🧩 Application Development
### 7. Create Django App
```
python manage.py startapp firstapp
```
________________________________________
### 8. Register App
In demoproject/settings.py:
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    'firstapp',
]
```
________________________________________
### 9. URL Configuration
```
firstapp/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
demoproject/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('firstapp.urls')),
]
```
________________________________________
### 10. Views Logic
```
firstapp/views.py
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello from First App")
```
________________________________________
### 🗄️ Database and Models
### 11. Model Definition
```
firstapp/models.py
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    age = models.IntegerField()

    def __str__(self):
        return self.name
```
_____________________________________
### 12. Create and Apply Migrations
```
python manage.py makemigrations
python manage.py migrate
```
Django automatically:
•	Generates migration files
•	Creates database tables
•	Tracks schema history
________________________________________
13. Database Inspection
•	Database file: db.sqlite3
•	Recommended VS Code extensions:
o	SQLite Viewer
o	SQLite Explorer
Key tables:
•	firstapp_user
•	auth_user
•	django_migrations
________________________________________
### 🛑 Stopping the Server
```
Ctrl + C
```

---

## 🎯 Skills Demonstrated
•	Django project architecture
•	Clean app separation
•	Django ORM fundamentals
•	URL routing and views
•	Virtual environment management
•	Migration-based database control
•	Professional GitHub documentation

---

## ⚠️ Disclaimer
This project is created strictly for educational purposes and portfolio demonstration.
It is not intended for production use, commercial deployment, or handling real user data. The focus is on demonstrating technical understanding, correct Django workflows, and clean project organization for learning and professional showcasing.

---

## 📄 License
This project is open for educational review and portfolio inspiration. Attribution is appreciated when reused.

---
