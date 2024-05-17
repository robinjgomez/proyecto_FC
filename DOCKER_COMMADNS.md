# Comandos Útiles de Docker y Docker Compose

## Comandos Docker Compose

### Levantar el Servicio en Modo Demonio
Este comando levanta todos los servicios definidos en el archivo docker-compose.yaml en segundo plano.
```bash
docker-compose up -d
```

### Listar los Servicios Activos y No Activos
Muestra el estado de los servicios definidos en el archivo docker-compose.yaml, indicando si están activos o no.
```bash
docker-compose ps
```

### Detener el Servicio
Detiene y elimina todos los contenedores, redes y volúmenes definidos en el archivo docker-compose.yaml.
```bash
docker-compose down
```

## ComandosDocker

### Listar Imágenes Instaladas
Muestra una lista de todos los contenedores activos y no activos en el sistema.
```bash
docker images
```

### Detener un Contenedor
Detiene un contenedor en ejecución especificado por su ID o nombre.
```bash
docker stop [CONTAINER_ID o CONTAINER_NAME]
```
