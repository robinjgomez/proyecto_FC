# Sistema Operativo Base para Docker y el Servidor WireGuard

El sistema operativo base para Docker y el servidor WireGuard de este proyecto es:

- **Ubuntu 22.04.4 LTS**
  - **Release:** 22.04
  - **Codename:** jammy

Docker, como proyecto de código abierto, fue originalmente desarrollado utilizando características de aislamiento de recursos del kernel Linux. A pesar de que pocos años después los responsables del proyecto anunciaban soporte para sistemas Mac OS X y Windows con el fin de poder funcionar sobre el mayor número de equipos posibles, sigue siendo Linux la elección acertada cuando se requiere ejecutar contenedores Docker en un entorno de producción. Esto se debe a una serie de razones, entre ellas:

## Razones para Elegir Linux

- **Rendimiento:** Linux es el sistema operativo nativo para Docker y, siendo así, los contenedores se ejecutan directamente en el kernel, lo que resulta en una menor sobrecarga y una mayor eficiencia.
- **Compatibilidad:** La mayoría de las imágenes de Docker están optimizadas y probadas para su ejecución en entornos Linux. Esto garantiza compatibilidad y estabilidad en entornos de producción.
- **Seguridad:** Los contenedores en Linux se benefician de las características de seguridad integradas en el kernel de Linux, como los espacios de nombres y los controles de acceso, que ayudan a aislar los contenedores y protegerlos contra posibles vulnerabilidades y ataques.
- **Escalabilidad:** Linux es altamente escalable y se puede implementar en una variedad de entornos de producción, desde servidores físicos hasta máquinas virtuales y plataformas en la nube.

## Implementación sobre Docker

Uno de los objetivos de este proyecto es la implementación sobre un contenedor de Docker. Por todas las razones citadas anteriormente, queda clara la elección de Linux, que además vuelve a ser un punto a favor de la economía del proyecto al tratarse de un SO de código abierto y ser altamente compatible con casi cualquier entorno empresarial. Esto permite elegir desde un hardware básico como un Raspberry Pi u otro mini ordenador hasta una máquina virtual dentro de la infraestructura que ya tenga montada nuestro futuro cliente para la implementación.

## Actualización del Sistema

Como en toda instalación de software sobre sistemas Linux, es básico como primer paso asegurarnos de comenzar por una actualización de la lista de paquetes disponibles en los repositorios y posterior actualización de los paquetes instalados en el sistema a las versiones más recientes disponibles en los repositorios configurados.

### Comandos para Actualización

Para sistemas basados en Debian, como Debian, Ubuntu y Raspbian:
```sh
apt-get update
apt-get upgrade
