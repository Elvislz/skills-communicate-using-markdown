# Título Principal
## Subtitulo principal
Este es el subtitulo principal
## Subtitulo secundario
Este es el subtitulo secundario
### Este es un subsubtitulo
Info random

## Imagen insertada
![Image of Yaktocat](https://beecrowd.com/wp-content/uploads/2024/04/2022-07-26-Coisas-importantes-que-um-programador-deve-saber.jpg)

Esta imagen fue sacada de google
##Imagen insertada de GitHub
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

## Ahora código en Python
### Ejemplo de MQTT
``` python
import paho.mqtt.client as mqtt
import time
import random
```
####  Definir los parámetros de conexión
``` python
broker = "localhost"
port = 1883
topic = "casa/habitacion1/temperatura"
topic2 = "casa/cocina/temperatura"
intervalo = 5  # Intervalo de tiempo en segundos para enviar datos
```
#### Definimos la función de callback para cuando se conecta al broker
``` python
def on_connect(client, userdata, flags, rc):
    if rc == 0:
        print(f"Me he conectado al broker MQTT Mosquitto!")
    else:
        print(f"Error al conectar al broker MQTT Mosquitto: {rc}")
```
#### Crear una instancia del cliente MQTT

``` python
client = mqtt.Client()
```
#### Asignar la función de callback
``` python
client.on_connect = on_connect
```
#### Conectar al broker
``` python
client.connect(broker, port, 60)
```
#### Dejar la conexión en loop
``` python
client.loop_start()
```
#### Publicar datos de temperatura simulados en el topic cada intervalo de tiempo
``` python
try:
    while True:
        temperatura = round(random.uniform(15.0, 30.0), 2)  # Generar una temperatura aleatoria entre 15.0 y 30.0
        temperatura_cocina = round(random.uniform(15.0, 30.0), 2)  # Generar una temperatura aleatoria entre 15.0 y 30.0
        client.publish(topic, str(temperatura))
        client.publish(topic2, str(temperatura_cocina))
        time.sleep(intervalo)
except KeyboardInterrupt:
    print("Desconectando del broker MQTT...")
    client.loop_stop()
    client.disconnect()
    print("Desconectado.")
 ```   
## Lista de tareas
- [ ] Primer item, marcalo si leiste todo.
- [ ] Comprendiste todo.
- [ ] Replicaste todo.






Rellené con texto en codigo markdown



