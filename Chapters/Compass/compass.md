## Finding the north with Compass 



In this chapter we will work on an alternative way to represent directions and move computation in the 2D plan. 


### Existing situation


In the Robot implementation we computed the new position of a robot as follows: 

```
computeNewPosition: anInteger 
	"Returns a point representing the location of the next move."
	
	^ direction = #east
		ifTrue: [ self x + anInteger @ self y ]
		ifFalse: [ direction = #west
			ifTrue: [ self x - anInteger @self y ]
			ifFalse: [ direction = #north
					ifTrue: [ self x @ (self y + anInteger)]
					ifFalse: [ self x @ (self y - anInteger) ].
				]
			]
```



#### Opposite direction

Similarly we computed the opposite direction as follows: 

```
computeOppositeDirection: aDirection 
	"Returns the opposite direction. 
	Note that this implementation should be rewritten taking into account Compass' way to represent direction and their computation'"

	^ aDirection = #east
		ifTrue: [ #west ]
		ifFalse: [ aDirection = #west
			ifTrue: [ #east ]
			ifFalse: [ aDirection = #north
					ifTrue: [ #south]
					ifFalse: [ #north].
				]
			]
```