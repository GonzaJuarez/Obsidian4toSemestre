- Fiel al estándar
- Migraciones 
- Portabilidad
- Structured Query Language (1974-1987)

--------> Prototipo de IBM, para uso interno de algunos clientes.

Hay 3 tipos de instrucciones fundamentales.

- DDL (Data Definition Language)
	- Se utilizan para crear, modificar o eliminar objetos de una BD
	- Tablas, vistas, restricciones, indices, procedimientos, esquemas
- DML
	- 
- DCL

__________________________________
**DDL**

**Tablas**

Las sentencias más frecuentemente asociadas a DDL son las de las tablas.

***CREATE, ALTER, DROP***

- CREATE TABLE <nombre tabla>
					(<<nombre campo> <tipo de datos> [NOT NULL] [DEFAULT valor] ….)

- ALTER TABLE <nombre tabla>
   ADD [COLUMN] <definición columna>
   | ALTER [COLUMN]<nombre columna>….
   | DROP [COLUMN] <nombre columna> {CASCADE | RESTRICT}

Alter se usa para editar, borrar o modificar columnas en una tabla existente, además de que se usa para agregar o eliminar constraints en una tabla.

- DROP TABLE <nombre tabla> {CASCADE | RESTRICT}.
Es para eliminar una tabla y elimina toda la información existente en la misma.

- TRUNC TABLE es para borrar solo el contenido de la tabla.

***RESTRICCIONES***

Restricciones de integridad para manejo correcto y seguro de datos.

-> NOT NULL
	- Fuerza a una columna a NO ACEPTAR valores NULL (siempre debe tener algo), ya que por default las columnas pueden ser valor nulo.
	- Ejemplo en un alter table:
												- ALTER TABLE Persons  
												  ALTER COLUMN Age int NOT NULL;
-> UNIQUE
	- Se asegura de que todos los valores en una columna sean diferentes. Se pueden tener varias UNIQUE CONSTRAINTS por tabla. Es parecido a PRIMARY KEY, pero admite varias claves únicas aunque ambas garanticen uniqueness.
	- Ejemplo:
						- CREATE TABLE Persons (  
																    ID int NOT NULL,  
																    LastName varchar(255) NOT NULL,  
																    FirstName varchar(255),  
																    Age int,  
																    UNIQUE (ID)  
																);
-> PRIMARY KEY
	- Es la clave primaria, identifica unicamente a valores de la tabla. SOLO puede haber UNA primary key, aunque puede estar compuesta de varias columnas.
-> FOREIGN KEY
	- Se usa para prevenir acciones que puedan afectar uniones o relaciones entre tablas. La FOREIGN KEY es un campo que refiere a la PRIMARY KEY de otra tabla.
	- A la tabla con la FOREIGN KEY se le llama TABLA HIJO, y la de la PRIMARY KEY se le llama TABLA PADRE o TABLA REFERENCIADA.
	- Se usa al final poniendo FOREIGN KEY(...)
-> CHECK
	- Se usa para limitar el rango de valores que se pueden colocar en una columna, si se pone este constraint se aceptaran solo ciertos valores.
	- Ejemplo: 
					- CREATE TABLE Persons (  
															    ID int NOT NULL,  
															    LastName varchar(255) NOT NULL,  
															    FirstName varchar(255),  
															    Age int,  
															    CHECK (Age>=18)  
															);
																
***VISTAS EN SQL***

- Una vista en SQL es una tabla que deriva de otras tablas. 
- Una vista no existe necesariamente en formato físico; está considerada como tabla virtual.
	- Se limita la actualizacion
	- Se le asigna: nombre, atributos, consulta SQL.

Operaciones: 
-> CREATE VIEW <nombre vista> [(<nombre campo>, <nombre campo> ….)] AS (SELECT …..)
-> DROP VIEW <nombre vista>

________________________________________________________________________________________________________

***DML***

DATA MANIPULATION LANGUAGE.

- INSERT
- UPDATE
- DELETE
- SELECT

