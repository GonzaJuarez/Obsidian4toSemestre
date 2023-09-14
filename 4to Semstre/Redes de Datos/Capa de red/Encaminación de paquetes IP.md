Los routers deciden cual es el próximo salto en base a:
- Dirección de destino del datagrama
- Tabla de conmutación

Se habla de REDES no de HOSTS, "querer llegar a Singapore" significa "querer llegar a la red de Singapore".

Entonces cuando un paquete entra a un router, este se fija en sus tablas si la IP de destino está en la tabla -> los saltos siempre son IPs.

Tipos de entradas en las tablas:
- Directamente conectadas
- Estaticas -> Configuradas por el admin
- Dinámicas:
	- RIP -> Aprendidas mediante el protocolo RIP
	- OSPF - Aprendida mediante el protocolo OSPF
- Default -> Ruta por defect configurada por el admin o aprendida dinámicamente.

Campo de la Tabla de ruteo:
- Red y máscara -> Describen la red de destino
- Interfaz de destino o próximo salto:
	-  Si la red de destino está directamente conectada se especifica la interfaz
	- Si no (completar)

**Look up en la tabla**

Se hace un AND entre la IP de destino del paquete y la máscara indicada en la tabla
El resultado se lo compara con la dirección de red de la misma entrada:
	- Si hay considencia, se conmuta (completar)
	- Si no, se sigue a la siguiente entrada

**Actualización de la Tabla**

En base a cambios topológicos de la red se utiliza:
- Ruteo estático: manualmente por el admin
- Ruteo dinámico: Se habilitan protocolos de ruteo, en los routers, para que estos actualicen la tabla dinámicamente:
	- Periódicamente cada router intercambia información, de alcanzabilidad a redes IP, con otros routers.
	- Existen distintos tipos de protocolos (RIP, OSPF, BGP, etc)
	- Solo van a la tabla las entradas con "mejor" métrica

**Conmutación de paquetes IP**

1. Examina dirección IP destino
2. Look up en la tabla

Si hay coincidencia:
1. Se decrementa el TTL
2. Se conmuta el paquete a la interfaz de salida indicada en la tabla

Si no:
1. Se descarta el paquete y se manda un paquete ICMP al origen (Red inalcanzable)

**Ruteo y conmutación**

? completar


