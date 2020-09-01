## Creating Tables

* create table "table_name"();

```
create table comclien(
n_numeclien int not null auto_increment,
c_codiclien varchar(10),
c_nomeclien varchar(100),
c_razaclien varchar(100),
d_dataclien date,
c_cnpjclien varchar(20),
c_foneclien varchar(20),
primary key (n_numeclien));
```

## Describe Table

* desc "table_name";

## Modify, Alter and Drop Table.

modify, alter drop.

## Insert Registers

insert into "table_name"();S
```
insert into comclien(n_numeclien,
c_codiclien,
c_nomeclien,
c_razaclien,
d_dataclien,
c_cnpjclien,
c_foneclien,
c_cidaclien,
c_estaclien)
values (1,
'0001',
'AARONSON',
'AARONSON FURNITURE LTDA',
'2015-02-17',
'17.807.928/0001-85',
'(21) 8167-6584',
'QUEIMADOS',
'RJ');
```

## Changing Registers

```
update comclien set c_nomeclien = 'AARONSON FURNITURE'
where n_numeclien = 1;

commit;
```

* rollback;

## Delete Registers

```
delete from comclien
where n_numeclien = 1;

commit;
```

* truncate table comclien;

