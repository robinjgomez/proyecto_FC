# Instalación de Docker y Docker Compose

Tal como se menciona en capítulos anteriores, parte fundamental del proyecto es el uso de contenedores y en este punto tenemos necesariamente que hablar de Docker. Si bien no es la única solución existente para la creación de entornos de trabajo aislados en contenedores, es sin duda la más ampliamente extendida.

Docker abarca aproximadamente un 75% de cuota de mercado gracias a su facilidad de uso, amplia comunidad y ecosistema de herramientas que le han convertido en la opción preferida para muchas empresas y desarrolladores. Entre otras alternativas a Docker que se reparten el 25% restante podemos mencionar a RKT, PodMan, Singularity, Linux Containers (LXC) y OpenVz.

La instalación de Docker en entornos Linux se puede realizar de diversas formas. Muchas distribuciones de Linux incluyen Docker y Docker Compose en sus repositorios oficiales. Para este caso y considerando que trabajamos en una distribución Ubuntu, procederemos a la instalación utilizando el administrador de paquetes de su distribución.

```bash
# Instalar Docker y docker compose
sudo apt-get install docker.io docker-compose

# Comprobando la versión instalada de docker y docker-compose
docker --version
docker-compose -version



