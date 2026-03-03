# 📦 Parcel Locker Management System  

[![Python](https://img.shields.io/badge/Python-3.13-blue.svg)](https://www.python.org/)  
[![Streamlit](https://img.shields.io/badge/Streamlit-UI-red.svg)](https://streamlit.io/)  
[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://www.docker.com/)  
[![Test Coverage](https://img.shields.io/badge/Coverage-100%25-brightgreen.svg)](https://damiankowalczykdk.github.io/parcel-report-dashboard/) 
 

---

## 📖 Overview

Parcel Locker Management System is a backend-focused Python application designed to manage:

- 📦 Parcels
- 🏢 Parcel Lockers
- 👤 Users
- 🚚 Deliveries

Instead of manual operations, the system acts as an **ETL-style pipeline**:

- **Extract** – reads parcel and locker data from JSON stores  
- **Transform** – validates business logic (locker capacity, delivery limits)
- **Load** – updates reports, triggers notifications, and persists data


A lightweight **Streamlit UI** allows interactive data exploration and reporting.  

This project demonstrates:

- Clean architecture and service separation  
- ETL-style data processing in memory  
- Integration with UI for interactive reporting  
- Strict typing and full test coverage

---

## 🏗️ Architecture & Design Principles
The project follows a layered architecture:

- **Domain Layer** – Data models and core business logic  
- **Repository Layer** – Data access abstraction  
- **Service Layer** – Business use cases and orchestration  
- **Validation Layer** – Input validation and data integrity enforcement  
- **UI Layer** – Streamlit-based presentation layer 

### Engineering Highlights

- Clear separation of concerns  
- Strong typing (MyPy + Pyright)  
- Dependency injection via constructor injection  
- High unit test coverage  
- Dockerized environment for reproducibility  

---

## ✨ Core Features

### 📦 Parcel Management
- Create and validate parcels
- Assign parcels to lockers
- Validate locker capacity constraints

### 📊 Reporting Services
- Most common parcel sizes per locker
- Cities with the highest shipment volume (by size)
- Longest delivery durations (sent → expected date)
- Locker compartment limit validation

### ✅ Validation Layer
- Email validation
- Positive numeric validation
- Required field enforcement
- Structured data transformation via converters

---

## 🧪 Testing & Code Quality

The project emphasizes reliability and maintainability:

- **pytest** for unit testing  
- Dedicated test structure per module  
- Modular pytest structure with dedicated conftest.py files  
- MyPy & Pyright static type checking  
- Coverage reporting enabled  
---
## 🚀 Getting Started (Local Development)

* **Build and run all services:**
```bash
docker-compose up -d --build
```

### 1. Install Pipenv (if not already installed)
```bash
pip install pipenv
```
### 2. Install dependencies
```bash
pipenv install
```
### 3. Activate the virtual environment
```bash
pipenv shell
```
### 4. Quality Checks (Linting & Testing)
Ensure code integrity before running:
```bash
# Run strict type checking
pipenv run mypy src/
```
```bash
# Run tests with coverage
pipenv run pytest --cov=src --cov-report=term-missing
```
---
## 🖥️ Running the Streamlit App (Web UI)
After activating the environment, run the **Streamlit** app:

```bash
streamlit run main_ui.py
```
The app will open in your browser (usually at: http://localhost:8501).
Use the interface to view reports, parcel statistics, and visual summaries generated from the data.
---
## 📄 Example Usage (Without UI)

All business logic is fully set up in `main.py`.  
To use a specific report or check a service method, you just need to call it — the repositories and service layer are already initialized.

* Example:

```python
# Print the result of the method you want
print(service.city_most_shipments_by_size())
print(service.most_common_parcel_sizes_per_locker())
service.is_parcel_limit_in_locker_exceeded()
service.max_days_between_sent_and_expected()
```

* Run application
```bash
pipenv run python main.py
```
* Example output:

```text
Output of city_most_shipments_by_size()
{'sent': {'small': 'Chicago'}, 'received': {'small': 'New York'}}

Output of most_common_parcel_sizes_per_locker()
{'L001': ['small', 'medium'], 'L002': ['small']}
```

📁 Project Structure
```text
src/
├── converter.py 
├── file_service.py
├── model.py
├── report_service.py
├── repository.py
├── service.py
├── ui_service.py
├── validator.py
tests/
├── test_file_service/
│   ├── conftest.py
│   └── test_file_service.py
├── test_repository/
│   └── data_repository/
│       ├── conftest.py
│       └── test_repository.py
│   ├── parcel_summary_repository/
│       ├── conftest.py
│       └── test_parcel_summary_repository.py
├── test_service/
│   ├── conftest.py
│   └── test_service.py
├── test_ui_service/
│   ├── test_find_parcel.py
│   ├── test_send_parcel.py
│   └── test_show_ui.py
├── conftest.py
├── test_converter.py
├── test_model.py
├── test_report_service.py
├── test_validator.py

Pipfile / Pipfile.lock # Project dependencies
```
---
## 🤝 Contact

* Designed and implemented by [Damian Kowalczyk](https://github.com/DamianKowalczykDK).
Feel free to connect or explore other backend projects.