# hass_mqtt_setup

### Mosquitto MQTT setup on k3s
Mosquitto runs as a single-replica Deployment in the apps namespace on the Raspberry Pi’s k3s cluster. The broker accepts MQTT connections on port 1883.

The Service is named mosquitto-mqtt-broker. Other pods in the cluster can connect at: 
'''
mosquitto-mqtt-broker.apps.svc.cluster.local:1883
'''
