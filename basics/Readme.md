# SQL Basics

## Structered Query Language (SQL)

> SQL is a language used for interacting with Relational Database Management Systems (RDBMS)

SQL can be used to get the RDBMS to do:

* Create, retrieve, update and delete data

* Create and manage databases

* Design & create databases tables

* Perform administration tasks

SQL is actually a hybrid language, it's basically 4 types of language in one:

* Data Query Language (DQL)
   * Used to query the database for information.
   * Get information that is already stored there.

* Data Definition Language (DDL)
   * Used for defining database schemas.
   * Commands: CREATE_TABLE, CREATE_INDEX, ALTER_TABLE, DROP_TABLE, DROP_VIEW and DROP_INDEX.

* Data Control Language (DCL)
    * Used for controlling access to the data in the database.
    * User and permission management.
    * Commands: COMMIT, ROLLBACK, GRANT and REVOKE.

* Data Manipulation Language (DML)
    * Used for inserting, updating and deleting data from the database.
    * Commands: INSERT, DELETE, UPDATE, SELECT and LOCK.

## Queries

> A query is a set of instructions given to the RDBMS (written is SQL) that tell the RDBMS what information you want it to retrieve for you.

## Getting started with MySQL

Download: https://dev.mysql.com/downloads/mysql/

### Linux Configuration (Ubuntu)

* $> sudo apt-get update

* $> sudo apt-get install mysql-server

* $> sudo mysql -u root -p