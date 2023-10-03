# Communication

To enable communication between multiple programming languages the MQTT protocol is used.

It handles two directions of message flow via a central MQTT broker integrated into this plugin.
All accessory control requests received by Homebridge will be published to the MQTT broker and thereby forwarded to **all** running programming language interfaces.
Furthermore, the programming language interfaces publish their logs to the MQTT broker, where they will be picked up and logged by `homebridge-bridge`.

## Messaging format

Probably JSON, tbd.
