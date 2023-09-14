**ARP (Addres Resolution Protocol)**

Suponer que un equipo quiere enviar un paquete IP con destino a otra máquina en el mismo segmento Ethernet; Es decir que están en la misma LAN, capa 2.

Ejemplo: 
- 192.168.1.1/24 -> 192.168.1.3/24

Si la comunicación es en capa 2, ¿cómo el equipo conoce la dirección MAC del host de destino?

El protocolo ARP se utiliza para encontrar la dirección MAC de destino una vez conocida la dirección IP del equipo de destino.

Se intercambian mensajes por la red:
- ARP Request: es un broadcast que pregunta: el que tenga esta IP que me diga su MAC (los broadcast que lleguen a una interfaz del router se descartan)
-  ARP Reply: Solo le responde el que tiene esa dirección MAC configurada

Cada dispositivo de capa 3 tiene un mapeo MAC - IP, es una nueva tabla.

Request: Target IP adress: 192.168.1.3
Reply: Sender MAC adress: 

En cmd: 
- arp -a -> Muestra el contenido de una tabla
- arp -d -> Borra una entrada
- arp -s -> Agrega una asociación estática

![[Pasted image 20230914081955.png]]

10.13.0.1 es el router. No aparecen los dispositivos de los demás compañeros porque no nos comunicamos. En cuanto se haga un ping a otro dispositivo, se configura en la tabla.

La dirección del router **SIEMPRE** va a aparacer porque cuando se prende una PC busca actualizaciones o puede haber aplicaciones que se inicien. Todo esto supone que el PC hable con el router.

El mapeo IP - MAC **no es estático**, por ejemplo: un dispositivo se puede mover de subred, entonces cada entrada de la tabla tiene un tiempo de vida (TTL).

Si un dispositivo A quiere mandar un paquete a otro dispositivo C, donde están en redes distintas, se utiliza la máscara de red para saber si estos dispositivos están en distina red.

IP A -> 192.168.1.0 /24
IP C -> 172.165.3.1 / 16

Máscara A -> 255.255.255.0
Máscara B -> 255.255.0.0

Cuando se sabe que pertenecen a redes distintas, se crea una trama (capa 2) donde la MAC de destino **NO ES** la del dispositivo C, si no la MAC de la interfaz del router perteneciente a esa red.

Cuando esta trama llega al router, este responde con su IP. Con estos datos de la trama, se crea un paquete de capa 3 con origen IP de A y destino IP de B.

Cuando este paquete llega al router y se transporta a la interfaz que conecta la red de C, se crea una trama con MAC de origen el router y destino la MAC de C, (con un broadcast) para saber cuál es la dirección MAC de C .

Entonces, el router tiene una tabla ARP por cada interfaz que tenga.

Ejemplo de uso de ARP:

Si hay 2 routers en alta disponibilidad, compartiendo la IP y MAC, cuando un router falla, el otro manda un **Gratuitous ARP**

Entonces el switch actualiza su dirección MAC en la tabla con la nueva ubicación de ese dispositivo, que ahora es dueño de la MAC compartida. Para esto, se utilizan las IP virtuales. (expandir esto, no entendi un culo)

**Protocolo ICMP**

Definido en RFC 792
Se usa para enviar mensaje de error
(completar)

Ejemplo: ping
- Echo request
- Echo reply

Traceroute: Herramienta usada para saber el camino que toman los paquetes IP hacia un cierto desitno (se hace expirando el TTL). Se miden los retardos hacia cada equipo intermedio (router) y se devuelve un echo reply por medio del protocolo ICMP.

Ejemplo:
![[Pasted image 20230914085750.png]]

**Protocolo DHCP (Dynamic Host Configuration Protocol)** 

Trabaja de forma dinámica y estática (por defecto dinámica) para asignar IP, máscaras de red y default gateway.

Estática:
- Requiere intervención del admin
- Ciertos equipos requieren IPs de este tipo
- No es escalable

Dinámica:
- Deseable para ciertos dispositivos
- Plug and play por parte del usuario
- Permite re-uso de direcciones IP y asignación "on-demand"

Se puede asignar la IP a los dipositivos, al tiempo que otros parámetros. La asignación puede ser temporal. Los mensajes DHCP se basan en broadcast, entonces debe existir un servidor DHCP en la LAN.

Funcionamiento:
1. Host solicita parámetros de autoconfiguración
2. DHCP server asigna parámetros IP

Los DHCP servers tienen una pool de IPs que pueden asignar. Puede pasar que varios dispositivos tengan la misma IP asignada si se hace una asignación dinámica.

Mensajes DHCP, handshaking:
1. DHCP discover -> El broadcast del host
2. DHCP offer       -> El server responde y se ofrece (broadcast)
3. DHCP request  -> El host pide una asignación de IP
4. DHCP ack         -> El server le envía la dirección IP

En cmd:
- ipgconig /all -> muestra la dirección IP y máscara asignada y la IP del servidor DHCP
- ipconfig /release -> libera la IP
- ipconfig /renew -> renueva la IP

Ejemplo:
![[Pasted image 20230914093631.png]]

