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
