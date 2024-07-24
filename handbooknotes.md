The notes here just document my readings of the handbook while working through the articles on car hacking and making connections.

## Chapter 1: Understanding Threat Models
Just skimmed over this chapter as it just goes over methods to brainstorm/model potential attack surfaces, and threat rating systems.
## Chapter 2: Bus Protocols
Prior to reading this handbook, I did some light research on CAN, such as CAN frame structure, how differential signalling works in CAN, and what CAN data looks like in real time from a youtube video.

Okay this was a confusing chapter since I am unfamiliar with a lot of the terminology here, but i think i have grasped some foundation on what CAN actually is and what a bus and protocols are.

### Bus VS Protocol
A Bus is physical infrastructure that facilitates communication between nodes (think of nodes as modules, ECU's), such as wiring, controllers, and electronics.

A Protocol is a language built on top of a particular Bus type that standardises some format for communication. A Protocol can also be a dialect of that language that provides additional usability.

### Then what is CAN?

CAN is BOTH a Bus and Protocol

CAN is the two wires, CANL and CANH (accessible from the ODB port), which utilises differential signalling to offer noise-proof and fast communication. The reason why its noise-proof is that when subject to noise, both the CANL and CANH wire voltages will be affected the same amount, and since only the difference between the wires is taken into account, it is noise-proof

### CAN packets/frames

A CAN packet or frame is the format/structure (following its protocol) of one transmission/message on the CAN bus. 

CAN has two types of packets which are standard and extended packets.

Both have:
- Arbitration ID's: some ID that identifies the sender node, with the purpose of winning the priority check and being the chosen message to excecute. Note that a lower transmission ID has higher priority.
- Identifier Extension: a 0 bit for standard CAN
- Data length code: Indicates the size of the data 
- Data: the data itself ranging from 0-8 bytes

Extended CAN packets are just multiple packets chained together to provide larger arbitration ID's, allowing for more unique identifiers.

There are many other older CAN implementations and protocols but aren't relevent to what I'm seeking from this handbook.

## Chapter 3: Vehicle Communication wtih Socketcan

SocketCAN is just an open-source API that supports CAN communication over the network, and CAN-utils is a collection of user commands/tools for SocketCAN on Linux.

Following code will be examples on Debian/Ubuntu, I am using Ubuntu:

Installing can-utils: 
```
$ sudo apt-get install can-utils
```

Since i do not have CAN hardware for sniffing, I am skipping the configuration for those and proceed with setting up a virtual CAN network using the "vcan" module:

```
$ modprobe vcan
$ ip link add dev vcan0 type vcan
$ ip link set up vcan0
```

There is a list here of the can-utils package tools which i may refer back to.

The rest of the information in this chapter are focussed on using hardware sniffers, I will skip this, though there is a useful section on coding SocketCAN Applications which I may come back to depending on how my experimentation goes.

## Chapter 5: Reverse Engineering the CAN Bus

As far as my understanding goes, though most modern vehicles use the CAN bus protocol, the actual protocol of each manufacturer or even model of car is different, which requires some reverse engineering for outsiders like me to make sense of, for reasons such as security of course. 

Skimming over this chapter, I believe Wireshark can be used to look at the CAN packets over the network, candump just dumps the packets in raw form, cansniffer groups packets and highlights changes in bytes, 


## Chapter 11: Weaponising CAN Findings


