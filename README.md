# JOINS-AND-UNION

## Description
This repository contains SQL scripts demonstrating fundamental database operations such as table joins and unions. The scripts use two sample tables: COUNTRY and PERSONS, showcasing how to perform inner joins, left joins, right joins, union operations, and data transformation techniques.

## Database Structure

1. COUNTRY Table
Contains information about countries, including:

ID: Primary key
COUNTRY_NAME: Name of the country
POPULATION: Population of the country
AREA: Geographical area of the country

2. PERSONS Table
Contains information about individuals, including:

ID: Primary key
F_NAME and L_NAME: First and last names
POPULATION: Associated population data
RATING: Individual rating
COUNTRY_ID: Foreign key linking to the COUNTRY table
COUNTRY_NAME: Name of the associated country

## SQL Tasks

1. Joins

INNER JOIN: Retrieves matching records from both tables based on the COUNTRY_ID.
LEFT JOIN: Retrieves all records from the PERSONS table and matching records from COUNTRY.
RIGHT JOIN: Retrieves all records from the COUNTRY table and matching records from PERSONS.

2. Distinct Country Names

Uses UNION to list unique country names from both tables.

3. All Country Names with Duplicates

Uses UNION ALL to list all country names, including duplicates.

4. Rounded Ratings

Rounds the RATING column in the PERSONS table to the nearest integer.

## How to Use

1. Set up a MySQL database.
2. Execute the CREATE TABLE and INSERT statements to create and populate the COUNTRY and PERSONS tables.
3. Run the provided SQL queries to explore the operations.

# SQL SCRIPT WITH OUTPUT SCREENSHOTS

## Creating Database and Country2 Table. Inserting values into COUNTRY2 table.

CREATE DATABASE JOINSUNIONS;
USE JOINSUNIONS;

-- Create and populate the COUNTRY2 table
CREATE TABLE COUNTRY2(
    ID INT PRIMARY KEY,
    COUNTRY_NAME VARCHAR(50),
    POPULATION INT,
    AREA FLOAT
);

INSERT INTO COUNTRY2 (ID, COUNTRY_NAME, POPULATION, AREA)
VALUES 
(1, 'USA', 331000000, 9834000),
(2, 'India', 1400000000, 3287000),
(3, 'China', 1440000000, 9597000),
(4, 'Brazil', 213000000, 8516000),
(5, 'Russia', 146000000, 17098200),
(6, 'Japan', 126000000, 377975),
(7, 'Germany', 83000000, 357386),
(8, 'UK', 67000000, 242495),
(9, 'France', 67000000, 551695),
(10, 'Australia', 25600000, 7692024);

SELECT * FROM COUNTRY2;

![image](https://github.com/user-attachments/assets/c9cf7d02-3367-4dca-a3a0-2854918fae54)


## Create and Insert Values into Table Person

-- Create and populate the PERSONS2 table
CREATE TABLE PERSONS2(
    ID INT PRIMARY KEY,
    F_NAME VARCHAR(50),
    L_NAME VARCHAR(50),
    POPULATION INT,
    RATING FLOAT,
    COUNTRY_ID INT,
    COUNTRY_NAME VARCHAR(50),
    FOREIGN KEY (COUNTRY_ID) REFERENCES COUNTRY2(ID)
);

INSERT INTO PERSONS2 (ID, F_NAME, L_NAME, POPULATION, RATING, COUNTRY_ID, COUNTRY_NAME)
VALUES
(1, 'John', 'Doe', 5000, 4.5, 1, 'USA'),
(2, 'Jane', 'Smith', 6000, 4.7, 1, 'USA'),
(3, 'Raj', 'Kumar', 7000, 4.9, 2, 'India'),
(4, 'Wei', 'Zhang', 5500, 4.6, 3, 'China'),
(5, 'Ana', 'Silva', 5000, 4.8, 4, 'Brazil'),
(6, 'Olga', 'Ivanova', 3000, 4.3, 5, 'Russia'),
(7, 'Taro', 'Yamamoto', 2000, 4.4, 6, 'Japan'),
(8, 'Hans', 'Müller', 2500, 4.2, 7, 'Germany'),
(9, 'Emma', 'Brown', 4000, 4.5, 8, 'UK'),
(10, 'Jean', 'Dupont', 3000, 4.1, 9, 'France');

SELECT * FROM PERSONS2;

![image](https://github.com/user-attachments/assets/b20c10c5-283c-473c-827d-9e0e5b59b8b8)


## Inseted two more values in Person2 table

INSERT INTO PERSONS2(ID, F_NAME, L_NAME, POPULATION, RATING, COUNTRY_ID, COUNTRY_NAME) VALUES 
(11,'Louis','Drake',2500,4.2,7,'Germany'),(12, 'Iyrol', 'zin' ,2000, 4.4, 6, 'Japan');

SELECT * FROM PERSONS2;

![image](https://github.com/user-attachments/assets/b8e485a4-6332-423e-bc21-d9ac857f5a5b)


## (1) Perform INNER JOIN, LEFT JOIN, and RIGHT JOIN on the tables

INNER JOIN

SELECT PERSONS2.ID,PERSONS2.F_NAME,PERSONS2.COUNTRY_NAME,COUNTRY2.ID AS COUNTRY_ID
FROM PERSONS2 
INNER JOIN COUNTRY2 ON PERSONS2.COUNTRY_ID = COUNTRY2.ID;

![image](https://github.com/user-attachments/assets/16f94451-4045-4ec6-95d3-b549bca6e810)


LEFT JOIN

SELECT PERSONS2.ID,PERSONS2.F_NAME,PERSONS2.COUNTRY_NAME,COUNTRY2.ID AS COUNTRY_ID
FROM PERSONS2 
LEFT JOIN COUNTRY2 ON PERSONS2.COUNTRY_ID = COUNTRY2.ID;

![image](https://github.com/user-attachments/assets/69f9897b-76d9-4906-9c60-93e5151c352f)

RIGHT JOIN

SELECT PERSONS2.ID,PERSONS2.F_NAME,PERSONS2.COUNTRY_NAME,COUNTRY2.ID AS COUNTRY_ID
FROM PERSONS2 
RIGHT JOIN COUNTRY2 ON PERSONS2.COUNTRY_ID = COUNTRY2.ID;

![image](https://github.com/user-attachments/assets/ce4b246a-fe8f-42eb-8235-90c40c6b3af3)

## (2) List all distinct country names from both the Country and Persons tables

SELECT DISTINCT COUNTRY_NAME FROM COUNTRY2
UNION 
SELECT DISTINCT COUNTRY_NAME FROM PERSONS2;

![image](https://github.com/user-attachments/assets/5739723b-4c80-466f-bce0-9c1a3e217744)

## (3) List all country names from both the Country and Persons tables, including duplicates

SELECT COUNTRY_NAME FROM COUNTRY2
UNION ALL
SELECT COUNTRY_NAME FROM PERSONS2;

![image](https://github.com/user-attachments/assets/f95ec5f8-0530-4606-af42-3abedbd0d10b)

## (4) Round the ratings of all persons to the nearest integer in the Persons table

SELECT ID,F_NAME,L_NAME,ROUND(RATING)AS ROUNDED_RATINGS FROM PERSONS2;

![image](https://github.com/user-attachments/assets/703f3157-35a8-47c6-bdbb-be373cf28cb6)


Feel free to fork, contribute, or raise issues in this repository! Happy querying! 🚀



















