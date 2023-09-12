SELECT * FROM nombre_tabla
SELECT nombre_columna FROM nombre_tabla WHERE ...
INSERT INTO nombre_tabla VALUES (valores a insertar)
CREATE DATABASE o TABLE nombre

**Sentencia create:

CREATE TABLE Alumnos(
    CI INTEGER PRIMARY KEY , <- Nombre - tipo - otras propiedades (primary key, not null, etc)
    NOMBRE VARCHAR(50) not null ,
    APELLIDO VARCHAR(50) not null
);

CREATE DATABASE db1;

**Sentencia use:**

USE db1;

**Sentencia insert:

INSERT INTO Alumnos(CI, NOMBRE, APELLIDO)  VALUES(53749274, "Jose", "De la santísima trinidad");

**Sentencia select: 

SELECT * FROM Alumnos;
SELECT COUNT(*) (o count(1)) from Alumnos; <- cantidad
SELECT * FROM alumnos WHERE nombre LIKE "%luis%"  <- (contains) sentencia costosa
SELECT * FROM Alumnos WHERE nombre in ("nombre1","nombre2") <- buscar por 2 atributos
SELECT * FROM Alumnos WHERE nombre is null
SELECT * FROM Alumnos WHERE fecha_nacimiento BETWEEN "01.01.1977" and "31.12.1977" <- igual que usar > y <

**Sentencia delete:

DETELE FROM Alumnos WHERE CI = 3538745;
DELETE FROM Alumnos <- borra todas las entradas, mala practica

**Sentencia update:

UPDATE Alumnos SET CI=5729473 WHERE NOMBRE="Juan";