```
Notas para aprovechar estos apuntes.  
Cada vez que los retomes repasa y simplifica el destilado
y al ser estos unos apuntes a largo plazo , crea un pocillo.

la proxima vez puedes subir esto a git.

El objetivo es tener unos apuntes en github organizados por temas, con indices, destilados , pocillos....

Un destilado no puede tener mas de 12 puntos.

<elemento> | <elementos>
[opcional] (ouno|uotro)
git diff (--catched |--staged ) [color] [<files>]
▼ pierde importancia
▲ gana importancia
🌓︎ contrastar, repasar , comprobar, poner en duda
```
 
# CONTENEDORES 

## **Desitilado**

1. `docker run hello-world` -> baja crea y arranca un contenedor a parir de la imagen hello-world.
1. `docker run -it ubuntu bash` -> run (crea y arranca a partir de una imagen) -i de interactive , t de terminal
1. `docker image|container  --help`
1. ▲ `docker image ls` -> te muestra todas las imágenes que tienes descargadas
1. ▼ dockerhub -> recuerda que existe 
1. `docker image pull ubuntu` -> te permite descargar una imagen de un repositorio.
1. `docker rmi <nombre_imagen>` para **borrar** una imagen
1. Las imágenes tipo : `doker pull ubuntu` son oficiales y Las imágenes tipo: `docker pull bliztone/baseimage` son imagenes no oficiales.
1. `docker stop 1e0e92b8255e` para parar el contenedor
1. tambien tienes docker kill , docker restart , docker pause docker unpause
1. `docker cp archivo.txt midocker:. ` esto copia el archivo archivo.txt al docker llamado midocker, a la ruta  /
1. `docker rm test01` para borrar el contenedor test01 🌓︎->primero hay que pararlo.
- `docker cp midocker:archivo2.txt .` esto copia el archivo del docker a fuera del docker
- `docker ps` 
  - ▲▲`docker ps -a` -> para ver todos los contenedores parados
- 🌓︎ `docker run -d --name <nombre_nuevo>` ejemplo blitznote/baseimage -> para poner nombre a un contenedor.
- `docker -d run blitznote/baseimage sleep 100`
  - -d hace que el contenedor se ejecute en segundo plano asi puedes hacer cosas, sin -d de bloquea el terminal.
  - sleep 100 es el comando que ejecutara el contenedor.
- docker commit test01 atareao/nginx:autocertificado

### Puntero a - https://www.atareao.es/tutorial/docker/ejecutar-contenedores-docker/

# Conceptos basicos

## Imagen vs contenedores:
- Un contenedor es una instancia de una imagen.
## Instalando :
- Existen dos versiones de dokker yo estoy viendo un manual de comunity.

Como casi todas las aplicaciones hay tres canales de actualizacion: **Stable** . Test. Nightly.

## probando:
ejecutando : ' docker run hello-world' 
obtendras:
```
		Hello from Docker!
		This message shows that your installation appears to be working correctly.

		To generate this message, Docker took the following steps:
		1. The Docker client contacted the Docker daemon.
		2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
			(amd64)
		3. The Docker daemon created a new container from that image which runs the
			executable that produces the output you are currently reading.
		4. The Docker daemon streamed that output to the Docker client, which sent it
			to your terminal.

		To try something more ambitious, you can run an Ubuntu container with:
		$ docker run -it ubuntu bash

		Share images, automate workflows, and more with a free Docker ID:
		https://hub.docker.com/

		For more examples and ideas, visit:
		https://docs.docker.com/get-started/
```

para meterte dentro de un contenedor :

`docker run -it ubuntu bash`

`docker run -it <contenedor> <comando>`
	
## GESTIONAR IMAGENES DOCKER.

docker hub.[existe]

docker image --help #->ayuda

build -> costruir tus propias imágenes 

history -> historial de una imagen en cocreto.

inspect -> detalles y entrañas de una imagen.

docker image ls -> te muestra todas las imágenes que tienes descargadas

prune -> borra las imagnes que no estes utilizando.

docker image pull ubuntu -> te permite descargar una imagen de un repositorio.

push permite subir una imagen a un repositorio.

docker rmi <nombre de la imagen> pra borrar una imagen


si te descargas una imagen que sea como : doker pull ubuntu, es oficial

si te cescargas una imagen como docker pull bliztone/baseimage son imagenes que han creado otras personas.

##Gestionado contenedores con docker.

# docker container --help

[lo mismo es :] docker container run blitznote/baseimage

#[lo mismo es :] docker run blitznote/baseimage

---

[lo mismo es :] docker ps 

[lo mismo es :] docker container ls.

#docker ps -a -> para ver todos los contenedores parados

----

#docker run -d --name ejemplo blitznote/baseimage -> para poner nombre a un contenedor.

#docker -d run blitznote/baseimage sleep 100

#con -d puedes hacer cosas, sin -d de bloquea el terminal.

#sleep 100 es el comando que ejecutara el contenedor.

#docker stop 1e0e92b8255e para parar el contenedor

#tambien tienes docker kill , docker restart , docker pause docker unpause

---

docker cp archivo.txt midocker:. esto copia el archivo archivo.txt al docker llamado midocker, a la ruta  /

docker cp midocker:archivo2.txt . esto copia el archivo del docker a fuera del docker


ahora toca esto :https://www.atareao.es/tutorial/docker/ejecutar-contenedores-docker/ #la-solución-no-deseable

## EJECUTAR CONTENEDORES DOCKER

Atareao, aconseja utilizar Bash-it . {https://www.atareao.es/software/utilidades/bash-it/} [https://www.atareao.es/software/utilidades/bash-it/] pero para no perderme en las profundidades, de los hipertextos, voy a pasar mucho del tema de momento.

Atareao aconseja hacer las pruebas con un contenedor de Nginx sobre Alpine.

Alpine es una distribucion linux enfocada a la simplicidad, eficiendia de recursos y seguridad.

Atareao se vuelve a liar y me manda estos dos links que pueden estar muy intereseantes:
https://www.atareao.es/tutorial/raspberry-pi-primeros-pasos/
https://www.atareao.es/tutorial/raspberry-pi-primeros-pasos/infraestructura-lemp-con-nginx-en-raspberry/
- docker images | nginx -> veo las caracteristicas de una imagen concreta.
- docker exec -it test01 sh
- ps -ef
- docker run -d --name test01 -p 81:80 nginx:alpine
- docker run -d --name test01 -p 80:80 -p 443:443 nginx:alpine
- mover archivos dentro y fuera del contenedor [ docker cp nginx-selfsigned.key test01:/ ]
- exponer el puerto 443 del contenedor permite acceder mediante https:
- certificados autofirmados [los navegadores no los cosideran seguros, si cualquiera se los puede firmas a si mismo.. ¿que demuestran? esto "solo" sirve para aprender]
- exponer volumenes: igual que puedes redirigir de un puerto a otro, puedes redirigir de una direcion del contenedor a una direccion del equipo, asi te ahorras crear un contenedor nuevo cada vez.

		docker run \
		-d -p  80:80 \
		-p 443:443 \
		-v "$(pwd)"/crt:/etc/ssl/certs \
		-v "$(pwd)"/conf:/etc/nginx/conf.d \
		-v "$(pwd)"/web:/var/www/html \
		--name test01 atareao/nginx:autocertificado
- si tienes un contenedor y no sabes que volumenes tienes espuestos:

		Puedes inspeccionar el contenedor con:
		docker inspect test01

		Te saldrá un extenso JSON. Busca la sección "Mounts"

		Si tienes instalado jq (una herramienta para extraer información de JSON desde línea de comandos usando un lenguaje propio para la consulta) puedes utilizarlo en la siguiente forma:

		docker inspect test01 | jq '.[].Mounts[]| "\(.Source):\(.Destination)"'
		y te imprimirá algo del estilo:

		/home/foo/folder/crt:/etc/ssl/certs
		/home/foo/folder/conf:/etc/nginx/conf.d
		/home/foo/folder/web:/var/www/html
