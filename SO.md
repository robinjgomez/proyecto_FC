# Sistema Operativo Base para Docker y el Servidor WireGuard

El sistema operativo base para Docker y el servidor WireGuard de este proyecto es:

**Ubuntu 22.04.4 LTS**
- **Release:** 22.04
- **Codename:** jammy

Docker, como proyecto de código abierto, fue originalmente desarrollado utilizando características de aislamiento de recursos del kernel Linux. A pesar de que pocos años después los responsables del proyecto anunciaron soporte para sistemas Mac OS X y Windows con el fin de poder funcionar sobre el mayor número de equipos posibles, sigue siendo Linux la elección acertada cuando se requiere ejecutar contenedores Docker en un entorno de producción, motivado entre otros por una serie de razones como:

- **Rendimiento:** Linux es el sistema operativo nativo para Docker y, siendo así, los contenedores se ejecutan directamente en el kernel, lo que resulta en una menor sobrecarga y una mayor eficiencia.
- **Compatibilidad:** La mayoría de las imágenes de Docker están optimizadas y probadas para su ejecución en entornos Linux. Esto garantiza compatibilidad y estabilidad en entornos de producción.
- **Seguridad:** Los contenedores en Linux se benefician de las características de seguridad integradas en el kernel de Linux, como los espacios de nombres y los controles de acceso, que ayudan a aislar los contenedores y protegerlos contra posibles vulnerabilidades y ataques.
- **Escalabilidad:** Linux es altamente escalable y se puede implementar en una variedad de entornos de producción, desde servidores físicos hasta máquinas virtuales y plataformas en la nube.

Siendo uno de los objetivos de este proyecto la implementación sobre un contenedor de Docker, y por todas las razones citadas anteriormente, queda clara la elección de Linux, que además vuelve a ser un punto a favor de la economía del proyecto al tratarse de un SO de código abierto y ser altamente compatible con casi cualquier entorno empresarial. Esto permite elegir desde un hardware básico como un Raspberry Pi u otro mini ordenador hasta una máquina virtual dentro de la estructura que ya tenga montada nuestro futuro cliente para la implementación.
