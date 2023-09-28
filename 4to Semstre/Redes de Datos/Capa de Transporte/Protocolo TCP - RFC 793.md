Provee un servicio confiable de "stream de bytes" sobre una red no confiable, como es IP.

- Para las capas superiores, TCP maneja los datos como una secuencia de bytes
- Para las capas inferiores, TCP manjea los datos en bloques (en segmentos)

**Encabezado TCP (HTCP)

- Puerto de origen y destino: 16 bits
- Sequence y Acknowledge number
- Flags: viajan datos 0 o 1, es discreto -> FIN, SYN, RST, ACK, etc
- Checksum
- Options

20 bytes máximos

**Sequence number (SeqNo)

- Se usa para identificar cada byte de datos transmitidos
- Cada dirección de la comunicación tiene un número de sequencia independiente.

**Acknowledge number (AckNo)
- Se utiliza para reconocer los datos recibidos.

Flag ACK -> Acknowledge Data Bit: Indica si el valor en el campo AckNo es válido o no

Estos parámetros garantizan la confiabilidad de la red.

**Transmisión confiable - Funcionamiento de los SeqNo y AckNo

El emisor:
- Numera cada segmento enviado (SeqNo)
- Para cada segmento enviado, lanza un timer y se guarda el segmento en un buffer
- Si el timer da time-out, se re transmite
- Si llega el antes el ACK, se borra del buffer

El receptor:
- Recibe los segmentos, verifica integridad y envía un ACK al transmisor, vía el AckNo y flag ACK = 1
- Utiliza "cumulative acknowledgement" (Es decir aumenta en 1 cada ACK)
- Además, ordena los segmentos en base al número de secuencia y los dispone para que los lea la capa de aplicación (capa superior)

**Establecimiento de la conexión

Previamente el Servidor comienza a escuchar, Estado Listen, en un puerto determinado, Passive Open, donde puede aceptar conexiones desde cualquier cliente (cualquier IP) o de clientes particulares.

**Control de flujo

El objetivo es que un transmisor no genere overflow en los buffers del receptor. Para ello, debe existir una coherencia entre lo que se transmite con lo que la aplicación receptora puede procesar.

Para ello, el tamaño inicial del buffer se establece durante la conexión. El receptor anuncia el tamaño libre del buffer, para esa conexión a través del encabezado TCP, campo windows size.

El receptor retorna dos parámetros de manejo del control de flujo: AckNo y Windows size:
1. Buffer libre, Win = 3000 bytes y mediante Ack = 1000 (se espera SeqNo = 1000)
2. Llegan 3 segmentos de 1000 bytes cada uno
3. La aplicación lee los datos y el buffer queda en 4000 bytes se envía Win = 4000 y Ack = 4000 (se espera SeqNo = 4000)
4. Llegan 4 segmentos de 1000 bytes cada uno

Comando netstat: para ver las conexiones activas en una computadora. Es muy útil para la seguridad porque alguna dirección IP podría llamar la atención.

![[Pasted image 20230928092513.png]]

**Control de congestión

TCP sufre consecuenicas por congestión de red, esto se manifiesta mediante:
- Pérdidas de paquetes (overflows en buffers)
- Aumento y variación de delays

Lo único que puede hacer TCP es reducir la cantidad de segmentos que envía a la red, esto se hace sin asistencia de red (completar)

**Problema de control

- Si se recibe un ACK: la red no está congestionada -> se puede aumentar la velocidad
- Si se vence un timer (segmento perdido) -> La red está congestionada -> Se debe disminuir la velocidad

¿Qué tan rápido se debe hacer?

El control de congestión se implementa mediante dos parámetros:
- Ventana de congestión (cwnd): limita la cantidad de segmentos que el transmisor puede transmitir sin ACKs
- Slow-star threshhold (ssthresh)

El control de congestión funciona en 2 fases:
- Slow start
- 

Slow start: Cuando una conexión comienza, se incrementa exponencialemtne la cantidad de segmentos hasta que ocurra el primer evento de pérdida. Se comienza transmitiendo 1 segmento (cwnd = 1), se recibe un ACK y se hace cwnd = cwnd + 1. Durante (completar)