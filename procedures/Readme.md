## Stored Procedure

```
mysql> delimiter $$
mysql>create procedure processa_comissionamento(
in data_inicial date,
in data_final date ,
out total_processado int )
begin

(...)

end$$
```

```
mysql> call
processa_comissionamento('2015-01-01','2015-05-30' ,@a);
mysql> select @a;
```

* Delete procedure: mysql> drop procedure processa_comissionamento;

## Functions

```
mysql>delimiter $$
mysql> create function rt_nome_cliente(vn_numeclien int)
returns varchar(50)
begin

(...)

return nome;
end $$
mysql> delimiter ;
```

```
mysql> select rt_nome_cliente(1);
```

## Dual Table

```
mysql> select rt_nome_cliente(1) from dual;
```

## Event Scheduler

```
mysql>set global event_scheduler = on;
```

```
mysql> delimiter $$
mysql> create event processa_comissao
on schedule every 1 week starts '2015-03-01 23:38:00'
do
begin
call processa_comissionamento(
current_date() - interval 7 day,
current_date(), @a );
end
mysql> $$
mysql> delimiter ;
```

```
mysql> alter event processa_comissao_event disable;

mysql> alter event processa_comissao_event enable;
```