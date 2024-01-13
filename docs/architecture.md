# Architecture

The architecture of this plugin and all subcomponents follows the so-called *Mediator* pattern.

The `homebridge-bridge` acts as a mediator between the supported programming language interfaces and Homebridge itself.
It forwards all accessory control requests coming from Homebridge as well as the logs coming from the programming language interfaces.

```mermaid
flowchart TD
    User["User (via Apple Home)"] --> HB
    HB["Homebridge"] <--> core

    pybridge <--> MQTT

    subgraph py["Python script"]
        pybridge["homebridge-bridge/pybridge"]
        pyscript["Accessory control"]

        pybridge <--> pyscript
    end
    subgraph core ["homebridge-bridge/core"]
        core-plugin["Homebridge plugin"]
        MQTT["MQTT broker"]
        core-plugin <--> MQTT
    end
    subgraph rust["Rust script"]
        rustbridge["homebridge-bridge/rustbridge"]
        rustscript["Accessory control"]

        rustbridge <--> rustscript
    end

    rustbridge <--> MQTT

    pyscript --> acc1["Non Homebridge accessory"]
    rustscript --> acc2["Non Homebridge accessory"]

    subgraph other["..."]
        otherbridge["homebridge-bridge/[...]bridge"]
        otherscript["Accessory control"]

        otherbridge <--> otherscript
    end
    
    MQTT <--> otherbridge
    otherscript --> acc3["Non Homebridge accessory"]
```
