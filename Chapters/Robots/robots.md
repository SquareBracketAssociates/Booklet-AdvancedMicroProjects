## Robots

![Pillar logo](figures/pillar.png width=30&anchor=fig)


### Robot space

- parseCommand
- space 
- 



A typical session

```
move 10
turnLeft
dropLoad
load
```
### Robot

implement orders

```
move 10
```

```
turnLeft
```

```
dropLoad
```


### Sending order to robots


- parseLines
- parseLine
- executeCommand: 


### Adding new command

```
dropLoad
```

```
turnRight
```

### Challenge one: Path optimizations

How to support path optimizations

```
move 10
move 20
```

```
move 30
```


### Challenge two: Replay
How to support replay

```
resetMonitor
move 10
turnLeft
orders
> #((move 10) (turnLeft))
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

### Add new order



















