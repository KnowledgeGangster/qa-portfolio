# Flask Backend Architecture & Relational Database Layer

## Architecture Overview
The backend of this educational platform is built using a decoupled, model-driven architecture leveraging **Flask** and **Flask-SQLAlchemy**. It connects natively to a **Microsoft SQL Server** instance using **PyODBC** database drivers.

By separating database models from application routing logic, the system completely prevents circular dependencies and optimizes performance via dynamic SQL generation.

```text
       +------------------+

       |   test_data.csv  | <--- Ingested and cleansed via Pandas
       +------------------+

                |
                v
       +------------------+
       |  etl_import.py   | <--- Resolves hierarchies & populates SQL lookups
       +------------------+

                |
                v
  +----------------------------+
  | MS SQL Database Engine     |
  | (Enforces FK Constraints)  |
  +----------------------------+
            ^      |
   Queries  |      | Hydrates Models

            |      v
       +------------------+
       |    models.py     | <--- SQLAlchemy ORM Core Definitions
       +------------------+
            ^      |
   Imports  |      | Binds Engine

            |      v
       +------------------+
       |     app.py       | <--- Flask Server & Advanced Multi-Join Router
       +------------------+

                |
                v
       +------------------+
       | Jinja UI Form    | <--- Zero-hardcoding dynamic dropdowns
       +------------------+
```

## Technical Highlights
- **Decoupled Database Binding**: Utilizes deferred session initialization (`db.init_app(app)`) to isolate database schema structures from operational web routes.
- **Dynamic Multi-Parameter Query Engine**: Features a programmatic querying algorithm that adjusts filtering dynamically based on web parameters. It safely interprets empty user criteria as global wildcards rather than empty constraints.
- **Automated Domain Taxonomy Normalization**: Employs an on-the-fly ETL sanitization layer that automatically catches Pandas `nan` artifacts and translates them into semantic database `NULL` references.
- **Relational Integrity Mapping**: Connects 5 distinct database entities using cascading relationships (`db.relationship` with explicit lazy-loaded backreferences) to eliminate database redundancy.

## Model Layer Specifications (`models.py`)
The data model maps directly to an industry-standard star-schema relational design, separating lookup categories from the core facts:

1. **`Tester`**: Tracks roles or teams executing tests (e.g., QA Team, Development Team).
2. **`TestLevel`**: Tracks software testing scope phases (e.g., Unit, Integration, System, Acceptance).
3. **`TestCategory`**: Identifies functional vs. non-functional testing dimensions.
4. **`TestClassification`**: Maps testing tactics (e.g., Testing Technique, Testing Approach, Testing Type).
5. **`ParentTestType`**: Establishes system-wide hierarchical grouping relationships.
6. **`TestType`**: The core data table mapping specific test names to all 5 foreign key lookup identifiers.

## Routing Engine & Endpoints (`app.py`)

### `GET /`
- **Purpose**: Main platform landing dashboard.
- **Backend Action**: Executes `TestType.query.all()` to pull the entire catalog grid. Hydrates structural lookup text references automatically using pre-bound database relationships.

### `GET /add_test`
- **Purpose**: Populates lookup choices for the manual creation layout.
- **Backend Action**: Extracts metadata collections from all 5 lookup tables simultaneously to render zero-hardcoded HTML dropdown variables.

### `POST /add_test`
- **Purpose**: Registers a new test entry into the platform.
- **Backend Action**: Sanitizes text form parameters. Gracefully intercepts empty selection variables and transforms them into strict database `NULL` attributes before committing transactions.

### `GET /query`
- **Purpose**: Populates the search engine option selectors.
- **Backend Action**: Queries and hands off active database records to feed search dropdown components.

### `GET /results`
- **Purpose**: Core platform search algorithm.
- **Backend Action**: Processes 5 optional web parameters. Builds filtering clauses dynamically on top of a single database session string. Automatically switches database lookup values into safe integer typings to execute lightning-fast index scanning inside SQL Server.

## Engineering Dependencies
Ensure the application is executed inside an isolated python environment containing the following packages:
```text
Flask>=3.0.0
Flask-SQLAlchemy>=3.1.0
pyodbc>=5.0.0
pandas>=2.0.0
openpyxl>=3.1.0
```
