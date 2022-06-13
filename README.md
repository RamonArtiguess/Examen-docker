# Examen-docker

- El examen lo he hecho con una VM alphine

## Apartado 1

 - Deberéis completar de los ejercicios 1, 2, 3 y 4 del primer link adjunto que lleva al apartado "2.1 Ejecutando contenedores" de nuestros apuntes.

#### Ejercicio 1:
Descargando y creando una máquina con un contenedor ubuntu:18.04 y corriendolo en la consola bash

![Imagen no encontrada](/Imagenes/Apartado.1/1.png)

#### Ejercicio 2:

Ejecutando un contenedor ubuntu:18.04 y listar todas las carpetas de la raíz


![Imagen no encontrada](/Imagenes/Apartado.1/2.png)

#### Ejercicio 3:

Creando un servidor apache 2.4 con la ip que se muestra(la máquina no muestra el comando entero) y sus logs en tiempo real

![Imagen no encontrada](/Imagenes/Apartado.1/3.png)

#### Ejercicio 4:

Creando i corriendo un contenedor debian:9 con el parámetro -w en la carpeta /etc donde haremos un ls

![Imagen no encontrada](/Imagenes/Apartado.1/4.png)

## Apartado 2

- Deberéis completar el ejercicio DOCKERFILE Proyecto Tomcat (del segundo link adjunto con el objetivo de  subir la imagen de Tomcat resultante a vuestro perfil de docker hub.

Lo primero sera crear un archivo dockerfile
`nano Dockerfile`

Lo segundo sera modificar este archivo con los comandos necesarios para crear el contenedor de forma funcional,
en el `Dockerfile` básicamente decimos que SO se instalara i que comandos ejecutaremos en el a la hora de crear el contenedor que concretamente consta de:

- Instalar herramientas básicas

`RUN apt update && apt install -y nano && apt install -y  vim `

- Habilitar las aplicaciones de tomcat

`RUN mv /usr/local/tomcat/webapps.dist/* /usr/local/tomcat/webapps
RUN rm -rf /usr/local/tomcat/webapps.dist`

- Copiando los usuarios de tomcat al contenedor

 `COPY mytomcat-users.xml /usr/local/tomcat/conf/tomcat-users.xml`

- Modificar el contexto del contenedor

`COPY mycontext.xml /usr/local/tomcat/webapps/host-manager/META-INF/context.xml
COPY mycontext.xml /usr/local/tomcat/webapps/manager/META-INF/context.xml`

- Copiando la aplicación

`COPY webapp.war /usr/local/tomcat/webapps/webapp.war`

![Imagen no encontrada](/Imagenes/Apartado.2/1.png)



En nano con `cntrl+x` salimos y guardamos el archivo modificado

Ahora solo hace falta comprovar que funciona y subirlo a dockerhub

- Creamos el contenedor a través de la imagen
(Debido a que los comandos COPY no funcionan he deicidido quitarlos)

![Imagen no encontrada](/Imagenes/Apartado.2/2.png)


![Imagen no encontrada](/Imagenes/Apartado.2/3.png)

Y ahora solo falta subir la imagen al dockerhub

-Iniciar sesión en docker


![Imagen no encontrada](/Imagenes/Apartado.2/4.png)

-Renombrando mi imagen creada y subiendola a dockerhub

![Imagen no encontrada](/Imagenes/Apartado.2/5.png)


![Imagen no encontrada](/Imagenes/Apartado.2/6.png)

Y ya está la imagen subida

![Imagen no encontrada](/Imagenes/Apartado.2/7.png)

[Repositorio link](https://hub.docker.com/repository/docker/ramonedib/mytomcat)


(Prueba del trabajo)

![Imagen no encontrada](/Imagenes/Comprovación.png)
