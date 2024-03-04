# Fundamentos de Docker
## ¿Por qué aprender Docker?
Docker es una herramienta que te permite crear, gestionar y publicar contenedores.

## Diferencia entre máquinas virtuales, contenedores y servicios

**Máquina virtual**
- Necesita un SO
- Hardware real
- Mantenimiento
- Instalación de software

**Docker**
- Imagen base
- Sin hardware
- Control de versiones
- Sin software adicional

Entornos exactos
Fragmentación (microservicios)
Hardware limitado
Escalabilidad

## Instalación de Docker

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

## Conociendo Docker CLI

```shell
docker --version
```

```shell
docker info
```

```shell
docker images
```

```shell
docker ps
```

```shell
docker images --help
```

```shell
docker build --help
```

```shell
docker run --help
```

# Creación de imágenes con Docker
## Mi primera imagen de Docker

Dockerfile -> Build -> Docker image -> Run -> Docker container

```dockerfile
FROM nginx:latest

COPY /sitio /usr/share/nginx/html
```

## Creación de imágenes con Dockerfile

```
/mnt/c/Users/Stephan
```

```shell
docker build .
```

```shell
docker images
```

```shell
docker rmi -f b3ee59f75d94
```

```shell
docker build -t sitioweb:latest .
```

## De mi imagen a un contenedor usando CLI

```shell
docker run -it --rm -d -p 8080:80 --name web sitioweb
```

## Administrar mis imágenes de Docker

```shell
docker images sitioweb
```

```shell
docker images --filter=reference='*:1.0'
```

```shell
docker images --no-trunc
```

```shell
docker image tag sitioweb:latest smpc/sitioweb:latest
```

```shell
docker rmi smpc/sitioweb:latest
```

## Administrar mis contenedores de Docker

```shell
docker ps -a
```

```shell
docker ps --size
```

```shell
docker stop 6992e569add2
```

```shell
docker stats
```

## Mejorando mi Dockerfile

```Dockerfile
FROM python:3.12-alpine3.17

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY . .

CMD [ "python", "-m", "flask", "run", "--host=0.0.0.0" ]
```

# Volúmenes y redes de Docker

## Configurar volúmenes básicos con Docker

```shell
docker run -it --rm -d -p 8080:80 -v ./sitio:/usr/share/nginx/html/sitio --name web nginx
```

```Dockerfile
FROM nginx:latest

COPY /sitio /usr/share/nginx/html  

VOLUME [ "/sitio", "/usr/share/nginx/html" ]
```

## Configurar redes básicas en Docker

```shell
docker inspect web
```

```shell
docker run -it --rm -d -p 127.0.0.1:8080:80 --name web nginx
```

```shell
docker network ls
```

```shell
docker network create platzinet
```

# Publicando imágenes de Docker

## Mi primera imagen en Docker Hub

```shell
docker login
```

```shell
docker build -t spenalozacortes/linktree:latest .
```

```shell
docker push spenalozacortes/linktree:latest
```

```shell
docker run --name aninweb --rm -it -p 8080:80 spenalozacortes/linktree:latest
```

## Inspección y capas de un contenedor

```shell
docker run --name aninweb --rm -it -p 8080:80 spenalozacortes/linktree:latest /bin/bash
```

```shell
docker run --name aninweb --rm -it -p 8080:80 spenalozacortes/linktree:latest sh
```

```shell
exit
```

## Guardar y recuperar imágenes de Docker

```shell
docker save sitioweb > sitioweb.rar
```

```shell
docker load --input sitioweb.rar
```

# Orquestación de contenedores de Docker

## Introducción a Docker Compose

- Servicios
- Redes
- Volúmenes
- Config
- Secrets

## Despliega un conjunto de imágenes

docker.compose.yml

```yml
version: '3.7'

services:
	backend:
		image: backend
		build:
			context: ./backend
			dockerfile: Dockerfile
		ports: 
			- 5000:5000
	frontend:
		image: frontend
		build:
			context: ./frontend
			dockerfile: Dockerfile
		ports: 
			- 8080:80
		depends_on:
			- backend
```

```shell
docker compose build
```

```shell
docker compose up
```

