Organización de una base de datos
	- Estructuras de la información
		> Estucturas
		> Métodos de acceso
	- Reglas de integridad
		> Condiciones a cumplir
	- Operadores
		> Cómo manipulamos los datos y estructuras
		> Definición de datos (Data Definition Language, DDL)
		> Control de datos (Data Control Language)
		> Manipulación de datos (Data Manipulation Language, DML)

**Generaciones de bases de datos**

--Primera generación--
	-> Modelos planos
	-> Modelos de listas invertidas
	-> Modelo jerárquico
	-> Modelo de red
	
--Segunda Generación--
	-> Modelo relacional
	
--Tercera generación--
	-> Bases de datos relacionales
		- extendidas
		- extensibles
	-> Bases de datos orientadas a objetos
	
**PRIMERA GENERACIÓN**

- No se basan en ninguna teoría
- Representan estrategias usadas por los distintos fabricantes
- Se pueden agrupar en "modelos" porque comparten características

- Nivel de abstracción bajo
- Poca expresividad respecto a estructuras y reglas de integridad
- Operadores tratan datos uno a uno
- Navegación en manos de la aplicación
- Herencia de lenguajes de programación 3GL

	- **MODELOS PLANOS**
		- Estructuras simples.
		- Orientadas a registros
		- Con archivos secuenciales o indexados
		- Se accede a los datos un archivo a la vez
		- No se puede tener utilitarios más allá de lo que da el producto
		- Mantenimiento amigable
		- Consultas y reportes fáciles de hacer
		
	- **LISTAS INVERTIDAS**
		- Datos ordenados físicamente con algun criterio previamente establecido
		- Se pueden definir ordenamientos adicionales con índices
		- Se pueden definir múltiples claves de búsqueda
		- Los operadores manejan registros, los cuales son direccionados con algun método de accesoo predefinido
		- Los operadores son dependientes de las ubicaciones
	