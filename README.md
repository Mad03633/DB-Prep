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

## Database Architecture

### DBMS Architecture

The architecture of a database management system (DBMS) is a multi-level structure that provides efficient data management, storage, processing and access. The architecture of a DBMS may vary depending on the specific system and its features, but the basic components and levels remain similar.
    - **User layer (External)**: 
        - **Users**: Includes end users, applications, and interfaces that interact with the database.
        - **User Views**: The views of the data that the user sees and works with. These can include various interfaces such as graphical user interfaces (GUIs), web interfaces, and applications.
    - **Conceptual layer**:
        - **Conceptual schema**: A single, global data model that describes the structure of the entire database and the relationships between the data. It defines the logical structure of the data, including tables, columns, relationships, constraints, and integrity rules.
        - **System Catalog**: Metadata about the structure of the database, including information about tables, indexes, constraints, users, and access rights.
    - **Internal Layer**:
        - **Internal schema**: Describes the physical structure of data storage, including files, indexes, access paths, and data storage methods.
        - **Physical Storage**: The mechanisms by which data is stored on physical media such as hard drives or SSDs.

### *file server" / Desktop DBMS

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/1_tier_level.jpg)

It is a model in which the database is stored on a **file server**, and clients access the database by interacting with files through **network protocols**. In this architecture, the database itself is located on the server, and client applications use network file systems to access the data.

- A local copy of the data is created for each user while they are running.
- **Advantages**: 
    - **Centralized data management**:
    All database files are stored in one place, making it easier to manage.
    - **Simplified administration**:
    Management of file permissions and security is centralized on the file server.
    - **Ease of setup**
- **Disadvantages**:
    - **Limited performance**:
    Performance may suffer due to network latency and bandwidth, especially with large amounts of data or many concurrent requests.
    - **Data consistency issues**:
    Possible issues with data consistency and transaction management.
    - **Single point of failure**:
    The file server becomes a single point of failure; if the server fails, all access to the database may be lost.

### 2-Tier-Level Architecture "client-server"

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/2_tier_level.jpg)

It is a model in which the main data processing and application logic is performed on the **client side**, and the **server** is responsible for **storing and managing data**. A thick client differs from a thin client in that it has more computing resources and functionality on the client side, allowing much of the work to be done locally.

- **Advantages**:
    - **Performance**: Most of the processing is performed on the client, the load on the server is reduced, which can improve overall system performance.
    - **Functionality**: A thick client can provide a richer, more interactive user interface that can operate offline during temporary network outages.
    - **Reduced network load**
- **Disadvantages**:
    - **Administration and updating**: Updating client applications can be complex, especially if there are many client devices to update
    - **Security**: Data processed and stored on the client device may be more vulnerable to attack.
    - **Compatibility**: Hardware and software requirements on client devices may vary.

### 3-Tier-level Architecture

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/3_tier_level.jpg)

It is a**client-server architecture** model in which the application logic is divided into **three** interconnected tiers: the **Presentation** Tier, the **Application Logic** Tier, and the **Data** Tier. This structure provides flexibility, scalability, and simplifies application management.

- **Main components**:
    - **Presentation Tier**: Web pages, mobile applications, desktop programs.
    - **Application Logic Tier**: Application server, request handlers, controllers, business logic services.
    - **Data Tier**: 
        - Technologies: DBMS (e.g. MySQL, PostgreSQL, Oracle, SQL Server), NoSQL databases (e.g. MongoDB, Cassandra), file systems, cloud storage. 
        - Examples: Databases, data management systems, data warehouses.
- **Advantages**: 
    - **Scalabilty**: Adding new servers or resources as needed.
    - **Flexibility and reuse**
    - **Increased reliability**

## Operations in Relational Algebra

- **UNION**: The union of two type-compatible relations 
F, consisting of attributes (A1, A2,..., An}
S, consisting of attributes (A1, A2,..., An} is a relation **R = (F U S)**
    - with the same schema as relations F and S
    - and a body consisting of tuples belonging to either F or S, or both at once.
    
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/UNION.png)
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/UNION_ex.jpg)

- **INTERSECTION**: The intersection of two type-compatible relations
F, consisting of attributes (A1, A2,..., An} and
S, consisting of attributes {A1, A2,..., An} is a relation **R = (F ∩ S)**
    - with the same schema as relations F and S
    - and a body consisting of tuples belonging to both relations simultaneously.

    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/INTERSECTION.png)
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/INTERSECTION_ex.jpg)

- **DIFFERENCE**: The difference of two type-compatible relations
F, consisting of attributes (A1, A2...., An} and
S, consisting of attributes (A1, A2,.., An} is a relation **R = (F - S)**
    - with the same schema as relations F and S
    - and a body consisting of tuples belonging to relation F and not belonging to relation S. 

    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/DIFFERENCE.png)
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/DIFFERENCE_ex.jpg)

- **Cartesian product and relations**: The Cartesian product of relations F, consisting of attributes {F1, F2,..., Fn} and S, consisting of attributes (S1, S2,..., Sm} is a relation **R = (F X S)**,
    - whose schema is the result of concatenating the schemas of the original relations: {F1, F2,.., Fn, S1, S2,., Sm},
    - and the body consists of a set of tuples {f1, f2,..., fn, s1, s2,..., sm}

    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/CARTESIAN.jpg)

- **Selection**: Main Concepts -> Relational Algebra -> Main operations -> Unary
- **Projection**: Main Concepts -> Relational Algebra -> Main operations -> Unary
- **JOIN**: A general name for binary operators on relations that allow data from two relations to be combined into one in some way. 
    - **Cross/Cartesian Join**: Two relations R1 and R2 that have no common attributes is a relation in which the header is the union of the headers of R1 and R2, and the body is the product of the bodies of R1 and R2. Notation: R1xR2. If two relations have at least one common attribute in the header, their cross join is not defined.

    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/CROSS_CARTESIAN_JOIN.jpg)

    - **Natural Join**: Two relations R1 and R2 is a relation in which the header is the union of the headers of R1 and R2, and the body consists of tuples obtained by all possible joins of tuples R1 and R2 that have equal values of the same attributes.

    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/NATURAL_JOIN.jpg)

    - **Semijoin**: 
        - **Left Semijoin**: Two relations R1 and R2 is a relation in which the header is equal to the header of R1, and the body consists of tuples in R1 for which there is a tuple from R2 with equal values of the same attributes.
        - **Right Semijoin**: Two relations R1 and R2 is a relation in which the header is equal to the header of R2, and the body consists of tuples in R2 for which there is a tuple from R1 with equal values of the same attributes. 

        ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/LEFT_RIGHT_Semijoin.jpg)

## Basics of ER-modelling

