# 📚 Library Management System — Relational Database & SQL Analytics

An end-to-end relational database design and analytical SQL project simulating a real-world **Library Management System (LMS)**. This project demonstrates schema creation, referential integrity constraints, relational data modeling, and complex analytical SQL querying to derive actionable operational insights.

---

## 📌 Project Overview

The objective of this project is to build and manage a centralized database system for a library network to track:
- **Branch Operations & Staffing**: Tracking multi-branch employee assignments and operational hierarchies.
- **Inventory & Catalog Management**: Managing book availability, rental status, authors, publishers, and category pricing.
- **Customer Transactions & Circulation History**: Recording rental histories (`IssueStatus`, `ReturnStatus`) and monitoring customer rental habits.

---

## 🛠️ Tech Stack & Database Architecture

* **Database Engine**: MySQL 8.0+ / Relational DBMS
* **SQL Concepts & Techniques**:
  * **DDL (Data Definition Language)**: `CREATE TABLE`, `PRIMARY KEY`, `FOREIGN KEY`, `REFERENCES`, `ON DELETE CASCADE / SET NULL`
  * **DML (Data Manipulation Language)**: `INSERT INTO`, data type validation
  * **Relational Joins**: `INNER JOIN`, `LEFT JOIN` across transactional and master tables
  * **Aggregations & Grouping**: `COUNT()`, `SUM()`, `AVG()`, `GROUP BY`, `HAVING`
  * **Subqueries & Filtering**: Multi-condition `WHERE`, Subqueries with `IN` / relational constraints

---

## 🗂️ Relational Schema Design

The database schema (`library`) contains 6 interconnected relational tables:

┌──────────────┐
              │    Branch    │
              └──────┬───────┘
                     │ 1:N
                     ▼
┌──────────────┐  1:N   ┌──────────────┐
│   Customer   │◄───────┤   Employee   │
└──────┬───────┘        └──────────────┘
│ 1:N
▼
┌──────────────┐  N:1   ┌──────────────┐
│ IssueStatus  │───────►│    Books     │
└──────┬───────┘        └──────┬───────┘
│ 1:1                   │ 1:1
▼                       ▼
┌──────────────┐        ┌──────────────┐
│ ReturnStatus │        │ Rental Price │
└──────────────┘        └──────────────┘

### Table Breakdown:
1. **`Branch`**: Stores branch identifiers, manager IDs, branch addresses, and contact numbers.
2. **`Employee`**: Records staff details, designations, salaries, and branch allocations.
3. **`Books`**: Master catalog storing ISBNs, book titles, categories, rental prices, availability status (`yes`/`no`), authors, and publishers.
4. **`Customer`**: Holds registered member profiles and registration dates.
5. **`IssueStatus`**: Captures active book issuance, customer-book transactions, and issue dates.
6. **`ReturnStatus`**: Logs returned books, return timestamps, and links back to the original book record.

---

## 🔍 Key Analytical Queries & Business Problems Solved

This repository includes SQL queries designed to solve operational circulation problems:

1. **Catalog Availability Tracking**: Querying all currently available books (`Status = 'yes'`) across titles, categories, and authors.
2. **Payroll & Staff Distribution**: Calculating total salary expenditures by designation and identifying branches with high staffing tiers (> 5 employees).
3. **Customer Circulation History**: Identifying members registered before specific dates who have active or past book checkout histories.
4. **High-Value Catalog Analysis**: Identifying books with rental prices exceeding threshold values ($6.00+) and segmenting books by rental frequency.
5. **Multi-Table Transaction Reports**: Generating consolidated reports combining Customer Name, Book Title, and Issue Date using `JOIN` operations.
6. **Category-Wise Distribution**: Aggregating total book counts categorized by genre/subject matter.
7. **Cross-Branch Staff Inquiries**: Isolating and analyzing branch operational teams and designated branch managers.

---

## 🚀 Getting Started / How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/ashilbrayan/E-Commerce-Customer-Churn-Retention-Analysis-SQL-.git](https://github.com/ashilbrayan/E-Commerce-Customer-Churn-Retention-Analysis-SQL-.git)
   cd E-Commerce-Customer-Churn-Retention-Analysis-SQL-
