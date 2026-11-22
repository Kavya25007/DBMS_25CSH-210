# DBMS Lab – 25CSH-210

Database Management Systems (DBMS) lab experiments, implemented in **MySQL**.
Each experiment folder contains the full SQL code, a queries-only file, and (for some experiments) the recorded output.

**Student:** Kavya Kushwaha

---

## 📁 Repository Structure

```
DBMS_25CSH-210/
├── Experiment_1.pdf                 # ER diagram (handwritten)
├── Experiment_2.pdf                 # ER → relational schema (handwritten)
├── Experiment_3/                    # Aggregates, GROUP BY, joins
├── Experiment_4/                    # Joins, subqueries, EXISTS, EXPLAIN
├── Experiment_5/                    # Views & recursive CTE
├── Experiment_6/                    # Stored procedure & triggers
├── Experiment_7/                    # Normalization (UNF → BCNF)
├── Experiment_8/                    # Transactions & isolation levels
├── Experiment_9/                    # Indexing on 5,000 records
├── Experiment_10/                   # Query optimization
├── sql_basic certificate.pdf        # SQL Basic certificate
└── f049200a-...pdf                  # SQL Developer certificate
```

In each experiment folder:

| File | Contents |
|------|----------|
| `Experiment_N.Code` | Complete script – table creation, data insertion and queries |
| `Experiment_N.Queries` / `.Queries.txt` | Only the queries (assumes the tables already exist) |
| `Experiment_N.Ouput.csv` | Recorded output (Experiments 3 and 4) |

---

## 🧪 Experiments Overview

| # | Topic | Aim | Key Concepts |
|---|-------|-----|--------------|
| 1 | ER Diagram | Design an ER diagram for an Indian e-commerce platform with entities Customer, Product, Order, OrderItem, Seller, Category, Payment, Delivery and Address | Entities, attributes, relationships, cardinality |
| 2 | Relational Schema | Convert the ER diagram into a relational schema and implement it with `CREATE TABLE` | Primary keys, foreign keys, `NOT NULL`, `UNIQUE`, `ON DELETE CASCADE`, `ON DELETE SET NULL` |
| 3 | Basic Queries | Create the `Department`, `Project` and `Employee` tables and run basic analytical queries | `WHERE`, aggregate functions (`COUNT`, `AVG`, `MAX`, `MIN`, `SUM`), `GROUP BY`, `HAVING`, `CASE`, `ORDER BY`, `JOIN` |
| 4 | Joins & Subqueries | Demonstrate joins, subqueries, `EXISTS`, simulated `INTERSECT` / `EXCEPT`, and `EXPLAIN` | Selection, projection, inner/outer joins, nested queries, query plans |
| 5 | Views & Recursive CTE | Create views for department salary summary and employee hierarchy, test view updatability, and display reporting chains | `CREATE VIEW`, updatable views, self join, `WITH RECURSIVE` |
| 6 | Procedures & Triggers | Stored procedure for employee transfer, salary-validation triggers, and an audit log | `CREATE PROCEDURE`, `SIGNAL`, `BEFORE INSERT/UPDATE` triggers, audit table |
| 7 | Normalization | Find functional dependencies in a denormalized `Sales` table and normalize it from UNF to 1NF, 2NF, 3NF and BCNF | Functional dependencies, lossless join, dependency preservation |
| 8 | Transactions | Demonstrate transaction control, savepoints, rollback and isolation levels on a banking database | `START TRANSACTION`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`, non-repeatable read vs repeatable read, isolation levels |
| 9 | Indexing | Create 5,000 railway booking records and benchmark single-column and composite indexes | `CREATE INDEX`, composite index, `SHOW INDEX`, `EXPLAIN ANALYZE` |
| 10 | Query Optimization | Identify slow queries on a sales analytics table and optimize them using indexes and query rewriting | Index design, sargable predicates, `EXPLAIN` before vs after |

---

## 🗃️ Databases Used

| Experiment(s) | Database | Main Tables |
|---------------|----------|-------------|
| 3, 4, 5, 6 | `DBMS_Experiment3` | `Department`, `Project`, `Employee`, `Employee_Audit` |
| 7 | `DBMS_Experiments` | `Sales_UNF`, `Sales_Order`, `Sales_OrderLine`, `Sales_Product`, `Sales_Customer`, `Sales_Salesperson` |
| 8 | `BankingDB` | `Bank_Account`, `Bank_Transactions` |
| 9 | `RailwayDB` | `Railway_Booking` |
| 10 | `QueryOptimizationDB` | `Sales_Analytics` |

---

## ⚙️ Requirements

- **MySQL 8.0 or above** (needed for recursive CTEs and `EXPLAIN ANALYZE`, which requires 8.0.18+)
- MySQL Workbench, the MySQL command-line client, or any compatible SQL client

---

## ▶️ How to Run

1. Clone or download this repository.
2. Open the SQL client and connect to your MySQL server.
3. Open `Experiment_N/Experiment_N.Code` and run the whole script.  
   It creates the database and tables, inserts the data and runs the queries.
4. To run only the queries, use `Experiment_N.Queries` – make sure the tables from the `.Code` file already exist.

Command-line example:

```bash
mysql -u root -p < Experiment_3/Experiment_3.Code
```

> **Order matters for Experiments 3–6.** They share the `DBMS_Experiment3` database, so run Experiment 3 first and continue in order.

---

## 📝 Notes

- Experiment 5 uses an `Employee.Manager_ID` column (for the hierarchy view and the recursive CTE). Make sure this column exists in the `Employee` table before running it.
- In Experiment 5, the `UPDATE` on the view is meant to be executed **only once**, otherwise the salary keeps increasing.
- In Experiment 6, the test calls that produce errors (invalid employee, department or salary) are commented out in the queries file; uncomment them one at a time to see the expected error messages.
- In Experiment 8, the non-repeatable-read and repeatable-read tests need **two separate MySQL sessions** open at the same time.
- Experiment 9 generates the 5,000 rows with a recursive CTE, so `cte_max_recursion_depth` is raised to 6000 inside the script.

---

## 🏅 Certifications

- SQL Basic – certificate included in this repository
- SQL Developer (Wingspan) – completed November 2026

---

## 🛠️ Tech Stack

![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?logo=mysql&logoColor=white)
![SQL](https://img.shields.io/badge/Language-SQL-orange)
