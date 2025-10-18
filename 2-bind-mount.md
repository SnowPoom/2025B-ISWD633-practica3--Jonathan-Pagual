# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
```
docker run --name nginx-vol -d -v "C:\Users\SnowPoom\Documents\Sexto\constr\nginx\html":/usr/share/nginx/html -P nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
Se puede visualizar un error 403 forbidden al ingresr al servidor nginx
### ¿Qué pasa con el archivo index.html del contenedor?
Parece que el archivo index que normalmente suele estar en el contenedor ahora no lo está y el directorio /usr/share/nginx/html esta vacío.
### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Se muestra el template que se descargó en la página.
### Eliminar el contenedor
```
docker rm -f nginx-vol
```
### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Se vuelve a cargar el html que se descargó antes, parece ser que persiste los de la carpeta host aunque el contenedor sea eliminado.
