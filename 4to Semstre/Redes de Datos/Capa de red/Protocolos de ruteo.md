
- Son un mecanismo para intercambiar información con otros routers, acerca fed la alcanzabilidad a redes IP
- Reaccionan frente a cambios topológicos, modifican las tablas de ruteo del propio router e informa a routers vecinos
- Utilizan un algoritmo de ruteo para calcular los mejores caminos y solo el mejor se carga en la tabla de ruteo
- Son procesos que se ejecutan en cada router

Clasificación:
- Estáticos (No adaptativos)
- Dinámicos (Adaptativos): Algoritmos Distance Vector, protocolo RIP

**Ruteo Estático

Consiste en introducir administrativamente rutas de forma fija enla tabla de ruteo.
No es escalable, pero no hay nada corriendo en el equipo, por lo que no hay consumo de recursos en el mismo para intercambio de información, ni de ancho de banda

Ejemplo de uso: Cuando existe un único enlace hacia un destino y/o se desea controlar el camino a seguir

Manejo de fallas: Si ocurre una falla en el camino escogido, los paquetes **no llegan al destino** y si existiera un camino alternativo, el administrador debe reconfigurar la ruta

**Ruteo Dinámico

Basan sus decisiones de cuál es el camino más adecuado en alguno de los siguientes aspectos:
- La cantidad de saltos de routers que hay para llegar a un destino
- La topología actual y el ancho de banda configurado de cada enlace

Los protocolos de enrutamiento difieren entre sí por:
- La información que utilizan para calcular rutas
- Los aspectos que se consideran en la métrica a utilizar
- La forma de intercambiar la información de ruteo

Manjeo de falla: Si existe una falla en el camino escogido:
- Si hay un camino redundante, automáticamente se modifica la decisión y se sigue reenviando paquetes IP

**Algoritmo de Vector Distancia

Ningún nodo tiene conocimiento global de la topología de la red, en cambio sabe a que nodo vecino debe enviar el paquete para alcanzar la red de destino, con la mayor cantidad de saltos (La cantidad de saltos es la cantidad de routers).

Ejemplo de tabla de ruteo completa con DV:

| Red | Cantidad de saltos | Router vecino |  
| -------- | -------- | -------- |  
| 10.0.0.0 / 24 | 5 | 192.168.1.1 |  
| 172.16.0.0 / 16 | 2 | 10.0.2.2 |

Periódicamente cada nodo paralelamente:
- Recibe información de sus vecinos: información de una lista de redes y distancias a las mismas. Las compara con las propias y si es menor las agrega a la tabla de ruteo
- Toma todas las entradas de su tabla de ruteo, le suma un salto y las envía por sus interfaces

**Default Gateway

Es una red default que tiene la red y máscara todo 0. Entonces, cualquier equipo que "no conoce" se lo envía a un GW. La operación de cualquier IP de destino **AND** 0.0.0.0 da 0.0.0.0, es decir que siempre coincide con el campo de red de la tabla (0.0.0.0). El GW por defecto debe pertenecer a la misma subred IP que a la que tiene configurada el propio equipo.

