## Variáveis de sistema

* mysql> show variables; || mysql> show variables like '%table%';

## Visualizando as conexões ativas

* mysql> show processlist;

* mysql> kill numero_id;


## Exportar e importar consultas para arquivos .csv e .txt

```
mysql> select * from comclien
into outfile 'c:/lista_clientes.txt'
fields terminated by ','
enclosed by '''';
```

```
mysql> create table comuser(
n_numeuser int not null auto_increment,
n_nomeuser varchar(100),
n_nascuser date,
primary key(n_numeuser));
```

## Localizar uma coluna no seu banco

```
mysql> select table_schema Banco_Dados,
table_name tabela,
column_name nome_coluna
from information_schema.columns
where table_schema = 'comercial'
and column_name = 'n_numeclien';
```

```
mysql> select table_schema Banco_Dados,
table_name tabela,
column_name nome_coluna
from information_schema.columns
where table_schema = @banco
and column_name = @coluna;
```

```
mysql> set @banco = 'comercial';
mysql> set @coluna = 'n_numeclien';
mysql> source c:/scripts/campo_tabela.sql;
```