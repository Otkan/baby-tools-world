# Baby Tools World

This repository contains the source code of "Baby Tools World", a simple full stack shop application written in Python using Django.  
It demonstrates basic e-commerce functionality such as product management and user authentication.  
The project was developed for educational purposes only and does not aim to be production-ready.

> [!NOTE]
> This project assumes you already know the Python programming language.

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Quickstart](#quickstart)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Apps Overview](#apps-overview)
- [Additional Notes](#additional-notes)

---

## Prerequisites

In order to seamlessly interact with the repository and the software it contains, you need the following tools installed:

- Python Interpreter
- pip (Python package manager)
- Optional: Virtual environment (`venv`)
- Optional: OCI-compliant container engine (e.g. Docker, Podman)
- Editor/IDE of your choice (VS Code, PyCharm, etc.)

---

## Quickstart

In order to quickly get started with the project, follow these steps:

1. Clone the repository:
   git clone <your-repo-url>

2. Navigate to the repository:
   cd baby-tools-world

3. (Optional) Create a virtual environment:
   python -m venv venv

4. Activate the virtual environment:
   - macOS/Linux: source venv/bin/activate
   - Windows: venv\Scripts\activate

5. Install the project dependencies:
   pip install -r requirements.txt

6. Configure environment variables:
   cp example.env .env

7. Navigate to the src directory:
   cd src

8. Prepare the database:
   python manage.py makemigrations
   python manage.py migrate

9. Start the application:
   python manage.py runserver

10. Open your browser and visit:
   http://localhost:8000

11. (Optional) Create a superuser:
   python manage.py createsuperuser

---

## Usage

### Configuration

To configure the project:

1. Copy the example environment file:
   cp example.env src/.env

2. Edit the `.env` file and set the required environment variables:

- ALLOWED_HOSTS: Comma-separated list of allowed hosts (default: localhost,127.0.0.1,0.0.0.0)
- DEBUG: True for development or False for production

> [!IMPORTANT]
> The `.env` file must be located in the same directory as `manage.py`.

---

### Running Linting Tools

To ensure code quality and PEP 8 compliance:

black .
isort .

> [!TIP]
> Run linting before pushing commits to avoid CI pipeline failures.

> [!NOTE]
> If a CI workflow fails, check the logs to identify the issue.

---

### Testing

This project contains tests within the individual Django apps.  
Tests are automatically discovered if their filenames contain `test`.

Example structure:

baby-tools-world/src/products  
├── management  
├── migrations  
├── templates  
└── tests  
    ├── __init__.py  
    ├── test_category_model.py  

To run tests:

python manage.py test

For more details, see: ./docs/testing.md

---

### Running with a WSGI Server

WSGI (Web Server Gateway Interface) defines how web servers communicate with Python applications.

In production, you can use a WSGI server such as gunicorn:

gunicorn projectname.wsgi:application

> [!NOTE]
> On Windows, you may need to use waitress instead of gunicorn.

For more information, see: ./docs/wsgi.md

---

### Seeding the Application

To populate the database with initial test data:

python manage.py seed_db

---

### Containerization

This project can also be run inside a container.

> [!NOTE]
> The following examples use Docker.

Build the image:

docker build -t baby-tools-world:local .

Run the container:

docker run --rm -it -p 8000:8000 baby-tools-world:local

Run with environment variables:

docker run --rm -it -p 8000:8000 --env-file .env baby-tools-world:local

---

## 📁 Project Structure

- `.gitlab`: GitLab specific project files
- `.github`: GitHub specific project files
- `src`: Application source code (Django project, apps, etc.)
- `requirements.txt`: Project dependencies

---

## Apps Overview

The project is modularized into several apps:

- `products`: Manages product listings and categories
- `users`: Handles user authentication and registration

Each app contains its own:

- models.py  
- views.py  
- urls.py  
- admin.py  

---

## Additional Notes

> [!WARNING]
> This project is intended for educational purposes only and is not production-ready.

- Code style follows PEP 8 using Black and Flake8  
- Environment variables are required for configuration  
- CI pipelines may fail if linting rules are violated  