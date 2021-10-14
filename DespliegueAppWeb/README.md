# Instalación de Apache-Tomcat en Linux

![logo-tomcat](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/apache-tomcat.png)

## Indice

- <a href="#1">1. Creacion de una App Web en Java</a>
- <a href="#2">2. Acceso</a>

<a href="1"></a>

### 1. Creacion de una App Web en Java

Para realizar esta tarea necesitamos tener instalado <b>Java</b>, el cual ya lo tenemos instalado. También necesitamos tener instalado <b>Maven</b>, el cual vamos a instalar a continuación. Para ello usaremos el comando <b>sudo apt install maven</b>.

![1](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/1.png)

Una vez instalado Maven haremos la construcción del proyecto, para ello usaremos el siguiente comando:<b> mvn archetype:generate -DgroupId=es.iespuerto.alumno -DartifactId=app-alumno -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false</b>

![2](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/2.png)

Vemos que se ha creado correctamente.

![3](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/3.png)

A continuación debemos de cambiar el fichero web.xml, en la etiqueta <b>"display-name"app-web-alumno "display-name"</b> por <b>"display-name" app-web-javier "display-name"</b>

![4](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/5.png)

En el fichero index.jsp debemos de agregar nuestro nombre en la etiqueta <b>p</b>

![5](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/6.png)

En el fichero pom.xml debemos cambiar el <b>artifactId</b> y <b>name</b> por <b>app-web-javier</b>

![6](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/9.png)

En el <b>finalName</b> también.

![7](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/10.png)

Por último, debemos de hacer el siguiente comando: <b>mvn clean install.</b>

![8](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/7.png)

Como vemos se nos ha creado el directorio target, y el paquete <b>app-web-javier</b>. El cual habrá que moverlo a la carpeta webapps de la instalación de tomcat.

![9](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/11.png)

Comprobamos que se ha movido la carpeta a la ruta siguiente.

![10](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/12.png)

<a href="2"></a>

### Acceso
Para poder acceder a la aplicación tendremos que poner en la url: <b>localhost:8083/app-web-javier</b> y vemos el Hola Mundo!

![11](https://github.com/Regnierd/Apache2/blob/main/DespliegueAppWeb/img/8.png)



