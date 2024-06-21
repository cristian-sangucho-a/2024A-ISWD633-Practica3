# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la documentación
![Volúmenes](imagenes/volumen-host.PNG)
```
docker run -d --name nginx -p 80:80 -v C:\html:/usr/share/nginx/html nginx:alpine 
```

### ¿Qué sucede al ingresar al servidor de nginx?
403 Forbidden
se muestra el error 403 que indica que el acceso esta restringido

### ¿Qué pasa con el archivo index.html del contenedor?
no se mostro por que no existe

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
el template se muestra al abrir la direccion del puerto mapeado

### Eliminar el contenedor
```
docker ps -a
docker rm -f id
```
el primer comando lista todos los contenedores 
el segundo elimina el contenedor segun la id

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
como el volumen ya esta definido aun carga la pagina web, aun asi el directorio este vacio
por que el link entre el contenedor y el volumen es directo.

### ¿Qué hace el comando pwd?
imprimir el directorio de trabajo actual, muestra los demas directorios y ficheros
Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

