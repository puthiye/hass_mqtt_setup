
### Mosquitto MQTT setup on k3s
Mosquitto runs as a single-replica Deployment in the apps namespace on the Raspberry Pi’s k3s cluster. The broker accepts MQTT connections on port 1883.

The Service is named mosquitto-mqtt-broker. Other pods in the cluster can connect at: 
```
mosquitto-mqtt-broker.apps.svc.cluster.local:1883
```

### MQTT topic and subscriber
The Home Assistant helper input_boolean.test publishes its state to the topic home/switch/status. When it changes, an automation sends the new state—`on` or off—to the Mosquitto broker. The message is retained, so the broker remembers the latest value and sends it to new subscribers.


### HASS config

<img width="1193" height="898" alt="image" src="https://github.com/user-attachments/assets/69d7486f-3930-436a-b763-30e63cad04ca" />


