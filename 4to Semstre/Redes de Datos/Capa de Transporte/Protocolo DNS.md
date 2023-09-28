
Facilitar la comunicación con los equipos de red, haciendo referencia a nombres en vez de direcciones numéricas. Traducción de nombres de equipos a direcciones IPs.

Ejemplo de uso: envío de correo a user@ucu.edu.uy
- Un name server va a traducir la dirección a la IP correspondiente

**Implementacion de DNS en Internet

- Estructura jerárquica
- Base de datos distribuida -> la información no está en 1 solo lado, si no que está distribuida geográficamente
- Arquitectura cliente-servidor

**Dominios

Conjuto de etiquetas separadas por punto. Todo dominio finaliza en punto. Ejemplo: www.ucu.edu.uy. - servidor.empresa.com.

**Espacio de nombre de dominios en Internet

Top level: 
- ccTLD (country code domains) .uy .br
- gTLD (generic domains) .com .edu .gov .net

Second level
- gTLD .com.uy .com.ar
- Plano 

Diferencia entre .com y .com.uy: 
- .com es el global y .com.uy es el global pero de cada país

Delegación .ucu.edu.uy.

Los dominios en cada nivel son administrados por distintas entidades. Las cuales a su vez pueden delegar la administración de los dominios dejabo de su nivel.

- Nivel 1: .uy - SECIU - UdeLaR
- Nivel 2: .com .edu - SCEIU - UdeLaR
- Nivel 3: .ucu - UCU

**Root servers https://root-servers.org/
- 13 servidores distribuidos por el mundo
- Identificados con letras desde la A a la M

Ventajas: fortalecimiento y estabilidad de recursos de Internet y menores retardos, mejora la calidad de la experiencia.

**Servidor autoritativo

Autoritativo, primario (master) de alguna zona
- Obtuvo la delegación
- Administra parte del espacio de nombres
- Tiene los archivos de la zona

Secundario (slave) de otro
- Toma los registros de un master -> sincroniza

**Arquitectura cliente-servidor

Cliente
- Se llama resolver
- Es una aplicación
- Realiza la consulta del dominio al servidor que tiene configurado

Servidores
- Responde las consultas (puerto UDP 53)

