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