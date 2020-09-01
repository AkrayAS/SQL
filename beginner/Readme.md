# Starting a Project

## Creating the first Database

* Create a new user for the mysql, like the good software development practices advise the creation of users other than root for accessing databases and for use by applications.
    * mysql> create user usermysql@'%' identified by 'cursomysql';

* Grant or revoke acess to a user:
    * mysql> grant all privileges on *.* to usermysql@'%' with grant option;
    * mysql> revoke all on *.* from usermysql;

### Access Control

> When we work with software development, there is a need to give access to a person or application in the database. In order not to grant full access, you use user rights to make this limitation.

* Global Level
    * mysql> grant all on *.* to usermysql@localhost;
    * mysql> revoke all on *.* from usermysql;

* Database Level
    * mysql> grant all to comercial.* to usermysql@localhost;
    * mysql> revoke all on comercial.*;

* Table Level
    * mysql> grant all on comercial.nome_tabela;
    * mysql> revoke all on comercial.nome_tabela;

* Collum Level
    * mysql>grant select(nomecoluna1), insert(nomecoluna1), update(nomecoluna1) on comercial.nome_tabela to usermysql@localhost identified by senha;

* Stored routine Level
    * mysql> grant routine on comercial.* to usermysql@localhost; (For Routines)
    * ysql> grant execute on procedure comercial.nomeprocedure to usermysql@localhost; (For procedures)

* Proxy User Level
    * mysql> grant PROXY on usermysql@localhost to 'usuarioexterno'@'hostexterno';    

### Project Requirements

A system for sales of products. (Exemple to made during the learning of SQL)

## Standardization of table names

* A relation between the system and with what she will refer to.

## Standardization of field names

The letter identifying the type of the field is the initial letter of the type name:

* C_: for a character type field;
* D_: for date type field;
* N_: for numeric type field;
* B_: for blob type field.

## Text Types

CHAR, VARCHAR, TEXT, BLOB

## Number Types

TINYINT, SMALLINT, MEDIUMINT, INT, BIGINIT, FLOAT, DOUBLE.

## DATE/TIME TYPES

DATE(), DATETIME(), TIME().