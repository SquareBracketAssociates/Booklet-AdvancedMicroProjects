## Designing little board games
@games

This chapter lists some game descriptions. The idea is to be able to use elements of such a list as design exercises. 
We suggest to focus first on designing the model of the game with tests.
In a second step you can add an UI layer based on the new Bloc framework. 

### Support 

All the games in this chapter requires a 2D grid that can be found in the package Array2D of the following http://github.com/Pharo-contribution repository.

```
Metacello new
  baseline: 'ContainersArray2D';
  repository: 'github://pharo-containers/Containers-Array2D/src';
  load.
```

### Loading Myg and Bloc

You can get some ideas how to develop your game UI by studying the Myg framework. The Myg framework is a framework to build little 2D board games. 
A Miner, Sokoban, Memory, and Takuzu have been built on top of it.
It provides ways to build levels and other facilities.

```
Metacello new
 	baseline: 'Myg';
 	repository: 'github://Ducasse/Myg:v1.0.1/src';
 	onConflictUseIncoming;
 	load
```

You will just need to execute `MygSokoban open` to get a little Sokoban game.


### Bloc 
Bloc is a new graphical library that will be part of Pharo.
If you see the name Toplo, Toplo is a new widget library built on top of Bloc. 
It is still under heavy development. 

You can find some slides: 
- https://www.slideshare.net/esug/bloc-for-pharo-current-state-and-future-perspective
- http://www.github.com/pharo-graphics/Bloc
- You can find the presentations of Bloc at ESUG 2022 and 2023 on youtube. 


### Possible Games

Here is a list of possible games to develop:

- Light Beamer
- Mimesweeper
- Flood it
- 2048
- Memory
- Tetris 
- Picross (nonogram)
- SlideOut
- SameGame
- Taquin
- Bomberman
- Maze generators

### Other resources

Besides the Myg framework mentioned above, there are some resources available that you can study.

The book Learning Object-oriented Design with TDD in Pharo available on http://books.pharo.org contains a chapter building step by step a model of Snakes and Ladders. 

In addition the book "Building a memory game with Bloc" available on http://book.pharo.org and https://github.com/SquareBracketAssociates/Booklet-BuildingMemoryGameWithBloc presents how to build a simple memory game. 
It does not use Myg.

In the Tutorial project of the Bloc repository there is an implementation of the 2048 game. It is in draft mode but you can get inspiration from it too.

```
Metacello new
    baseline: 'BlocTutorials';
    repository: 'github://pharo-graphics/Tutorials:dev-1.0/src';
    load
```

Note that the implementation of 2048 is a sketch and was used to brainstorm on skinning. It should be rewritten using more recent implementations of Bloc.

### Some generic extensions

Here is a list of generic extensions that can be applied to many games:

- Support the definition of levels by proposing a progression in terms of difficulties or different challenges.
- Offer the possibility to replay a given level.
- Offer the possibility to save a game.
- Offer the possibility to replay a game up to a certain point.
- Record the time or the number of moves to finish a game with high score management. 

![ Minesweeper: identifying mines based on the number of adjacent cells containing a bomb.](figures/MineSweeper2.png width=60&label=mine)

### Minesweeper

The user should identify the bombs using hints based on the number of adjacent bombs in the 8 directions. 

The user has two kinds of action: 
- declare that a cell contains a bomb or 
- declare that a cell is free and ask for a validation.

##### Free cell declaration: 

If the user is wrong and there is a bomb then he loses the game. If the user is right then the cell displays the number of adjacent bomb around the cell. 

##### Bomb declaration: 
when a cell is declared as a bomb a bomb is displayed.

When all the cells have been revealed or marked as a bomb, the game proceeds to the validation.  If the bombs are correctly identified the user wins.

Since the Myg framework already propose an implementation we suggest the following possible extensions:

##### Specific extensions:
- Define multiple algorithms to place the bombs. Right now it is fully random. For example make sure that the user with all the information does not have to select a tile randomly.

![ Flood it: change the color of any adjacent tiles with the same color. ](figures/FloodIt.png width=40&label=Floodit)

### Flood it

A certain configuration of tiles of different colors is placed on the board (See Figure *@Floodit@*)
The player can do a "flood fill" on the top left tile, changing the color of any adjacent tiles of the same color. The player wins if he is able to make the entire board a single color within a certain number of moves.



##### Specific extensions:
- you can introduce a color that matches multiple ones
- tiles that do not match any colors
- tiles that change colors every n actions

### Tetris and variations

With Tetris, shapes fall from the top of the screen and lines can be eliminated only when they are entirely filled up. 

##### Specific extensions

Here are some possible extensions:
- Add tiles that cannot be removed.
- Add shapes that shrink/expand when placed.


Using Tetris like tile shapes, many games can be built with different gameplay. 
Figure *@Tetris@* shows a game where the shapes do not fall from the top of the screen but the player has to select them and drop them. 
When a line is full it is removed not changing the lines on top. 

##### Specific extensions 
- Adding special tiles with diamonds and others and we different scoring and objectives.
- Placing tiles that cannot be matched and removed. 

![ Tetris variations: Here the user places forms to remove rows and lines. ](figures/BlockBlast.png width=30&label=Tetris)




### 2048

The user should merge multiple of two  numbers that are randomly drawn. 
Two numbers of the same value are merged. The resulting number of the sum replaces the sum. 
The user decides the merge by choosing one direction. All the numbers that can merge are merged in the chosen direction.

The game starts with 2 and continues with the sum e.g., 4, 8, 16, 64.... It should adapt the numbers that are placed on the board in the sense that it does not have to 2 when the average numbers are 512.

![ 2048 ](figures/2048.png width=40&label=2048)

The game ends when the board is full.

##### Specific extensions

- Merging two numbers could produce an explosion and destroy unmergeable tiles that are close to the resulting tile.


### Memory

With the memory game, two pictures are revealed one by one and the user should pair them across the game. 
Each player gets points based on the pairs he found. 

![ Memory ](figures/Memory.png width=40&label=Memory)

##### Specific extensions
- Pairing three similar tiles. Instead of identify two similar tiles, the game would have three similar tiles. 
- Some tiles could be blurry and provide more points when paired.
- Pairing many similar tiles could be a different game and the largest sequence could give more points: 2 for 1 points, 3 for 3 points, 4 for 6 points.
- Adding joker tiles. Joker tiles could pair with any tiles.


### SlideOut

Figure *@SlideOut@* describes the game: it is composed on shapes that slide in one direction. 
By sliding the different pieces, the player should be able to move the red elements to the exit.

![SlideOut: Elements can slide in one direction but are blocked by others. The goal is to get the red element out.](figures/SlideOut.png width=40&label=SlideOut)


### Laser game

A laser beam is activated from a source specific location.  As the laser beam traverses the grid it can hit deflecting mirrors. These mirrors will divert the laser beam's direction as it travels. Ultimately the beam should hit a target location inside our grid.  

![(a) Starting from its origin, the laser beam should reach the target. (b) Rotating a mirror changes the path of the laser beam](figures/Laser-2-Concept-MirrorRotation.png width=60&label=GameOne)
It becomes more interesting to have the user manipulate the mirrors to find the longest possible path to the target.  

That's the general idea. We can add laser cell-path counters and other game instrumentation as we develop.


### Same game

The goal of the game is to eliminate all the colored cells of the game. A group of connected cells of the same color are eliminated. When a column is empty, it is eliminated so that the two sides are touching each other. Figure *@same@* shows a same game instance. 

![ SameGame: collapsing columns by removing one by one colored of the cell of the same color. ](figures/SameGame.png width=40&label=same)



### Nonogram

Nonograms are logic puzzles where you use the number clues around the sides to color the cells in the grid to reveal a picture.  The other names of nonograms are Griddler or Picross (Nintendo game).

[https://delightfulpaths.com/what-are-nonograms-or-griddlers](https://delightfulpaths.com/what-are-nonograms-or-griddlers) explains the rules of the game. 
You can see an example in Figure *@nonograms@*. Nonograms can be in black and white or with colors.
The player should select a tile and declare whether it contains or not a color. 
The players can make a certain number of mistakes before losing the game. 

![ Nonograms: coloring cells based on number clues. ](figures/nonograms.png width=35&label=nonograms)

### Conclusion

Developing such games using Testing Driven Development is  pedagogically worth because each test can validate a given aspect of the game. In addition, a bunch of UML diagrams do not easily capture the essence of a game, as some new developers may think. Adding new features may invalidate certain previously passing tests and often require refactoring the model. 

We definitively encourage you to play the game and develop a game and variations to exercise your object-oriented skills. 

 