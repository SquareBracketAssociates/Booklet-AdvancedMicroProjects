## Designing little board games

This chapter lists some game descriptions. The idea is to be able to use elements of such a list as design exercises. All the games in this chapter requires a 2D grid that can be found in the package Array2D of the following http://github.com/Pharo-contribution repository.

We suggest to focus first on designing the model of the game with tests.
In a second step you can add an UI layer based on the new Bloc framework. 

### Loading Myg and Bloc

You can get some ideas how to develop your game UI by studying the Myg framework. The Myg framework is a framework to build games. 
A Miner, Sokoban and Takuzu have been built on top of it.
It provides ways to build levels and other facilities.

```
Metacello new
 	baseline: 'Myg';
 	repository: 'github://Ducasse/Myg:v1.0.1/src';
 	onConflictUseIncoming;
 	load
```
You will just need to execute `MygSokoban open`.




### Bloc 

Bloc is a new graphical library that will be part of Pharo in the future.
If you see the name Toplo, Toplo is new widgets library built on top of Bloc. It is still under heavy development. 

You can find some slides: 
- https://www.slideshare.net/esug/bloc-for-pharo-current-state-and-future-perspective
- http://www.github.com/pharo-graphics/Bloc
- You can find the presentations of Bloc at ESUG 2022 and 2023 on youtube. 


### Possible Games

Here is a list of possible games to develop:

- Light Beamer
- Sudoku
- 2048
- Memory
- Snakes and Ladders
- Tetris 
- Picross (nonogram)
- SlideOut
- SameGame
- Taquin
- Bomberman
- Four in a row
- Maze generator

You can find some ideas of games at: 
[https://inventwithpython.com/blog/2012/02/20/i-need-practice-programming-49-ideas-for-game-clones-to-code/](https://inventwithpython.com/blog/2012/02/20/i-need-practice-programming-49-ideas-for-game-clones-to-code)

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

Note that the implementation of 2048 is a sketch and was used to brainstorm on skinning. It should be rewrite using more recent implementations of Bloc.




## Minesweeper

#### Game field: 
The field is composed of cells: a cell may be clean or suspected to contain a bomb. 
At the beginning, the status of a cell status is unknown or closed.
Once a cell is open, a clean cell displays the number of its adjacent bombs. 
Using this information closed cells can be tagged as suspected to contain a bomb. 


#### Goal: 
The user should identify the bombs using hints based on the number of adjacent bombs in the 8 directions. 

The user has two kinds of action: 
- declare that a cell contains a bomb or 
- declare that a cell is free and asking for a validation.

- Free cell declaration: If the user is wrong and there was a bomb then he loses the game. If the user is right then the cell displays the number of adjacent bomb around the cell. 
- Bomb declaration: when a cell is declared as a bomb a bomb is displayed.

When all the cells have been revealed or marked as a bomb, the game proceeds to the validation.  If the bombs are correctly identified the user wins.

![ Minesweeper: identifying mines based on the number of adjacent cells containing a bomb.](figures/MineSweeper2.png width=80&label=mine)







## 2048

![ 2048 ](figures/2048.png width=40&label=2048)

## Lightout

![ LightOut or Quinto ](figures/Quinto.png width=60&label=quinto)

## Memory

![ Memory ](figures/Memory.png width=40&label=Memory)

## SlideOut

![SlideOut: Elements can slides in one direction but are blocked by others. The goal is to get the red element out.](figures/SlideOut.png width=60&label=GameOne)

## Laser game

The game will be played on a grid. We will imagine having a laser beam that can be activated by the user. This will fire into the grid from a specific location. The laser beam will always fire from the bottom edge underneath the first column of cells (marked by the arrow in Figure *GameOne*). As the laser beam traverses inside our grid it can hit deflecting mirrors. These mirrors will divert the laser beam's direction as it travels. Ultimately the beam should hit a target location inside our grid.  Once the laser is fired we will see how the cells guide the laser to a destination. 

The cells of our grid will either be blank, have a target (shown as a circle here) or a deflecting mirror. The mirrors may be oriented in either of two ways, leaning left or right.

![(a) Starting from its origin, the laser beam should reach the target. (b) Rotating a mirror changes the path of the laser beam](figures/Laser-2-Concept-MirrorRotation.png width=60&label=GameOne)

Initial locations and orientations of the mirror cells will be randomly controlled by the game. In *GameOne*(a) the mirrors yield a correct result. However, the user has control over mirror rotation and position (to a certain amount). The user can click on a mirror cell and cause the mirror cell to rotate 90 degrees. This could alter the laser's direction as shown by Figure *GameOne*(b). When the laser hits a grid wall, its path ends.

Since, initially, this is a solitaire game, it becomes more interesting to have the user manipulate the mirrors to find the longest possible path to the target.  

The user may click on a mirror cell and cause it to slide one grid-cell in a vertical or horizontal direction. Note that a mirror cell cannot move through the grid walls nor through another mirror cell nor the target cell. In this way the user can adjust the mirror cells to get an intermediate result as shown by Figure *LongerPathOne*.

%+Finding a longer path, first move, slide %mirror.>file://figures/2-LongerPath1-Slide.png|width=60|label=LongerPathOne+

A further intermediate result is produced by rotating the mirror shown in Figure *LongerPathTwo*.

%+Finding a longer path, second move, rotate %mirror.>file://figures/2-LongerPath2-Rotate.png|width=60|label=LongerPathTwo+

%+Finding a longer path, last move, rotate %mirror.>file://figures/2-LongerPath3-Slide.png|width=60|label=LongerPathThree+

As a last step, one more mirror is moved to get the laser back to the target cell as shown in Figure *LongerPathThree*. This time the path of the laser is longer than before. And of course it was strictly a random coincidence that the initial cells configuration already provided a correct path for the laser.

That's the general idea. We can add laser cell-path counters and other game instrumentation as we develop.


## Same game

![ SameGame : collapsing columns by removing one by one colored of the cell of the same color. ](figures/SameGame.png width=40&label=mine)

## Nonogram

## Taquin

## Four in a row
