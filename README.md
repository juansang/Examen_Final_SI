# Examen Final Sistemas Informáticos
## Despliegue de aplicacion en Docker

### INTRODUCCIÓN
El objetivo de este ejercicio es desplegar nuestra aplicación mediante el uso de docker compose. Aparte de esto, crearemos una imagen personalizada de nuestro proyecto, la cual subiremos a docker hub. Posteriormente con esta imagen, se podrá hacer un pull y ejecutarla en cualquier equipo.

### PASO 1 : EXPORTAR PROYECTO
Una vez instalado docker engine y docker-compose, el primer paso consiste en exportar el proyecto en un archivo .war, el cual guardamos en una nueva carpeta, que llamamos Prueba_Login.

### PASO 2 : DOCKERFILE
Dentro de la carpeta creada previamente, hacemos un Dockerfile que contiene los comandos necesarios que se ejecutarán para crear nuestra imagen. El Dockerfile queda de la siguiente manera:

![dockerfile](https://user-images.githubusercontent.com/91699247/173105222-f445d18d-4a41-4133-9059-32f75add9e2d.png)



Ahora llevamos a cabo un docker build de nuestra imagen personalizada donde indicamos el nombre que le vamos a dar a la imagen y donde se encuentra el archivo Dockerfile, para ello hay que ejecutar el siguiente comando : 
```
docker build -t  jsanc/appservicios -f Dockerfile .
```
![dockerfile2](https://user-images.githubusercontent.com/91699247/173109801-50a35538-f6bd-4585-b92f-a7997693962e.png)


### PASO 3 : FICHERO DOCKER-COMPOSE 
Para poder levantar todos los servicios que componen nuestra aplicación, debemos crear un fichero docker-compose.yml , donde se definirán estos servicios. Este fichero lo guardamos también en la carpeta creada anteriormente.

La estructura del docker-compose es la siguiente :

```
version: // indica la versión del formato
services: // indica el contenedor/es que conforman la aplicación
web: // indica el tipo de servicio
image: // indica la imagen
ports: // Indicamos el redireccionamiento de puertos
volumes: // indica el volúmen/es que usará la imagen
```

De esta manera, el archivo docker-compose.yml queda tal que así: 

![compose](https://user-images.githubusercontent.com/91699247/173110258-d16c1a9c-4510-4edc-96c1-e58fb434c265.png)

Para poder arrancar los contenedores descritos en el docker-compose.yml ejecutamos el comando  
```
docker-compose up
```
![compose-up](https://user-images.githubusercontent.com/91699247/173111178-17c17f0d-4d75-4882-b8b8-8dfd460ae8fd.png)

Ya arrancados, nos dirigimos al navegador y escribimos la dirección ``localhost:8081/ProjecteFinal``, donde podemos comprobar que se ha arrancado correctamente y podemos visualizar nuestro proyecto. Por lo tanto, el despliegue de nuestra aplicación se ha conseguido de manera satisfactoria.

![pagina](https://user-images.githubusercontent.com/91699247/173111444-c7c41a1c-beb0-42a5-a888-f21d3ee825f6.png)


### PASO 4 : SUBIR IMAGEN A DOCKER HUB

Por último, para poder ejecutar nuestra imagen desde cualquier equipo, tenemos que subirla a Docker Hub, para ello debemos ejecutar dos comandos :

``docker login`` , que nos permite iniciar sesión, acceder a nuestra cuenta de Docker Hub

``docker push usuario/nombre_imagen`` , que subirá nuestra imagen a nuestra cuenta de Docker Hub

![push](https://user-images.githubusercontent.com/91699247/173112040-5848d748-6690-44d5-8145-1a54d797970b.png)


Una vez acabado, podemos acceder a nuestra cuenta de Docker Hub y comprobar que la imagen se ha subido con éxito.

![dockerhub](https://user-images.githubusercontent.com/91699247/173112795-610fed92-4185-495c-91d4-c5b282920c58.png)



### ANNEXOS

Enlace a imagen en Docker Hub : https://hub.docker.com/r/jsanc/appservicios
