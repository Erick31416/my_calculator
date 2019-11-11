```
Notas para aprovechar estos apuntes.
Cada vez que los retomes repasa y simplifica el destilado
y al ser estos unos apuntes a largo plazo , crea un pocillo.

la proxima vez puedes subir esto a git.

El objetivo es tener unos apuntes en github organizados por temas, con indices, destilados , pocillos....

Un destilado no puede tener mas de 12 puntos.
```
 
# CONTENEDORES 

## **Desitilado**

1. **docker run hello-world** -> baja una imagen y ejecuta un contenedor.
2. **docker run -it ubuntu bash** -> se mete dentro de un conteidor y ejecuta el comando bash.
3. `docker image` --help
4. dockerhub -> recuerda que existe ▼
5. docker container --help
6. docker image ls -> te muestra todas las imágenes que tienes descargadas
7. docker image pull ubuntu -> te permite descargar una imagen de un repositorio.
8. docker rmi \<nombre de la imagen\> para **borrar** una imagen
9. Las imágenes tipo : _doker pull ubuntu_ es oficial y Las imágenes tipo: _docker pull bliztone/baseimage_ son imagenes no oficiales.
10. docker stop 1e0e92b8255e para parar el contenedor
11. tambien tienes docker kill , docker restart , docker pause docker unpause
12. docker cp archivo.txt midocker:. esto copia el archivo archivo.txt al docker llamado midocker, a la ruta  /
- docker cp midocker:archivo2.txt . esto copia el archivo del docker a fuera del docker
- docker ps 
  - docker ps -a -> para ver todos los contenedores parados
- docker run -d --name ejemplo blitznote/baseimage -> para poner nombre a un contenedor.
- docker -d run blitznote/baseimage sleep 100
  - -d hace que el contenedor se ejecute en segundo plano asi puedes hacer cosas, sin -d de bloquea el terminal.
  - sleep 100 es el comando que ejecutara el contenedor.
- docker commit test01 atareao/nginx:autocertificado

### Puntero a - https://www.atareao.es/tutorial/docker/ejecutar-contenedores-docker/

# Conceptos basicos

## Imagen vs contenedores:
- Un contenedor es una instancia de una imagen.
### Instalando :
Existen dos versiones de dokker yo estoy viendo un manual de comunity.

Como todos las aplicaciones hay tres canales de actualizacion: **Stable** . Test. Nightly.

### probando:
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

docker run -it ubuntu bash
	
## GESTIONAR IMAGENES DOCKER.

		docker hub.[existe]
		# docker image --help #->ayuda
		build -> costruir tus propias imágenes 
		history -> historya de una imagen en cocreto.
		inspect -> detalles y entrañas de una imagen.
		# docker image ls -> te muestra todas las imágenes que tienes descargadas
		prune -> borra las imagnes que no estes utilizando.
		# docker image pull ubunto -> te permite descargar una imagen de un repositorio.
		push permite subir una imagen a un repositorio.
		# docker rmi <nombre de la imagen> pra borrar una imagen
		-----
		# si te descargas una imagen que sea como : doker pull ubuntu, es oficial
		# si te cescargas una imagen como docker pull bliztone/baseimage son imagenes que han creado otras personas.
	Gestionado contenedores con docker.
		# docker container --help
		--
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
Atareao aconseja hacer las pruebas con un centenedor de Nginx sobre Alpine, 
Alpine es una distribucion linux enfocada a la simplicidad, eficiendia de recursos y seguridad.
Atareao se vuelve a liar y me manda estos dos links que pueden estar muy intereseantes:
https://www.atareao.es/tutorial/raspberry-pi-primeros-pasos/
https://www.atareao.es/tutorial/raspberry-pi-primeros-pasos/infraestructura-lemp-con-nginx-en-raspberry/
- docker images | nginx -> veo las caracteristicas de una imagen concreta.
- docker exec -it test01 sh
- ps -ef
- docker run -d --name test01 -p 81:80 nginx:alpine
- docker run -d --name test01 -p 80:80 -p 443:443 nginx:alpine
- exponer el puerto 443 del contenedor permite acceder mediante https:
- certificados autofirmados 
Aqui hay mucha tela que cortar, me he quedado bloqueado con un problema en los certificados.
# Buscar: certificados https, configuracion de servidor engins arquitectura lemp... 

