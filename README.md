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
    <a href="#functional-dependency-and-keys">Functional dependency and Keys</a> •
    <a href="#table-relationships">Table Relationships</a> •
    <a href="#aggregate-functions">Aggregate Functions</a> •
    <a href="#filtering-and-searching-data">Filtering and Searching data</a> •
    <a href="#sorting-and-grouping-results">Sorting and Grouping results</a> •
    <a href="#data-selection">Data selection</a> •
    <a href="#interactive-mode-with-db">Interactive mode with DB</a> •
    <a href="#database-management">Database Management</a> •
    <a href="#subqueries">Subqueries</a> •
    <a href="#data-models">Data Models</a> •
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
    <a href="#as-keyword">AS Keyword</a> •
    <a href="#case-expression">CASE Expression</a> •
    <a href="#join">JOIN</a> •
    <a href="#union">UNION</a> •
    <a href="#dml">Data Manipulaion Language</a> •
    <a href="#ddl">Data Definition Language</a> •
    <a href="#data-types">Data types</a> •
    <a href="#constraints">Constraints</a> •
    <a href="#additions">Additions</a>
</p>

## Main Concepts

### Relational Data Model

The **relational model** represents how data is stored and managed in **Relational Databases**. Data is organized into **tables**, each known as a relation, consisting of **rows (tuples)** and **columns (attributes)**. Each row represents an **entity** or record, and each column represents a particular attribute of that entity. A relational database consists of a collection of tables each of which is assigned a **unique name**.

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/relational_model.jpg)

- **Main elements**:
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

### Elements of ER-diagram

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/ER_model.jpg)
![](https://github.com/Mad03633/DB-Prep/blob/main/Media/ER_model_symbols.jpg)

- **Entities**: 
    - **Entities** represent real-world objects or concepts that have meaning to the system.
    - **Example**: "Student", "Course", "Teacher", "Book".
    - **Notation**: Rectangles.
        - **Strong entity**: A Strong Entity does not depend on any other Entity in the Schema for its identification.
        - **Weak Entity**: It depends on a strong entity to be identified.
        - **Example**: An order must always be made by a customer 
            - Customer - **Strong entity**
            - Order - **Weak entity**
- **Attributes**: 
    - **Attributes** describe properties or characteristics of **entities**.
    - **Example**: Attributes of the entity "Student" might include "Name", "Age", "Student ID Number".
    - **Notation**: **Ellipses** connected by lines to entities.
        - **Simple**: Cannot be broken down into smaller parts (e.g. "Age").
        - **Composite**: Can be broken down into smaller parts (e.g. "Address" might include "Street", "City", "Zip Code").
        - **Key**: Attributes that allow to uniquely identify the entity, must be unique (ID, Ticket/Order Number).
        - **Non-key**: Non-unique attributes of the entity (First Name, Last Name, Color).
        - **Single-valued**: Can have only one value (e.g. "Student ID Number").
        - **Multi-valued**: Can have multiple values (e.g. "Phone Numbers"). *not supported by relational models.
- **Relationships**:
    - **Relationships** describe how entities are related to each other.
    - **Examples**: Student is enrolled in a Course", "Instructor teaches a Course".
    - **Notations**: Diamonds connected by lines to entities.
        - **One-to-one (1:1)**: Each entity of one category is related to at most one entity of another category.
            - **Example**: One principal manages one school, and each school has only one principal.
        - **One-to-many (1:M)**: Each entity of one category is related to multiple entities of another category.
            - **Example**: One instructor teaches many courses, but each course is taught by only one instructor.
        - **Many-to-many (M:M)**: Each entity of one category can be related to multiple entities of another category, and vice versa.
            - **Example**: Students are enrolled in many courses, and each course can have many students.

## Functional dependency and Keys

### The concept of functional dependency

- **Functional dependency** is a fundamental concept in database theory used to analyze and normalize relational databases. A functional dependency defines a **relationship between attributes** in a table, indicating that the value of **one set of attributes** uniquely determines the value of **another set of attributes**.
    - A functional dependency between two sets of attributes A and B in a relational table is written as: **A→B**
    - This is read as **"A functionally determines B"** and means that if two rows in table I have the same value for attribute A, then they will also have the same value for attribute B.

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/functional_dependency.jpg)

   - *student_id → name, birthdate, major*
    **A student identifier (student_id) uniquely identifies a student's name, birthdate, and major.**
    - *name, birthdate → student_id*:
    **The combination of name and birthdate uniquely identifies a student identifier (in this case).**

- **Types of functional dependencies**:
    - **Trivial functional dependency**: A dependency is called trivial if the dependent set of attributes **is a subset** of the defining set.
        - **Example**: **{name, birthdate} → name**
    - **Non-trivial functional dependency**: A dependency is called non-trivial if the dependent set of attributes is **not a subset** of the defining set.
        - **Example**: **student_id → name**
    - **Fully functional dependency**: A dependency is called complete if the dependent set of attributes **depends on the entire defining set** and does not depend on its subset.
        - **Example**: **{student_id, name} → major** (if major depends only on the combination of **both attributes**, and not on each separately).
    - **Partial functional dependency**: A dependency is called partial if the **dependent set** of attributes **depends on a subset** of the defining set.
        - **Example**: **{student_id, major} → name** (if name can be determined only from student_id).
    - **Example**: 
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/functional_dependency_ex.jpg)
        - **course_id -> course_name, instructor_name**
        - Math appears 2 times because both students are taking the same course.
        - To eliminate redundancy, we can **split** the table **into two**.
            - !!! We have now removed redundancy by using functional dependencies to normalize the data.

### The process of extracting a primary key from a candidate key

- **Primary key selection criteria**:
    - **Uniqueness**
    - **Minimum size**
    - **Immutability**
    - **Simplicity and efficiency**: Numeric keys are preferred because they are fast to process and require less storage than text keys.
    - **Usage frequency**: Keys that are frequently used in queries and references to other tables should be selected as primary keys to improve performance.
- **Algorithm**:
    1. **Identifying all candidate keys**: This step involves identifying all possible combinations of attributes that can uniquely identify a row in the table.
    2. **Minimality check**: Ensure that each **candidate key** is **minimal**, meaning it does not contain any extra attributes that can be removed while maintaining unique identification.
    3. **Selecting a primary key**:
        - From all identified **candidate keys**, select one to be used as the **primary key**. This choice can be based on various criteria, such as:
            - **Simple composition**: the key should be as simple as possible (fewer attributes).
            - **Frequency of use**: keys that are used more often for references are preferred.
            - **Performance**: keys with numeric values are usually preferred due to faster processing.

## Table Relationships

### Types of Relationships

- **One-to-one (1:1)**: In this relationship, each row in one table corresponds to one row in the other table.
    - **Example**: Users table and UserProfiles table:
        - Users (user_id, username, password)
        - UserProfiles (profile_id, user_id, address, phone)
        - In each **Users table**, a **user_id row** will correspond to exactly **one user_id row** in the **UserProfiles table**.
    ```
    CREATE TABLE Users (
        user_id INT PRIMARY KEY,
        username VARCHAR(50),
        password VARCHAR(50)
    )

    CREATE TABLE UserProfiles (
        profile_id INT PRIMARY KEY,
        user_id INT UNIQUE,
        address VARCHAR(255),
        phone VARCHAR(20),
        FOREIGN KEY (user_id) REFERENCES Users(user_id)
    )
    ```
- **One-to-Many (1:M)**: In this relationship, each row in one table corresponds to multiple rows in the other table.
    - **Example**: Departments table and Employees table:
        - **Departments** (department_id, department_name).
        - **Employees** (employee_id, employee_name, department_id).
        - A department can have many employees, but each employee belongs to only one department.
    ```
    CREATE TABLE Departments (
        department_id INT PRIMARY KEY,
        department_name VARCHAR(50)
    )

    CREATE TABLE Employees (
        employee_id INT PRIMARY KEY,
        employee_name VARCHAR(50),
        department_id INT,
        FOREIGN KEY (department_id) REFERENCES Departments(department_id)
    )
    ```
- **Many-to-Many (M:M)**: In this relationship, each row in one table can correspond to multiple rows in another table and vice versa.
- To implement such a relationship, a third intermediate table (a relationship table) is required that stores the corresponding pairs of keys from the related tables.
    - **Example**: Students table, Courses table, and Enrollments relationship table:
        - **Students** (student_id, student_name).
        - **Courses** (course_id, course_name).
        - **Enrollments** (student_id, course_id).
        - A single student can be enrolled in multiple courses, and a single course can have multiple students.
    ```
    CREATE TABLE Students (
        student_id INT PRIMARY KEY,
        student_name VARCHAR(50)
    )

    CREATE TABLE Courses (
        course_id INT PRIMARY KEY,
        course_name VARCHAR(50)
    )

    CREATE TABLE Enrollments (
        student_id INT,
        course_id INT,
        PRIMARY KEY (student_id, course_id),
        FOREIGN KEY (student_id) REFERENCES Students(student_id),
        FOREIGN KEY (course_id) REFERENCES Courses(course_id)
    )
    ```

## Aggregate Functions

- **COUNT()**: It returns the number of rows that match a given condition or are present in a column.
    - **COUNT(*)**: Counts all rows.
    - **COUNT(column_name)**: Counts non-NULL values in the specified column.
    - **COUNT(DISTINCT column_name)**: Counts unique non-NULL values in the column.
    - **Examples**:
        ```
        -- Total number of records in the table
        SELECT COUNT(*) AS TotalRecords FROM Employee;

        -- Count of non-NULL salaries
        SELECT COUNT(Salary) AS NonNullSalaries FROM Employee;

        -- Count of unique non-NULL salaries
        SELECT COUNT(DISTINCT Salary) AS UniqueSalaries FROM Employee;
        ```
- **SUM()**: It calculates the total sum of a numeric column.
    - **SUM(column_name)**: Returns the total sum of all non-NULL values in a column.
    - **Examples**: 
        ```
        -- Calculate the total salary
        SELECT SUM(Salary) AS TotalSalary FROM Employee;

        -- Calculate the sum of unique salaries
        SELECT SUM(DISTINCT Salary) AS DistinctSalarySum FROM Employee;
        ```
- **AVG()**: It calculates the average of a numeric column. It divides the sum of the column by the number of non-NULL rows.
    - **AVG(column_name)**: Returns the average of the non-NULL values in the column.
    - **Examples**: 
        ```
        -- Calculate the average salary
        SELECT AVG(Salary) AS AverageSalary FROM Employee;

        -- Average of distinct salaries
        SELECT AVG(DISTINCT Salary) AS DistinctAvgSalary FROM Employee;
        ```
- **MIN() and MAX()**: The MIN() and MAX() functions return the smallest and largest values, respectively, from a column.
    - **MIN(column_name)**: Returns the minimum value.
    - **MAX(column_name)**: Returns the maximum value.
    - **Examples**:
        ```
        -- Find the highest salary
        SELECT MAX(Salary) AS HighestSalary FROM Employee;

        -- Find the lowest salary
        SELECT MIN(Salary) AS LowestSalary FROM Employee;
        ```

## Filtering and Searching data

- **Main operators for filtering**:
    - **WHERE**: Used to filter rows based on a specified condition.
        ```
        SELECT * FROM Employees WHERE departmend_id = 1;

        SELECT * FROM Employees WHERE salary > 5000
        ```
    - **LIKE**: Used to find rows that match a pattern. Often used with wildcards.
        ```
        SELECT * FROM Employees WHERE name LIKE 'A%; -- Name starting with 'A'
        SELECT * FROM Employees WHERE name LIKE '%son'; -- Name ending with 'son'
        SELECT * FRON Employees WHERE name LIKE '_a%'; -- Name, where the second symbol is 'a'
        ```
    - **IN**: Used to filter rows whose value is within a specified list of values.
        ```
        SELECT * FROM Employees WHERE departmend_id IN (1, 2, 3);

        SELECT * FROM Employees WHERE position IN ('Manager', 'Developer')
        ```
    - **BETWEEN**: Used to filter rows whose value is within a specified range.
        ```
        SELECT * FROM Employees WHERE salary BETWEEN 40000 AND 60000;

        SELECT * FROM Employees WHERE hire_date BETWEEN '2020-01-01' AND '2021-01-01'
        ```
    - **IS NULL**: Used to find rows whose values are NULL.
        ```
        SELECT * FROM Employees WHERE manager_id IS NULL
        ```

## Sorting and Grouping results

- **ORDER BY**: It is used **to sort** the query results by one or more columns. By default, sorting is performed in ascending order (ASC), but you can also specify descending order (DESC).
    ```
    -- Sorting by one column in descending order
    SELECT * FROM Employees ORDER BY salary DESC
    ```
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/order_by.jpg)

    ```
    -- Sorting by multiple columns
    SELECT * FROM Employees ORDER BY department_id, salary
    ```
- **GROUP BY**: It is used **to group rows** that have the same values in the specified columns. It is **often used** together with **aggregate functions** (e.g. COUNT, SUM, AVG, MIN, MAX) to perform calculations on each group.
    ```
    -- Grouping by one column
    SELECT department_id, COUNT(*) AS num_employees FROM Employees
    GROUP BY department_id
    /* OUTPUT
    | department_id | num_employees |
    |      10       |       30      |
    |      11       |       25      |
    */

    -- Grouping by multiple columns
    SELECT department_id, job_title, COUNT(*) AS num_employees FROM Employees
    GROUP BY department_id, job_title
    ```
- **Having with GROUP BY**: It is used **to filter groups** after **GROUP BY** has been applied. It allows you to specify a condition that must be met for each group.
    ```
    -- Filtering groups by an aggregate function
    SELECT department_id, COUNT(*) AS num_employees FROM Employees
    GROUP BY department_id
    HAVING COUNT(*) > 25
    /* OUTPUT
    | department_id | num_employees |
    |      10       |       30      |
    */
    ```

## Data Selection

### Data Selection from one table

- **Selecting all columns**: 
    ```
    SELECT * FROM Employees
    ```
- **Selecting several columns**:
    ```
    SELECT employee_id, name, salary FROM Employees
    ``` 
- **Selecting with condition**:
    ```
    SELECT employee_id, name, salary FROM Employees
    WHERE department_id = 1
    ```
- **Selecting with sortion**:
    ```
    SELECT employee_id, name, salary FROM Employees
    WHERE department_id = 1
    ORDER BY salary DESC
    ```

### Data Selection from multiple tables

- To retrieve data from multiple tables, use JOINs

1. Student Table
![](https://github.com/Mad03633/DB-Prep/blob/main/Media/data_selection_ex_1.jpg)
2. StudentCourse Table
![](https://github.com/Mad03633/DB-Prep/blob/main/Media/data_selection_ex_2.jpg)

- **INNER JOIN**: Returns rows that have matching values in both tables.
    ```
    SELECT StudentCourse.COURSE_ID, Student.NAME, Student.Age FROM Student 
    INNER JOIN ON Student.ROLL_NO = StudentCourse.ROLL_NO
    ```
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/data_selection_inner_join.jpg)

- **LEFT JOIN**: Returns all rows from the left table and matching rows from the right table. If there is no match, NULL is returned for the right table.
    ```
    SELECT Student.NAME, StudentCourse.COURSE_ID FROM Student 
    LEFT JOIN StudentCourse ON StudentCourse.ROLL_NO = Student.ROLL_NO
    ```
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/data_selection_left_join.jpg)

- **RIGHT JOIN**: Returns all rows from the right table and matching rows from the left table. If there is no match, NULL is returned for the left table.
    ```
    SELECT Student.NAME, StudentCourse.COURSE_ID FROM Student 
    RIGHT JOIN StudentCourse ON StudentCourse.ROLL_NO = Student.ROLL_NO
    ```
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/data_selection_right_join.jpg)

- **FULL JOIN**: Returns all rows when there is a match in one of the tables. If there is no match, NULL is returned for the opposite table.
    ```
    SELECT Student.NAME, StudentCourse.COURSE_ID FROM Student
    FULL JOIN StudentCourse ON StudentCourse.ROLL_NO = Student.ROLL_NO

    /*
    |     NAME     |   COURSE_ID  |
    |    HARSH     |       1      |
    |    PRATIK    |       2      |
    |    RIYANKA   |       2      |
    |    DEEP      |       3      |
    |    SAPTARHI  |       1      |
    |    DAHNRAJ   |       NULL   |
    |    ROHIT     |       NULL   |
    |    NIRAJ     |       NULL   |
    |    NULL      |       4      |
    |    NULL      |       5     |
    |    NULL      |       4     |
    */
    ```
- **SELF JOIN**: Join a table with itself. Used to compare rows in one table.
    ```
    SELECT E1.employee_id, E1.name, E2.name AS manager_name FROM Employees AS E1
    INNER JOIN Employees AS E2 ON E2.employee_id = E1.manager_id
    ```
- **Joining using subqueries**: Subqueries are used to perform nested queries.
    ```
    SELECT s.name, sc.course_count
    FROM Students s
    JOIN (
        SELECT student_id, COUNT(*) AS course_count
        FROM Enrollments
        GROUP BY student_id
    ) sc
    ON s.student_id = sc.student_id;
    ```

## Interactive mode with DB

- **Command Line Interface (CLI)**: Many DBMSs provide command line interfaces through which you can execute SQL queries and manage the database.
    - **Examples**: mysql for MySQL, psql for PostgreSQL, sqlplus for Oracle.
- **Graphical User Interface (GUI)**: Graphical tools provide a more convenient way to work with the database by providing visual means for creating and executing queries.
    - **Examples**: МySQL Workbench, pgAdmin, SQL Server Management Studio (SSMS).
- **Interactive Shells**: Shells such as IPython or Jupyter Notebooks can be used to work interactively with the database via SQLAlchemy or other libraries.

## Database Management

### CREATE

- **Example**:
    ```
    CREATE TABLE Departments (
        department_id INT PRIMARY KEY,
        department_name VARCHAR(100) NOT NULL
    );

    CREATE TABLE Employees (
        employee_id INT PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        position VARCHAR(50),
        salary DECIMAL(10, 2),
        hire_date DATE,
        department_id INT,
        FOREIGN KEY (department_id) REFERENCES Departments(department_id)
    )
    ```
### ALTER

- **Adding columns**:
    ```
    ALTER TABLE Employees
    ADD COLUMN email VARCHAR(255)
    ```
- **Removing columns**:
    ```
    ALTER TABLE Employees
    DROP COLUMN email
    ```
- **Changing the data type of a column**:
    ```
    ALTER TABLE Employees
    MODIFY COLUMN salary FLOAT
    ```
- **Renaming a column**:
    ```
    ALTER TABLE Employees
    RENAME COLUMN name TO full_name
    ```
- **Adding constraints**:
    ```
    ALTER TABLE Employees
    ADD CONSTRAINT unique_email UNIQUE(email)
    ```
- **Removing constraints**:
    ```
    ALTER TABLE Employees
    DROP CONSTRAINT unique_email
    ```
- **Renaming a table**:
    ```
    ALTER TABLE Employees
    RENAME TO Staff
    ```

### DROP

- **Dropping a single table**:
    ```
    DROP TABLE Employees
    ```
- **Deleting a table with cascading dependency deletion**:
    - Let's delete the Departments table referenced by the Employees table with a foreign key:
        ```
        -- If DBMS supports CASCADE
        DROP TABLE Departments CASCADE
        ```
- **Deleting a table with existence check**:
    ```
    DROP TABLE IF EXISTS Employees
    ```

## Subqueries

- **Nested Subqueries**: Nested subqueries are used to execute a query within another query. They can be in the SELECT, FROM, WHERE, or HAVING clauses. **Note: Nested → independent result.**
    ```
    SELECT department_id, avg_salary
    FROM (SELECT department_id, AVG(salary) AS avg_salary FROM Employees
    GROUP BY department_id) AS dept_avg_salaries
    ```
- **Correlated Subqueries**: Correlated subqueries depend on the outer query and are executed for each row of the outer query. These subqueries use values from the outer query in their conditions. **Note: Correlated → depends on outer query (row).**
    ```
    SELECT name, salary
    FROM Employees E1
    WHERE salary > (SELECT AVG(salary) 
                    FROM Employees
                    WHERE E1.department_id = E2.department_id)
    ```

## Data Models

- **Conceptual data models**: This stage creates a conceptual data model that represents the structure of data and its relationships **without** taking into account **technical details**.
    - **Activities**:
        - Create an **ER (Entity-Relationship) diagram** to visualize entities, attributes, and the relationships between them.
        - Define **entities** and **attributes**.
        - Define **relationships** between entities (one-to-one, one-to-many, many-to-many).
        - Define **primary** and **foreign keys**.
- **Logical**: Logical design transforms the conceptual model into a **logical database structure** that can be implemented in a specific DBMS.
    - **Activities**:
        - Transform the **ER diagram into tables and columns**.
        - Define **data types** for each column.
        - Define **integrity constraints** (primary keys, foreign keys, unique and NOT NULL constraints).
        - **Normalize data** to eliminate redundancy and ensure data integrity (apply normal forms).
- **Physical**: Physical design involves creating the physical structure of the database taking into account the specific **DBMS features** and **performance requirements**.
    - **Activities**:
        - Defining the **data storage structure**(tables, indexes, views).
        - Selecting data storage **methods** (table partitioning, indexing, clustering).
        - Defining the **data backup and recovery policy**.
        - **Tuning performance parameters** (e.g. caching, parallel processing).

## Modelling methods

### ER-modelling

### Normalization

- It is the process of organizing data in a database to **reduce redundancy** and **ensure data integrity**. Normalization is achieved by **breaking large tables into smaller ones** and establishing relationships between them. This process consists of several **normal forms (NF)**, each of which provides a certain level of normalization. Let's look at normal forms from **0NF to 3NF**.
    - **0NF**: A table is in zero normal form if it does not satisfy any normalization rules. The data may be unstructured and contain duplicate records.

    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/0NF.jpg)
        - Skills contains many values in a single column
    - **1NF**: 
        - A table is in 1NF if it satisfies the following conditions:
             - All columns contain **atomic values** (i.e., indivisible values).
            - Each **row** is unique (i.e., no duplicate rows).
            - Each **column** has a unique name.
            - The order in which data is stored does not matter.
        ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/1NF.jpg)
            - Here, each skill value is atomic.
    - **2NF**: A relation is in 2NF if it satisfies the conditions of **1NF** and **additionally**. **No partial dependency exists**, meaning every non-prime attribute (non-key attribute) must depend on the entire **primary key**, not just a part of it.
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/2NF.jpg)
        - Let's split the Employees table into two tables: Employees and Skills.
        - Here, Name depends only on EmployeeID, and Skill on the entire EmployeeID key.
    - **3NF**: A relation is in 3NF if it satisfies **2NF** and **additionally**, there are **no transitive dependencies**. In simpler terms, non-prime attributes should **not depend** on other non-prime attributes.
    ![](https://github.com/Mad03633/DB-Prep/blob/main/Media/3NF.jpg)
        - Let's split the Employees table into three tables: Employees, Skills and Departments.
        - Here, each table contains only those attributes that depend on its key.

### Denormalization

- The process of deliberately introducing redundancy into a database to improve performance by reducing the number of complex joins and optimizing data access.
- **Denormalization** is used to **improve database performance** in situations where normalized data structures are **too slow** for certain operations.

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/unnormalized.jpg)
- What’s wrong with it?
    - **Redundancy**: For example, "Alice" and "Math" are repeated multiple times. Similarly, "Mr. Smith" is stored twice for the same class.
    - **Update Anomalies**: If "Mr. Smith" changes to "Mr. Brown," we have to update multiple rows Missing one row could lead to inconsistencies.
    - **Inefficient Storage**: Repeated information takes up unnecessary space.
![](https://github.com/Mad03633/DB-Prep/blob/main/Media/normalized.jpg)
- Why is this better?
    - **No Redundancy**: "Mr. Smith" appears only once in the Classes Table, even if multiple subjects are associated with the class.
    - **Easier Updates**: If "Mr. Smith" changes to "Mr. Brown," you only update the Classes Table and it automatically reflects everywhere.
    - **Efficient Storage**: Repeated data is eliminated, saving space.
![](https://github.com/Mad03633/DB-Prep/blob/main/Media/denormalized.jpg)
- What’s happening here?
    - All related information (student name, class name, teacher and subject) is stored in a single table.
    - This simplifies querying because you **don’t need to join multiple tables**.

- **Common Reasons for Denormalization**:
    - **Improved Performance**: Reducing the number of joins between tables can significantly speed up queries.
    - **Query Simplification**: Denormalization can simplify SQL queries, making them clearer and easier to maintain.
    - **Optimized Data Reads**: In systems where data is read significantly more often than written, denormalization can improve performance.
- **Advantages**:
    - **Increased Query Speed**: Fewer joins mean faster queries.
    - **Reduced Query Complexity**: Simpler SQL queries are easier to write and maintain.
    - **Optimized Data Reads**: Improved read performance in read-heavy systems.
- **Disadvantages**:
    - **Data Redundancy**: Introducing duplicate data increases storage requirements.
    - **Increased complexity of updates**: Updating data may require changing multiple records in different locations, increasing the likelihood of errors.
    - **Data integrity issues**: It is more difficult to maintain data consistency, which can lead to anomalies.
- **NOTE** that denormalization does not mean 'reversing normalization' or 'not to normalize'. It is an optimization technique that is applied after normalization.

## Architecture of DB(SQL-server)/physical/logical

### Architecture of DB(SQL-server)

- **Database Engine**:
    - **System core**: The main component that manages data storage, processing, and security.
    - **Data storage**: Manages data files and transaction logs.
    - **Procedures and functions**: Execute stored procedures and user-defined functions.
- **SQL Server Agent**:
    - **Task automation**: Schedule and execute tasks such as database backup, restore, and maintenance.
- **SQL Server Browser**:
    - **Query routing**: Helps clients connect to the correct 5QL Server instances.
- **Analysis Services**:
    - **Analytics**: Support for multidimensional data models and analytical queries.
- **Reporting Services**:
    **Reports**: Create, manage, and deploy reports.
- **Integration Services**:
    - **Data integration**: Tools for extracting, transforming, and loading (ETL) data.
- **SQL Server instances**: These are separate SQL Server installations that can run on a single physical or virtual server. Each instance operates independently of the others, with its own settings, databases, services, and security. 
    - **Default Instance**: The master instance installed by default.
    - **Named Instance**: Additional instances that can be installed on the same server.
- **Memory Architecture**:
    - **Buffer Pool**: The main memory pool for caching data and indexes.
    - **Data Cache**: Stores data pages in memory for fast access.
    - **Procedure Cache**: Caches query execution plans and stored procedures.

### Architecture of DB in physical layer

- **Pages**: Basic units of data storage (8 KB each).
    - **Data Pages**: Store rows of data.
    - **Index pages**: Store indexes.
    - **Text/Image Pages**: Store large objects (LOBs).
    - **Global Allocation Map (GAM)**: Manage extent allocation.
    - **Shared Global Allocation Map (SGAM)**: Manage free extents.
    **Page Free Space (PFS)**: Manage free space on pages.
- **Extents**: Groups of pages (8 pages or 64 KB).

### Architecture of DB in logical layer

- **Logical Objects**:
    - **Tables**: Basic structures for storing data.
    - **Views**: Logical tables based on query results.
    - **Indexes**: Structures for speeding up data retrieval.
    - **Schemas**: Logical association of database objects.
    - **Constraints**: Rules for ensuring data integrity.
- **Data types**:
    - **Numeric data types**: int, decimal, float, etc.
    - **Character data types**: char, varchar, text, etc.
    - **Date and time**: date, datetime, time, etc.
    - **Binary data types**: binary, varbinary, image.
    - **Special data types**: XML, JSON, spatial.
- **Security Management**:
    - **Logins**: Managing access to the server.
    - **Users**: Managing access to databases.
    - **Roles**: Permission groups for managing access.
    - **Permissions**: Assigning access rights.
    - **Encryption**: Protecting data at the database level.

## Data Query Language

- **SELECT**:
    - A data query begins with SELECT, followed by the columns to be displayed, the FROM keyword, and the table name.
    - Multiple requested columns are specified separated by commas.
        ```
        SELECT CustomerName, City FROM Customers
        ```
    - If you want to return all columns, insert * after the SELECT word.
        ```
        SELECT * FROM Customers
        ```
    - The DISTINCT keyword after SELECT will return only unique values, without duplicates. Using the DISTINCT keyword in the COUNT function, we can return the number of different countries.
        ```
        SELECT COUNT(DISTINCT Country) FROM Customers
        ```
    - The SELECT TOP clause is used to specify the number of records to return.
        ```
        SELECT TOP 3 * FROM Customers
        ```
    - The SELECT INTO statement copies data from one table to a new table.
        ```
        SELECT * INTO CustomersBackup2017
        FROM Customers
        ```

## WHERE Clause

- The WHERE keyword is used to filter queries. Using it, the query will return only rows that satisfy the condition.
    ```
    SELECT * FROM Customers
    WHERE Country = 'Mexico'
    ```

### Comparison Operators

- **=**: Equal to.
- **>**: Greater than.
- **<**: Less than.
- **>=**: Greater than or equal to.
- **<=**: Less than or equal to.
- **<>**: Not equal to.
- **BETWEEN**: In an inclusive Range. This means that when you use BETWEEN value1 AND value2, both value1 and value2 are included in the result set.
    ```
    SELECT * FROM Products
    WHERE Price BETWEEN 10 AND 20
    ```
- **LIKE**: Search for a pattern. 
    - **Wildcards** that are used with the LIKE operator:
        - The **percent sign %** represents zero, one, or more characters.
            ```
            SELECT * FROM Customers
            WHERE CustomerName LIKE 'a%' -- Words that start with the letter 'a'
            
            SELECT * FROM Customers
            WHERE city LIKE '%L%' -- Words that have the letter 'L' anywhere

            SELECT * FROM Customers
            WHERE CustomerName LIKE 'b%s' -- Words that start with 'b' and end with 'ѕ'
            ```
        - The **underscore _** represents a single character.
            ```
            SELECT * FROM Customers
            WHERE CustomerName LIKE '_r%' -- Words with the letter 'r' in the second position
            ```
        - **[]** returns a result if any of the characters inside it matches.
            ```
            SELECT * FROM Customers
            WHERE CustomerName LIKE '[bsp]%' -- Words that start with 'b', 's', or 'р'
            ```
        - **- the wildcard** allows you to specify a range of characters inside the wildcard [].
            ```
            SELECT * FROM Customers
            WHERE CustomerName LIKE '[a-f]%' -- Words that start with letters 'a' through 'f' alphabetically 'a', 'b', 'c', 'd', 'e', 'f'
            ```
        - **#** represents any numeric character.
            ```
            SELECT * FROM Customers
            WHERE CustomerId LIKE '2#5' -- '2#5' will find 205, 215, 225, 235, 245, 255, 265, 275, 285, and 295
            ```
        - **!** Represents any character not enclosed in square brackets.
            ```
            SELECT * FROM Customers
            WHERE CustomerWorld LIKE 'h[!oa]t' -- It will find the word 'hit', but NOT hot or hat
            ```
- **IN**: To specify multiple possible values for a column.
    ```
    SELECT * FROM Customers
    WHERE Country IN ('Germany', 'France', 'UK')
    ```

### Logical operators

- **AND**: Using logical **AND**, you can set several conditions for the WHERE keyword.
    ```
    SELECT * FROM Customers
    WHERE Country = 'Germnay'
    AND City = 'Berlin'
    AND PostalCode = 12000
    ```
- **OR**: Logical **OR** will return results in which one of the conditions matches.
    ```
    SELECT * FROM Customers
    WHERE Country = 'Germany' OR Country = 'Spain'
    ```
- **NOT**: Logical **NOT** will return the opposite result from the condition. It can also be used in combination with other comparison operators.
    ```
    SELECT * FROM Customers
    WHERE NOT Country = 'Spain'
    ```

## Aggregate functions in SQL

- **COUNT()**: It returns the number of rows that match a given condition or are present in a column.
    - **COUNT(*)**: Counts all rows.
    - **COUNT(column_name)**: Counts non-NULL values in the specified column.
    - **COUNT(DISTINCT column_name)**: Counts unique non-NULL values in the column.
    - **Examples**:
        ```
        -- Total number of records in the table
        SELECT COUNT(*) AS TotalRecords FROM Employee;

        -- Count of non-NULL salaries
        SELECT COUNT(Salary) AS NonNullSalaries FROM Employee;

        -- Count of unique non-NULL salaries
        SELECT COUNT(DISTINCT Salary) AS UniqueSalaries FROM Employee;
        ```
- **SUM()**: It calculates the total sum of a numeric column.
    - **SUM(column_name)**: Returns the total sum of all non-NULL values in a column.
    - **Examples**: 
        ```
        -- Calculate the total salary
        SELECT SUM(Salary) AS TotalSalary FROM Employee;

        -- Calculate the sum of unique salaries
        SELECT SUM(DISTINCT Salary) AS DistinctSalarySum FROM Employee;
        ```
- **AVG()**: It calculates the average of a numeric column. It divides the sum of the column by the number of non-NULL rows.
    - **AVG(column_name)**: Returns the average of the non-NULL values in the column.
    - **Examples**: 
        ```
        -- Calculate the average salary
        SELECT AVG(Salary) AS AverageSalary FROM Employee;

        -- Average of distinct salaries
        SELECT AVG(DISTINCT Salary) AS DistinctAvgSalary FROM Employee;
        ```
- **MIN() and MAX()**: The MIN() and MAX() functions return the smallest and largest values, respectively, from a column.
    - **MIN(column_name)**: Returns the minimum value.
    - **MAX(column_name)**: Returns the maximum value.
    - **Examples**:
        ```
        -- Find the highest salary
        SELECT MAX(Salary) AS HighestSalary FROM Employee;

        -- Find the lowest salary
        SELECT MIN(Salary) AS LowestSalary FROM Employee;
        ```

## ORDER BY Clause

- The **ORDER BY** keyword is used to **sort** the result in **ascending** or **descending** order.
    ```
    SELECT * FROM Products
    ORDER BY Price
    ```
- The **ORDER BY** keyword sorts the records in **ascending** order by **default**. To sort the records in **descending** order, use the **DESC** keyword.
    ```
    SELECT * FROM Products
    ORDER BY Price DESC
    ```

## GROUP BY Clause

- The **GROUP BY** operator groups rows with the same values into **summary rows**, such as "find the number of customers in each country".
- It is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result set by one or more columns.
    ```
    SELECT COUNT(CustomerID), Country FROM Cusomers
    GROUP BY Country
    ```

## HAVING Clause

- The **HAVING clause** was added to SQL because the WHERE keyword cannot be used with aggregate functions.
    ```
    SELECT COUNT(CustomerID), Country
    FROM Customers
    GROUP BY Country
    HAVING COUNT(CustomerID) > 5
    ```

## ANY/ALL Clause

-  The **ALL and ANY** operators are logical operators used to compare a value with a set of values returned by a subquery.
    - The **ALL** must be preceded by comparison operators and evaluates true if all of the subqueries values meet the condition.
    - ALL is used with SELECT, WHERE, and HAVING statements.
    ```
    SELECT column_name(s)
    FROM table_name
    WHERE column_name comparison_operator ALL
        (SELECT column_name
        FROM table_name
        WHERE condition(s))

    SELECT ProductName FROM Products
    WHERE ProductID = ALL
        (SELECT ProductID FROM OrderDetails
        WHERE Quantity = 10)
    -- The following SQL statement prints the product name if the quantity in all records in the Order Details table is 10. This will of course return FALSE since the Quantity column contains many different values.
    ```
    - **ANY** compares a value to each value in a list or results from a query and evaluates to true if the result of an inner query contains at least one row.
    - **ANY** return true if any of the subqueries values meet the condition.
    - **ANY** must be preceded by comparison operators.
    ```
    SELECT column_name(s) FROM table_name
    WHERE column_name comparison_operator ANY
        (SELECT column_name 
        FROM table_name
        WHERE condition(s))

    SELECT ProductName FROM Products
    WHERE ProductID = ANY
        (SELECT ProductID FROM OrderDetails
        WHERE Quantity = 10)
    -- The following SQL statement prints the product name if it finds any records in the Order Details table whose quantity is 10.
    ```

## AS Keyword

- SQL **aliases** are used to give a table or column in a table a temporary name.
    ```
    SELECT CustomerID as ID
    FROM Customers
    ```

## CASE Expression

- The **CASE expression** loops through the conditions and returns a value when the first condition is met (like an if-then-else statement). So once a condition is met, it stops reading and returns the result. If none of the conditions are met, it returns the value in the ELSE clause.
    ```
    CASE case_value
    WHEN condition THEN result1
    WHEN condition THEN result2
    ...
    Else result
    END CASE;

    SELECT OrderId, Quantity,
    CASE
        WHEN Quantity > 30 THEN 'The quantity is greater than 30'
        WHEN Quantity = 30 THEN 'The quantity is 30'
        ELSE 'The quantity is under 30'
    END AS QuantityText
    FROM OrderDetails;
    -- The CASE result will be returned in the QuantityText column as text.

    SELECT CustomerName, Country
    FROM Customer
    ORDER BY
    (CASE
        WHEN Country = 'India' THEN Country
        ELSE Age
    END);
    -- Let's take the Customer Table which contains CustomerID, CustomerName, LastName, Country, Age, and Phone. We can check the data of the Customer table by using the ORDER BY clause with the CASE statement.
    ```
- **Important Points About CASE Statement**:
    - The SQL CASE statement is a conditional expression that allows for the execution of different queries based on specified conditions.
    - There should always be a SELECT in the CASE statement.
    - **END ELSE** is an optional component but WHEN THEN these cases must be included in the CASE statement.
    - We can make any conditional statement using any conditional operator (like WHERE ) between WHEN and THEN. This includes stringing together multiple conditional statements using AND and OR.
    - We can include multiple WHEN statements and an ELSE statement to counter with unaddressed conditions.

## JOIN

![](https://github.com/Mad03633/DB-Prep/blob/main/Media/JOINS.jpg)

- The **JOIN** clause is used to combine rows from two or more tables based on a related column between them.
    - **INNER JOIN**: This mode of combining search results in SQL databases is enabled **automatically**. If you do not intentionally specify the Join type, then Inner Join will work. With it, you can specify two criteria at once (two tables) and filter the content by them.
        ```
        SELECT * FROM table-1
        JOIN table-2 ON table-1.parameter = table-2.parameter
        WHERE table-1.parameter IS 'myData'
        ```
    - **SELF JOIN**: Self Join queries are useful in cases where you need to filter content within one table. For example, you have a list of products in a database. Each of them has its own brand, but there are also those that are supplied by the same manufacturer. Self Join can be used to combine two stacks of information from one table.
        ```
        SELECT * FROM Products
        JOIN Products ON table.product = table.brand
        -- This scenario is useful in almost any type of database, since one table can often store information about products or content that have a large number of common parameters.
        ```
    - **LEFT JOIN**: Left join means when we take one table, connect the Second and at the same time show not only exact matches, but also the entire list of rows obtained from the left table, for which there was no pair in the right table.
        ```
        SELECT * FROM table-1
        LEFT JOIN table-2 ON table-1.parameter = table-2.parameter
        ```
            ```
            SELECT * FROM Russian
            LEFT JOIN Rap ON Russian.genreId = Rap.genreId
            -- Let's imagine that we have launched an advanced search on a website with music albums. We want to listen to something in Russian. And we are even ready to evaluate the quality of Russian rap. At the same time, in general, we do not like rap and do not want it to come across in any other languages.
            ```
    - **RIGHT JOIN**: It is clear that the right join will work in the opposite direction and will show elements from the right table, for which there was no pair in the left.
        ```
        SELECT * FROM table-1
        LEFT JOIN table-2 ON table-1.parameter = table-2.parameter
        ```
    - **FULL OUTER JOIN**: This is an option for those who want to use two different criteria at once to search for some content. Let's go back to the example with the music application. Join Full can be useful if you want to listen to **either something in Russian or any rap**. You don't care about any other parameters. You care only about two characteristics. At the same time, you don't care whether they intersect. That is, you don't care whether it's rap in Russian or some aggressive metal in Russian.
        ```
        SELECT * FROM table-1
        FULL OUTER JOIN table-2 ON table-1.parameter = table-2.parameter
        ```
    - **CROSS JOIN**: The most specific option for filtering data. It involves collecting all combinations of elements from several tables at once, without accessing any additional information. In fact, this is a Cartesian product.
        ```
        SELECT * FROM table-1
        CROSS JOIN table-2
        ```

## UNION

- The **UNION operator** is used to combine the result set of two or more SELECT statements.
    - Each SELECT statement in a UNION must contain the **same number of columns**.
    - The columns must also contain **similar data types**.
    - The columns in each SELECT statement must also be in the **same order**.
- Note: SQL UNION and UNION ALL difference is that **UNION** operator **removes duplicate rows** from results set and **UNION ALL** operator **retains all rows**, including duplicate.
    ```
    SELECT Country FROM Emp_1
    UNION 
    SELECT Country FROM Emp_2
    ```

## Data Manipulaion Language

- **INSERT INTO**: The INSERT INTO statement is used to insert new records into a table.
    - **Example**: 
        ```
        INSERT INTO Customers(CustomerName, ContactName, Address, City, PostalCode, Country)
        VALUES('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway')
        ```
    - There are two ways to write the INSERT INTO statement:
        - Specify both the column names and the values to be inserted.
            ```
            INSERT INTO table_name(column1, column2, column3, ...)
            VALUES(value1, value2, value3, ...);
            ```
        - If you are adding values for all the columns in a table, you do not need to specify the column names in the SQL query. However, make sure that the order of the values matches the order of the columns in the table. Here, the INSERT INTO syntax is:
            ```
            INSERT INTO table_name
            VALUES(value1, value2, value3, ...)
            ```
- **UPDATE**: The UPDATE statement is used to change existing records in a table.
    ```
    UPDATE <table_name>
    SET <column_name = value>
    WHERE condition;

    UPDATE Customers
    SET ContactName = 'Alfred Schmidt', City = 'Frankfurt'
    WHERE CustomerID = 1 
    ```
- **DELETE**: The DELETE statement is used to delete existing records in a table.
    ```
    DELETE FROM <table_name>
    WHERE <condition>; 

    DELETE FROM Customers
    WHERE CustomerName = 'Magnus Carlsen'
    ```
    - **NOTE**: If we do not specify the 'WHERE' condition then all the rows would be erased or deleted.
        ```
        DELETE FROM Customers
        ```

## Data Definition Language

- **DROP**: The SQL DROP command is used to permanently remove an object from a database, such as a table, database, index, or view. To delete an entire table, type DROP TABLE table name. To delete an entire database and all of its associated tables
    ```
    DROP TABLE table_name;

    DROP DATABASE database_name;
    ```
- **CREATE**: The CREATE TABLE command in SQL is used to define a new table within a database. A table's structure, including column names, data types, and constraints like NOT NULL, PRIMARY KEY, and CHECK, are defined when it is created in SQL.
    ```
    CREAT TABLE table_name(
        column_name_1 datatype(size),
        column_name_2 datatype(size),
        column_name_3 datatype(size),
        ...
        column_name_N datatype(size)
    )

    CREATE TABLE Persons(
        PersonID INT,
        LastName VARCHAR(255),
        FirstName VARCHAR(255),
        Address VARCHAR(255),
        City VARCHAR(255)
    )
    ```
- **TRUNCATE**: The TRUNCATE TABLE statement is used to delete data within a table, but not the table itself. Although TRUNCATE is similar to the DELETE command (without the WHERE clause), it is much faster because it bypasses certain integrity constraints and locks.
    ```
    TRUNCATE TABLE table_name;
    ```
- **ALTER**: The ALTER TABLE statement is used to add, delete, or change columns in an existing table. 
    - **ADD**:
        ```
        ALTER TABLE Customers
        ADD Email VARCHAR(255)
        ```
    - **DROP COLUMN**:
        ```
        ALTER TABLE Customers
        DROP COLUMN Email
        ```
    - **RENAME COLUMN**:
        ```
        ALTER TABLE table_name
        RENAME COLUMN old_name TO new_name
        ```
    - **ALTER COLUMN**:
        ```
        ALTER TABLE table_name
        ALTER COLUMN column_name datatype
        ```

## Data types

- **INT**: Standard integer values. Range(-2,147,483,648 to 2,147,483,647)
- **VARCHAR(size)**: The maximum length of 8000 characters.(Variable-Length non-Unicode Characters).
- **DECIMAL(M, N)**: Exact fixed-point numbers. Total number of digits is specified in M size. Example: decimal(10, 4) = 654321.1234.
- **BLOB**: For BLOBs (Binary Large Objects). Contains up to 65535 bytes of data. Can be used to store images.
- **DATE**: Format: YYYY-MM-DD. Supported range of values is from "1000-01-01" to "9999-12-31".
- **TIMESTAMP**: Timestamp values are stored as the number of seconds since the Unix epoch ('1970-01-01 00:00:00' UTC). Format: YYYY-MM-DD, hhmm:ss. The supported range is from '1970-01-01 00:00:01' UTC to '2038-01-09 03:14:07' UTC.
- **TIME**: Stores the data of time (hour, minute,second).
............. (There are many types. It was described main types.)

## Constraints

- SQL **constraints** are essential elements in relational database design that ensure the **integrity, accuracy, and reliability** of the data stored in a database. SQL constraints are rules applied to **columns or tables** in a relational database to **limit the type of data** that can be inserted, updated, or deleted.
- Constraints can be specified when a table is created with the CREATE TABLE statement or after the table is created with the ALTER TABLE statement.
    ```
    CREATE TABLE table_name(
        column_1 datatype constraint,
        column_2 datatype constraint,
        column_3 datatype constraint,
        ...
    )
    ```

### Types

- **NOT NULL**: By default, a column can contain **NULL values**. The **NOT NULL constraint** ensures that a column **cannot contain** NULL values. This is particularly important for columns where a **value is essential** for identifying records or performing calculations.
    ```
    CREATE TABLE Students(
        ID INT(6) NOT NULL,
        Name VARCHAR(10) NOT NULL,
        Address VARCHAR(20)
    )
    ```
- **UNIQUE**: The **UNIQUE** constraint ensures that all values in a column are **distinct** across all rows in a table. Unlike the **PRIMARY KEY**, which requires **uniqueness** and **does not allow NULLs**, the **UNIQUE constraint allows NULL values** but still enforces uniqueness for non-NULL entries.
    ```
    CREATE TABLE Students(
        ID INT(6) NOT NULL UNIQUE,
        Name VARCHAR(10), -- in the above example name column has not null constraint, but as we use NOT NULL UNIQUE in ID column, Name cannot have not null
        Address VARCHAR(20)
    )
    ```
- **PRIMARY KEY**: A **PRIMARY KEY** constraint is a combination of the **NOT NULL and UNIQUE** constraints. It uniquely identifies each row in a table. A table can only have **one PRIMARY KEY**, and it **cannot accept NULL** values.
    ```
    CREATE TABLE Students(
        ID INT(6) NOT NULL UNIQUE,
        Name VARCHAR(10),
        Address VARCHAR(20),
        PRIMARY KEY(ID)
    )
    ```
- **FOREIGN KEY**: A **FOREIGN KEY** constraint is used to **prevent actions** that could break relationships between tables. A **FOREIGN KEY** is a field (or set of fields) in **one table that references a PRIMARY KEY** in another table. The **table with the foreign key** is called the **child table**, and the table with the **primary key** is called the **referencing** or **parent table**.
    ```
    CREATE TABLE Orders(
        OrderID INT NOT NULL,
        Order_no INT NOT NULL,
        CustomerID INT,
        PRIMARY KEY(OrderID),
        FOREIGN KEY (CustomerID) REFERENCES Customers(OrderID)
    )
    ```
- **CHECK**: The **CHECK constraint** allows us to specify a **condition** that data must satisfy **before it is inserted** into the table. This can be used to enforce rules, such as ensuring that a column’s value meets **certain criteria** (e.g., age must be greater than 18).
    ```
    CREATE TABLE Student(
        ID INT(6) NOT NULL,
        NAME VARCHAR(10) NOT NULL,
        AGE INT NOT NULL CHECK (AGE >= 18)
    )
    ```
- **DEFAULT**: The **DEFAULT** constraint provides a **default value** for a **column when no value** is specified during insertion. This is useful for ensuring that certain columns always have a **meaningful value**, even if the user does not provide one.
    ```
    CREATE TABLE Student(
        ID INT(6) NOT NULL,
        NAME VARCHAR(10) NOT NULL,
        AGE INT DEFAULT 18
    )
    ```
- **CREATE INDEX**: The **CREATE INDEX** Statement in SQL is used to **create indexes** in tables and **retrieve data** from the database **faster** than usual. Indexes are **invisible** structures that work behind the scenes to **speed up data retrieval operations** in databases. They are essential for **optimizing query** performance and improving overall system efficiency.
    ```
    CREATE INDEX index_name
    ON table_name(column_1, column_2, ...);

    CREATE UNIQUE UNDEX index_name
    ON table_name(column_1, column_2, ...);
    -- A unique index ensures that all values in the indexed columns are unique preventing duplicate values.

    CREATE INDEX idx
    ON Students(Name)
    ```

## Additions

### Auto increment

- In SQL databases, a primary key is important for uniquely identifying records in a table. **However**, sometimes it is **not practical** to manually assign **unique values for each record**, especially when handling large datasets. To simplify this process, SQL databases offer an **Auto Increment** feature that **automatically generates unique numerical values for a specified column**.
    ```
    CREATE TABLE Persons (
        Personid INT NOT NULL AUTO INCREMENT,
        LastName VARCHAR(255) NOT NULL,
        FirstName VARCHAR(255),
        Age INT, 
        PRIMARY KEY (Personid)
    )
    ```
    - By default, the **starting value for AUTO_INCREMENT is 1**, and it will increment by 1 for each new record. To let the AUTO_INCREMENT sequence start with **another value**, use the following SQL statement:
        ```
        ALTER TABLE Persons
        AUTO INCREMENT = 100
        ```

### View

- **Views** in SQL are a type of **virtual table** that simplifies how users interact with data across one or more tables. **Unlike traditional tables**, a view in SQL **does not store data on disk**; instead, it **dynamically retrieves data** based on a pre-defined query each time it’s accessed.
    ```
    CREATE VIEW [Norwegian Customer] AS
    SELECT CustomerName, ContactName FROM Customers
    WHERE Country = 'Norway';

    SELECT * FROM [Norwegian Customer];

    -- Updating a View
    CREATE OR REPLACE VIEW [Norwegian Customer] AS
    SELECT CustomerName, ContactName, City
    FROM Customers
    WHERE Country = 'Norway';

    -- Dropping a View
    DROP VIEW [Norwegian Customer];
    ```

### Transactions & ACID

- A **transaction** in SQL is a **sequence** of one or more SQL statements executed as a **single unit of work**. These statements could be performing operations like **INSERT, UPDATE, or DELETE**. The **main goal** of a transaction is to ensure that all operations within it should be either **completed successful** or **rolled back entirely if an error occurs**.
- **Key properties of transactions (ACID)**:
    - **Atomicity**: The outcome of a transaction can either be ***completely successful or completely unsuccessful**. The whole transaction must be rolled back if one part of it fails.
    - **Consistency**: Transactions maintain **integrity restrictions** by moving the database from one valid state to another.
    - **Isolation**: Concurrent transactions are isolated from one another, assuring the accuracy of the data.
    - **Durability**: Once a transaction is **committed**, its modifications remain in effect even in the event of a **system failure**.

| Command                    | Definition                                     |
| ---------------------------| -----------------------------------------------|
| START TRANSACTION or BEGIN |Begins a transaction                            |
| COMMIT                     |Commits the transaction, changes are saved      |
| ROLLBACK                   |Rolls back the transaction, discards all changes|
| SAVEPOINT                  |Sets a savepoint within the transaction         |
| ROLLBACK TO SAVEPOINT      |Reverts the transaction to a specific SAVEPOINT |
| SET AUTOCOMMIT = 0/1       |Enables/disables automatic commit of operations |

- **START TRANSACTION or BEGIN**: 
    ```
    START TRANSACTION;
    
    -- Deduct $150 from Account A
    UPDATE Accounts
    SET Balance = Balance - 150
    WHERE AccountID = 'A';

    -- Add $150 to Account B
    UPDATE Accounts
    SET Balance = Balance + 150
    WHERE AccountID = 'B';

    -- Commit the transaction if both operations succeed
    COMMIT;
    ```
- **COMMIT**: 
    ```
    DELETE FROM Student WHERE Age = 20;

    COMMIT;
    ```
- **ROLLBACK**:
    ```
    DELETE FROM Student WHERE AGE = 20;

    ROLLBACK;
    -- Delete those records from the table which have age = 20 and then ROLLBACK the changes in the database. In this case, the DELETE operation is undone, and the changes to the database are not saved.
    ```
- **SAVEPOINT and ROLLBACK TO SAVEPOINT**:
    ```
    SAVEPOINT SP1;
    -- Savepoint created.
    DELETE FROM Student WHERE AGE = 20;
    -- deleted
    SAVEPOINT SP2;
    -- Savepoint created.

    ROLLBACK TO SP1;
    //Rollback completed
    ```

### Autocommit

- **AUTOCOMMIT** is a database mode of operation in which each individual SQL statement is committed automatically upon execution, without the need to manually call COMMIT.

- **When AUTOCOMMIT is on**:
    - The DBMS automatically COMMITs changes after each query.
    - You can't ROLLBACK the result - it's already committed.
- **When  AUTOCOMMIT is off**:
    - Changes are saved temporarily (in a transaction) until you call COMMIT.
    - If something goes wrong, you can ROLLBACK.
    ```
    SET AUTOCOMMIT = 0;

    START TRANSACTION;

    INSERT INTO test 
    VALUES (2);
    ```

| SQL Commands                   | AUTOCOMMIT                           |
| -------------------------------|--------------------------------------|
| DML (INSERT, UPDATE, DELETE)   |Yes, if autocommit is on              |
| DDL (CREATE, DROP, ALTER)      |Yes, always, even if autocommit is off|
| DCL (GRANT, REVOKE)            |Yes, always                           |
| DQL (SELECT)                   |No                                    |