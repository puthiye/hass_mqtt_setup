
### Mosquitto MQTT setup on k3s
Mosquitto runs as a single-replica Deployment in the apps namespace on the Raspberry Pi’s k3s cluster. The broker accepts MQTT connections on port 1883.

The Service is named mosquitto-mqtt-broker. Other pods in the cluster can connect at: 
```
mosquitto-mqtt-broker.apps.svc.cluster.local:1883
```

### MQTT topic and subscriber
The Home Assistant helper input_boolean.tv_control_flag publishes its state to the topic home/switch/status. When it changes, an automation sends the new state—`on` or off—to the Mosquitto broker. The message is retained, so the broker remembers the latv_control_flag value and sends it to new subscribers.

<img width="394" height="306" alt="image" src="https://github.com/user-attachments/assets/0361c50b-9f01-4375-b298-4e908cb6900b" />


### HASS config

<img width="1193" height="898" alt="image" src="https://github.com/user-attachments/assets/69d7486f-3930-436a-b763-30e63cad04ca" />

<img width="473" height="338" alt="mqtt4" src="https://github.com/user-attachments/assets/b7bed156-d70c-4430-bcaf-1ce96a08163d" />
<img width="1403" height="1032" alt="mqtt3" src="https://github.com/user-attachments/assets/53d00d87-a3c0-4faa-948e-941c4c84a1a0" />
<img width="1209" height="807" alt="mqtt2" src="https://github.com/user-attachments/assets/04f34cb2-4eda-4f91-95b3-9489bd93a8af" />
<img width="1249" height="718" alt="mqtt1" src="https://github.com/user-attachments/assets/311a4f57-e2e2-44b1-9762-66fd9b0fbe93" />



