Classes - Frame, Computer, Switch

Details:

I. Frame

    Objects - f1, f2, etc.

    Properties
        1. sourceMAC
        2. destinationMAC
        3. payload

II. Computer

    Objects - Node1, Node2, etc

    Properties
        1. MACAddress
        2. payload

    Behaviours
        1. pluginPort()
        2. unplugPort()
        3. sendFrame()
        4. checkRecievedFrame()
        5. recieveFrame()

III. Switch

    Object - switch

    Properties
        1. port
        2. forwardingTable

    Behaviours
        1. onRecieve()
        2. parseFrame()
        3. sendTo()
        4. flood()
        5. updateForwardingTable()
        6. 