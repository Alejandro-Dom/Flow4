# Flow4
En este repositorio se encuentra el Flow 4 del Diplomado de IoT

MQTT (Mosquitto) es un servicio de mensajería push con patrón publicador/suscriptor. En este tipo de infraestructura  los clientes se conectan con un servidor central denominado broker.

Para filtrar los mensajes que son enviados, los mensajes se disponen en topics (temas) organizados jerárquicamente. Para este ejercicio vamos a usar el siguiente tema:
	- codigoIoT/g7/mosquitto/msg
	
Ejercicio
1. Usaremos un broker público de hivemq, por lo que necesitamos conocer la dirección IP del broker usando el siguiente comando
	- nslookup.broker.hivemq.com
2. Hacer el flow 4 con los siguientes nodos
	- mqtt in; en este nodo debemos configurar el broker con cualquier nombre y la IP que se obtuvo en el paso anterior, y el tema seleccionado
	- JSON, con la acción Always convert to JavaScript Object
	- function, en el cual programaremos una función que tome el valor de la temperatura con el siguiente código:
		- msg.topic = msg.payload.id;
		- msg.payload = msg.payload.temp;
		- return msg;
	- chart, configurado con un valor minimo de 0° y un valor máximo de 45°
	- inject para mandar el siguiente mensaje en formato JSON, {"id":"Alex","temp":20}, cada 5 segundos
	- mqtt out con la misma configuración que el nodo mqtt in

