## Designing little board games
@games

This chapter lists some game descriptions. The idea is to be able to use elements of such a list as design exercises. All the games in this chapter requires a 2D grid that can be found in the package Array2D of the following http://github.com/Pharo-contribution repository.

We suggest to focus first on designing the model of the game with tests.
In a second step you can add an UI layer based on the new Bloc framework. 

### Loading Myg and Bloc

You can get some ideas how to develop your game UI by studying the Myg framework. The Myg framework is a framework to build little 2D board games. 
A Miner, Sokoban, and Takuzu have been built on top of it.
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

In the Tutorial project of the Bloc repository there is an implementation of the 2048 game. It is in draft mode but you can get inspiration from it too.

```
Metacello new
    baseline: 'BlocTutorials';
    repository: 'github://pharo-graphics/Tutorials:dev-1.0/src';
    load
```

Note that the implementation of 2048 is a sketch and was used to brainstorm on skinning. It should be rewritten using more recent implementations of Bloc.




### Minesweeper

The user should identify the bombs using hints based on the number of adjacent bombs in the 8 directions. 

The user has two kinds of action: 
- declare that a cell contains a bomb or 
- declare that a cell is free and ask for a validation.

- Free cell declaration: If the user is wrong and there is a bomb then he loses the game. If the user is right then the cell displays the number of adjacent bomb around the cell. 
- Bomb declaration: when a cell is declared as a bomb a bomb is displayed.

When all the cells have been revealed or marked as a bomb, the game proceeds to the validation.  If the bombs are correctly identified the user wins.

![ Minesweeper: identifying mines based on the number of adjacent cells containing a bomb.](figures/MineSweeper2.png width=60&label=mine)


### Flood it

A certain configuration of tiles of different colors are placed on the board.
The player can do a "flood fill" on the top left tile, changing the color of any adjacent tiles of the same color. The player wins if he is able to make the entire board a single color within a certain number of moves. Figure @*Floodit*@ illustrates the situation.

![ Flood it ](figures/FloodIt.png width=40&label=Floodit)

### Tetris and variations

 Figure @*Tetris*@

![ Flood it ](figures/FloodIt.png width=40&label=Tetris)




### 2048

The user should merge numbers that are randomly drawn. 
Two numbers of the same value are merged. The resulting number of the sum replaces the sum. 
The user decides the merge by choosing one direction.

The game starts with 2 and continues with the sum e.g., 4, 8, 16, 64.... It should adapt the numbers that are placed on the board in the sense that it does not have to 2 when the average numbers are 512.

![ 2048 ](figures/2048.png width=40&label=2048)

The game ends when the board is full.


### Memory

![ Memory ](figures/Memory.png width=40&label=Memory)

### SlideOut

![SlideOut: Elements can slide in one direction but are blocked by others. The goal is to get the red element out.](figures/SlideOut.png width=40&label=GameOne)


### Laser game

The game will be played on a grid. We will imagine having a laser beam that can be activated by the user. This will fire into the grid from a specific location. The laser beam will always fire from the bottom edge underneath the first column of cells (marked by the arrow in Figure *GameOne*). As the laser beam traverses inside our grid it can hit deflecting mirrors. These mirrors will divert the laser beam's direction as it travels. Ultimately the beam should hit a target location inside our grid.  Once the laser is fired we will see how the cells guide the laser to a destination. 

The cells of our grid will either be blank, have a target (shown as a circle here) or a deflecting mirror. The mirrors may be oriented in either of two ways, leaning left or right.

![(a) Starting from its origin, the laser beam should reach the target. (b) Rotating a mirror changes the path of the laser beam](figures/Laser-2-Concept-MirrorRotation.png width=60&label=GameOne)

Initial locations and orientations of the mirror cells will be randomly controlled by the game. In *GameOne*(a) the mirrors yield a correct result. However, the user has control over mirror rotation and position (to a certain amount). The user can click on a mirror cell and cause the mirror cell to rotate 90 degrees. This could alter the laser's direction as shown by Figure *GameOne*(b). When the laser hits a grid wall, its path ends.

Since, initially, this is a solitaire game, it becomes more interesting to have the user manipulate the mirrors to find the longest possible path to the target.  

The user may click on a mirror cell and cause it to slide one grid-cell in a vertical or horizontal direction. Note that a mirror cell cannot move through the grid walls nor through another mirror cell nor the target cell. In this way the user can adjust the mirror cells to get an intermediate result as shown by Figure *LongerPathOne*.

%+Finding a longer path, first move, slide %mirror.>file://figures/2-LongerPath1-Slide.png|width=60|label=LongerPathOne+

A further intermediate result is produced by rotating the mirror shown in Figure @*LongerPathTwo*@.

%+Finding a longer path, second move, rotate %mirror.>file://figures/2-LongerPath2-Rotate.png|width=60|label=LongerPathTwo+

%+Finding a longer path, last move, rotate %mirror.>file://figures/2-LongerPath3-Slide.png|width=60|label=LongerPathThree+

As a last step, one more mirror is moved to get the laser back to the target cell as shown in Figure @*LongerPathThree*@. This time the path of the laser is longer than before. And of course, it was strictly a random coincidence that the initial cell configuration already provided a correct path for the laser.

That's the general idea. We can add laser cell-path counters and other game instrumentation as we develop.


### Same game

The goal of the game is to eliminate all the colored cells of the game. A group of connected cells of the same color are eliminated altogether. When a column is empty, it is eliminated so that the two sides are touching each other. Figure *@same@* shows a same game. 

![ SameGame: collapsing columns by removing one by one colored of the cell of the same color. ](figures/SameGame.png width=40&label=same)



### Nonogram

Nonograms  are addictive types of logic puzzles where you use the number clues around the sides to color in boxes to reveal a picture.  
The other names of nonograms are Griddler or Picross (Nintendo game)

https://delightfulpaths.com/what-are-nonograms-or-griddlers explains the rules of the game. 
You can see an example in Figure @*nonograms*@. Nonograms can be in black and white or colors.

![ Nonograms: coloring cells based on number clues. ](figures/nonograms.png width=40&label=nonograms)

### Taquin

### Conclusion