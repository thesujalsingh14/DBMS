<div align="center">

# DBMS Lab

**Database Management Systems laboratory experiments: from ER modelling to query optimization, implemented in MySQL**

![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![SQL](https://img.shields.io/badge/Language-SQL-F29111?style=for-the-badge)
![Experiments](https://img.shields.io/badge/Experiments-10-2EA44F?style=for-the-badge)

[Experiments](#experiments) •
[Repository Structure](#repository-structure) •
[Getting Started](#getting-started) •
[Databases Used](#databases-used) •
[Concepts Covered](#concepts-covered)

</div>

---

## About

This repository contains my **DBMS lab experiments**, covering database design, SQL programming, transaction management, normalization, indexing, and query optimization.

Each experiment is organized as a lab record containing the aim, theory, implementation, sample data or queries, output, and result. SQL scripts can be added alongside the records to reproduce the implementation.

The experiments are designed for **MySQL 8.0**. Execution plans and benchmark timings depend on the MySQL version, machine, dataset, and database configuration; record actual results from your own runs rather than treating example timings as universal.

---

## Experiments

| No. | Experiment | Key Topics | Lab Record | SQL Script |
|:---:|---|---|:---:|:---:|
| **1** | **ER Diagram: Indian E-Commerce Platform** | Entities, primary keys, composite and multi-valued attributes, weak entities, Product specialization, participation constraints | [Exp_1.md](Exp_1.md) | — |
| **2** | **ER-to-Relational Schema** | MySQL `CREATE TABLE`, primary and foreign keys, `NOT NULL`, `UNIQUE`, `ON DELETE CASCADE / SET NULL`, sample data, referential integrity | [Exp_2.md](Exp_2.md) | [ecommerce_schema.sql](ecommerce_schema.sql) |
| **3** | **Employee–Department–Project Queries** | Selection, projection, aggregates, `GROUP BY`, `HAVING`, `CASE`, `ORDER BY`; at least 30 employees, 5 departments and 8 projects | [Exp_3.md](Exp_3.md) | [employee_queries.sql](employee_queries.sql) |
| **4** | **Joins, Subqueries and EXPLAIN** | `INNER JOIN`, `LEFT JOIN`, self-join, 3-way join, correlated subqueries, `EXISTS`, simulated `INTERSECT` / `EXCEPT`, execution plans | [Exp_4.md](Exp_4.md) | [joins_subqueries.sql](joins_subqueries.sql) |
| **5** | **Views and Recursive CTEs** | Department salary summary, employee hierarchy, view updatability, recursive reporting chains | [Exp_5.md](Exp_5.md) | [views_recursive_cte.sql](views_recursive_cte.sql) |
| **6** | **Stored Procedures and Triggers** | `transfer_employee(emp_id, new_dept_id)`, validation, error handling, salary validation, audit logging, edge-case testing | [Exp_6.md](Exp_6.md) | [procedures_triggers.sql](procedures_triggers.sql) |
| **7** | **Normalization: UNF to BCNF** | Functional dependencies, UNF, 1NF, 2NF, 3NF, BCNF, lossless join and dependency preservation | [Exp_7.md](Exp_7.md) | [normalization.sql](normalization.sql) |
| **8** | **Transactions and Concurrency** | `BEGIN`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`, partial failures, isolation levels and concurrency anomalies using two sessions | [Exp_8.md](Exp_8.md) | [transactions_concurrency.sql](transactions_concurrency.sql) |
| **9** | **Railway Booking Index Benchmark** | At least 5,000 records, single and composite indexes, query timing, `EXPLAIN` plan comparison | [Exp_9.md](Exp_9.md) | [railway_benchmark.sql](railway_benchmark.sql) |
| **10** | **Query Optimization and Benchmarking** | At least 10,000 rows, five slow queries, `EXPLAIN`, indexing, query rewriting, before-and-after performance comparison | [Exp_10.md](Exp_10.md) | [query_optimization.sql](query_optimization.sql) |

---

## Repository Structure

```text
DBMS-Lab/
│
├── README.md
│
├── Exp_1.md
├── Exp_2.md
├── Exp_3.md
├── Exp_4.md
├── Exp_5.md
├── Exp_6.md
├── Exp_7.md
├── Exp_8.md
├── Exp_9.md
├── Exp_10.md
│
├── ecommerce_schema.sql
├── employee_queries.sql
├── joins_subqueries.sql
├── views_recursive_cte.sql
├── procedures_triggers.sql
├── normalization.sql
├── transactions_concurrency.sql
├── railway_benchmark.sql
└── query_optimization.sql
```

> The filenames above are a suggested organization for the lab records and scripts. Keep the links and filenames in this README aligned with the files actually present in the repository.

---

## Getting Started

### Prerequisites

- **MySQL 8.0** (MySQL 8.0.16 or later is recommended for enforced `CHECK` constraints).
- MySQL command-line client or **MySQL Workbench**.
- Git, if cloning the repository.

### Clone the repository

```bash
git clone https://github.com/thesujalsingh14/<repository-name>.git
cd <repository-name>
```

Replace `<repository-name>` with the actual GitHub repository name.

### Run the experiments

Run each SQL script in MySQL Workbench or from the command line. For example:

```bash
mysql -u root -p < ecommerce_schema.sql
mysql -u root -p < employee_queries.sql
mysql -u root -p < joins_subqueries.sql
mysql -u root -p < views_recursive_cte.sql
mysql -u root -p < procedures_triggers.sql
mysql -u root -p < normalization.sql
mysql -u root -p < transactions_concurrency.sql
mysql -u root -p < railway_benchmark.sql
mysql -u root -p < query_optimization.sql
```

Run the Employee–Department–Project setup before Experiments 4, 5 and 6, since those experiments use the employee schema. Experiments 1 and 2 cover the e-commerce design and implementation. Follow each lab record for any additional setup or execution order.

> [!NOTE]
> Some experiments intentionally attempt invalid operations to demonstrate constraint violations or error handling. Run those tests deliberately and inspect the expected errors. Use a test database, especially for transaction, trigger, and performance experiments.

---

## Databases Used

### 1. Indian E-Commerce Platform (Experiments 1–2)

The conceptual design includes the following entities:

- **Customer**, **Address**, **Order**, **OrderItem**
- **Product**, **Seller**, **Category**
- **Payment**, **Delivery**

The ER model identifies primary keys, composite and multi-valued attributes, weak entities, Product specialization, and participation constraints. The relational implementation maps the design to MySQL tables and demonstrates key constraints and referential integrity.

### 2. Employee–Department–Project (Experiments 3–6)

The company database supports SQL queries, joins, views, recursive reporting relationships, stored procedures, and triggers.

| Table / concept | Required data or purpose |
|---|---|
| `employee` | At least 30 employees; includes department and reporting relationships |
| `department` | 5 departments |
| `project` | 8 projects |
| Employee–project assignments | Supports joins and project-related queries |

### 3. Sales, Banking and Performance Datasets (Experiments 7–10)

| Experiment | Dataset / focus |
|---|---|
| **7** | Denormalized Sales data used to identify dependencies and normalize through BCNF |
| **8** | Banking-style account transactions used to demonstrate transaction control and concurrency |
| **9** | Railway Booking table with at least 5,000 records for index benchmarking |
| **10** | Dataset with at least 10,000 rows for slow-query analysis and optimization |

---

## Concepts Covered

### Data Modelling and Integrity

- [x] ER diagrams, entities, attributes and relationships
- [x] Primary keys, composite and multi-valued attributes
- [x] Weak entities and Product specialization
- [x] Participation constraints and ER-to-relational mapping
- [x] Foreign keys, `NOT NULL`, `UNIQUE` and referential integrity
- [x] `ON DELETE CASCADE` and `ON DELETE SET NULL`

### SQL and Relational Queries

- [x] Selection, projection, sorting and aggregate functions
- [x] `GROUP BY`, `HAVING` and `CASE`
- [x] Inner, left, self and multi-table joins
- [x] Correlated subqueries and `EXISTS`
- [x] Simulated `INTERSECT` and `EXCEPT`
- [x] Views, view updatability and recursive CTEs

### Database Programming and Transactions

- [x] Stored procedures and parameter validation
- [x] Error handling and triggers
- [x] Salary validation and audit logging
- [x] `BEGIN`, `COMMIT`, `ROLLBACK` and `SAVEPOINT`
- [x] Isolation levels and concurrency anomalies
- [x] Functional dependencies and normalization from UNF to BCNF
- [x] Lossless join and dependency preservation

### Indexing and Query Optimization

- [x] Single-column and composite indexes
- [x] `EXPLAIN` execution-plan analysis
- [x] Slow-query identification and query rewriting
- [x] Before-and-after execution-time benchmarking
- [x] Railway booking and large-dataset performance testing

---

## Tools and Technologies

| Tool | Purpose |
|---|---|
| **MySQL 8.0** | Database implementation and query execution |
| **MySQL Workbench / CLI** | Running SQL scripts and viewing results |
| **Git and GitHub** | Version control and hosting lab records |

---

<div align="center">

**Author:** [thesujalsingh14](https://github.com/thesujalsingh14)

*If you find this repository helpful, consider giving it a star.*

</div>
