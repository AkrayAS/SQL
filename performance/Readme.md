## Index

```
mysql> create table comclien(
n_numeclien int not null auto_increment,
c_codiclien varchar(10),
c_nomeclien varchar(200),
c_razaclien varchar(200),
d_dataclien date,
c_cnpjclien varchar(15),
c_foneclien varchar(15),
primary key (n_numeclien),
index idx_comclien_2(c_codiclien));
```

```
mysql> alter table comclien add
index idx_comclien_3(c_razaclien);
mysql> alter table comclien add
index idx_comclien_4(c_codiclien);
```

* mysql> show indexes from comclien;

#### Unique Index

* mysql> alter table comvenda add unique index idx_comvenda_1(c_codivenda);

* mysql> alter table comvenda drop index idx_comvenda_1;

## Views

* A view can be used, for example, to return a value of only one column in the table;

* Also to promote restrictions on data to increase its security and define access policies at the table and column level;

* Can be configured to show different columns for different database users;

* Can also be used with a set of tables joined to other sets of tables using joins.

```
mysql> create or replace view clientes_vendas as
select c_razaclien,
c_nomeclien,
c_cnpjclien,
c_codivenda,
n_totavenda,
d_datavenda
from comclien,
comvenda
where comclien.n_numeclien = comvenda.n_numeclien
order by 1;
```

* mysql> select * from clientes_vendas;