# Educational Test Types Platform

## Overview
This full-stack application acts as an educational platform and taxonomy catalog for software testing types. It features a relational database tracking engine, an automated Python ETL pipeline to ingest raw spreadsheet data, and a multi-variable dynamic search dashboard.

The project demonstrates full-stack proficiency by seamlessly connecting a relational database with a Python backend and dynamic HTML5 user interfaces.

## Core Features
- **Dynamic Search Dashboard**: Multi-parameter filtering across 5 relational dimensions (Tester, Level, Category, Classification, Parent Type).
- **Automated ETL Pipeline**: Custom Python parsing script that sanitizes data, maps text metrics to primary keys, and resolves circular taxonomy dependencies on the fly.
- **Relational Data Mapping**: Zero-hardcoding frontend forms that dynamically generate UI dropdowns directly from live SQL lookup metadata tables.
- **Data Integration Wizard**: Web-based submission interface allowing users to manually expand the test catalog while enforcing foreign key constraints.

## Tech Stack
- **Backend Framework**: Python, Flask
- **ORM / Database Layer**: Flask-SQLAlchemy, PyODBC
- **Database Engine**: Microsoft SQL Server (MS SQL)
- **Data Engineering / ETL**: Pandas
- **Frontend Engine**: HTML5, Jinja Templating

## Domain Taxonomy Covered
The platform maps and resolves complex relationships across:
- **Tester Roles**: QA Team, QA Tester, Development Team, Performance Team, End User, etc.
- **Testing Levels**: Unit Testing, Integration Testing, System Testing, Acceptance Testing.
- **Testing Categories**: Functional Testing, Non-Functional Testing, Both.
- **Test Classifications**: Testing Technique, Testing Approach, Testing Type, Testing Level.
- **Parent Hierarchies**: Resolves circular references (e.g., UAT under Acceptance Testing, Localization under Internationalization).

## Database Schema (Relational Architecture)
The application utilizes an industry-standard relational database design with 5 lookup tables to ensure data integrity and eliminate redundancies:
- `TestTypes` (Core fact table: `test_id`, `test_name`, and 5 foreign keys)
- `Testers` (`tester_id`, `name`)
- `TestLevels` (`level_id`, `level_name`)
- `TestCategories` (`category_id`, `category_name`)
- `TestClassifications` (`classification_id`, `classification_name`)
- `ParentTestTypes` (`parent_id`, `parent_name`)

## Project Structure
```text
├── app.py                  # Main Flask application, routing engine, and search API
├── models.py               # SQLAlchemy relational database models and schema bindings
├── etl_import.py           # Automated Pandas script for cleansing and ingesting CSV data
├── test_data.csv           # Raw source spreadsheet containing testing taxonomy catalog
└── templates/              # Jinja HTML5 user interface views
    ├── index.html          # Main dashboard grid displaying all 89 test catalog records
    ├── query_form.html     # Dynamic multi-parameter search engine form
    ├── query_results.html  # Filtered search results data grid matching user queries
    └── add_test_type.html  # Interactive data insertion tool for new test entries
```

## Setup and Execution

### 1. Database Initialization
Execute the database schema inside SQL Server Management Studio (SSMS) to build the empty table structures:
```sql
CREATE DATABASE TestManagement;
```

### 2. Run the Automated ETL Data Import
Navigate to your project directory and run the data pipeline to automatically sanitize and load your spreadsheet data into SQL Server:
```bash
.\venv\Scripts\python etl_import.py
```

### 3. Launch the Application
Start the local Flask development server:
```bash
python app.py
```
Open `http://127.0.0.1:5000` in your web browser to navigate the platform.
