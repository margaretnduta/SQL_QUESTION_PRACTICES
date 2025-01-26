# SQL_QUESTION_PRACTICES
A collection of SQL practice questions designed to enhance database querying skills. This repository includes problems covering basic to advanced SQL concepts such as SELECT queries, joins, subqueries, aggregate functions, and more. Ideal for beginners and intermediates looking to improve their understanding of SQL.
# SQL Practice Readme

## Overview
This document outlines SQL practice exercises for creating, managing, and querying relational databases. It covers scenarios involving table creation, data insertion, updates, and generating various reports. These exercises are designed to solidify SQL knowledge and demonstrate proficiency in database management and querying.

## Table of Contents
1. [NHIF Table Practices]
2. [Products Table Practices]
3. [Football Table Practices]


## NHIF Table Practices

### i) Create the `NHIF` Table
```sql
CREATE TABLE NHIF (
    National_ID INT PRIMARY KEY,
    Names VARCHAR(50),
    Date_of_Birth DATE,
    NHIF_No VARCHAR(10),
    Sex VARCHAR(6),
    Basic_Salary DECIMAL(10, 2),
    Deduction DECIMAL(10, 2)
);
```

### ii) Populate `Deduction` Column
```sql
UPDATE NHIF
SET Deduction = Basic_Salary * 0.01;
```

### iii) Insert Data into the `NHIF` Table
```sql
INSERT INTO NHIF (National_ID, Names, Date_of_Birth, NHIF_No, Sex, Basic_Salary)
VALUES
    (4000678, 'Hellen Ochillo', '1987-02-11', 'A567985', 'Female', 100000.50),
    (1099768, 'Edward Kamau', '1962-01-25', 'D876445', 'Male', 75890.00),
    (5544782, 'Richard Mutua', '1977-01-16', 'C986745', 'Male', 56000.55),
    (9566453, 'Allen Kadenge', '1969-12-13', 'A451256', 'Male', 97665.00),
    (11876552, 'Joyce Onyango', '1991-11-27', 'B67528', 'Female', 350000.00),
    (8764670, 'Irene Kwamboka', '1977-10-03', 'C78722', 'Female', 150000.50),
    (15798432, 'Gerald Gatcheka', '1969-04-15', 'D321675', 'Male', 10000.00);
```

### iv) Report: Sort by Date of Birth (Descending)
```sql
SELECT * FROM NHIF
ORDER BY Date_of_Birth DESC;
```

### v) Reports: Maximum Deduction and Average Deduction
- Maximum Deduction:
```sql
SELECT * FROM NHIF
ORDER BY Deduction DESC
LIMIT 1;
```
- Average Deduction:
```sql
SELECT * FROM NHIF
WHERE Deduction = (SELECT AVG(Deduction) FROM NHIF);
```

### vi) Create a Copy of the Table
```sql
CREATE TABLE Employees AS SELECT * FROM NHIF;
```

---

## Products Table Practices

### i) Create the `Products` Table
```sql
CREATE TABLE Products (
    Product_id INT PRIMARY KEY,
    Product_Name VARCHAR(50),
    Product_Date DATE,
    Unit_Price DECIMAL(10, 2)
);
```

### ii) Insert Data into the `Products` Table
```sql
INSERT INTO Products (Product_id, Product_Name, Product_Date, Unit_Price)
VALUES
    (101022, 'Iron Sheets', '2016-12-01', 2000),
    (123465, 'Iron Doors', '2017-05-02', 12000),
    (357854, 'Aluminum Sheets', '2018-09-03', 1500),
    (567453, 'Aluminum Locks', '2017-03-04', 3500);
```

### iii) Add a New Column `Product_Store`
```sql
ALTER TABLE Products ADD Product_Store VARCHAR(50);

UPDATE Products
SET Product_Store = CASE
    WHEN Product_id = 101022 THEN 'Westlands'
    WHEN Product_id = 123465 THEN 'City Centre'
    WHEN Product_id = 357854 THEN 'Upper Hill'
    WHEN Product_id = 567453 THEN 'Ngong'
END;
```

### iv) Enforce Unique `Product_id`
```sql
ALTER TABLE Products ADD CONSTRAINT unique_product_id UNIQUE (Product_id);
```

### v) Report: Sorted by `Product_Name`
```sql
SELECT * FROM Products
ORDER BY Product_Name;
```

### vi) Create and Relate `Orders` Table
- Create `Orders` table with a foreign key relationship:
```sql
CREATE TABLE Orders (
    Order_id INT PRIMARY KEY,
    Order_date DATE,
    Product_id INT,
    FOREIGN KEY (Product_id) REFERENCES Products(Product_id)
);
```
- Insert Sample Data:
```sql
INSERT INTO Orders (Order_id, Order_date, Product_id) VALUES
    (1, '2025-01-01', 101022),
    (2, '2025-01-15', 123465),
    (3, '2025-01-20', 357854);
```

---

## Football Table Practices

### i) Create the `Football` Table
```sql
CREATE TABLE Football (
    Team VARCHAR(50),
    Wins INT,
    Draws INT,
    Losses INT
);
```

### ii) Insert Data into the `Football` Table
```sql
INSERT INTO Football (Team, Wins, Draws, Losses) VALUES
    ('A', 5, 3, 2),
    ('B', 3, 2, 5),
    ('C', 6, 2, 2),
    ('D', 2, 4, 4),
    ('E', 7, 1, 2),
    ('F', 4, 5, 1);
```

### iii) Queries for Specific Criteria
- Team with Most Wins:
```sql
SELECT Team, Wins
FROM Football
ORDER BY Wins DESC
LIMIT 1;
```
- Team with Fewest Losses:
```sql
SELECT Team, Losses
FROM Football
ORDER BY Losses ASC
LIMIT 1;
```

### iv) Add and Populate `Points` Column
- Add `Points` column:
```sql
ALTER TABLE Football ADD Points INT;
```
- Populate `Points` column:
```sql
UPDATE Football
SET Points = (Wins * 3) + (Draws * 1) + (Losses * 0);
```

### v) Report Sorted by Wins
```sql
SELECT Team, Wins, Draws, Losses, Points
FROM Football
ORDER BY Wins DESC;
```

---

## Key Highlights
- The exercises cover essential SQL operations such as creating tables, managing constraints, updating data, and establishing relationships between tables.
- Includes real-world use cases for querying data effectively, such as generating sorted and filtered reports.
- Demonstrates relational database design through the use of foreign keys.
## How to Use

1. **Clone the Repository**: Clone this repository to your local machine.
   ```sh
   https://github.com/margaretnduta/SQL_QUESTION_PRACTICES.git
   ```

2. **Set Up the Database**: Execute the SQL scripts in the `database_setup.sql` file to create and populate the database.
3. **Run the Queries**: Use the SQL queries in the `analysis_queries.sql` file to perform the analysis.
4. **Explore and Modify**: Customize the queries as needed to explore different aspects of the data or answer additional questions.

## Author - Margaret Wambui

This project showcases SQL skills essential for database management and analysis. For more content on SQL and data analysis, connect with me through the following channels:



- **LinkedIn**: [Connect with me professionally](https://www.linkedin.com/in/margaretwambui12)

Thank you for your interest in this project!

