## Little unguided projects

In this chapter we present a list of small projects that we encourage you to code. 
Such projects are fun and playing with them will force you to practice different coding idioms or design patterns.
In many exercises you should avoid to rely on conditionals. 

### LAN simulator

A LAN is composed of different kinds of nodes. Packets circulate inside the LAN from node to node. 
The code is available at:

```
Metacello new
  baseline: 'SimpleLAN';
  repository: 'github://Ducasse/SimpleLAN/src';
  load.
```

A node has an address and a next node to which it forwards packets that are not addressed to it. 
When the packet is addressed to a node, then depending on the node kind it performs its action. 
A packet has an address and contents.

A simple LAN is composed of simple nodes. Simple nodes just forward the packets that are not addressed to them to their next node.

### Extensions

There are several possible extensions: 

### Hook for accept

Subclasses such as `LNWorkstation` or `LNPrinter` redefine the `accept:` method and systematically check that the packet is sent to the receiver to perform a specific action else they pass it to the next node. 
The following method illustrates this behavior:

```
LNPrinter >> accept: aPacket	(aPacket isAddressedTo: self) 
		ifTrue: [ 'Node ' , aPacket originatorName , ' sent to printer: '		, aPacket contents traceCr ]
	ifFalse: [ super accept: aPacket ]
```

This repetition indicates that this behavior could be factored out in the superclass.
So define such behavior in the superclass and introduce a new method called `treatPacket:`. Such a new method will be redefined in all the subclasses. 




##### Better way to follow the execution of the simulation. 
In the default implementation, the `accept:` method writes on the Transcript. This is not good since the trace is mixed with 
other program traces. (Note that the Transcript is a global variable shared by the complete environment). In addition, it is not easy to write tests for the `send:` and `accept:` methods. 
One solution is to have a stream shared by all the nodes of a simulation, stream on which all the messages written to the Transcript are now written to. Propose one solution. To validate your solution, write some tests for `send:` and `accept:`. 
They should be able to run without writing to the Transcript.

##### Star node

Introduce a star node that supports the creation of star network. A star node does not have one but many following nodes. 


##### Avoiding some conditions.
The way the instance variable `nextNode` is managed (having nil or a node as value) is based on conditions in different places: the method `accept:` or the method `send:`. Propose a solution to be able to remove such conditions. One possible solution is to apply the NullObject design pattern.


##### Trottling node

This node accumulates packets and waits before forwarding them.
They wait to have received a certain number of packets before sending a batch of collected packets.

##### Handling loops

Introduce an origin to the packet and make sure that if it reaches the node that emitted it is not propagated. 

##### Limited packet distance

We decided that a packet can only be forwarded a given number of times. After that, it should reemitted or is not propagated if it did not reach its destination. 
Introduce a repeating node that recharges the distance number of packet can have. 

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


### About the die DSL 

In the die DSL we can implement the solution without double dispatch. Do it.


### About Visitors

Pharo has a Visitor library for its Abstract Syntax Tree (AST). 
Browse the class `RBProgramNodeVisitor`. This class is an abstract class. It defines all the methods available for building 
specialized Visitors. All the nodes in an AST are subclasses of RBProgramNode. 
The following shows the core elements where the indentation reflects the inheritance.

```
RBProgramNode
	RBComment
	RBMethodNode
	RBPragmaNode
	RBReturnNode
	RBSequenceNode
	RBValueNode
		RBArrayNode
		RBAssignmentNode
		RBBlockNode
		RBCascadeNode
		RBLiteralNode
			RBLiteralArrayNode
			RBLiteralValueNode
		RBMessageNode
		RBSelectorNode
		RBVariableNode
			RBArgumentNode
			RBGlobalNode
			RBInstanceVariableNode
			RBSelfNode
			RBSuperNode
			RBTemporaryNode
			RBThisContextNode
```

The following script shows how to execute a visitor on the AST of the method `Point>>#degrees`.

```
MyVisitor new visit: (Point>>#degrees) ast 
```

Here is a list of possible Visitors that you can simply define:
- a visitor that checks whether a method is a utility method: it does not access instance variables not self or super.
- a visitor that returns the list of instance variables accessed by the method. 
- a visitor that checks all the self-message sends of a method and returns the list of the compiled method found in the class or its superclass. You can use the method `lookupSelector:` defined on `Class` to find the corresponding method.
- a visitor that adds a return to the expression given. For SequenceNode it will put the return node on the last statement of the sequence node.


### Microdown 

Microdown is a markup language compatible with a subset of markdown. It is used by the Pharo community to produce slides, booklets, and documentation. 
A nice little project is to use Microdown to define a blog and its posts.
A potential roadmap is the following:

- Given a file repository we should generate a little table of contents. For this, we can reuse the HTML generation of Microdown. To do so we can do it either by generating a microdown document using the microdown builder and passing it to the HTML visitor. Or by creating the tree of objects for the table of contents and applying the HTML generation on it. 
- You can also render all the post to generate HTML files. 
- Finally having a visitor that extract the title of a post and a couple of line of the first paragraph so that the user can see a summary before clicking to get access to the full post can be nice. 



