# Custom ELT Project

This repository contains a custom Extract, Load, Transform (ELT) project that utilises Docker and PostgreSQL to demonstrate a simple ELT process.

---

## 🗂 Repository Structure

### 1. `docker-compose.yaml`
This file contains the configuration for Docker Compose, which is used to orchestrate multiple Docker containers. It defines three services:

- **`source_postgres`**: The source PostgreSQL database.
- **`destination_postgres`**: The destination PostgreSQL database.
- **`elt_script`**: The service that runs the ELT script.

### 2. `elt_script/Dockerfile`
This Dockerfile sets up a Python environment and installs the PostgreSQL client. It also copies the ELT script into the container and sets it as the default command.

### 3. `elt_script/elt_script.py`
This Python script performs the ELT process:
- Waits for the source PostgreSQL database to become available.
- Dumps its data to a SQL file.
- Loads this data into the destination PostgreSQL database.

### 4. `source_db_init/init.sql`
This SQL script initialises the source database with sample data. It:
- Creates tables for users, films, film categories, actors, and film actors.
- Inserts sample data into these tables.

---

## 🐳 How to Run

1. Ensure you have Docker and Docker Compose installed.
2. Clone this repository.
3. Navigate to the repository directory and run docker-compose up.
4. Once all containers are up and running, the ELT process will start automatically.
5. After the ELT process completes, you can access the source and destination PostgreSQL databases on ports 5433 and 5434, respectively.