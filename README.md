::: {align="center"}
# DBMS Lab

**Database Management Systems laboratory experiments: from data
modelling to query optimization, implemented in MySQL**

![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![SQL](https://img.shields.io/badge/Language-SQL-F29111?style=for-the-badge)
![Experiments](https://img.shields.io/badge/Experiments-10-2EA44F?style=for-the-badge)

[Experiments](#experiments) • [Repository
Structure](#repository-structure) • [Getting Started](#getting-started)
• [Databases Used](#databases-used) • [Concepts
Covered](#concepts-covered)
:::

------------------------------------------------------------------------

## About

This repository contains my **DBMS laboratory experiments**, covering
database design, SQL queries, database programming, transaction
management, and query optimization.

Each experiment is organized as a lab record (`Exp_N.md`) containing the
aim, theory, implementation, sample output, and result. Where
applicable, a separate SQL script is included so the experiment can be
reproduced in MySQL.

The repository uses **MySQL 8.0**. ER diagrams can be written in Mermaid
and rendered directly by GitHub.

------------------------------------------------------------------------

## Experiments

  --------------------------------------------------------------------------------------------------------------------------------------------------
        No.        Experiment                        Key Topics                                         Lab Record                SQL Script
  ---------------- --------------------------------- ------------------------------------------- ------------------------ --------------------------
       **1**       **ER Diagram: Indian E-Commerce   Entities, primary keys, composite and         [Exp_1.md](Exp_1.md)              ---
                   Platform**                        multi-valued attributes, weak entities,                              
                                                     Product specialization, participation                                
                                                     constraints                                                          

       **2**       **ER-to-Relational Mapping**      Relational schema, `CREATE TABLE`, primary    [Exp_2.md](Exp_2.md)     [Exp_2.sql](Exp_2.sql)
                                                     and foreign keys, `NOT NULL`, `UNIQUE`,                              
                                                     `ON DELETE CASCADE` / `SET NULL`, sample                             
                                                     data, referential integrity                                          

       **3**       **Employee--Department--Project   At least 30 employees, 5 departments, 8       [Exp_3.md](Exp_3.md)     [Exp_3.sql](Exp_3.sql)
                   Queries**                         projects; selection, projection,                                     
                                                     aggregates, `GROUP BY`, `HAVING`, `CASE`,                            
                                                     `ORDER BY`                                                           

       **4**       **Joins, Subqueries and EXPLAIN** `INNER JOIN`, `LEFT JOIN`, self-join, 3-way   [Exp_4.md](Exp_4.md)     [Exp_4.sql](Exp_4.sql)
                                                     join, correlated subqueries, `EXISTS`,                               
                                                     simulated `INTERSECT` / `EXCEPT`, execution                          
                                                     plans                                                                

       **5**       **Views and Recursive CTEs**      Department salary summary, employee           [Exp_5.md](Exp_5.md)     [Exp_5.sql](Exp_5.sql)
                                                     hierarchy, view updatability, recursive                              
                                                     reporting chains                                                     

       **6**       **Stored Procedures and           `transfer_employee(emp_id, new_dept_id)`,     [Exp_6.md](Exp_6.md)     [Exp_6.sql](Exp_6.sql)
                   Triggers**                        validation, error handling, salary                                   
                                                     validation, audit logging, edge cases                                

       **7**       **Normalization of Sales Data**   Functional dependencies, UNF, 1NF, 2NF,       [Exp_7.md](Exp_7.md)     [Exp_7.sql](Exp_7.sql)
                                                     3NF, BCNF, lossless join, dependency                                 
                                                     preservation                                                         

       **8**       **Transactions and Concurrency    `BEGIN`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`,   [Exp_8.md](Exp_8.md)     [Exp_8.sql](Exp_8.sql)
                   Control**                         partial failures, isolation levels,                                  
                                                     concurrency anomalies using two sessions                             

       **9**       **Railway Booking Index           At least 5,000 records, single and            [Exp_9.md](Exp_9.md)     [Exp_9.sql](Exp_9.sql)
                   Benchmarking**                    composite indexes, `EXPLAIN`,                                        
                                                     execution-plan and performance comparison                            

       **10**      **Query Optimization and          At least 10,000 rows, five slow queries,     [Exp_10.md](Exp_10.md)   [Exp_10.sql](Exp_10.sql)
                   Performance Analysis**            `EXPLAIN`, indexing, query rewriting,                                
                                                     before-and-after execution-time comparison                           
  --------------------------------------------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

## Repository Structure

``` text
DBMS-Lab/
│
├── README.md
│
├── Exp_1.md                    # E-commerce ER diagram
├── Exp_2.md                    # ER-to-relational mapping
├── Exp_3.md                    # Basic SQL queries
├── Exp_4.md                    # Joins, subqueries and EXPLAIN
├── Exp_5.md                    # Views and recursive CTEs
├── Exp_6.md                    # Stored procedures and triggers
├── Exp_7.md                    # Normalization
├── Exp_8.md                    # Transactions and concurrency
├── Exp_9.md                    # Railway booking index benchmark
├── Exp_10.md                   # Query optimization benchmark
│
├── Exp_2.sql                   # E-commerce schema and integrity tests
├── Exp_3.sql                   # Employee, department and project data/queries
├── Exp_4.sql                   # Joins and subqueries
├── Exp_5.sql                   # Views and recursive CTEs
├── Exp_6.sql                   # Procedure and trigger implementation
├── Exp_7.sql                   # Normalization examples and verification
├── Exp_8.sql                   # Transaction demonstrations
├── Exp_9.sql                   # Railway booking dataset and index tests
└── Exp_10.sql                  # Dataset, slow queries and optimizations
```

*The filenames above are a suggested organization. Adjust the links and
tree if your repository uses different filenames.*

------------------------------------------------------------------------

## Getting Started

### Prerequisites

-   **MySQL 8.0** or later
-   MySQL command-line client or **MySQL Workbench**
-   Git, if you want to clone the repository

### Clone the repository

Replace `<repository-name>` with the name of your GitHub repository.

``` bash
git clone https://github.com/priyanshi2807/<repository-name>.git
cd <repository-name>
```

### Run the experiments

Run each SQL script in MySQL Workbench or from the command line. For
example:

``` bash
mysql -u root -p < Exp_2.sql
mysql -u root -p < Exp_3.sql
```

Run the remaining scripts in the order required by their lab records.
Experiments that use an existing schema or dataset must be run after the
corresponding setup script.

> **Note:** Experiments 8--10 include transaction or performance tests.
> For meaningful results, follow the session, dataset, and measurement
> instructions in each experiment record. Execution times can vary with
> hardware, MySQL configuration, and server load.

------------------------------------------------------------------------

## Databases Used

### 1. `ecommerce_db`: Indian E-Commerce Platform (Experiments 1--2)

The e-commerce database models customers, products, sellers, categories,
orders, order items, payments, deliveries, and addresses.

``` mermaid
erDiagram
    CUSTOMER ||--o{ ORDERS : places
    CUSTOMER ||--o{ ADDRESS : has
    SELLER ||--o{ PRODUCT : sells
    CATEGORY ||--o{ PRODUCT : classifies
    ORDERS ||--|{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : appears_in
    ORDERS ||--o{ PAYMENT : has
    ORDERS ||--o{ DELIVERY : ships_as
```

The ER model identifies keys, composite and multi-valued attributes,
weak entities, Product specialization, and participation constraints.
Experiment 2 maps the model to relational tables and tests integrity
constraints.

### 2. `company_db`: Employee--Department--Project (Experiments 3--6)

The company database supports SQL querying, joins, views, recursive
CTEs, procedures, and triggers.

``` mermaid
erDiagram
    DEPARTMENT ||--o{ EMPLOYEE : employs
    EMPLOYEE o|--o{ EMPLOYEE : manages
    DEPARTMENT ||--o{ PROJECT : controls
    EMPLOYEE ||--o{ WORKS_ON : assigned_to
    PROJECT ||--o{ WORKS_ON : includes
```

The dataset contains at least 30 employees across 5 departments and 8
projects. The `WORKS_ON` relation represents employee-project
assignments; the employee self-reference represents reporting
relationships.

### 3. `sales_db`: Normalization (Experiment 7)

A denormalized Sales relation is analyzed through functional
dependencies and decomposed from UNF through 1NF, 2NF, and 3NF to BCNF.
SQL queries are used to examine the resulting relations and verify
lossless join and dependency preservation.

### 4. `banking_db`: Transactions (Experiment 8)

A banking-style dataset demonstrates transaction control, savepoints,
partial failures, isolation levels, and concurrency anomalies. Two
database sessions are used where required to observe concurrent
behavior.

### 5. `railway_db`: Indexing Benchmark (Experiment 9)

A Railway Booking table with at least 5,000 records is used to compare
query plans and performance before and after adding single-column and
composite indexes.

### 6. `optimization_db`: Query Optimization (Experiment 10)

A dataset with at least 10,000 rows is used to study five slow queries.
Each query is analyzed with `EXPLAIN`, then improved through indexing
and query rewriting, with execution times compared before and after
optimization.

------------------------------------------------------------------------

## Concepts Covered

### Data Modelling and Integrity

-   [x] ER diagrams, entities, attributes, and relationships
-   [x] Primary keys and foreign keys
-   [x] Composite and multi-valued attributes
-   [x] Weak entities and identifying relationships
-   [x] Specialization and participation constraints
-   [x] ER-to-relational mapping
-   [x] `NOT NULL`, `UNIQUE`, and referential integrity
-   [x] `ON DELETE CASCADE` and `ON DELETE SET NULL`

### SQL and Relational Queries

-   [x] Selection and projection
-   [x] Aggregate functions, `GROUP BY`, and `HAVING`
-   [x] `CASE` expressions and `ORDER BY`
-   [x] Inner, left, self, and multi-table joins
-   [x] Correlated subqueries and `EXISTS`
-   [x] Simulated `INTERSECT` and `EXCEPT`
-   [x] Views and view updatability
-   [x] Recursive CTEs

### Database Programming and Design

-   [x] Stored procedures and parameter validation
-   [x] Error handling and triggers
-   [x] Salary validation and audit logging
-   [x] Functional dependencies and normalization
-   [x] 1NF, 2NF, 3NF, and BCNF
-   [x] Lossless join and dependency preservation
-   [x] Transactions, savepoints, and rollback
-   [x] Isolation levels and concurrency anomalies

### Performance and Optimization

-   [x] Single-column and composite indexes
-   [x] `EXPLAIN` execution-plan analysis
-   [x] Query rewriting and index-based optimization
-   [x] Before-and-after execution-time benchmarking
-   [x] Dataset generation and performance comparison

------------------------------------------------------------------------

## Tools and Technologies

  -----------------------------------------------------------------------
  Tool                                Purpose
  ----------------------------------- -----------------------------------
  **MySQL 8.0**                       Database engine used for SQL
                                      implementation

  **MySQL Workbench / CLI**           Executing scripts and inspecting
                                      query results

  **Mermaid**                         Rendering ER diagrams in GitHub

  **Git and GitHub**                  Version control and hosting the lab
                                      records
  -----------------------------------------------------------------------

------------------------------------------------------------------------

::: {align="center"}
**Author:** [priyanshi2807](https://github.com/priyanshi2807)

*DBMS Laboratory --- Experiments 1--10*
:::
