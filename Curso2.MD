show databases

use curso_sql

show tables

describe usuarios

drop table usuarios

create table usuarios (
	usuario_id int unsigned auto_increment primary key,
	nombre varchar(30) not null,
	apellidos varchar(30) not null,
	correo varchar(50) unique,
	edad int default 0
)

insert into usuarios (nombre, apellidos, correo, edad) values
('kenai','mircha','kenai@gmail.com',10),
('jhon','mircha','jhon@gmail.com',38),
( 'irma','campos', 'irma@gmail.com', 20),
( 'pepito','perez','pepito@gmamil.com', 45 ),
( 'rosita','juarez','rosita@gmail.com', 88 )


create table productos (
	producto_id int unsigned auto_increment primary key,
	nombre varchar(50) not null,
	descripcion varchar (50),
	precio decimal (7,2),
	cantidad int unsigned
)

insert into productos (nombre, descripcion, precio, cantidad ) values 
('computadora', 'mac book air m2', 29999.99, 5 ),
( 'celular', 'nothing phone 1', 11999.99, 15 ),
( 'camara web', 'logitech c33', 1500, 13 ),
( 'microfono', 'blue yeti', 2500, 13 ),
( 'audifonos', 'audifonos base', 6500, 10 )

select * from usuarios 

select * from productos

truncate table usuarios 
truncate table productos 
 

* generar calculos con mysql 

select 6+6

select mod(4,2)

select ceiling (7.1)

select floor ( 7.9)

select round (7.4)

select power(2,6)

* columnas calculadas 

select nombre, precio, cantidad, (precio * cantidad) from productos

* funciones de agrupamiento 

select max(precio) as precio_max from productos

select min(precio) as precio_min from productos

select sum(cantidad) as sumatoria_total from productos

select avg(precio) as precio_promedio from productos

select count(*) as prod_total from productos

select nombre, precio, max(precio) as precio_max from productos group by precio, nombre 

## crear tabla de los caballeros del zodiaco

create table caballeros (
	caballero_id int auto_increment primary key,
	nombre varchar(30),
	armadura varchar(30),
	rango varchar(30),
	signo varchar(30),
	ejercito varchar(30),
	pais varchar(30)
)


insert into caballeros values
( 0, 'seiya', 'pegado', 'bronce', 'sagitario', 'athena', 'japon' ),
( 0, 'shiryu', 'dragon','bronce', 'libra', 'athena', 'japon' ),
( 0, 'hyoga','cisne', 'bronce', 'virgo','athena', 'rusia' ),
( 0, 'shun', 'andromeda', 'bronce', ' virgo', ' athena', 'japon' ),
( 0, 'ikki', 'fenix', 'bronce', 'leo', 'athena', 'japon' ),
( 0, 'kanon', 'geminis', 'oro', 'geminis', 'athena', 'japon' ),
( 0, 'saga', 'geminis', 'oro', 'acuario', 'athena', 'grecia' ),
( 0, 'camus', 'acuario', 'oro', 'acuario', 'athena', 'francia' ),
( 0, 'radhamantis','wyvern', 'espectro', 'escorpion', 'hades', 'inglaterra'),
( 0, 'kanon', 'dragon marino', 'marino', 'geminis', 'poseidon', 'grecia'),
( 0, 'kagaho', 'bennu', 'espectro', 'leo', 'hades', 'rusia' )

select * from caballeros


* cuantos signos tienes de cada uno ? 

select signo, count(*) as total_signos from caballeros group by signo

* cuantas armaduras diferente hay? 

select armadura, count(*) as total_armaduras from caballeros group by armadura

* cuantos rangos hay?

select rango, count(*) as rangos from caballeros group by rango

select ejercito, count(*) as ejercitos from caballeros group by ejercito

select rango, count(*) as total from caballeros where ejercito = 'athena' group by rango having total >= 4

* eliminar valores repetidos con DISTINCT

select distinct signo from caballeros

* ordenar con clausula order 

select * from caballeros order by nombre asc

select * from caballeros order by nombre, signo asc

* clausula between 

select * from productos where precio between 5000 and 15000 

* manejo de expresiones regulares 

select * from productos where descripcion regexp '[a-z]'

select ('hola mundo')

* mostrar indices de una tabla 

show index from usuarios

* definir un indice se hace con unique o con llave primaria 



create table caballeros (
	caballero_id int auto_increment primary key,
	nombre varchar(30),
	armadura varchar(30),
	rango varchar(30),
	signo varchar(30),
	ejercito varchar(30),
	pais varchar(30), 
	index i_rango (rango),
	index i_armadura (armadura),
	index i_caballeros (ejercito,pais)
)

* clausula alter table 

alter table caballeros add constraint pk_caballero_id primary key

alter table caballeros modify column caballero_id int auto_increment 

alter table caballeros add index i_rango (rango)

alter table caballeros add index i_jercito_pais (ejercito, pais)

