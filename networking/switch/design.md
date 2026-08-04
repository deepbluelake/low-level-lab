                Switch
          ┌───────────────────┐
          │                   │
          │ Forwarding Table  │
          │                   │
          └─────────┬─────────┘
                    │
         ┌──────────┼──────────┐
         │          │          │
      Port1      Port2      Port3
         │          │          │
         │          │          │
      DeviceA  DeviceB  DeviceC




    Device
      │
createFrame()
      │
      ▼
Frame
      │
      ▼
Switch.receiveFrame()
      │
      ▼
Port.transmitFrame()
      │
      ▼
Device.receiveFrame()

---

# Classes

1. Frame
2. Device
3. Port
4. Switch

---

# I. Frame

## Objects

```
f1
f2
...
```

## Responsibility

Represents one Ethernet Frame travelling through the network.

A Frame is simply a container carrying information from one device to another.

## Properties

1. sourceMAC
2. destinationMAC
3. payload

## Behaviours

1. Constructor
2. display() *(optional for debugging)*

---

# II. Device

## Objects

```
DeviceA
DeviceB
Printer
Server
...
```

## Responsibility

Represents any network device connected to the switch.

A Device can create frames, send them and receive them.

It does **not** know anything about the forwarding table.

## Properties

1. MACAddress
2. connectedPort

## Behaviours

1. createFrame()
2. sendFrame()
3. receiveFrame()

---

# III. Port

## Objects

```
Port1
Port2
...
Port10
```

## Responsibility

Represents one physical switch port.

A Port acts as the connection between a Device and the Switch.

## Properties

1. portNumber
2. connectedDevice

## Behaviours

1. connectDevice()
2. disconnectDevice()
3. transmitFrame()

---

# IV. Switch

## Objects

```
switch
```

## Responsibility

Represents a Layer 2 Ethernet Switch.

The Switch receives frames, learns source MAC addresses, updates the forwarding table and decides whether to forward or flood a frame.

## Properties

### Ports

```
Collection of Port objects
```

### Forwarding Table

```
MAC Address  --->  Port
```

Stores the port on which each MAC Address was last seen.

## Behaviours

1. receiveFrame()
2. learnSourceMAC()
3. lookupDestination()
4. forwardFrame()
5. floodFrame()
6. connectDevice()
7. disconnectDevice()

---

# Simulation Flow

Device

↓

createFrame()

↓

sendFrame()

↓

Switch.receiveFrame()

↓

learnSourceMAC()

↓

lookupDestination()

↓

Known Destination ?

├── Yes → forwardFrame()
│
└── No → floodFrame()

↓

Port.transmitFrame()

↓

Device.receiveFrame()
