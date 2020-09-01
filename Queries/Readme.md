## Basic Queries

* mysql> select * from comclien;

* mysql> select n_numeclien, c_codivenda, c_razaclien from comclien;

* mysql> select n_numeclien, c_codiclien, c_razaclien from comclien where c_codiclien = '0001';

* mysql> select n_numeclien, c_codiclien, c_razaclien from comclien where c_razaclien like 'L%';

## Distinct()

* mysql> select distinct n_numeclien from comvenda;

## Subquery

alternative for joins

#### in, not in, exists e not exists

* mysql> select c_codiclien, c_razaclien from comclien where n_numeclien in (1,2);

* mysql> select c_codiclien, c_razaclien from comclien where n_numeclien not in (1,2);

* mysql> select c_razaclien from comclien where n_numeclien in (select n_numeclien from comvenda where n_numeclien);

#### "Nicknames"

* myql> select c_codiclien CODIGO, c_nomeclien CLIENTE from comclien where n_numeclien not in(1,2,3,4);

## Joins

* mysql> select c_codiclien, c_razaclien, c_codivenda Cod_Venda from comvenda, comclien where comvenda.n_numeclien = comclien.n_numeclien order by c_razaclien;

