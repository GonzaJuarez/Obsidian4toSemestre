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