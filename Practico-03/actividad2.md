## Actividad 2

# Explicar cómo funciona el sistema
 
 Se crea una Api donde se importan una base de datos "Redis" y un "Flask" que sirve para crear pequeñas aplicaciones. "_name_" sera nuestro valor de referencia de la api.  La aplicacion consiste de un contador de visitas que se incrementa al visitar el endpoint
 ![captura3] 

¿Para qué se sirven y porque están los parámetros -e en el segundo Docker run del ejercicio 1?
¿Qué pasa si ejecuta docker rm -f web y vuelve a correr docker run -d --net mybridge -e REDIS_HOST=db -e REDIS_PORT=6379 -p 5000:5000 --name web alexisfr/flask-app:latest ?
¿Qué occure en la página web cuando borro el contenedor de Redis con docker rm -f db?
Y si lo levanto nuevamente con docker run -d --net mybridge --name db redis:alpine ?
¿Qué considera usted que haría falta para no perder la cuenta de las visitas?
Para eliminar los elementos creados corremos: