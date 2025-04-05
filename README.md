# PPS-Unidad3Actividad1-AdrianCurtoSanchez

Creación de entornos:
- [Vulnerables](#entornos-vulnerables)
- [Pruebas](#entornos-pruebas)


## Entornos vulnerables

Partiendo del fichero [docker-compose.yml](./entorno-vulnerables-adriancurtosanchez/docker-compose.yml) levantaremos las diferentes máquinas vulnerables, pero antes deberemos establecer el directorio de la máquina anfitrión donde se guadarán los datos del volumen del servicio Kali.

![Kali volume](images/kali-volume.png)

Ejecutaremos los servicios desde la carpeta en la que se encuentra el fichero [docker-compose.yml](./entorno-vulnerables-adriancurtosanchez/docker-compose.yml) con el comando `docker-compose up -d` para la versión 1 de docker compose y para la versión 2 empleamos `docke compose up -d`.

![Docker compose up](images/docker-compose-up.png)

Tras finalizar la ejecución anterior podemos verificar que los contenedores se encunetran en ejecución con el comando `docker compose ps`.

![Docker compose ps](images/docker-compose-ps.png)

### DVWA
Para saber por que puerto es accesible el servicio consultamos el servico en [docker-compose.yml](./entorno-vulnerables-adriancurtosanchez/docker-compose.yml), en este caso la url con el puerto de acceso es http://localhost:8002.

![DVWA port](images/dvwa-port.png)

Una vez hemos accedido las credenciales de acceso iniciales las dejamos vacías.

![DVWA login](images/dvwa-login.png)

Deberemos inicializar la base de datos pinchando en el botón "Create / Reset Database".

![dvwa init db](images/dvwa-init-db.png)

Tras inicializar la base de datos nos redirige a la página de login donde introducimos el usuario "admin" y la contraseña "password".

![dvwa login real](images/dvwa-login-real.png)

Y ya tenemos acceso a las vulnerabilidades que ofrece.

![dvwa vulnerabilities](images/dvwa-vulnerabilities.png)


### BWAPP
Para saber por que puerto es accesible el servicio consultamos el servico en [docker-compose.yml](./entorno-vulnerables-adriancurtosanchez/docker-compose.yml), en este caso la url con el puerto de acceso es http://localhost:8001.

![BWAPP port](images/bwapp-port.png)

Nos indica que debemos inicializar la base de datos, para ello accedemos a la URL http://localhost:8001/install.php y hacemos clic en "Click here to install bWAPP.".

![Bwap install db](images/bwapp-install.png)

Nos indica que la instalación se ha realizado satisfactoriamente.

![Bwap install db succes](images/bwapp-install-succes.png)

Accedemos a "Login" e introducimos las credenciales usuario "bee" y contraseña "bug".

![Bwap login](images/bwapp-login.png)

Y ya tenemos acceso a las vulnerabilidades que ofrece.

![Bwapp vulnerabilities](images/bwapp-vulnerabilities.png)


### OWASP Multillidae ii
Para saber por que puerto es accesible el servicio consultamos el servico en [docker-compose.yml](./entorno-vulnerables-adriancurtosanchez/docker-compose.yml), en este caso la url con el puerto de acceso es http://localhost:80.

![Multillidae port](images/multillidae-port.png)

Inicializamos la base de datos pinchando en el enlace del punto 1 "Clic here".

![Mutillidae init db](images/mutillidae-init-db.png)

Nos muestra un modal indicando que la base de datos se ha creado satisfactoriamente.

![Mutillidae init db succes](images/mutillidae-init-db-succes.png)

Y automáticamente ya hemos accedido a la web vulnerable de prática.

![Mutillidae acces](images/mutillidae-acces.png)

#### PhpMyAdmin
Podemos gestionar las bases de datos desde el entorno gráfico de PHPMyAdmin en la URL http://localhost:81.

![PhpMyAdmin](images/phpmyadmin.png)

#### PhpLdapAdmin
Podemos gestionar desde el entorno grágico PhpLdapAdmin el servicio LDAP en la URL http://localhost:82.

![PhpLdapAdmin](images/php-ldap-admin.png)

## Entornos pruebas
Creamos un entorno de pruebas con el stak LAMP (Linux Apache MariaDB PHP). Para ello emplearemos el repositorio https://github.com/sprintcube/docker-compose-lamp.

Solo tenemos que seguir las instrucciones del repsitorio ejecutando los siguientes comandos:
```
git clone https://github.com/sprintcube/docker-compose-lamp.git
cd docker-compose-lamp/
cp sample.env .env
// modify sample.env as needed
docker compose up -d
// visit localhost
```
El comando `git clone https://github.com/sprintcube/docker-compose-lamp.git` descarga el repositorio.
`cd docker-compose-lamp/` nos situa en la carpeta que se crea con el contenido del repositorio.
`cp sample.env .env` realiza una copia del fichero de las variables de entorno de ejemplo, creando el fichero ".env" el cual modificaremos para cambiar puertos, contraseñas, etc.
Y con `docker compose up -d` levantamos los servicios.

![LAMP init](images/lamp-init.png)

Tenemos acceso a **Apache2** en la URL http://127.0.0.1:80.

![Apache2](images/apache2.png)

Acceso a **PHPMyAdmin** en la URL http://localhost:8080.

![PHPMyAdmin](images/phpmyadmin-lamp.png)

Acceso a **Redis** en la URL http://127.0.0.1:6379 pero este servicio no tiene entorno gráfico.

Y ya tenemos listo nuestro entorno de pruebas.