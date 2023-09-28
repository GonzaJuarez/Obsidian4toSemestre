
Es responsable de la transimisón a través de la red. El concepto de datos en esta capa es en términos de una "conversación" en lugar del concepto de paquetes individuales. Para esto, se utilizan protocolos que definen las "reglas de la comunicación".

**Objetivos

La capa de transporte proporciona mecanismos de intercambio de datos entre sistemas finales o extremo a extremo libre de errores, en consecuencia, sin pérdidas ni duplicados y cumpliendo los requisitos establecidos.

- Recibir los datos de la capa superior, y dividirlos si fuera necesario, y enviarlos a la capa de red.
- Control de flujo de extremo a extremo
- Establececimiento, mantenimiento y cierre de la conexión.
- Optimizar el empleo del nivel de red (multi y demultiplexación)
- Control de errores
- Direccionamiento del punto de servicio

**Aplicaciones de red

Se necesitan **protocolos de red** para soportar **aplicaciones de red**. El software de estas aplicaciones están distribuidos entre dos o más "end systems".

Ejemplo:
- El browser, software en el PC del usuario (Chrome, Firefox, etc)
- Web Server, software en el servidor (Apache, IIS, etc)

Aplicación: Es un programa interactuable. El software de estas aplicaciones están distribuidos entre dos o más end systems.

Proceso: Es una instancia de un ejecutable en particular, el cual puede interactuar con otros procesos locales o remotos a través de la red. Una aplicacion puede contar con varios procesos ejecutandose en forma simultánea

Servicio: Es un proceso (completar)

**Paradigma cliente-servidor

Las aplicaciones de red típicas tienen 2 partes: cliente y servidor.
(completar)

**Transmisor-Receptor

La capa de transporte provee una comunicación lógica entre 2 procesos que corren en diferentes hosts. Los protocolos de capa de transporte se ejecutan solo en los sistemas finales.

Transmisor: segmenta los mensajes de las aplicaciones en segmentos (PDU)
Receptor: (completar)

**Comunicación entre procesos

El socket es la interfazz de E/S de datos que permite la comunicación entre procesos. Los servers normalmente tienen un socket asociado a un port específico. El (completar)

**Propiedades de los sockets

Fiabilidad de la transmisión, no se pierden los datos transmitidos
(completar)

**Tipo de sockets

Orientados a la conexión -> Stream socket
- Secuencia de caracteres que fluye desde o hacia un proceso. Conexión bidimensional
- Entrega ordenada y confiable de paquetes
- Se una el protocolo TCP

No orientado a la conexión -> Datagram socket
- No hay conexión. Cada paquete es enviado de forma independiente del resto
- Entrega desordenada y no confiable de paquetes, no importa que se pierdan datos.
- Se usa el protocolo UDP
- Se utiliza cuando es muy importante que el programa no se quede bloqueado.

**Concepto de puerto

Identifica a la entidad de capa de aplicación. Cada segmento contiene:
- Puerto de origen
- Puerto de destino

Campo de 16 bits: Rango de puertos 0 - 65535. Del 0 al 1023 -> "Puertos bien conocidos":
- 21 - FTP
- 23 - Telnet
- 25 - SMPT
- 80 - HTTP
- 110 - POP3

Un segmento del cliente web al servidor: Origen: 10263, Destino: 80 (servidor). El navegador por defecto utiliza el puerto 80

**Interacción de sockets en cliente/servidor TCP

El cliente debe contactar al servidor:
- El proceso del servidor debe estar corriendo desde antes
- El servidor debe tener asociado un socket el cual envíe y reciba segmentos.

Interacción de sockets en cliente/servidor UDP

- De forma análoga, el cliente requiere un socket propio
- Además, necesita saber la IP y el número de puerto del servidor (requiere el socket del servidor)

**Protocolos de la capa de transporte

TCP:
- Confiable
- Entrega con orden
- Orientado a la conexión
- Unicast

UDP:
- No confiable
- Entrega sin orden
- No orientado a la conexión
- Sin control de flujo y congestión
- Unicast y multicast

**NINGUNO** garantiza un ancho de banda o un delay acotado.

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