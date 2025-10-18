## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```
### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
nada, está vacia.
### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name cont-mysql --network net-wp -e MYSQL_ROOT_PASSWORD=snowpoom -e MYSQL_DATABASE=db_wordpress -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=snowpoom1 -v "C:\Users\SnowPoom\Documents\Sexto\constr\ejercicio3\db":/var/lib/mysql mysql:8

```
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
se crearon archivos de mysql dentro de la carpeta
### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name cont-wordpress --network net-wp -v "C:\Users\SnowPoom\Documents\Sexto\constr\ejercicio3\www":/var/www/html/ -p 9500:80 -e WORDPRESS_DB_HOST=cont-mysql -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=snowpoom1 -e WORDPRESS_DB_NAME=db_wordpress wordpress
```
### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1913" height="870" alt="image" src="https://github.com/user-attachments/assets/bcc179b5-81be-4f6b-bddd-61a95956a31d" />
<img width="1902" height="872" alt="image" src="https://github.com/user-attachments/assets/23c4416a-f056-4f78-8546-69334dd30dbd" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
Se recuperó el sitio web con la entrada creada anteriormente.

