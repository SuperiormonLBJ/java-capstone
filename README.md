# Terminal-Based Transaction Management System for Bank

This is a terminal-based banking application developed as part of the UOB TDP Capstone 2 project. The application manages users, accounts, and transactions using a PostgreSQL database and a Java backend. It features role-based access control, secure authentication, and a modular design.

## Features

### 1. **Database Management with PostgreSQL**

- Utilizes PostgreSQL for storing and managing user data, accounts, and transactions.
- Includes SQL scripts (`create_db_via_django.sql`) to initialize the database schema.

### 2. **User Authentication and Authorization**

- Implements secure login with role-based access control (Admin, Teller, Customer).
- Uses BCrypt for password hashing and verification.

### 3. **Transaction Management**

- Supports CREDIT, DEBIT, and TRANSFER operations.
- Ensures data consistency by updating account balances after each transaction.

### 4. **Terminal-Based User Interface**

- Provides a user-friendly terminal interface for interacting with the application.
- Enhances the terminal experience with ANSI colors and formatting.

### 5. **Data Population and Testing**

- Includes a `PopulateData.java` script to insert sample data into the database for testing and demonstration.

### 6. **Audio Integration**

- Integrates an audio player (`AudioPlayer.java`) to play background music during the application runtime.

### 7. **Maven Build System**

- Uses Maven for dependency management and build automation.
- Includes dependencies for PostgreSQL, JSON, Joda-Time, and BCrypt.

## Technical Skills

- **Programming Languages**: Java (JDK 17)
- **Database**: PostgreSQL, JDBC
- **Security**: BCrypt for password hashing
- **Tools**: Maven, Docker, Git
- **Concepts**: Object-Oriented Programming (OOP), Role-Based Access Control (RBAC), Transaction Management

## Getting Started

### Prerequisites

- **Java Development Kit (JDK)**: Version 17 or compatible.
- **Maven**: For building and running the project.
- **Docker**: For running the PostgreSQL database.
- **PostgreSQL Client (`psql`)**: Optional, for running SQL scripts.

### Running the Application

1. **Start the PostgreSQL Docker Container**:

   ```bash
   docker run -d -v capstone2_db:/var/lib/postgresql/data -e POSTGRES_USER=capstone2 -e POSTGRES_PASSWORD=password -e POSTGRES_DB=capstone2 -p 5432:5432 --name capstone2_db postgres
   ```

2. **Create the Database Tables**:

   ```bash
   psql -h localhost -U capstone2 -d capstone2 -p 5432 -f create_db_via_django.sql
   ```

3. **Populate the Database**:

   ```bash
   cd capstone
   mvn exec:java -Dexec.mainClass="capstone.PopulateData"
   ```

   > This file provides sample users and transaction data for the application user to have some dummy data to play around with.
   >
   > The users provided are as follows:
   >
   > - admin_1
   > - admin_2
   > - teller_1
   > - teller_2
   > - teller_3
   > - teller_4
   > - teller_5
   > - customer_1
   > - customer_2
   > - customer_3
   > - customer_4
   > - customer_5
   >
   > The default password for all the users is `password`.

4. **Run the Application**:
   ```bash
   mvn exec:java -Dexec.mainClass="capstone.Main"
   ```

## Code Structure

- **`capstone/src/main/java/capstone/Objects/`**: Contains classes for users, accounts, and transactions.
- **`capstone/src/main/java/capstone/Views/`**: Contains terminal-based UI views.
- **`capstone/src/main/java/capstone/Enums/`**: Contains enums for access levels, account types, and transaction types.
- **`capstone/src/main/java/capstone/Extras/`**: Contains helper classes for console colors and audio.
