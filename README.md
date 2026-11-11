
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

<img width="402" height="357" alt="image" src="https://github.com/user-attachments/assets/0361239b-c234-45a5-a4ac-1d96bb466a77" />



Create a helper function for the toggle switch
<img width="1249" height="718" alt="mqtt1" src="https://github.com/user-attachments/assets/8a24d8e9-6ca5-4cd5-a25a-776e62404e6b" />

Add the toggle switch to dashboard using entities card
<img width="1209" height="807" alt="mqtt2" src="https://github.com/user-attachments/assets/e89885d1-ab49-4ced-b9c8-f62e93a79b3b" />


<img width="836" height="550" alt="mqtt2_1" src="https://github.com/user-attachments/assets/9c938150-a586-4440-9c44-ca471a70cbd6" />

Put the MQTT publish logic in a separate automation, under Settings → Automations & scenes → Create automation → Edit in YAML
<img width="1403" height="1032" alt="mqtt3" src="https://github.com/user-attachments/assets/f2008857-3157-4517-a214-d5db80237826" />

<img width="473" height="338" alt="mqtt4" src="https://github.com/user-attachments/assets/d3e4466b-a195-4152-bfbb-e666a143b923" />







