## Triggers

* Check data integrity, as it is possible to perform a verification before inserting the record;

* Work around errors in the system's business rule in the database;

* Use as a substitute for event_scheduler. However, it does not replaces it in processes that are not triggered from a table;

* Audit the changes in the tables.

## Triggers before insert & before update

```
mysql> delimiter $$
mysql> create function rt_percentual_comissao(vn_n_numevende int)
returns float
deterministic
begin
declare percentual_comissao float(10,2);
select n_porcvende
into percentual_comissao
from convende
where n_numevende = vn_n_numevende;
return percentual_comissao;
end;
mysql> $$
mysql> delimiter ;

mysql> delimiter $$
mysql> create trigger tri_vendas_bi
before insert on comvenda
for each row
begin
declare percentual_comissao float(10,2);
## busco o percentual de comissão que o vendedor deve
## receber
select rt_percentual_comissao(new.n_numevende)
into percentual_comissao;
## calculo a comissão
set valor_comissao = ((total_venda * comissao) / 100);
## recebo no novo valor de comissão
set new.n_vcomvenda = valor_comissao;
end
mysql> $$
mysql> delimiter ;
```

## Triggers after insert & after update

```
mysql> delimiter $$
mysql> create trigger tri_vendas_ai
after insert on comivenda
for each row
begin
## declaro as variáveis que utilizarei
declare vtotal_itens float(10,2);
declare vtotal_item float(10,2);
declare total_item float(10,2);
## cursor para buscar os itens já registrados da venda
declare busca_itens cursor for
select n_totaivenda
from comivenda
where n_numevenda = new.n_numevenda;
## abro o cursor
open busca_itens;
## declaro e inicio o loop
itens : loop
fetch busca_itens into total_item;
## somo o valor total dos itens(produtos)
set vtotal_itens = vtotal_itens + total_item;
end loop itens;

close busca_itens;
## atualizo o total da venda
update comvenda set n_totavenda = vtotal_itens
where n_numevenda = new.n_numevenda;
end
mysql> $$
mysql> delimiter ;
```

## Triggers before delete & after delete

```
mysql> delimiter $$
mysql> create trigger tri_ivendas_af
after delete on comivenda
for each row
begin
## declaro as variáveis que utilizarei
declare vtotal_itens float(10,2);
declare vtotal_item float(10,2);
declare total_item float(10,2);

## cursor para buscar os itens já registrados da venda
declare busca_itens cursor for
select n_totaivenda
from comivenda
where n_numevenda = old.n_numevenda;
## abro o cursor
open busca_itens;
## declaro e inicio o loop
itens : loop
fetch busca_itens into total_item;
## somo o valor total dos itens(produtos)
set vtotal_itens = vtotal_itens + total_item;
end loop itens;
close busca_itens;
## atualizo o total da venda
update comvenda set n_totavenda = vtotal_itens
where n_numevenda = old.n_numevenda;
end
mysql> $$
mysql> delimiter ;
```

## Triggers Status

* mysql> alter trigger tri_vendas_bi desable;

* mysql> alter trigger tri_vendas_bi enable;

* mysql> drop trigger tri_vendas_bi;