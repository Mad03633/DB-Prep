<h1 align="center">
    <br>
    DataBase: A Simple Guide
    </br>
</h1>

<p align="center">
    <a href="#main-concepts">Main Concepts</a> •
    <a href="#data-integrity">Data Integrity</a> •
    <a href="#dbms-architecture">Database Architecture</a> •
    <a href="#operations-in-relational-algebra">Operations in Relational Algebra</a> •
    <a href="#basics-of-ER-modelling">Basics of ER-modelling</a> •
    <a href="#keys">Keys</a> •
    <a href="#table-relationships">Table Relationships</a> •
    <a href="#aggregate-functions">Aggregate Functions</a> •
    <a href="#filtering-and-searching-data">Filtering and Searching data</a> •
    <a href="#sorting-and-grouping-results">Sorting and Grouping results</a> •
    <a href="#data-sampling">Data Sampling</a> •
    <a href="#interactive-mode-with-db">Interactive mode with DB</a> •
    <a href="#database-management">Database Management</a> •
    <a href="#subqueries">Subqueries</a> •
    <a href="#modelling-types">Modelling types</a> •
    <a href="#modelling-methods">Modelling methods</a> •
    <a href="#architecture-of-db-(sql-server)/physical/logical">Architecture of DB(SQL-server)/physical/logical</a> 
</p>

<p align="center">
    <br>
    Additions
    </br>
    <a href="#dql">Data Query Language</a> •
    <a href="#where-clause">WHERE Clause</a> •
    <a href="#aggregate-functions-in-sql">Aggregate functions in SQL</a> •
    <a href="#order-by-clause">ORDER BY Clause</a> •
    <a href="#group-by-clause">GROUP BY Clause</a> •
    <a href="#having-clause">HAVING Clause</a> •
    <a href="#any/all-clause">ANY/ALL Clause</a> •
    <a href="#as-clause">AS Clause</a> •
    <a href="#case-expression">CASE Expression</a> •
    <a href="#join">JOIN</a> •
    <a href="#union">UNION</a> •
    <a href="#dml">Data Manipulaion Language</a> •
    <a href="#ddl">Data Definition Language</a> •
    <a href="#data-types">Data types</a> •
    <a href="#constraints">Constraints</a> 
</p>

## Main Concepts

### Relational Data Model

The **relational model** represents how data is stored and managed in **Relational Databases**. Data is organized into **tables**, each known as a relation, consisting of **rows (tuples)** and **columns (attributes)**. Each row represents an **entity** or record, and each column represents a particular attribute of that entity. A relational database consists of a collection of tables each of which is assigned a **unique name**.

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/relational_model.jpg)

Main elements:
    - **Key terms**:
        - **Relation Schema**: A relation schema defines the structure of the relation and represents the name of the relation with its attributes.
        - **Attribute**: Attributes are the properties that define an entity. (column)
        - **Tuple**: A Tuple represents a **row** in a relation. Each tuple contains a set of attribute values that describe a particular entity.
        - **Degree**: The number of attributes in the relation is known as the degree of the relation.
        - **Cardinality**: The number of tuples in a relation is known as cardinality.
        - **Domain**: A domain is a set of valid values for one or more attributes. For example, the domain for the **age attribute** might be limited to **integers** between 0 and 120.
    - Types of keys:
        - Primary Key: A Primary Key uniquely identifies **each tuple** in a relation. It must contain unique values and **cannot have NULL values**. **Example**: ROLL_NO in the STUDENT table is the primary key.
        - **Foreign Key**: A Foreign Key is an attribute in **one relation that refers to the primary key of another relation**. It establishes relationships between tables. **Example**: BRANCH_CODE in the STUDENT table is a foreign key that refers to the primary key BRANCH_CODE in the BRANCH table.
        - **Candidate Key**: A Candidate Key is a set of attributes that can uniquely identify a tuple in a relation. There can be multiple candidate keys, and one of them is chosen as the primary key.
        - **Super Key**: A Super Key is a set of attributes that can uniquely identify a tuple. It may contain extra attributes that are not necessary for uniqueness.
        - **Composite Key**: A Composite Key is formed by combining two or more attributes to uniquely identify a tuple. Example: A combination of FIRST_NAME and LAST_NAME could be a composite key if no one in the database shares the same full name.

### Relational Algebra

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/relational_algebra.jpg)

- **Main operations**:
    - **Unary**:
        - **Selection(σ)**: The Selection Operation is basically used to **filter out rows** from a given table based on certain given **condition**. 
        ```
        SELECT * FROM table WHERE logic
        ```
        - **Rename(ρ)**: Rename operator basically allows you to give a **temporary name** to a specific relational table or to its columns.
        ```
        ALTER TABLE table RENAME COLUMN old_name TO new_name
        ```
        - **Projection(π)**: While Selection operation works on rows, similarly projection operation of relational algebra **works on columns**.
        ```
        SELECT col_1, col_2 FROM table
        ```
    - **Set operations**:
        - **Union(U)**: The Union Operator is basically used to **combine** the results of two queries into a single result, excluding duplicates.
        ```
        SELECT * FROM table_1 UNION SELECT * FROM table_2
        ```
        - **Intersection(∩)**: Set Intersection basically allows to **fetches only those rows** of data that are **common** between **two sets** of relational tables.
        - **Difference(-)**: Set difference basically provides the rows that are present in **one table**, but **not in** another tables.
        - **Cartesian Product(X)**: The Cartesian product **combines every row** of **one table** with **every row of another table**, producing all the possible combination.
    - **Binary**:
        - **Join**: Join operations in relational algebra **combine** data from two or more relations based on a related attribute, allowing for more complex queries and data retrieval.
        **Example**: Inner JOIN, Left JOIN, Outer JOIN.
        - **Division (÷)**: The Division Operator is used to **find tuples** in one relation that are **related to all tuples** in another relation.

### Relational Calculus

**Relational calculus** is a **declarative** approach to querying relational databases, which describes what should be retrieved rather than how it should be performed. Unlike relational algebra, which uses operations to manipulate and retrieve data, relational calculus focuses on describing the **conditions** that query results must satisfy.
- **Two types**:
    - **Tuple Relational Calculus – TRC**
    - **Domain Relational Calculus – DRC**

- **Example**:
    - **Relational Algebra**:
    ```
    π_name (σ_age>18 (Students))
    ```
    - **Relational Calculus**:
    ```
    { s.name | Students(s) AND s.age > 18 }

    { <name> | ∃ age (Students(name, age) AND age > 18) }
    ```

## Data Integrity

**Data integrity** is a process and set of **rules** designed to ensure the correctness, accuracy, and reliability of data in a database.

- **Integrity Constraints**: 
    - **PRIMARY KEY**: Ensures uniqueness and does not allow NULL values.
    - **FOREIGN KEY**: Ensures referential integrity between tables.
    - **UNIQUE**: Ensures unique values in a column or group of columns.
    - **NOT NULL**: Ensures that a column does not contain NULL values.
    - **CHECK**: Ensures that a value in a column meets a certain condition.
- **Triggers**: 
    - A **trigger** is a procedural statement in a database that is automatically executed in response to certain events such as INSERT, UPDATE, or DELETE.
    ```
    CREATE TRIGGER SalaryCheck
    BEFORE INSERT ON Employees
    FOR EACH ROW
    BEGIN
        IF NEW.salary < 0 THEN
        SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Salary must be positive number'
        END IF
    END
    ```
- **RULES**:
    - **Rules** define business logic and constraints that must be met when working with data.
    - It can include user-defined functions and procedures for validating and processing data.

### Integrity Types

- **Physical integrity**:
    - Protecting data from external factors such as natural disasters, power outages, or hackers falls under the scope of physical integrity.
- **Logical integrity**:
    - **Domain**: Domain constraints are a type of integrity constraint that **ensure the values stored** in a column (or attribute) of a database are valid and within a specific range or domain.
    ```
    CREATE TABLE Employees (
        id INT PRIMARY KEY,
        name VARCHAR(100) NOT NULL
        age INT CHECK (age >= 0 AND age <= 120), // range
        email VARCHAR(255) UNIQUE
    )
    ```
    - **Referential**: Referential integrity constraints are rules that ensure relationships between tables remain consistent. They enforce that a **foreign key** in one table must either match a value in the **referenced primary key** of another table or be NULL
    - **Semantic**: Semantic integrity ensures that data complies with the business logic and rules established for a specific application or business process. CHECK and TRIGGERS.

## 