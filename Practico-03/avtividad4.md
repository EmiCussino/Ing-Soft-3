# Actividad 4 

## Clonar el repositorio https://github.com/dockersamples/example-voting-app

## Abrir una línea de comandos y ejecutar

## Una vez terminado acceder a http://localhost:5000/ y http://localhost:5001
## Emitir un voto y ver el resultado en tiempo real.

![captura9](https://github.com/EmiCussino/Ing-Soft-3/blob/faa10e81cbed0739af751a399501dc645a207835/Practico-03/images/captura9.png)


![captura10](https://github.com/EmiCussino/Ing-Soft-3/blob/faa10e81cbed0739af751a399501dc645a207835/Practico-03/images/captura10.png)


## Para emitir más votos, abrir varios navegadores diferentes para poder hacerlo

![captura11](https://github.com/EmiCussino/Ing-Soft-3/blob/faa10e81cbed0739af751a399501dc645a207835/Practico-03/images/captura11.png)


Explicar como está configurado el sistema, puertos, volumenes componenetes involucrados, utilizar el Docker compose como guía.

El sistema utiliza dos networks:

front-tier, a través de la cuál se interconectan las apps de votación y resultados, utilizando websockets.
back-tier, a través de la cuál éstas se comunican con redis y postgres. A su vez, el worker de java se comunica con estas últimas, actualizando postgres a partir de redis.
La persistencia de datos de postgres se realiza sobre el volumen db-data.

Ambas aplicaciones web exponen su puerto 80 interno a través de los puertos 5000 y 5001 del host, respectivamente.

¿Que ocurre?
1. Ingreso del voto de un usuario por 'localhost:5000' a la aplicación python.
2. Ingreso de la información del voto desde la app de python a redis.
3. El worker de java esta observando la cola en redis, al momento en que ingresan votos los toma.
4. El worker ingresa a la db el voto tomado desde la cola.
5. La app node esta constantemente pidiendo los nuevos votos desde la db.
6.La app node visualiza la cuenta de votos en 'localhost:5001'.