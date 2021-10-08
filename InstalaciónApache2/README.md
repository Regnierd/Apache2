# Instalación de Apache en Linux

![logo-apache](https://github.com/Regnierd/Apache2/blob/main/img/apache2.jpeg)

## Índice 

- <a href="#1">1. Instalación de Apache2</a>
- <a href="#2">2. Configuración Apache</a>
- <a href="#3">3. Acceso</a>

Para esta práctica necesitaremos una máquina con Ubuntu 20.04 instalado. 



<a name="1"></a>

### 1. Instalación de Apache2
Para empezar esta práctica instalamos apache2 con el comando <b>sudo apt install apache2.</b>

![1](https://github.com/Regnierd/Apache2/blob/main/img/1.png)

Podemos comprobar que se ha instalado mirando su servicio con el comando <b> sudo systemctl status apache2.</b>

![2](https://github.com/Regnierd/Apache2/blob/main/img/2.png)

<a name="2"></a>

### 2. Configuración Apache2
Para que no haya conflictos de puertos con el Gitlab instalado en la práctica anterior tendremos que cambiar al puerto que llama apache, que por defecto es el 80, por el puerto 8081, como podemos ver en la siguiente imagen. El primer archivo se encuentra en la ruta <b>/etc/apache2/ports.conf.</b>

![3](https://github.com/Regnierd/Apache2/blob/main/img/9.png)

El segundo archivo se encuentra en la ruta <b>/etc/apache2/sites-enabled/000-default.conf</b> y cambiamos la primera línea por <b><VirtualHost *:8081></b>

![4](https://github.com/Regnierd/Apache2/blob/main/img/8.png)

Para que se guarden los cambios tenemos que reiniciar el servicio apache2 con el comando <b>sudo systemctl restart apache2</b> y <b>sudo service apache2 restart</b>

![5](https://github.com/Regnierd/Apache2/blob/main/img/10.png)

A continuación, tenemos que configurar el Firewall, en el caso nuestro usaremos el que viene por defecto, UFW. Para ver toda la lista de perfiles que usa por defecto Apache tendremos que usar el siguiente comando: <b>sudo ufw app list</b>

![6](https://github.com/Regnierd/Apache2/blob/main/img/3.png)

En esta tarea vamos a usar el perfil de ‘Apache’, porque no será necesario usar la conexión cifrada. Usaremos el comando: <b>sudo ufw allow ‘Apache’.</b>

![7](https://github.com/Regnierd/Apache2/blob/main/img/4.png)

Después de seleccionar el perfil de Apache, tendremos que activarlo con el comando <b>sudo ufw enable</b> y luego comprobamos el estado del perfil con el comando <b>sudo ufw status</b>

![8](https://github.com/Regnierd/Apache2/blob/main/img/6.png)

<a name="3"></a>

### 3. Acceso
Para comprobar que todo funciona abrimos un navegador y ponemos en la url: <b>locahost:8081</b> y veremos la siguiente pantalla.

![9](https://github.com/Regnierd/Apache2/blob/main/img/11.png)