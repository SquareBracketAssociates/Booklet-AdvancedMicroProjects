## Robots

![Pillar logo](figures/pillar.png width=30&anchor=fig)

We launch a pathfinder robot on Mars and the communication with the robot is difficult.
To interact with this robot we can send it orders from Earth and the robot execute them. 
Energy and communication are limited so we use a compact representation of scripts. 

This micro project is about a robot handling orders and executing them.
Doing this project you will learn the Command design pattern.

### Robot and its space

A robot lives in a 2D space and receives script containing orders.
The following test illustrates this. 
- First a robot is created.
- Second a board is created. The robot is placed in the space

```
testExecute

	| rb b |
	rb := RbsRobot new.
	b := RbsBoard new.
	rb setBoard: b.
	rb startLocation: 4@1.
	rb execute: 
'dir #east
mov 2
mov 3
dir #north
mov 3'.
	self assert: rb position equals: 9@4
```

#### A typical session

```
mov 10
dir #east
dropL
load
```

### Robot

The first step is to implement orders such as `mov`, `dir`




```
mov 10
```

```
dir #east
```


### Sending order to robots

- `parseLines`
- `parseLine`
- `executeCommand:`





### Adding new orders

We propose now to introduce new orders

#### Base

It was strange to not have the base position as part of the script so we propose to introduce a new order `base` taking two numbers as x and y.

```
base 10 20
```
Here is a test

```
testStartPositionAsOrder

	| rb b |
	rb := RbsRobot new.
	b := RbsBoard new.
	rb setBoard: b.
	rb execute: 
'base 4 1
dir #east
mov 2
mov 3
dir #north
mov 3'.
	self assert: rb position equals: 9@4
```


#### Introduce the possibility for the robot to drop an item on the map


```
dropL
```


### Introducing Commands

Imagine that you defined `execute:` as follows: 

```
execute: aString

	(self identifyOrdersOf: aString)
		do: [ :each | 
		each first = #mov
			ifTrue: [ self move: (Object readFrom: each second) ]
			ifFalse: [ 
				each first = #dir ifTrue: [ 
					self direction: (Object readFrom: each second) ] ] ]
```

You saw that adding a new order is tedious and make the conditional statements more and more complex. 
This can get even more complex if we want to implement a replay of the orders.

We will now propose to introduce Commands.

#### Command

Each command can have its own state and in addition its should know how to execute itself and convert the order arguments into a Pharo object.
Here is an example for the `RbsMoveCommand`.

```
RbsCommand << #RbsMoveCommand
	slots: { #distance };
	package: 'Robots'
```	

```
RbsMoveCommand >> executeOn: aRobot
	aRobot move: distance
```

```
RbsMoveCommand >> handleArguments: aCol
	distance := Object readFrom: aCol first
```

#### Registering commands

```
RbsMoveCommand class >> commandName 
	^ 'mov'
```

The robot class should have a way to map 'mov' to the class of the command
Something like:


```
initializeCommandMapping

	cmdMap := Dictionary new.
	RbsCommand allSubclassesDo: [ :each |
		cmdMap at: each commandName put: each 	
		]
```

that the `executeCommandBased: aString` should use when creating and executing commands.

```
executeCommandBasedV1: aString

	(self identifyOrdersOf: aString) do: [ :each |
		((self commandClassFor: each first) new
			handleArguments: each allButFirst; yourself) executeOn: self ]

Implement all the commands so that the following test should pass.

```
testExecuteCommandBased

	| rb b |
	rb := RbsRobot new.
	b := RbsBoard new.
	rb setBoard: b.
	rb startLocation: 4@1.
	rb executeCommandBased: 
'dir #east
mov 2
mov 3
dir #north
mov 3'.
	self assert: rb position equals: 9@4
```


### Challenge: Replay

How to support replay


```
testReplay

	| rb b |
	rb := RbsRobot new.
	b := RbsBoard new.
	rb setBoard: b.
	rb executeCommandBased: 
'base 4 1'.
	rb executeCommandBased: 
'dir #east
mov 2
mov 3
dir #north
mov 3'.
	self assert: rb position equals: 9@4.
	rb startLocation: 5@1.
	rb replay.
	self assert: rb position equals: 10@4
```

Let us imagine that the method execute commandBased: was implemented as

```
RbsRobot >> executeCommandBased: aString

	(self identifyOrdersOf: aString) do: [ :each |
		((self commandClassFor: each first) new
			handleArguments: each allButFirst; yourself) executeOn: self ]
```

Now you should introduce a way to keep the created commands so that they can be replayed.

#### Introduce new commands to control replay

Note that in the test above we used `rb startLocation: 5@1.` instead of `rb executeCommandBased: 
'base 4 1'`. This is due to the fact that we cannot control when the recording is starting and that we cannot reset it either.
We propose you to introduce the following commands: `resetMonitor` and `replay`.


```
resM
mov 10
dir #east

```

### Orders as commands

Commands and Factory


### Reimplement optimization

### Reimplement replay

### Challenge Three: Automatic way back home

```
resetMonitor
move 10
turnLeft
checkBackHome
> #((turnRight) (move 10))
```

### Challenge: way back home

It can be tedious to bring back the robot to its location be inverting one by one the orders that compose a script. 
We propose to enhance our robots with a wayBack action. 
A way back action with take a list of commands and produce a new list of commands with the opposite actions.





### Challenge: Path optimizations

This extension is about supporting path optimizations.
Indeed n following `mov` commands merge as the sum of the commands.

```
move 10
move 20
move 5
```

```
move 35
```

Several following direction commands merge as the last command.
```
dir #east 
dir #south
dir #north
```
is optimized into 

```
dir #north
```

We suggest the following design. Introduce a message `aCommand mergeWith: anotherCommand` that returns a list containing the situation after trying to merge: 
When two commands can merge returns a list containing the command resulting from the merge.
When two commands do not merge returns a list containing the two original commands.



```
RbsRobotTest >> testMergeMoveCommandsProducesTheSum

	| cmdList |
	cmdList := (RbsMoveCommand new distance: 10; yourself)
		mergeWith: (RbsMoveCommand new distance: 10; yourself).
	self assert: cmdList size equals: 1.
	self assert: cmdList first distance equals: 20.
```

```
RbsRobotTest >> testMergeUNmergeableCommandsBecauseDifferent

	| cmdList |
	cmdList := (RbsMoveCommand new distance: 10; yourself)
		mergeWith: (RbsDirectionCommand new direction: #east; yourself).
	self assert: cmdList size equals: 2.
	self assert: cmdList first distance equals: 10.
```


### Conclusion









