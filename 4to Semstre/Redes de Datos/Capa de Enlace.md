Su principal función es:

1. Preparar los paquetes de la capa de red
2. Controlar el acceso a los medios físicos

En esta capa:

- Se envían los datos que se convirtieron a bits
- Se le añade información sobre el direccionamientos físico
- Brinda servicio a la capa de red (capa 3) para acceder a los medios utilizando técnicas como tramas

Se encarga de lograr una comunicación eficiente entre dos equipos "adyacentes" ocultando a la capa de red los problemas de la capa física.

Los problemas son:

- Errores del medio físico
- Retardo de los canales
- Diferencias entre velocidad de receptor y transmisor

La capa de enlace de datos esta incorporada en una entidad física como tarjeta de red(NIC), QUE HACE LA CONEXION ENTRE LOS PROCESOS DE SOFTWARE

Servicios hacia la capade red

- Servicios SIN conexión SIN confirmación

- No se garantiza la entrega fiable de tramas

- Se detectan errores de la transmisión t se descartan las tramas erróneas
- La tramas perdidas o erróneas no se retransmiten
- Las tramas correctas no se confirman
- No se detectan no descartan posibles tramas duplicadas
- Las tramas se entregan a la capa superior en el orden que llegan
- No se realiza el control de flujo entre el emisor y el receptos

- No hay fases de establecimientos o fin de confirmación

- Cada trama se considera independiente del resto

- Uso: Redes con tasas de errores baja

- LANs (Ethernet)

- Servicios SIN conexión CON confirmación

- Garantiza la entrega fiable de tramas

- Detectan los errores de la transmisión y se detectan las tramas erróneas
- Todas las tramas perdidas o erróneas se retransmiten
- Se detectan y descartan todas  las tramas duplicadas
- Las tramas se entregan a la capa superior ordenadas y libres de errores
- Se realiza el control de flujo entre el emisor y el receptor

- Para llevar a cabo control de errores, se utilizan

- Técnicas de detención de errores y numeración de tramas
- Confirmacion de las tramas recibidas OK y retransmisión de tramas no confirmadas

- Los protocolos de enlace orientados a conexión incluyen tres fases

- Establecimiento de la conexión de la enlace, transmisión y finalización de la conexión

Entramado (Frame)

- Hay que delimitar el inicio y fin de cada frame, técnicas:

- Cuenta de caracteres
- Inserción de caracteres (patrón) de inicio y fin

- Inserción de patrones de inicio y fin

- Todas las tramas comienzan y finalizan con un patrón conocido
- Para evitar

Control y detección de errores

- Necesidad de técnicas de detección de errores ya que los medios disco de transmisión son propensos a errores, debido a los distintos tipos de perturbación existentes

- Atenuación

- La técnicas de detección de errores se aplican a nivel de la capa de enlace