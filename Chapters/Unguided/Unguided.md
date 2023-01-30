## Unguided projects

In this chapter we present a list of small projects that we encourage you to code. 
In many exercises you should avoid to rely on conditionals. 

### LAN simulator

A LAN is composed of different kinds of nodes. Packets circulate inside the LAN from node to node. 

A node has an address and a next node to which it forward packets that are not addressed to it. 
When the packet is addressed to a node, then depending on the node kind it performs its action. 
A packet has an address and a contents.

A LAN is composed of different kinds of node.
- simple nodes just forward the packets they receive to their next node.
- printer nodes print the contents of the packet they receive if the packet is addressed.
- workstation nodes can emit packets.

### Lan Extension

There are several possible extensions: 

##### Star node
Introduce a star node that supports the creation of star network. A star node does not have one but many following nodes. 

##### Trottling node

This node accumulates packets and wait before to forward them. 

##### Handling loops

Introduce a origin to the packet and make sure that if it reaches the node that emitted it is not propagated. 

##### Limited packet distance

We decide that a packet can only be forward a given number of times. After that it should reemitted or is not propagated if it did not reach its destination. 
Introduce a repetiting node that recharges the distance number of packet can have. 

##### Different kinds of packets

In this extension we introduce several kinds of packet.

- Some packets can auto replicate themselves to flood the LAN, it means that when they are accepted by a node and even if they are addressed to a node
receiving them they force their forwarding. 
- Urgent packets cannot be trottled by trollting node. 
