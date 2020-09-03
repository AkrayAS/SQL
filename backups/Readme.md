## Backup Online

* It is less intrusive to other clients, who can connect to the MySQL server during the backup and may be able to access data, depending on what operations need to perform;

* Care must be taken to impose appropriate blocking so that data modifications do not occur in such a way as to compromise their integrity.

## Backup Offline

* Clients can be adversely affected, because the server is not is available during backup. For this reason, they are often taken from a parallel replication server that can be taken from the air without compromising availability;

* The backup process is simple, because there is no possibility of interference from customer activity.

## Create Backups

```
mysql\bin> mysqldump -u root -p
comercial > c:/bkp_tables_views.sql

mysql\bin> mysqldump -u root -p --routines --triggers
comercial > c:/bkp_full.sql

mysql\bin> mysqldump -u root -p comercial
comclien > c:/bkp_clien.sql

mysql\bin> mysqldump -u root -p --all-databases > c:/bkp_all.sql
```

## Import Backup

```
mysql> create database comercial2;

mysql\bin> mysql -h localhost -u root -p -d
comercial2 < c:/bkp_full.sql
```

