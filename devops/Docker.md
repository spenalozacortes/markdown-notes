# Introducción

## Las tres áreas en el desarrollo de software profesional
- Construir
- Distribuir
- Ejecutar

### Problemas al construir software
- Entorno de desarrollo
- Dependencias
- Entorno de ejecución
- Equivalencia con entorno productivo
- Servicios externos

### Problemas al distribuir software
- Divergencia de repositorios
- Divergencia de artefactos
- Versionado

### Problemas al ejecutar software
- Compatibilidad con el entorno productivo
- Dependencias
- Disponibilidad de servicios externos
- Recursos de hardware

Docker te permite construir, distribuir y ejecutar cualquier aplicación en cualquier lado.

## Virtualización

### Problemas de las VMs
- **Peso**. En el orden de los GBs. Repiten archivos en común. Inicio lento.
- **Costo de administración**. Necesita mantenimiento igual que cualquier otra computadora.
- **Múltiples formatos**. VDI, VMDK, VHD, raw, etc.

### Contenedores
- Flexibles
- Livianos
- Portables
- Bajo acoplamiento
- Escalables
- Seguros

## Qué es y cómo funciona Docker

### Arquitectura de Docker
- Docker daemon / server
- REST API
- Client / Docker CLI

- Container
- Image
- Data volumes
- Network

# Contenedores

## Primeros pasos: hola mundo

```shell
docker run hello-world
```

## Comprendiendo el estado de Docker

```shell
docker rename hello-platzi hola-platzi
```

```shell
docker container prune
```

## El modo interactivo

```shell
docker run -it ubuntu
```

## Ciclo de vida de un contenedor

```shell
docker run --name alwaysup -d ubuntu tail -f /dev/null
```

```shell
docker exec -it alwaysup bash
```

```shell
ps -aux
```

```shell
docker inspect --format '{{.State.Pid}}' alwaysup
```

## Exponiendo contenedores

```shell
docker run -d --name proxy nginx
```

```shell
docker rm -f alwaysup
```

```shell
docker run --name proxy -p 8080:80 nginx
```

```shell
docker logs -f proxy
```

```shell
docker logs --tail 10 -f proxy
```

# Datos en Docker

## Bind mounts

```shell
docker run -d --name db mongo
```

```shell
docker exec -it db bash
```

```mongosh
mongosh
show dbs
use platzi
db.users.insert({"nombre": "fanjo"})
db.users.find()
```

```shell
mkdir mongodata
```

```shell
docker run -d --name db -v /mnt/c/Users/Stephan/Documents/dockerdata/mongodata:/data/db mongo
```

## Volúmenes

```shell
docker volume ls
```

```shell
docker volume create dbdata
```

```shell
docker run -d --name db --mount src=dbdata,dst=/data/db mongo
```

## Insertar y extraer archivos de un contenedor

```shell
docker cp prueba.txt copytest:/testing/test.txt
```

```shell
docker cp copytest:/testing localtesting
```

tmpfs mount

# Imágenes

## Conceptos fundamentales de Docker: imágenes

```shell
docker image ls
```

```shell
docker pull ubuntu:20.04
```

## Construyendo una imagen propia

```dockerfile
FROM ubuntu:latest

RUN touch /usr/src/hola-platzi.txt
```

```shell
docker build -t ubuntu:platzi .
```

```shell
docker tag ubuntu:platzi spenalozacortes/ubuntu:platzi
```

```shell
docker push spenalozacortes/ubuntu:platzi
```

## El sistema de capas

```shell
docker history ubuntu:platzi
```

docker commit

# Docker como herramienta de desarrollo

## Usando Docker para desarrollar aplicaciones

```Dockerfile
FROM node:12

COPY [".", "/usr/src/"]

WORKDIR /usr/src

RUN npm install

EXPOSE 3000

CMD ["node", "index.js"]
```

```shell
docker run -d --rm -p 3000:3000 platziapp
```

## Aprovechando el caché de capas para estructurar correctamente tus imágenes

```Dockerfile
FROM node:12

COPY ["package.json", "package-lock.json", "/usr/src/"]

WORKDIR /usr/src

RUN npm install

COPY [".", "/usr/src/"]

EXPOSE 3000

CMD ["npx", "nodemon", "index.js"]
```

```shell
docker run --rm -p 3000:3000 -v  $(pwd)/index.js:/usr/src/index.js platziapp
```

## Docker networking: colaboración entre contenedores

# Docker compose

## Docker Compose: la herramienta todo en uno

## Subcomandos de Docker Compose

## Docker Compose como herramienta de desarrollo

## Compose en equipo: override

# Docker avanzado

## Administrando tu ambiente de Docker

## Deteniendo contenedores correctamente: SHELL vs. EXEC

## Contenedores ejecutables: ENTRYPOINT vs CMD

## El contexto de build

## Multi-stage build

## Docker-in-Docker

