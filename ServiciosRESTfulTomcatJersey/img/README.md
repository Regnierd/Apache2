# Servicios RESTful con Tomcat y Jersey

![logo-tomcat](https://github.com/Regnierd/Apache2/blob/main/InstalacionTomcat/img/apache-tomcat.png)

## Indice

- <a href="#1">1. Requisitos previos</a>
- <a href="#2">2. Despliegue del servicio</a>
- <a href="#3">2.1 Problemas durante el despliegue</a>

<a name="1"></a>

### 1. Requisitos previos
Para poder hacer esta práctica necesitaremos instalado <b>Java</b> y <b>Maven</b>. Crear un proyecto <b>Java</b> con <b>Maven</b>. En nuestro caso usaremos el proyecto del profesor.

<a name="2"></a>

### 2. Despliegue del servicio
Una vez que tengamos el proyecto con maven se generará el fichero pom.xml, el cual tendrá las dependencias que necesitaremos. Hacemos <b>mvn clean install</b> para desplegar la aplicación. Una vez hecho se nos creará el directorio target el cual tendrá otro directorio llamado <b>rest-service</b>. Este directorio lo tendremos que mover al servidor tomcat, al siguiente directorio: <b>/opt/tomcat/apache-tomcat/webapps </b>donde se alojan todos los proyectos que se despliegan.

![1](https://github.com/Regnierd/Apache2/blob/main/ServiciosRESTfulTomcatJersey/img/2.png)

Para ello tenemos que comprobar las librerías que tenemos en el proyecto para ello tenemos que ir al directorio que se muestra en la imagen.

![2](https://github.com/Regnierd/Apache2/blob/main/ServiciosRESTfulTomcatJersey/img/4.png)

<a name="3"></a>

### 2.1 Problemas durante el despliegue
Al ya estar en el servidor, podemos abrir un navegador y poner la siguiente ruta: <b>ip-local:puerto/rest/users</b>. Tomcat nos dirá que el despliegue está hecho correctamente, pero en realidad no se ejecutará nada porque tendremos conflictos con las dependencias que tenemos.

![3](https://github.com/Regnierd/Apache2/blob/main/ServiciosRESTfulTomcatJersey/img/3.png)

Para ver con más detalle los errores que tenemos tendremos que ir a los ficheros .logs. El primer error que nos dará será el siguiente. 
Por si no se ve bien en la imagen es el siguiente: 
<b>SEVERE [http-nio-8082-exec-6] org.apache.catalina.core.StandardContext.loadOnStartup Servlet [Jersey Web Application] in web application [/rest-service] threw load() exception java.lang.ClassNotFoundException: com.sun.jersey.spi.container.servlet.ServletContainer</b>
El cual quiere decir que la versión de spi no es compatible con la versión que tenemos en las librerías. Para ello tenemos que cambiar el fichero <b>web.xml</b> ubicado en <b>WEB_INF/web.xml</b> que está dentro del proyecto por otra configuración para arreglar el problema.

![4](https://github.com/Regnierd/Apache2/blob/main/ServiciosRESTfulTomcatJersey/img/5.PNG)

Una vez cambiado el fichero web.xml nos saltará otro error: <b>java.lang.ClassNotFoundException: java.servlet.Filter. </b>
No he podido arreglar este fallo.

![5](https://github.com/Regnierd/Apache2/blob/main/ServiciosRESTfulTomcatJersey/img/6.png)
