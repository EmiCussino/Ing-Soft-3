# Actividad 2

## Explicar cómo funciona el sistema
 
 Se crea una Api donde se importan una base de datos "Redis" y un "Flask" que sirve para crear pequeñas aplicaciones. "_name_" sera nuestro valor de referencia de la api.  La aplicacion consiste de un contador de visitas que se incrementa al visitar el endpoint
 ![captura3](https://github.com/EmiCussino/Ing-Soft-3/blob/39e498b92586da4fe2409d369e21a48968125299/Practico-03/images/captura3.png) 

## ¿Para qué se sirven y porque están los parámetros -e en el segundo Docker run del ejercicio 1?
El parametro -e define las variables de entorno. En el punto anterior es utilizada para configurar el host y el puerto redis.

## ¿Qué pasa si ejecuta docker rm -f web y vuelve a correr docker run -d --net mybridge -e REDIS_HOST=db -e REDIS_PORT=6379 -p 5000:5000 --name web alexisfr/flask-app:latest ?
Con el comando docker rm -f web1 estariamos eliminando el contenedor y al correr "docker run -d --net mybridge -e REDIS_HOST=db1 -e REDIS_PORT=6379 -p 5000:5000 --name web alexisfr/flask-app:latest" levante nuevamente la aplicacion, pero el estado del contador se manteniene, ya que la variable no fue reiniciada. 

## ¿Qué occure en la página web cuando borro el contenedor de Redis con docker rm -f db?
Pierdo la conexion con la base de datos y me sale el error. 
![captura4](https://github.com/EmiCussino/Ing-Soft-3/blob/39e498b92586da4fe2409d369e21a48968125299/Practico-03/images/captura4.png) 
## Y si lo levanto nuevamente con docker run -d --net mybridge --name db redis:alpine ?
En mi caso levanto nuevamente la app, pero con el contador en 1. 
![captura5](https://github.com/EmiCussino/Ing-Soft-3/blob/39e498b92586da4fe2409d369e21a48968125299/Practico-03/images/captura5.png) 
## ¿Qué considera usted que haría falta para no perder la cuenta de las visitas?
Crear un volumen de datos aparte para guardar la informacion independientemente de su contenedor. 
