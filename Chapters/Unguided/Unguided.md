## Little unguided projects

In this chapter we present a list of small projects that we encourage you to code. 
Such projects are fun and playing with them will force you to practice different coding idioms or design patterns.
In many exercises you should avoid to rely on conditionals. 

### LAN simulator

A LAN is composed of different kinds of nodes. Packets circulate inside the LAN from node to node. 

A node has an address and a next node to which it forward packets that are not addressed to it. 
When the packet is addressed to a node, then depending on the node kind it performs its action. 
A packet has an address and a contents.

A simple LAN is composed of simple nodes. Simple nodes just forward the packets that are not addressed to them to their next node.

##### Different kind of nodes

Let us introduce new kind of nodes.
- printer nodes print the contents of the packet they receive if the packet is addressed.
- workstation nodes can emit packets.

### Extensions

There are several possible extensions: 

##### Star node
Introduce a star node that supports the creation of star network. A star node does not have one but many following nodes. 



##### Trottling node

This node accumulates packets and wait before to forward them.
They wait to have received a certain number of packets before sending a batch of collected packets.

##### Handling loops

Introduce a origin to the packet and make sure that if it reaches the node that emitted it is not propagated. 

##### Limited packet distance

We decide that a packet can only be forward a given number of times. After that it should reemitted or is not propagated if it did not reach its destination. 
Introduce a repetiting node that recharges the distance number of packet can have. 

##### Different kinds of packets

In this extension we introduce several kinds of packet.

- Some packets can auto replicate themselves to flood the LAN, it means that when they are accepted by a node and even if they are addressed to a node receiving them they force their forwarding. 
- Urgent packets cannot be trottled by trollting nodes.

##### Signing node

A signing node encodes the contents of a package and only nodes with the same signing behavior can decode the contents. 
We would like to have different combinations of contents encodings. One possible design is to use a Decorator design pattern,
where the decorators will expose the same API that the packet but they implement different encodings. 
Here is a list of encodings:
- adding one to each character of the contents,
- substituing one character by another one based on a map, or
- uuencoding - Check the base64 encoder available in Pharo.


### Die players

We want to model dice (as in the DSL chapter) but with different kinds of players and dices.
Let us imagine that we have die and die handle and that we can roll a die and a die handle.

A normal player is one player that roll normally its die handle. Introduce the class Player and make sure that it gets the possibility to roll die handles.

##### Kind of players
Now we want to introduce different kind of players.
- A cheater player is one player that will take the max of value of its die handle value and multiply by the number of dices. For example if he gets 2,3,4, after rolling its dice, he will say that he hot 4,4,4.
- A lucky player is a player that will always have plus one to its roll. For example, rolling its dice returns, 2,3,4 and the lucky player will have 10 and not 9.
- A super lucky player is a player that will always have plus one to the values of all the value of its dices. For example, rolling its dice returns 2,3,4 and the super lucky player will return 3,4,5 i.e. 12.

##### Different kinds of die
Now we introduce different kinds of dice. 
- A normal die has equi proportional values from 1 to its max face number: e.g., 1, 2, 3, 4, 5, 6.
- A middle die has no 1 and 6 but two 3 and two 4: e.g. 2, 3, 3, 4, 4, 5.
- A cheated die has no 1 and 2 but 3 6 values: e.g. 3, 4, 5, 6, 6, 6.

##### Pair of player and die

Now certain dices can only be played by certain player: 
- A middle die can only be played by a lucky or super lucky player.
- A cheating dice that can only be played by a cheater. 


### About the DSL 

In the DSL we can implement the solution without double dispatch. Do it.






