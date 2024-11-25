# Procedures
Este conjunto de procedures foi criado no banco de dados produceres, com o objetivo de gerenciar e consultar informações sobre os países registrados na tabela Pais.
Procedures.sql
CREATE SCHEMA IF NOT EXISTS produceres DEFAULT CHARACTER SET utf8;
use produceres;

CREATE TABLE IF NOT EXISTS Pais (
id_pais int not null auto_increment,
nome_pais VARCHAR(100) not null,
primary key (id_pais)
);

select * from Pais;

insert into pais values
(null,"Brasil"),(null,"Chile");
insert into pais values
(null,"Argentina"),(null,"Mexico"),(null,"Bolivia");

Delimiter $$

create procedure lista_paises(in id int)
begin
if (id is null) then
select *from Pais;
else
select * from Pais where id_pais = id;
end if;
end $$
Delimiter ;

Delimiter $$
create procedure verificarQuantidadepaises (in id int)
begin
if (id is null) then
select * from Pais;
else 
select * from Pais where id_pais = id;
end if;
end $$
Delimiter ;

Delimiter $$
create procedure Selecionarpaises (in id int)
begin
if (id is null) then
select * from Pais;
else
select * from Pais where id_pais = id;
end if;
end $$
Delimiter ;

Delimiter $$
create procedure SelecionarPaisescom(in id int)
begin
if (id is null) then
select * from Pais;
else
select * from Pais where id_pais = id;
end if;
end $$
Delimiter ;

call lista_paises(null);
call lista_paises (2);

call verificarQuantidadepaises(@total);
select @total;

call Selecionarpaises(5);

call SelecionarPaisescom("b");
