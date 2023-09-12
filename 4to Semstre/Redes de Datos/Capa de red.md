red par
=======
Se encarga de "rutear" los paquetes según el destino. La capa de red conecta las diferentes LAN. Las interfaces de los routers **forman** parte de la red. 
No puede pasar que dos dispositivos pertenezcan a la misma red. En las tarjetas de red, cada interfaz se toma como distintos dispositivos, es decir que una conexión wifi tiene distinta IP que una cableada en la misma PC.

Dos maneras de rutear:
- Conmutación de paquetes: Cada ruta mira el cabezal de IP -> dirección de destino, y en función de eso arma el camino. Caminos distintos de ida y vuelta
- CV (circuito virtual): Donde no se fija en la dirección de destino, si no que cada router decide qué camino toma cada paquete según la etiqueta de circuito virtual. Mismos caminos de ida y vuelta

Pros paquetes: Más barato, (completar)
Cons: No se asegura de que lleguen los paquetes, ni los retransmite.

Pros circuitos: Los paquetes llegan en orden, los paquetes no se pierden, más seguro.
Cons: Caro (completar)

**Fragmentación

Cuando un paquete sobrepasa los 1500 bytes, el paquete se fragmenta en paquetes de hasta 1500 bytes. (completar)

**Direccionamiento IP

No existe una sola ruta para llegar a un destino, entonces los dispositivos usan el *esquema de direccionamiento* de la capa de red para determinar el destino de los datos a medida que se desplazan en la red.
Cada interfaz de un router tiene distinto tipo de interfaces según sean las tecnologías: seriales o ethernet.

**IPv4

Dirección de 32 bits formada por 2 partes:
1. Porción de red -> bits de la red (izquierda)
2. Porción de host -> bits del host (derecha)

Se representa con 4 contenedores de 8 bits, donde cada contenedor puede tener desde 2^0 hasta 2^7. (0 hasta 255)

Sean las direcciones: 
10.13.142.185 
10.13.230.202

10.13 representa que ambos dispositivos están conectados a la misma red. (No siempre se divide a la mitad entre poción de red y de host).

La máscara: Son los bits que representan las partes de una dirección IP. Los 1 representan los bits de red y los 0 representan los bits de host. Entonces, en el ejemplo de la IP 10.13.142.185 la máscara sería 255.255.0.0. Esto se hace para que el sistema operativo pueda saber cuál es cada parte. Por esto, una dirección IP por sí sola no tiene sentido.

Direcciones de clase A

Rango del primer octeto: 1 a 126 -> es decir que el primer octeto se usa para la porción de red. Desde 1.0.0.0 hasta 126.0.0.0, con solo 126 redes disponibles y la cantidad de host por red son 2^7 - 2. (16 millones más o menos) por red.

Direcciones de clase B

Rango del primer octeto: 128 hasta 191 -> los primeros 2 octetos son para la porción de red. Desde 128.0.0.0 hasta 255.255.0.0. Hay 255^2 cantidad de redes y 65 mil hosts válidos por red.

Direcciones de clase C
Rango del primer octeto: 192 hasta 223 -> los primeros 3 octetos para la porción de red. Desde 192.0.0.0 hasta 255.255.255.0. Hay 255^3 cantidad de redes y 256 - 2 hosts válidos por red.

Direcciones de clase D

(completar)

Direcciones de clase E

(completar)

Cuando una dirección IP no especifica la máscara, el sistema operativo mira las direcciones de clases y las asigna (máscaras por defecto).

Direcciones reservadas:

0.0.0.0 -> Por defecto de la red

255.255.255.255 -> Broadcast

Dirección IP de red de la católica es 10.13.0.0 y la dirección de broadcast es 10.13.255.255 (por eso siempre son - 2 hosts válidos).

**RFC 1918 - IP privadas y públicas**

Si la católica tiene 2000 estudiantes, en una clase no se tiene que salir a internet para hacer una prueba en webasignatura, entonces se definieron redes que no se rutean en internet. Caso red webasignatura.

Redes privadas según la clase: 
- Clase A: 10.0.0.0 a 10.255.255.255
- Clase B: 172.16.0.0 a 172.31.255.255
- Clase C: 192.168.0.0 a 192.168.255.255
<<<<<<< HEAD

**Subredes

A veces se necesitan dividir las redes, especialmente las de gran tamaño, en redes más pequeñas para tener mayor flexibilidad. 

Ejemplo: 25 laboratorios de 10 personas en la Católica. -> Dividir la red para que soporte 10 máquinas en los 25 laboratorios. 

Una posible solución es a cada laboratorio asignarle una IP /24. El problema de esto es que cada una soporta hasta 255 hosts, pero se van a utilizar solo 10, es decir que se están desperdiciando hosts. 

Entonces, se pueden crear subredes, donde se toman bits del host para prestarle a la porción de red. Para saber cuántos bits prestar, se tiene en cuenta la siguiente inecuación: 
**2^x - 2 > cantidad de dispotisivos** 
El - 2 es porque la IP de red y la de broadcast no se usan. Entonces, se necesitan prestar 4 bits. (2^4 - 2 = 14)

La red más chica que se puede hacer es un /30, dejando solo 2 bits para hosts (2 hosts válidos).

Ejercicio 1:
Direccionar la red sin realizar subnetting
Partir la red clases C 192.168.1.0 en tres subredes

E0 -> 122 hosts : 2^x - 2 > 122 - x = 7 - IP de red: 192.168.0.0 / 25 (32 - 7), IP válida: 192.168.0.1 / 24, máscara: 255.255.
E1 -> 61 hosts : 2^x - 2 > 61 - x = 6 - IP de red : 192.168.3.0 /26, IP válida: 192.168.3.1 /24
E2 -> 61 hosts : 2^x - 2 > 61 - x = 6 - IP de red: 192.168.1.0 /26, IP válida: 192.168.1.1 / 24

Una red de /24 (Dos /25 y una de ellas dividida en 2 /26)

Para evitar el solapamiento de redes, al asignar las redes, se hace en orden descendiente, es decir primero la más grande.

