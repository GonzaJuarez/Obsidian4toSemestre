Los primeros programas se enfocaban en la codificación y los algoritmos. Los datos se consideraban "los restos" del procesamiento.

Cuando las computadoras empiezan a comercializarse, los datos toman un rol clave

A partir de eso, comienza un camino de evolución de las bases de datos.

***Organización de una DB:***

- Estructuras de información

	- Estructuras
	- Métodos de acceso

- Reglas de Integridad

	- Qué condiciones queremos que cumplan los datos

- Operadores

	- Como lo manipulamos los datos y estructuras

		- Definición de datos (Data Definition Language, DDL)
		- Control de datos (Data Control Language, DCL)
		- Manipulación de datos ( Data Manipulation Language, DML)

***Generaciones de DB:***
- Primera Generación
	- Modelos planos
	- Modelos de listas invertidas
	- Modelo jerárquico
	- Modelos de red

- Segunda generación
	- Modelo relacional

- Tercera generación
	- Bases de datos relacionales extendidas o extensibles
	- Bases de datos orientadas a objetos

***Primera Generación***
- Estos modelos
		No se basan en ninguna teoría
		Representan las estrategias utilizadas por los distintos fabricantes
		Comparten características que permiten agruparlos en "modelos"
	
- Nivel bajo de abstracción
- Poca expresividad con respecto a estructuras y reglas de integridad
- Los operadores tratan los datos uno a uno. Dejan la navegación en manos de la aplicación.
- Herencia de lenguajes de programación  3GL.
	1. Modelos Planos:
		- Estructuras simples, orientadas a objetos, con archivos secuenciales o indexados
		- La forma de acceder es de un archivo a la vez
		- Es amigable de mantener
	
	2. Modelo de Listas invertidas:
		- Estructuras de archivos ordenados fácilmente a través de algún criterio previamente establecido
		- Se pueden definir ordenamientos adicionales a través de índices
		- Se pueden definir múltiples claves de búsqueda
		- Los operadores manejan registros
		- Los operadores dependen de las ubicaciones
	
	3. Modelos jerárquicos:
		- Es como un árbol
		- Cada uno tiene una raíz
		- Los datos se relacionan de 1 a n
		- Cada DB tiene su propio conjunto de operadores
		- La organización tiene que ser codificada por programas
		- Sirven para OLTP
		- La herramienta de administración son muy elaboradas y de gran desempeño
	
	4. Modelos de red:
		- Parte del modelo jerárquico
		- Permite la relación 1 a n y n a n
		- Es posible que el nodo tenga más de un hijo

***Segunda Generación***

- Surge basada en la teoría de conjunto
- Los conjuntos pueden consistir de:
	- Entidades (registros)
	- Atributos (campos)
	- Dominios (valore posibles para los atributos)
	- Relaciones

- Las relaciones se representa físicamente como una tabla, donde cada fila representa una entidad y cada columna sus atributos
- Modelo Relacional:
	- Cada celda tiene un solo valor
	- Cada columna tiene un nombre distinto y representa un atributo
	- El valor de una columna proviene del mismo dominio
	- Los diferente usuarios pueden ver la misma información de distinta forma
	- Proporciona un control de autorización simple
	- El orden de las columnas y filas es irrelevante, No hay valores duplicados en una tabla
	- Proporciona independencias al programa de la definición de las base de datos conceptual
	- Introduce el lenguaje de consulta estructurado (SQL) que consiste en un lenguaje completo de DDL, DML y un lenguaje de autorización

***Tercera Generación***
- Bases de datos relacionales extendidas o extensibles
- Bases de datos orientadas a objetos
	- Es un modelo de datos que consta de un conjunto de conceptos centrales orientados a objetos que se encuentran en la mayoría de los lenguajes y sistemas de programación orientados a objetos
	
- Principales diferencias con el modelo relacional
	- Admite tipos de datos abstractos definidos por el usuario y no esta restringido a nociones de registros
	- Admite operaciones arbitrariamente complejas y no esta restringido a un conjunto predefinido como sucede con SQL
	- El código para implementar servicios (funciones) se almacena en la base de datos y es activado por el DBMS (Data Base Management System)
	
- Ventajas 
	- Eficiencia y velocidad cuando tengo relaciones complejas.
	- Navegación de la data suele ser mas fácil que el los demás tipos de BD vistas.
	- Los objetos no requieren montaje/desmontaje => se ahorra tiempo de codificación y ejecución.

- Desventajas
	- Menos nivel de eficiencia cuando los datos o relaciones son simples
	- Para accedes a los datos preciso una API o lenguaje en particular (no es el caso de bases de datos relacionales)