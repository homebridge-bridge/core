# Bridges

A bridge, such as [`pybridge`](https://github.com/homebridge-bridge/pybridge), is a collection of utilities around the basic MQTT [communication](./communication.md).
Theoretically speaking, a bridge is not required to use achieve communication between `homebridge-bridge/core` and a programming language.
It does make it a lot easier to use though, since it adds another layer of abstraction on the bare communication.
The concrete functionality is dependent on the bridge implementation, but always includes:

- Establishing the MQTT connection to the broker
- Subscribing/Publishing to the correct topics
- Keeping the connection alive
