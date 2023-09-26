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

