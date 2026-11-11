# DentaNueva Dental Clinic Management System

DentaNueva is a web-based Dental Clinic Management System designed to manage patient records, appointments, dental charting, clinical images, inventory, and billing. It provides clinic staff, doctors, and patients with an organized platform for handling dental clinic operations, reducing manual record-keeping, and improving overall clinic management. The system also includes email/SMS notification integrations, Xendit payment processing, and an AI-assisted appointment forecasting module to support clinic planning and decision-making.

---

## Group Members & Roles

- **Limen, Princelyn** – Project Leader / Documentation
- **Jacaba, Erwin** – Main Programmer / Backend Developer / Database Administrator
- **Amican, Karl Angelo** – Frontend Developer / UI-UX Developer
- **Ignacio, Jericho** – Documentation
- **Salisali, Christian** – Documentation

---

## Tech Stack

- **Frontend:** HTML5, CSS3, JavaScript
- **Backend:** PHP
- **Forecasting Module:** Python
- **Database:** MySQL
- **Database Management:** phpMyAdmin
- **Payment Integration:** Xendit API
- **Email Integration:** PHPMailer / SMTP (if configured)
- **SMS Integration:** SMS API Provider
- **AI / Forecasting:** Python-based appointment forecasting module
- **Tools & Version Control:** Git, GitHub, Visual Studio Code, XAMPP, Composer

---

## System Requirements & Prerequisites

Before installing and running DentaNueva, make sure the following software and tools are installed:

- Windows 10 or higher (or a compatible operating system)
- XAMPP with Apache and MySQL
- PHP 8.0 or higher
- MySQL Server
- Composer (PHP dependency manager)
- Python 3.9 or higher (for the forecasting module)
- pip (Python package manager)
- Git
- Visual Studio Code or another code editor
- A modern web browser (Google Chrome recommended)
- Internet connection for external API integrations

---

## Installation & Setup Instructions

Follow these steps to install and configure DentaNueva on your local machine.

### 1. Clone the Repository

Open your terminal or command prompt and execute:

```bash
git clone https://github.com/Erw1xn/NEW-UPDATED-CAPSTONE-CODES.git
```

Navigate to the cloned project directory:

```bash
cd NEW-UPDATED-CAPSTONE-CODES
```

If the repository has a different name, use its actual GitHub repository URL and folder name.

### 2. Move the Project to XAMPP

Copy or move the project folder into the XAMPP `htdocs` directory.

Example:

```text
C:\xampp\htdocs\DENTAL_CLINIC
```

Make sure the project folder contains the following directories and files:

```text
DENTAL_CLINIC/
├── api/
├── database/
├── doctor/
├── forecasting/
├── homepage/
├── img/
├── login/
├── navigation_bar/
├── patients/
├── php/
├── shared/
├── signup/
├── staff/
├── uploads/
├── vendor/
├── composer.json
├── composer.lock
├── index.php
└── README.md
```

### 3. Install PHP Dependencies

Open the terminal inside the project directory and execute:

```bash
composer install
```

This installs the PHP libraries and dependencies specified in `composer.json`.

---

## Database Setup & Configuration

DentaNueva uses MySQL as its database management system.

### 1. Start XAMPP Services

1. Open the XAMPP Control Panel.
2. Start **Apache**.
3. Start **MySQL**.

### 2. Create the Database

1. Open your browser.
2. Navigate to:

   `http://localhost/phpmyadmin`

3. Create a new database named:

   `dental_clinic_system`

4. Use the `utf8mb4` character set when configuring the database.

### 3. Import the Database SQL Files

The project contains SQL schema files inside the `database/` directory.

Import the following files into the `dental_clinic_system` database:

**First: `patient_records.sql`**

This file contains the main database structures, including:

- User accounts (`tbl_users`)
- Patient records (`tbl_patients`)
- Medical forms (`tbl_medical_forms`)
- Patient appointments (`tbl_patient_appointments`)
- Finance transactions (`tbl_finance_transactions`)
- Staff notifications (`tbl_staff_notifications`)
- Reschedule requests (`tbl_reschedule_requests`)
- Patient treatments (`tbl_patient_treatments`)
- Dental charts (`tbl_dental_chart`)
- Clinical images (`tbl_clinical_images`)

**Second: `inventory_forecasting.sql`**

This file contains the database structures for inventory management and forecasting:

- Inventory items (`tbl_inventory_items`)
- Inventory movements (`tbl_inventory_movements`)
- Inventory demand history (`tbl_inventory_demand_history`)
- Inventory forecast runs (`tbl_inventory_forecast_runs`)

To import each file:

1. Select the `dental_clinic_system` database in phpMyAdmin.
2. Click the **Import** tab.
3. Choose the corresponding `.sql` file.
4. Click **Import** or **Go**.
5. Repeat the process for the second SQL file.

**Important:** Import `patient_records.sql` first because the inventory schema is intended to work with the main clinic database.

### 4. Configure Database Connection

Open:

`php/db_connect.php`

Review the database connection settings:

```php
$host = "127.0.0.1";
$port = 3307;
$username = "root";
$password = "";
$database = "dental_clinic_system";
```

Make sure these settings match your local MySQL configuration.

The default configuration shown above uses port `3307`. If your MySQL server uses another port, update the configuration accordingly.

The project may also use a local `php/db_credentials.php` file for database credentials. Configure this file locally when required.

**Security Reminder:** Never upload database passwords or private credentials to a public GitHub repository.

---

## External API & Service Configuration

DentaNueva supports external services for payment processing, email notifications, SMS notifications, and forecasting.

These integrations may require separate API accounts, credentials, and configuration before their corresponding features can operate.

### 1. Xendit Payment Integration

The system uses Xendit for payment processing.

Setup instructions:

1. Create or access a Xendit developer account.
2. Obtain the required API credentials from the Xendit Dashboard.
3. Configure the credentials in the project's Xendit configuration file:

   `php/xendit_config.php`

4. Configure the appropriate webhook URL in the Xendit Dashboard if webhook notifications are implemented.
5. Use test credentials and test mode for development.

**Note:** Actual payment processing requires valid Xendit credentials and the appropriate account configuration.

### 2. Email Notification Integration

The system supports email notifications for relevant clinic activities.

Setup instructions:

1. Configure the SMTP settings in:

   `php/mail_config.php`

2. Provide the required SMTP host, port, username, password, and sender email.
3. Make sure the email service and PHPMailer dependencies are properly configured.
4. Test email delivery using an authorized email account.

Email notifications require valid SMTP credentials and an active email service.

### 3. SMS Notification Integration

The system includes SMS notification integration for sending text message notifications.

Related configuration files include:

- `php/sms_config.php`
- `php/skysms_config.php`
- `php/sms_sender.php`

Setup instructions:

1. Obtain API credentials from the configured SMS provider.
2. Add the required credentials to the appropriate configuration file.
3. Configure the sender information and API settings.
4. Test SMS delivery using an authorized phone number.

**Note:** SMS delivery may require an active provider account, available credits, and valid API credentials. If SMS integration is not activated, the SMS functionality may remain unavailable until properly configured.

### 4. Python Forecasting Module

DentaNueva includes a Python-based forecasting module for supporting clinic planning.

Setup instructions:

1. Install Python 3.9 or higher.
2. Open a terminal in the project directory.
3. Navigate to the `forecasting/` folder.
4. Install the Python dependencies specified by the project's requirements file, if provided.

Example:

```bash
cd forecasting
pip install -r requirements.txt
```

If the forecasting directory does not contain a `requirements.txt` file, install the dependencies listed in the actual Python scripts.

Make sure Python is properly installed and accessible through the system PATH.

**Note:** The forecasting module requires its Python dependencies and database connection to be properly configured.

### 5. AI-Related Configuration

If the deployed forecasting or other AI-assisted features use an external AI provider, configure the required API credentials and settings in the corresponding project configuration.

Do not publish private API keys or access tokens in the public repository.

---

## Running the Application

After completing the installation and database configuration:

### 1. Start XAMPP

Open the XAMPP Control Panel and make sure the following services are running:

- Apache
- MySQL

### 2. Open the Application

Open your web browser and navigate to:

`http://localhost/DENTAL_CLINIC/`

If the project uses a different folder name, replace `DENTAL_CLINIC` with the actual folder name.

### 3. Access the System

Navigate through the available system pages and log in using an existing registered account with the appropriate access role.

The available user roles include:

- Administrator / Staff
- Doctor
- Patient

---

## Default Login Credentials

DentaNueva uses its database authentication system for user accounts.

There are no universal default login credentials specified in this repository documentation.

Use an existing registered account or an administrator account created and provided by the project administrator.

For security purposes, do not publish actual account passwords or private login credentials in the public repository.

---

## Project Directory Structure

The following is an overview of the main project directories:

| Directory / File  | Description                           |
| ----------------- | ------------------------------------- |
| `api/`            | Application API endpoints             |
| `database/`       | SQL database schema files             |
| `doctor/`         | Doctor-related system modules         |
| `forecasting/`    | Python forecasting module             |
| `homepage/`       | Homepage and landing page             |
| `img/`            | System images and visual assets       |
| `login/`          | User authentication pages             |
| `navigation_bar/` | Shared navigation components          |
| `patients/`       | Patient-side modules                  |
| `php/`            | PHP configuration and backend scripts |
| `shared/`         | Shared application resources          |
| `signup/`         | User registration pages               |
| `staff/`          | Staff-side management modules         |
| `uploads/`        | Uploaded system files                 |
| `vendor/`         | Composer-installed PHP dependencies   |
| `index.php`       | Application entry point               |

---

## Security & Configuration Notes

- Never commit private API keys, passwords, database credentials, or SMTP credentials to GitHub.
- Keep local configuration files containing sensitive information private.
- Use test credentials when developing and testing payment integrations.
- Configure external services using valid provider accounts.
- Make sure the database connection settings match the local environment.
- Uploaded files and required dependencies must be available for the system to function correctly.

---

## Troubleshooting

**Database Connection Failed**

- Check whether MySQL is running in XAMPP.
- Verify the database name, username, password, and port.
- Make sure `dental_clinic_system` exists.

**PHP Dependencies Missing**

- Open the project directory in the terminal.
- Run `composer install`.

**Email Notifications Not Working**

- Verify SMTP credentials.
- Check the SMTP host and port.
- Make sure the email service is active.

**SMS Notifications Not Working**

- Verify the SMS provider credentials.
- Check whether the account has sufficient credits.
- Confirm that the SMS API configuration is correct.

**Xendit Payment Not Working**

- Verify the API credentials.
- Check the payment configuration.
- Confirm that the webhook settings are correct when applicable.

**Forecasting Module Not Working**

- Verify the Python installation.
- Install the required Python dependencies.
- Check the database connection and forecasting configuration.

---

## Repository Information

**Project:** DentaNueva Dental Clinic Management System

**Repository:** https://github.com/Erw1xn/NEW-UPDATED-CAPSTONE-CODES

**Version Control:** Git and GitHub

**Project Type:** Web-Based Dental Clinic Management System

**Database:** MySQL

**Development Environment:** XAMPP

---

_Developed as a Capstone Project._
