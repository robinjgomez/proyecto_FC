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
