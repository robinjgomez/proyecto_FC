# Creación del Servicio WireGuard

Con Docker y Docker Compose instalados, podemos pasar a los aspectos de configuración que se relacionan directamente con el servicio VPN WireGuard y es en esta etapa donde entramos a utilizar Docker Compose.

Docker Compose es una herramienta útil para coordinar una o varias imágenes de contenedor en un solo equipo host. En Compose, se usa un archivo YAML para configurar los servicios de la aplicación. Después, con un solo comando, se crean (durante la primera ejecución) y se inician todos los servicios o se detienen. Esto se traduce a futuro en varias ventajas interesantes para nuestro proyecto:

- Definiremos el archivo YAML de configuraciones básicas para nuestro servicio con todas las características deseadas una sola vez.
- Si a futuro queremos realizar modificaciones técnicas al servicio, bastará con modificar el archivo de configuración YAML, detener el servicio y lanzarlo nuevamente. De forma automática, cargará atendiendo a los cambios realizados.
- Podemos tener varios archivos de configuración listos con diferentes características para aplicar en determinados casos.
- Con el mismo archivo podemos lanzar simultáneamente múltiples instancias del mismo servicio en el mismo o en diferentes dispositivos.
- Al estar pensado para manejar múltiples contenedores en el mismo archivo YAML, podemos incluir uno o varios servicios adicionales según nuestra conveniencia, como un servidor de archivos o bases de datos.

Dado que estamos trabajando con contenedores, es común encontrarnos que para la mayoría de los servicios populares, ya alguien ha creado una configuración funcional y la ha colgado en algún repositorio para que esté disponible de forma pública tanto en formato Docker como para Docker Compose. En muchos casos, podemos usar directamente esa configuración o crear nuestra propia versión a partir de ella. En ocasiones, el propio creador del servicio cuelga en su propia web oficial una versión probada y funcional recomendada de instrucciones Docker y Docker Compose.

A pesar de que una de las características claves de WireGuard es que es de fácil manejo, en su versión original resulta suficiente para el usuario común, crear, modificar y eliminar usuarios VPN. Tomando en cuenta que se quiere ofrecer un producto accesible a nivel de configuración básica para el usuario final, para este proyecto he seleccionado como base el código de configuración de un repositorio de GitHub con una versión modificada de WireGuard llamada WireGuard Easy. Esta versión incluye una consola web para la administración de los usuarios, lo que lo hace más manejable por parte del usuario final, quien podrá, con los conocimientos que se le impartirán en una inducción de 20 minutos, incluir, suspender y/o eliminar usuarios con acceso VPN a su red empresarial.

La base del proyecto que básicamente define las configuraciones del servicio está disponible para su descarga en el repositorio citado anteriormente en la siguiente URL:
[https://github.com/wg-easy/wg-easy](https://github.com/wg-easy/wg-easy)

La versión modificada y final del archivo de configuración adaptada a este proyecto está disponible en [docker-compose.yaml](docker-compose.yaml).

## A continuación se detalla de forma más específica cada una de sus secciones y cómo pueden ser modificadas para una personalización completa

### 1. Volúmenes (volumes)

Los volúmenes son una característica esencial que permite la persistencia de datos fuera de los contenedores. Esto significa que los datos almacenados en un volumen no se eliminan cuando se detiene o reinicia un contenedor, lo que lo convierte en una solución ideal para almacenar datos que necesitan ser accedidos por múltiples contenedores o que deben conservarse incluso después de que un contenedor haya finalizado su ciclo de vida.

La primera declaración del archivo es del volumen de nombre `etc_wireguard`, de esta forma estará disponible de forma global, lo que podría resultar útil si más adelante otros servicios declarados en el mismo archivo pueden acceder a los datos de ese volumen. Dentro de la sección services nuevamente se hará una declaración de volumen definiendo la ruta y mapeando la ruta de los datos dentro del contenedor contra los del anfitrión.

### 2. Servicios (services)

La sección **services** del archivo `docker-compose.yaml` define los servicios que se ejecutarán dentro del entorno Docker Compose. En este caso, solo hay un servicio (contenedor) definido que es `wg-easy`.

Dentro de la sección servicios hay varias subsecciones explicadas a continuación:

- **Environment:** Define las variables de entorno que pasarán al contenedor. Estas variables pueden configurar varios aspectos del servicio:
  - `LANG=`: Configura el idioma del servicio.
  - `WG_HOST=`: Esta variable es muy importante ya que define nuestra dirección IP pública o dominio si lo tenemos que apunte a esa IP pública y nos lleva hasta nuestro servidor VPN.
  - `PASSWORD=`: Establece una contraseña para acceder a la interfaz web de wg-easy, habilitada para crear, modificar y eliminar usuarios con acceso VPN.
  - `PORT=51821`: Define el puerto en el host que se usará para la interfaz web. Por defecto es 51821, es necesario descomentar y modificar si se desea cambiar el puerto.
  - `WG_PORT=51820`: Por defecto es 51820, especifica el puerto que usará WireGuard dentro del contenedor.
  - `WG_DEFAULT_ADDRESS=10.8.0.x`: Por defecto es la red 10.8.0.x, define la red interna del contenedor de la que se asignarán direcciones IP para los clientes que se conecten a la VPN.
  - `WG_DEFAULT_DNS=1.1.1.1`: Establece el servidor DNS que usarán los clientes de WireGuard. Por defecto apunta al DNS público operado por Cloudflare.
  - `WG_MTU=1420`: Por defecto 1420, configura el tamaño máximo de unidad de transmisión (MTU) para WireGuard.
  - `WG_ALLOWED_IPS=`: Define las subredes permitidas a través del túnel de WireGuard.
  - `WG_PERSISTENT_KEEPALIVE`: Establece el intervalo de keepalive para mantener el túnel activo, útil en configuraciones NAT. Este valor es en segundos y determina cada cuánto tiempo el cliente envía un paquete keepalive para mantener la conexión.
  - `WG_PRE_UP, WG_POST_UP, WG_PRE_DOWN, WG_POST_DOWN`: Dentro de estas variables se pueden especificar scripts para que sean ejecutados antes o después de establecer un túnel VPN y antes o después de finalizar un túnel VPN.
  - `UI_TRAFFIC_STATS`: Su valor por defecto es true, esta variable habilita las estadísticas de tráfico en la interfaz web de wg-easy. Permite ver el uso de datos en la interfaz gráfica.
  - `UI_CHART_TYPE`: Esta variable configura el tipo de gráfico que se mostrará en la interfaz web para visualizar las estadísticas de tráfico. Las opciones disponibles son:
    - `0`: Desactiva los gráficos.
    - `1`: Muestra un gráfico de líneas.
    - `2`: Muestra un gráfico de área.
    - `3`: Muestra un gráfico de barras.

- **Image:** Esta subsección especifica la imagen Docker que se utilizará para crear el contenedor. En este caso, se está utilizando la imagen `ghcr.io/wg-easy/wg-easy`.

- **Container_name:** Define el nombre del contenedor. Esto facilita la administración del contenedor al darle un nombre amigable ya que por defecto Docker le asignará un UID numérico poco amigable y difícil de recordar a la hora de administrarlos.

- **Volumes:** Monta el volumen definido anteriormente (`etc_wireguard`) en el directorio `/etc/wireguard` dentro del contenedor. Esto permite que los datos en `/etc/wireguard` se mantengan persistentes y se compartan entre reinicios o recreaciones del contenedor.

- **Ports:** Mapea los puertos del contenedor a los puertos del host.
  - `51820:51820/udp`: Mapea el puerto 51820 del contenedor al puerto 51820 UDP del host. Este puerto se usa para la comunicación de WireGuard.
  - `51821:51821/tcp`: Mapea el puerto 51821 del contenedor al puerto 51821 TCP del host. Este puerto se usa para acceder a la interfaz web de wg-easy.

- **Restart:** Define la política de reinicio del contenedor. `unless-stopped` indica que el contenedor se reiniciará automáticamente si se detiene de forma inesperada.

- **Cap_add:** Otorga al contenedor capacidades adicionales. En este caso, se le otorgan las capacidades `NET_ADMIN` para la administración de red y `SYS_MODULE` para cargar módulos del kernel.

- **Sysctls:** Configura variables del kernel del sistema operativo dentro del contenedor.
  - `net.ipv4.ip_forward`: Se establece con valor 1 para habilitar el reenvío de paquetes IP dentro del contenedor, necesario para que wg-easy funcione como una VPN.
  - `net.ipv4.conf.all.src_valid_mark=1`: Permite el marcado de paquetes de origen para el reenvío de IP.
