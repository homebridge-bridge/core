# Security considerations

The [communication](./communication.md) between the bridges and the MQTT broker is protected using a password.
This password is generated randomly on the first start, but can be overwritten via the plugin settings inside the Homebridge UI.

Keep in mind that anyone with access to the Homebridge UI is able to see and change the password.
