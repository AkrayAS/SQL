Exercises on Data Manipulation Language (DML) & Data Definition Language (DDL)

1) Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id.

```MySQL
mysql> create table countries(
    -> country_id varchar(2),
    -> country_name varchar(50),
    -> region_id decimal(10,0));
```
2) Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id which is already exists. 

```MySQL
mysql> create table if not exists countries(
    -> country_id varchar(2),
    -> country_name varchar(40),
    -> region_id decimal(10,0));
```

3) Write a SQL statement to create the structure of a table dup_countries similar to countries.

```MySQL
mysql> create table if not exists dup_countries 
    -> like countries;
```

4) Write a SQL statement to create a duplicate copy of countries table including structure and data by name dup_countries.

```MySQL
mysql> create table if not exists dup_countries
    -> as select * from countries;
```

5) Write a SQL statement to create a table countries set a constraint NULL.

```MySQL
mysql> create table if not exists countries(
    -> country_id varchar(2) not null,
    -> country_name varchar(50) not null,
    -> region_id decimal(10,0) not null);
```
