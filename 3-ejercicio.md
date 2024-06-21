## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create --driver bridge net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es .../var/lib/mysql
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
esta vacia

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name sql8 --network net-wp --env-file=sqlev.env -v C:\p3\ejercicio3\db:/var/lib/mysql mysql:8
```
````
sqlev.env file
MYSQL_ROOT_PASSWORD=1234
MYSQL_DATABASE=wordpress
MYSQL_USER=abc
MYSQL_PASSWORD=1234
````

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
ahora se refleja el contenido de la carpeta del contenedor
````
C:\p3\ejercicio3\db>dir
 El volumen de la unidad C es BOOTCAMP
 El número de serie del volumen es: 0246-9FF7

 Directorio de C:\p3\ejercicio3\db

21/06/2024  08:44    <DIR>          .
21/06/2024  08:44    <DIR>          ..
21/06/2024  08:43         6.291.456 #ib_16384_0.dblwr
21/06/2024  08:42        14.680.064 #ib_16384_1.dblwr
21/06/2024  08:44    <DIR>          #innodb_redo
21/06/2024  08:44    <DIR>          #innodb_temp
21/06/2024  08:42                56 auto.cnf
21/06/2024  08:43         2.943.824 binlog.000001
21/06/2024  08:44               158 binlog.000002
21/06/2024  08:44                32 binlog.index
21/06/2024  08:43             1.705 ca-key.pem
21/06/2024  08:43             1.108 ca.pem
21/06/2024  08:43             1.108 client-cert.pem
21/06/2024  08:43             1.705 client-key.pem
21/06/2024  08:44        12.582.912 ibdata1
21/06/2024  08:44        12.582.912 ibtmp1
21/06/2024  08:43             5.661 ib_buffer_pool
21/06/2024  08:43    <DIR>          mysql
21/06/2024  08:44        32.505.856 mysql.ibd
21/06/2024  08:43    <JUNCTION>     mysql.sock [...]
21/06/2024  08:43               124 mysql_upgrade_history
21/06/2024  08:43    <DIR>          performance_schema
21/06/2024  08:43             1.705 private_key.pem
21/06/2024  08:43               452 public_key.pem
21/06/2024  08:43             1.108 server-cert.pem
21/06/2024  08:43             1.705 server-key.pem
21/06/2024  08:43    <DIR>          sys
21/06/2024  08:44        16.777.216 undo_001
21/06/2024  08:44        16.777.216 undo_002
21/06/2024  08:43    <DIR>          wordpress
              22 archivos    115.158.083 bytes
               8 dirs  557.229.604.864 bytes libres
````

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name wp --network net-wp -p 9500:80 -env-file=wpev.env -v C:\p3\ejercicio3\www:/var/www/html  wordpress
```
````
wpev.env file
WORDPRESS_DB_HOST=1234
WORDPRESS_DB_USER=abc
WORDPRESS_DB_PASSWORD=1234
WORDPRESS_DB_NAME=wordpress
````

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA



