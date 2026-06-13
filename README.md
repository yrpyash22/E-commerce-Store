
# 🛒 Django eCommerce Application
A robust, full-stack eCommerce web application built using Python and the Django framework. This platform features a responsive frontend interface for customers to browse items and a comprehensive administrative backend panel for inventory, order, and user management.

---

## Key Features

* **Dynamic Catalog:** Beautiful customer storefront displaying live product listings.
* **Admin Control Center:** Full CRUD capabilities (Create, Read, Update, Delete) for products, feedback, and user models.
* **Automated Invoicing:** On-the-fly PDF receipt and invoice generation using `xhtml2pdf`.
* **Lightweight Storage:** Zero-configuration local data pipeline powered by a serverless SQLite architecture.

---

## Architecture & Database Configuration

By default, Django is configured to use an **SQLite** database. Unlike enterprise databases that require separate server setups, SQLite is completely serverless and stores the entire schema, relational tables, and datasets within a single file.

| Configuration Item | Detail | File Path |
| :--- | :--- | :--- |
| **Database Engine** | `django.db.backends.sqlite3` | `ecommerce/settings.py` |
| **Data Storage File** | `db.sqlite3` | Root Directory (`./db.sqlite3`) |

---

## Technical Setup & Installation

To avoid package and dependency version mismatches, it is highly recommended to deploy this application within an isolated **Anaconda Virtual Environment** running Python 3.10.

### Step 1: Environment Isolation
Open your **Anaconda Prompt** and execute the following to set up a clean workspace:
```bash
# Create a fresh Python 3.10 environment
conda create -n ecom_env python=3.10 -y

# Activate the environment
conda activate ecom_env
```

### Step 2: Directory Navigation & Dependency Installation
Navigate to your local project directory and install all required modules sequentially:
# Switch to your working drive (Example: D drive)
D:

# Change directory to the project folder
cd "Web Dev\ecommerce-master"

# Install project core dependencies
pip install -r requirement.txt

# Install the PDF rendering extension explicitly
pip install xhtml2pdf


### Step 3: Database Migrations
Initialize the database tracking and apply schemas to build out your local db.sqlite3 file structure: one-by-one
> python manage.py makemigrations
> python manage.py migrate

Administrative Account Setup (Superuser)
To access the backend portal and populate your storefront with products, you must initialize an administrator account.

Generate the Account:
python manage.py createsuperuser

# Follow Prompts: Provide a secure Username and Password when prompted by the terminal.


### Authorization Troubleshooting: If your admin account throws a permission or authorization error at login, execute the following commands in order to force-grant global staff and superuser privileges:
> python manage.py shell

Paste these lines one by one inside the interactive Python shell (>>>):
# Python
from django.contrib.auth.models import User
u = User.objects.get(username='YOUR_USERNAME')
u.is_staff = True; u.is_superuser = True; u.save()
exit()

### Execution & Local Deployment
To spin up the local development engine, fire up the server from your terminal:
>python manage.py runserver
Once the compilation is complete and the server is running, access your application locally using these endpoints:

# Customer Storefront: http://127.0.0.1:8000/customer-home
# Django Administration Panel: http://127.0.0.1:8000/admin (Log in here to click + Add on Products to populate your storefront UI)



# 🛒 Full-Stack Django eCommerce Application

A robust, enterprise-grade eCommerce web platform engineered using Python and the Django framework. This application delivers a dynamic, responsive customer storefront alongside an administrative backend panel for fluid inventory, feedback, and order lifecycle management.

---

## 🚀 Key Features

* **Dynamic Storefront:** End-to-end customer interface with product grids, shopping cart tracking, and secure checkout simulation.
* **Granular Admin Dashboard:** Dedicated operational workspace featuring full CRUD controls for inventory items, feedback review, and order dispatching.
* **Automated Invoice Engine:** Structural HTML-to-PDF rendering system powered natively by `xhtml2pdf`.
* **Zero-Config Database Architecture:** Serverless data processing backed by a local SQLite pipeline.

---

## 📁 Project Directory Structure

Below is the complete architectural mapping of the repository repository files:

```text
ecommerce-master/
│
├── ecom/                               # Core Business Logic Application
│   ├── migrations/                     # Database evolutionary state logs
│   │   ├── 0001_initial.py
│   │   ├── 0002_product.py
│   │   ├── 0003_orders.py
│   │   ├── 0004_feedback.py
│   │   └── 0005_feedback_date.py
│   ├── admin.py                        # Model registrations for Django Admin UI
│   ├── apps.py                         # App structural configuration
│   ├── forms.py                        # Validation rules for User inputs
│   ├── models.py                       # Relational Database Blueprints (Products, Orders, Feedback)
│   ├── tests.py                        # Application unit test suites
│   └── views.py                        # HTTP Request controllers & core workflows
│
├── ecommerce/                          # Project Governance & Settings Matrix
│   ├── settings.py                     # Global app matrices, middleware, & assets routing
│   ├── urls.py                         # Top-level URL routing registries
│   ├── asgi.py & wsgi.py               # Asynchronous/Synchronous server interfaces
│
├── static/                             # Client-Side Assets pipeline
│   ├── images/                         # UI/UX structural graphics
│   ├── product_image/                  # Storage node for uploaded merchant inventories
│   ├── profile_pic/                    # User account personalization objects
│   └── screenshots/                    # Visual portfolio data for GitHub preview
│
├── templates/ecom/                     # Dynamic Presentation Layer (HTML Engine)
│   ├── admin_*.html                    # Operational dashboards and inventory management templates
│   ├── customer_*.html                 # Secured user profiles, address management, and interfaces
│   ├── cart.html, payment.html         # Transaction simulation workflows
│   ├── download_invoice.html           # Document layer compiled via xhtml2pdf
│   └── base files & navbars            # Reusable core template layouts
│
├── db.sqlite3                          # Fully integrated local serverless relational database file
├── manage.py                           # Command-line administrative gateway utility
├── requirement.txt                     # Package build dependency manifest
└── README.md                           # Master structural documentation
