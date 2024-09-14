
# Hospital Database Management System

## Project Overview

This project is an implementation of a MySQL-based database. The database is designed to handle data for a hospital job management system, tracking job vacancies, candidates, interviews, and job offers across various hospitals. The system allows hospitals to advertise job positions requiring specific skills and to manage candidate interviews and job offers.

## Features

The database contains seven tables to handle the relationships between hospitals, candidates, job positions, skills, and interviews. The relationships are designed to allow hospitals to advertise positions requiring specific skills and to manage the hiring process.

### Key Entities
1. **Hospitals**: Stores hospital identifiers, names, addresses, and contact numbers.
2. **Candidates**: Contains candidate identifiers, names, addresses, contact numbers, and associated skills.
3. **Positions**: Defines job positions, the hospital advertising the position, and the skills required.
4. **Skills**: A table to manage various skills, linking to both candidates and job positions.
5. **Interviews**: Tracks interviews conducted for candidates, positions, and hospitals, including the interview date and whether the candidate was offered the job.

### Additional Entities
- **Position Skills**: Links positions with required skills.
- **Candidate Skills**: Links candidates with their skills.

### Stored Procedures
- Stored procedures were created for each table to allow easy insertion of new data.
- Additionally, parametric queries were implemented to retrieve specific information from the database, such as:
  - Finding hospitals by name or identifier.
  - Finding candidates by surname or skills.
  - Retrieving positions requiring certain skills.
  - Listing interviews conducted on specific dates.

## Database Design

The database structure was designed with integrity and flexibility in mind:
- **Primary Keys**: Each table contains unique identifiers to ensure data integrity.
- **Foreign Keys**: Relationships between tables are enforced with foreign keys, ensuring referential integrity.
- **Composite Keys**: In some tables, composite keys are used to model many-to-many relationships, such as candidates having multiple skills or positions requiring multiple skills.

### Modifications and Assumptions
- **Interview Table**: A `jobOffered` field (using `TINYINT`) was added to the interview table to track whether a candidate was offered the position. A trigger was implemented to ensure only valid values (1 or 0) are entered, mimicking a Boolean field.
- **Foreign Key Cascading**: Cascade policies are used to ensure consistent data when parent records are deleted or updated, especially for candidate and interview data.
- **Redundant Data**: Initially, a `hospitalID` column was included in the interview table, but it was removed to avoid redundancy, as this information is already linked via the position details.

### Data Population
- Each table is populated with at least 10 rows of sample data to demonstrate the system's functionality.

## ER Diagram

An **Entity-Relationship (ER)** diagram was created to visualize the structure of the database, showing how the various entities are connected through relationships. This diagram is available in the documentation for a clear representation of how data flows between tables.

## Technologies Used

- **MySQL**: The database management system used to store and manage the hospital data.
- **Triggers**: Implemented to ensure data integrity, particularly for managing the `jobOffered` field.
- **Windows OS**: The project was developed and tested on a Windows operating system.

## How to Run

1. Clone this repository to your local machine.
2. Import the provided `.sql` file into your MySQL database system.
3. Execute the stored procedures to insert, update, and retrieve data.
4. The database is pre-populated with sample data for demonstration purposes.

## Documentation

For detailed explanations of the database schema, assumptions, stored procedures, and entity relationships, please refer to the accompanying **PDF documentation**. The ER diagram is included in the documentation for reference.
