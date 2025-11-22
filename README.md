# Django Blog Backend API

This project implements a robus backend for a Blog application using **Django** and **Django REST Framework (DRF)**. It features a content management system via the Django Admin panel and exposes the data through a RESTful API.

## Project Overview

The goal of this project is to demonstrate how to build a scalable backend architecture with relational database models and API endpoints.

**Key Features:**
    * **Django Admin Interface:** A powerful GUI for managing blog posts (Create, Read, Update, Delete).
    * **RESTful API:** Exposes blog data as JSON via `/api/posts/` for external consumption.
    * **Database Modeling:** Uses Django ORM to define a structured `BlogPost` schema.
    * **Browsable API:** Leverages DRF's built-in interface for easy testing and interaction.

## Prerequisites

* **Python 3.8+**

## Setup & Installation

1. **Clone the Repository**
    ```bash
    git clone https://github.com/shivamgravity/django-blog-backend-api
    cd django-app
    ```
2. **Set Up Virtual Environment**
    ```bash
    # Create venv
    python -m venv venv

    # Activate venv (Windows)
    venv\Scripts\activate

    # Activate venv (Mac/Linux)
    source venv/bin/activate
    ```
3. **Install Dependencies**
    ```bash
    pip install django djangorestframework
    ```
4. **Initialize Database**
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```
5. **Create Admin User**
    ```bash
    python manage.py createsuperuser
    ```

## How to Run

1. **Start the Server:**
    ```bash
    python manage.py runserver
    ```
2. **Access the Admin Panel:**
    * Go to `http://127.0.0.1:8000/admin`
    * Log in with your superuser credentials.
    * You can add, edit, and delete blog posts here.
3. **Access the API:**
    * Go to `http://127.0.0.1:8000/api/posts/`
    * You will see the JSON representation of your blog posts.

## Solution Architecture

This project follows the **MVT (Model-View-Template)** architecture standard in Django, extended with a Serializer layer for the API.

* **Model (`models.py`):** Defines teh `BlogPost` structure (title, content, created_at). Django ORM maps this to a SQL database table.
* **Serializer (`serializers.py`):** Converts the complex `BlogPost` model instances into native Python datatypes (JSON) for the API.
* **View (`views.py`):** Uses DRF's `ModelViewSet` to handle the logic for all CRUD operations (Create, Retrieve, Update, Delete) automatically.
* **URLConf (`urls.py`):** Routes incoming HTTP requests to the appropriate view logic.

## API Endpoints

| **Method** | **Endpoints** | **Description** |
|:----------:|:-------------:|:---------------:|
| `GET` | `/api/posts/` | List all blog posts |
| `POST` | `/api/posts/` | Create a new blog post |
| `GET` | `/api/posts/<id>/` | Retrieve a specific post |
| `PUT` | `/api/posts/<id>/` | Update a specific post |
| `DELETE` | `/api/posts/<id>/` | Delete a specific post |
