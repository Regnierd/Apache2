# Instalación de Apache-Tomcat en Linux

![logo-tomcat](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/apache-tomcat.png)

## Indice

- <a href="#1">1. Instalación de Java</a>
- <a href="#2">2. Instalación de Apache-Tomcat</a>
- <a href="#3">3. Acceso</a>

Para esta práctica necesitaremos una máquina con Ubuntu 20.04 instalado.

<a name="1"></a>

### 1. Instalación de Java
Para poder hacer esta práctica es necesario tener instalado Java. Como no lo tenemos instalado previamente procederemos a instalarlo ahora. Para ello tenemos que actualizar los repositorios con el comando <b>sudo apt update</b>

![1](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/1.png)

Ahora podemos empezar con la instalación de java. Con el siguiente comando podremos instalar java con la versión default. <b>sudo apt install default-jdk</b>

![2](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/2.png)

Para comprobar la versión que se instaló de Java usaremos <b>java --version- </b>

![3](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/3.png)

<a name="2"></a>

### 2. Instalación de Apache-Tomcat
Ya que tenemos instalado Java podemos empezar a descargar el fichero Tomcat de la página de Apache. Con el comando <b>wget https://downloads.apache.org/tomcat/tomcat-10/v10.0.12/bin/apache-tomcat-10.0.12.tar.gz</b>

![4](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/4.png)

Después de la instalación crearemos un usuario, llamado tomcat con el comando: <b>sudo useradd -U -m -d /opt/tomcat -k /dev/null -s /bin/false tomcat</b>. Luego de crear el usuario descomprimimos el .tar.gz descargado anteriormente con el comando <b>sudo tar xf apache-tomcat-10.0.12.tar.gz -C /opt/tomcat/</b>

![5](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/5.png)

Le damos permisos de propietario al usuario tomcat que creamos anteriormente con el comando <b>sudo chown -R tomcat: /opt/tomcat</b>. Creamos un enlace simbólico con otro nombre para que no sea más difícil de buscar con el siguiente comando:
<b>sudo ln -s /opt/tomcat/apache-tomcat-10.0.12/ /opt/tomcat/apache-tomcat</b>

![6](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/6.png)

Vemos que se ha creado correctamente.

![7](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/7.png)

A continuación, creamos el servicio de Tomcat para poder usar sus servicios sin tener problemas. Para crear el servicio solo hace falta crear el fichero que se ve en la siguiente imagen.

![8](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/8.png)

Después de crearlo, encendemos el servicio con el comando <b>sudo systemctl start tomcat10</b> y para comprobar que está activo hacemos el siguiente comando <b>sudo systemctl status tomcat10</b>.

![9](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/9.png)

<a name="3"></a>

### 3. Acceso
Para que todo funcione tendremos que cambiar el puerto al 8083, ya que por defecto nos pondrá el puerto 8080 el cual ya está siendo usado por Gitlab. El fichero se encuentra en la siguiente dirección: <b>opt/tomcat/apache-tomcat/conf</b>

![10](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/10.png)

Para comprobar que todo funciona abriremos un navegador y pondremos en la url: <b>localhost:8083</b> y veremos como se nos muestra la página de tomcat.

![11](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/11.png)

