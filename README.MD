# CURSO SQL 

### Tipos de sentencias SQL 

* Data definition language (DDL): CREATE, ALTER, DROP, TRUNCATE 
* Data manipulation Languaje (DML): SELECT, INSERT, UPDATE, DELETE 
* Data Control Languaje (DCL): GRANT, REVOKE 
* Transaction Control Languaje (TCL): COMMIT, ROLLBACK, SET TRANSACTION

### comandos mas usados 

![comandos mas usados](comandos_regulares.jpg)

### funciones mas comunes en sql 

![funciones comunes](funciones_sql.png)

* mostrar bases de datos de un usuario

show databases;

-- comentario en una linea de sql 

/*
*
este es comentario en varias lineas
*/

show DATABASES;

* COMO CREAR UNA BASE DE DATOS

create database curso_sql

* eliminar db 

drop database curso_sql

* condicionales

create database if not exists curso_sql 
drop database if existis curso_sql

* usuarios y privilegios 

* crear usuario 

create user 'benja'@'localhost' identified by 'qwerty';

* crear base de datos 

create database parabenja

*ALTER USER 'benja'@'localhost' IDENTIFIED WITH mysql_native_password BY 'asdfa';

* asignarle privilegios 

grant all privileges on curso_sql to 'benja'@'localhost'


* se actualiza la lista de privilegios

flush privileges:

* mostrar los priviegios de un user 

show grants for 'benja'@'localhost'

* quitar prvilegios a un usuario 
revoke all, grant option from 'benja'@'localhost'

* como poder eliminar usuario 

drop user 'benja0'@'localhost'


* COMO CREAR TABLAS / usar tablas / etc etc  


* como ver las tablas de una base de datos

* usar una base de datos 
use curso_sql

* mostrar las tablas de una DB
show tables

* obtener descripcion de una tabla 

describe usuarios

* como crear una tabla 

create table usuarios(
	nombre VARCHAR(50),
	correo varchar(50)
);


* modificar una tabla existente 

alter table usuarios add column cumpleanos varchar(15)

alter table usuarios modify cumpleanos date;

alter table usuarios rename column cumpleanos to nacimiento

alter table usuarios drop column nacimiento

* eliminar tabla 

drop table usuarios 


create table usuarios(
	usuario_id int unsigned auto_increment primary key,
	nombre varchar(30) not null,
	apellidos varchar(30) not null,
	correo varchar(50) unique,
	direccion varchar(100) default "sin direccion" ,
	edad int default 0
	
);

describe usuarios

* operaciones del crud 

* insertar un registro / existen 3 formas de insertar

insert into usuarios values (0,"benja", "mendez", "benja@gmail.com", "palma mz 9 lt 3", 22 )

* leer datos de una tabla 

select * from usuarios

insert into usuarios (nombre, apellidos, edad) values ( "balto","mendez", 22 )

insert into usuarios set nombre = "maria", apellidos="flores", edad = 33

* como ingresar varios datos 

insert into usuarios (nombre, apellidos, edad) values 
( "peppito","mendez", 22 ),
( "rosita","guzman", 24 ),
( "macario","mendez", 92 );


* como leer datos 

select * from usuarios 

select nombre, edad, usuario_id from usuarios

select count(*) from usuarios

select count(*) as total_usuarios from usuarios

* clausula where

select * from usuarios where nombre = 'benja'

-- para hacer where a 2 valores o mas
select * from usuarios where nombre in ('valor1', 'valor2', 'valor3')

* clausula like

select * from usuarios where apellidos like 'M%'

select * from usuarios where correo like '%@gmail.com'

select * from usuarios where nombre like '%enja%'

* clausula not like

select * from usuarios where apellidos not like 'M%'

select * from usuarios where correo not like '%@gmail.com'

select * from usuarios where nombre not like '%enja%'

* where + = !=  DIFERENTE DE 

select * from usuarios where edad != 20 

select from usuarios where edad <> 30

select from usuarios where not edad = 30 and correo = "%gmail.com"

* CLAUSULA OR 

select from usuarios where not edad = 30 OR correo = "%gmail.com"

* CLAUSULA UPDATE 

update usuarios set correo = "benja@gmail.com", direccion = "nueva direccion" where user_id = 2


* CLAUSULA DELETE 

delete from usuarios where usuario_id = 3

* ELIMINAR COMPLETAMENTE INCLUSO EL CACHE 

truncate table usuarios 