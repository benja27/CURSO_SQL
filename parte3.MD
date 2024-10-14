create table armaduras (
	armadura_id int primary key auto_increment,
	armadura varchar(30)
)

create table signos (
	signo_id int primary key auto_increment,
	signo varchar(30)
)

create table rangos (
	rango_id int primary key auto_increment,
	rango varchar(30)
)

create table ejercitos (
	ejercito_id int primary key auto_increment,
	ejercito varchar(30)
)

create table paises (
	pais_id int primary key auto_increment,
	pais varchar(30)
)

show databases

use curso_sql

drop table caballeros

truncate table caballeros

create table caballeros (
	caballero_id int auto_increment primary key,
	nombre varchar(30),
	armadura int,
	rango int,
	signo int, 
	ejercito int,
	pais int,
	foreign key(armadura) references armaduras(armadura_id),
	foreign key(rango) references rangos(rango_id),
	foreign key(signo) references signos(signo_id),
	foreign key(ejercito) references ejercitos(ejercito_id),
	foreign key(pais) references paises(pais_id)
)


show tables

insert into armaduras values
(0,'pegaso'),
(0,'dragon'),
(0,'cisne'),
(0,'andromeda'),
(0,'fenix'),
(0,'geminis'),
(0,'acuario'),
(0,'wyvern'),
(0,'dragon marino'),
(0,'bennu')

insert into rangos values
(0,'bronce'),
(0,'oro'),
(0,'espectro'),
(0,'marino')

insert into signos values 
(0,'aries'),
(0,'tauro'),
(0,'geminis'),
(0,'cancer'),
(0,'leo'),
(0,'virgo'),
(0,'libra'),
(0,'escorpion'),
(0,'sagitario'),
(0,'capricornio'),
(0,'acuario'),
(0,'picis')

insert into ejercitos values 
(0,'athena'),
(0,'hades'),
(0,'poseidon')

insert into paises values
(0,'japon'),
(0,'rusia'),
(0,'grecia'),
(0,'francia'),
(0,'inglaterra')

insert into caballeros values 
(0,'seiya',1,1,9,1,1),
(0,'shiryu',2,1,7,1,1),
(0,'hyoga',3,1,11,1,2),
(0,'shun',4,1,6,1,1),
(0,'ikki',5,1,5,1,1),
(0,'kannon',6,2,3,1,3),
(0,'saga',6,2,3,1,3),
(0,'camus',7,2,11,1,4),
(0,'rhadamantis',8,3,8,2,5),
(0,'kanon',9,4,3,3,3),
(0,'kagaho',10,3,5,2,2)


* como usar los sql joints

select * from caballeros c
left join signos s  
on c.signo = s.signo_id

select * from caballeros c
right join signos s  
on c.signo = s.signo_id

select c.caballero_id, c.nombre, a.armadura
s.signo, r.rango, e.ejercito, p.pais
from caballeros c
inner join armaduras a on c.armadura = a.armadura_id
inner join signos a on s.signo = s.s.signo_id
inner join armaduras a on c.armadura = a.armadura_id
inner join armaduras a on c.armadura = a.armadura_id
inner join armaduras a on c.armadura = a.armadura_id

* subconsulta 

* vistas 

create view  vista caballeros as
	select * from caballeros 
	
drop view vista caballeros 

show full tables in curso_sql where table_type like 'view'

