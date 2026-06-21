
# 🛒 Django eCommerce Application
A robust, full-stack eCommerce web application built using Python and the Django framework. This platform features a responsive frontend interface for customers to browse items and a comprehensive administrative backend panel for inventory, order, and user management.

---
## 🌟 Key Features

* **Dynamic Catalog:** Beautiful customer storefront displaying live product listings.
* **Admin Control Center:** Full CRUD capabilities (Create, Read, Update, Delete) for products, feedback, and user models.
* **Automated Invoicing:** On-the-fly PDF receipt and invoice generation using `xhtml2pdf`.
* **Lightweight Storage:** Zero-configuration local data pipeline powered by a serverless SQLite architecture.
---


# ⚙️ FUNCTIONS

## 👤 Customer
- Customer can view/search products without login.
- Customer can also add/remove product to cart without login (if customer try to add same product in cart. It will add only one)
- When customer try to purchase product, then he/she must login to system.
- After creating account and login to system, he/she can place order.
- There is a payment page also (just for demo, DONT FILL YOUR CARD DETAILS THERE ,By the way, website do not save that details)
- If customer click on pay button, then their payment will be successful and their order will be placed.
- Customer can check their ordered details by clicking on orders button.
- Customer can see the order status (Pending, Confirmed, Delivered) for each order  
- Customer can Download their order invoice for each order
- Customer can send feedback to admin (without login)

## 👑 Admin
- First admin will login ( for username/password run following command in cmd )
```
py manage.py createsuperuser
```
- Give username, email, password and your admin account will be created.
- After login, there is a dashboard (attached in screenshot) where admin can see how many customer is registered, how many products are there for sale, how many orders placed.
- Admin can add/delete/view/edit the products.
- Admin can view/edit/delete customer details.
- Admin can view/delete orders.
- Admin can change status of order (order is pending, confirmed, out for delivery, delivered)
- Admin can view the feedbacks sent by customers.

## 🛡️ Other Features
- customer places order and admin deleted that user(fraud detection), then their orders will automatically deleted
- suppose 1 customer places 4 products order and admin deleted 2 product from website, then that 2 product order will
    also be deleted and other 2 will be their
- If user click on purchase button without having products in their cart, then website will ask to add product in cart first.
--- 


## 🏗️ Architecture & Database Configuration
By default, Django is configured to use an **SQLite** database. Unlike enterprise databases that require separate server setups, SQLite is completely serverless and stores the entire schema, relational tables, and datasets within a single file.
| Configuration Item | Detail | File Path |
| :--- | :--- | :--- |
| **Database Engine** | `django.db.backends.sqlite3` | `ecommerce/settings.py` |
| **Data Storage File** | `db.sqlite3` | Root Directory (`./db.sqlite3`) |
---


--- 
# 🚀 Technical Setup & Installation
---

## Option 1: Standard Installation (Pip)
-1. Install Python(3.7.6) (Dont Forget to Tick Add to Path while installing Python)

-2. Open Terminal and Execute Following Commands :
```
pip install django==3.0.5
pip install django-widget-tweaks
pip install xhtml2pdf
```
### Extract the downloaded project ZIP file and navigate into the folder:
> cd "E-commerce Store"

```
py manage.py makemigrations
py manage.py migrate
py manage.py runserver
```
- Now enter following URL in Your Browser Installed On Your Pc
```
http://127.0.0.1:8000/
```
---



## Option 2: Isolated Installation (Anaconda)
- To avoid package and dependency version mismatches, it is highly recommended to deploy this application within an isolated **Anaconda Virtual Environment** running Python 3.10.


### Step 1: Environment Isolation
- Open your **Anaconda Prompt** and execute the following to set up a clean workspace:
```bash
# Create a fresh Python 3.10 environment
conda create -n ecom_env python=3.10 -y

# Activate the environment
conda activate ecom_env
```

### Step 2: Extract the downloaded project ZIP file and navigate into the folder:
> cd "E-commerce Store"


### Step 3: Directory Navigation & Dependency Installation
Navigate to your local project directory and install all required modules sequentially:

- Change directory to the project folder
> cd "...\E-commerce Store"

- Install project core dependencies
```
> pip install -r requirement.txt
```
- Install the PDF rendering extension explicitly
```
> pip install xhtml2pdf
```

### Step 4: Initialize Database Tables
Initialize the database tracking and apply schemas to build out your local db.sqlite3 file structure: one-by-one
```
python manage.py makemigrations
``````
python manage.py migrate
```

### Step 5: Run server
```
py manage.py runserver
```
- Now enter following URL in Your Browser Installed On Your Pc
```
http://127.0.0.1:8000/
```
---

# Note:- During starting of project all things are empty because your database have empty to fill this then setup Superuser  


---
## Create Admin Superuser
Generate an administrative account to access the backend panel:
```
python manage.py createsuperuser
```

### Follow the terminal prompts to set up your username, email, and password.
- In settins.py file, You have to give your email and password
```
EMAIL_HOST_USER = 'youremail@gmail.com'
EMAIL_HOST_PASSWORD = 'your email password'
EMAIL_RECEIVING_USER = 'youremail@gmail.com'
```

---
### Authorization Troubleshooting: (If it Occur)
- If your admin account throws a permission or authorization error at login, execute the following commands in order to force-grant global staff and superuser privileges:
```
python manage.py shell
```
- Paste these lines one by one inside the interactive Python shell (>>>):
### Python
```
from django.contrib.auth.models import User
u = User.objects.get(username='YOUR_USERNAME')
u.is_staff = True
u.is_superuser = True
u.save()
exit()
```
--- 

---
## Run the Application
- Start the local development server:
```
python manage.py runserver
```

---
## Open your browser and navigate to:
- Customer Storefront: ```http://127.0.0.1:8000/customer-home```

- Django Administration Panel: ```http://127.0.0.1:8000/admin``` 
(Log in here to click + Add on Products to populate your storefront UI)

---

## Disclaimer
This project is developed for demo purpose and it's not supposed to be used in real application.


---
---
# 📁 Project Directory Structure

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
