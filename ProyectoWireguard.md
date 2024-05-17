# Proyecto VPN con WireGuard en Docker

## Descripción
Este proyecto de fin de curso del ciclo superior de ASIR del IES San Vicente plantea la implementacion de un servicio VPN utilizando WireGuard en un contenedor Docker. El objetivo es demostrar las ventajas de usar contenedores Docker para implementar servicios VPN en pequeñas y medianas empresas (PYMES).

El repositorio se ha creado a fin hacer disponible públicamente al jurado y a futuro a otros estudiantes, los aspectos técnicos del proyecto que no se incluyen en el propio informe como la version final utilizada de el archivo yaml utilizado para crear el contenedor con WireGuard y otros aspectos relativos a la preparación previa como el propio sistema operativo elegido y su configuración, la instalación de docker y docker compose en el entorno elegido, comandos básicos para la manipulacion del servicio

## Contenidos
- [Descripción del Proyecto](#descripción)
- [Sistema operativo](#Sistema Operativo)
- [Instalación](#instalación)
- [Configuración de Docker Compose](#configuración-de-docker-compose)
- [Estructura del Repositorio](#estructura-del-repositorio)


## Sistema Operativo
Justificacón del sistema operativo seleccionado como base para Docker [SO.md](SO.md).

## Instalación
Para instrucciones detalladas sobre cómo instalar Docker y Docker Compose, consulta [INSTALLATION.md](INSTALLATION.md).

## Configuración de Docker Compose
El archivo `docker-compose.yaml` se utiliza para configurar y desplegar el servicio WireGuard. Para una explicación detallada, consulta [DOCKER_COMPOSE_SETUP.md](DOCKER_COMPOSE_SETUP.md).

## Estructura del Repositorio
- `README.md`: Descripción general del proyecto.
- `INSTALLATION.md`: Instrucciones de instalación.
- `DOCKER_COMPOSE_SETUP.md`: Detalles de configuración de Docker Compose.
- `docker-compose.yaml`: Archivo de configuración para Docker Compose.
