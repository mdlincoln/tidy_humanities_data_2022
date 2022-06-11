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

A wide nubmer of programs - desktop GUIs, command line, ad browser-based, can interact with SQLite files. We'll use <https://sqliteonline.com/> since it can easily read local files and has a good query editor and cheatsheet.

[SQL cheatsheet](https://www.sqltutorial.org/sql-cheat-sheet/)
[SQL functions](https://sqlite.org/lang_corefunc.html)

## Lesson data

[complex_knoedler.sqlite3](/assets/data/complex_knoedler.sqlite3)