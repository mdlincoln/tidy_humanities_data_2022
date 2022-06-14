---
title: Intro to SQL
date: 2022-06-14
description: |
  Intro to SQL: turning a data design into reality
---

SQL (Structured Query Language) is a method for writing queries for tabular data that is commonly used across a wide array of databases. While each database software (from MySQL to PostgreSQL to SQLite to Oracle) has its own extensions to the language, we will be looking at the core functions that you will generally be able to apply to almost any database.

Likewise if you query data in programming languages like Python's `pandas` or R's `dplyr`, you will see very similar concepts to the ones we'll learn here.

## SQLite

[SQLite](https://sqlite.org/index.html) is an extremely widely-used database software and format. It's special because unlike MySQL, PostgreSQL, or other databases that run as a separate ongoing process on your machine or on a remote server, SQLite sits as a single self-contianed file in your filesystem. It is a great way to explore SQL and relational database creation because there is virtually no software setup involved.

A wide nubmer of programs - desktop GUIs, command line, ad browser-based, can interact with SQLite files.

This tutorial will focus first on using sqlite for data quering and analysis, and only secondarily on using it for data entry and editing.
We will not be going over key database concepts such as indices and transactions.
These are very important features, but because they relate more towards programming database-backed applications and issues of performance optimization, they are out of scope for this introductory lesson.

## Quick references

- [SQL cheatsheet](https://www.sqltutorial.org/sql-cheat-sheet/)
- [SQL core functions](https://sqlite.org/lang_corefunc.html) - used inside `SELECT` statements to modify the data on the fly, such as modifying strings.
- [SQLite aggregation functions](https://www.sqlite.org/lang_aggfunc.html) - used with `SELECT ... GROUP BY` statements to aggregate multiple values into one based on grouping.
- [SQLite date and time functions](https://www.sqlite.org/lang_datefunc.html)
## Getting started

Navigate to <https://sqliteonline.com>. This website uses an implementation of SQLite that runs entirely in your internet browser (like Palladio), so your data does not leave your computer. It also provides a query editor with affordances like autocompletion and formatting, and a query result dispay that provides a nicely-formatted table.

Download the lesson data to your computer: [normalized_knoedler.sqlite3]({{ site.baseurl}}assets/data/normalized_knoedler.sqlite3)

In the sqliteonline menubar, select File -> Open DB, and select the `normalized_knoedler.sqlite3` file you just downloaded. (N.B. sqlite files have a bunch of possible file extensions, but you'll often see `.db`, `.sqlite`, and `.sqlite3`, the latter noting that the file was made with the most recent major version of SQLite available from 2004)

This file contains the exact same information as we used in the Palladio lesson, but arranged according to a different database schema:

1. `sales`
2. `artists`
   1. join table between `sales` and `artists`
3. `collectors`
   1. join table between `sales.sellers` and `collectors`
   2. join table between `sales.buyers` and `collectors`

## SELECT, INSERT/UPDATE, JOINS

Together, we will walk through:

1. Getting all data from a table
2. Getting select columns from a table
3. Getting select rows from a table
4. Limiting/skipping results
5. Computing new columns based on existing ones
   1. Arithmetic
   2. String concatenation with `||`
   3. `CASE WHEN`
   4. `COALESCE`
   5. Dealing with dates - `date()` and `julianday()`
6. Wildcard searching with `LIKE/ILIKE`
7. `UNION` and `INTERSECT` queries
8. Aggregation with `GROUP BY`
   1. `COUNT`
   2. `SUM`, `AVG`, `MIN`, `MAX`
   3. `group_concat(x, sep)`


## Creating tables and constraints

1. `CREATE TABLE`
2. Specifying columns / attributes
   1. `PRIMARY KEY`
   2. `TEXT / INT / FLOAT`
   3. `UNIQUE`
   4. `NOT NULL`
   5. `DEFAULT`
3. `INSERT` data with `VALUES`
5. `FOREIGN KEY` (run `PRAGMA foreign_keys = ON;` first!)
6. `CHECK` constraints on columns and tables
   1. Checking for valid dates with `CHECK (datecol IS date(datecol))`
7. Compound `UNIQUE`
8. Running bulk `UPDATE`

## Compound queries
1. Storing queries with `VIEW`s
2. Common Table Expressions (`WITH inter_tbl AS (SELECT ...) SELECT ... FROM inter_tbl...`)

## More software

Create tables and then import from CSVs:

https://sqlitebrowser.org/
