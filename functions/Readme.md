## Agregation Function

* group by

* count() - count the queries that are grouped

```
mysql> select c_codiclien, c_razaclien, count(n_numevenda) Qtde
from comclien, comvenda
where comvenda.n_numeclien = comclien.n_numeclien
group by c_codiclien, c_razaclien
order by c_razaclien;
```

## Having count()

```
mysql> select c_razaclien, count(n_numevenda)
from comclien, comvenda
where comvenda.n_numeclien = comclien.n_numeclien
group by c_razaclien
having count(n_numevenda) > 2;
```

## Max() & Min()

```
mysql> select max(n_totavenda) maior_venda
from comvenda;
```

```
mysql> select min(n_totavenda) menor_venda, max(n_totavenda)
maior_venda from comvenda;
```

```
mysql> select min(n_totavenda) menor_venda, max(n_totavenda)
maior_venda from comvenda;
```

## Sum()

```
mysql> select sum(n_valovenda) valor_venda,
sum(n_descvenda) descontos,
sum(n_totavenda) total_venda
from comvenda
where d_datavenda between '2015-01-01' and '2015-01-01';
```

## Avg()

```
mysql> select format(avg(n_totavenda),2)
from comvenda;
```

## substr() & length()

```
mysql> select c_codiprodu, c_descprodu
from comprodu
where substr(c_codiprodu,1,3) = '123'
and length(c_codiprodu) > 4;
```

```
mysql> select substr(c_razaclien,1,5) Razao_Social,
length(c_codiprodu) Tamanho_Cod
from comclien
where n_numeclien = 1;
```

## Concat() e concat_ws()

```
mysql> select concat(c_razaforne,' - fone: ', c_foneforne)
from comforne
order by c_razaforne;
```

```
mysql> select
concat_ws(';',c_codiclien, c_razaclien, c_nomeclien)
from comclien
where c_razaclien like 'GREA%';
```

## Lcase() e lower()

```
mysql> select lcase(c_razaclien)
from comclien;
```

## Ucase()

```
mysql> select ucase('banco de dados mysql')
from dual;
```

## Round()

```
mysql> select round('213.142',2)
from dual;
```

```
mysql> select format('21123.142',2) from dual;
```

## Truncate

```
mysql> select truncate(max(n_totavenda),0) maior_venda
from comvenda;
```
