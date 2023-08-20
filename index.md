# Advanced Micro Projects

This booklet is a collection of design exercises at different levels of guidance. 
- The first part proposes several little projects to exercise double dispatch, command patterns, and visitor.
- The second part proposes some unguided extensions to the previous projects.
- The third part presents some games.


# Guided Exercices
<!inputFile|path=Chapters/SimpleLan/Simple-LAN-Definition.md!>
<!inputFile|path=Chapters/SimpleLan/Simple-LAN-Self.md!>
<!inputFile|path=Chapters/SimpleLan/Simple-LAN-Hooks.md!>
<!inputFile|path=Chapters/SimpleLan/Simple-LAN-Responsibility.md!>

<!inputFile|path=Chapters/DSL/DSL.md!>
<!inputFile|path=Chapters/DSLDoubleDispatch/DSLDoubleDispatch.md!>
<!inputFile|path=Chapters/Robots/robots.md!>
<!inputFile|path=Chapters/Compass/compass.md!>
<!inputFile|path=Chapters/Expression/Expression.md!>
<!inputFile|path=Chapters/Visitor/Visitor.md!>

# Unguided Extensions

<!inputFile|path=Chapters/SimpleLan/Simple-LAN-Extensions.md!>
<!inputFile|path=Chapters/Unguided/Unguided.md!>



# Unguided Games

In this part, we propose you to design some simple board games. 
You can get some ideas how to develop your game studying the Myg Framework.
This framework has been used to develop a Miner, Sokoban and Takuzu. 

The Myg framework is a framework to build games. 
A Miner, Sokoban and Takuzu have been built on top of it.
It provides ways to build levels and other facilities.

```
Metacello new
 	baseline: 'Myg';
 	repository: 'github://Ducasse/Myg:toplo-paging/src';
 	onConflictUseIncoming;
 	load
```
You will just need to execute `MygSokoban openWithMenuBar`.

You can find some other examples in 

```
Metacello new
    baseline: 'BlocTutorials';
    repository: 'github://pharo-graphics/Tutorials:dev-1.0/src';
    load
```

It is based on the Bloc framework 

## Bloc 
Bloc is a new graphical library
- https://www.slideshare.net/esug/bloc-for-pharo-current-state-and-future-perspective
- http://www.github.com/pharo-graphics/Bloc

## Possible Games

- Light Beamer
- Sudoku
- 2048
- Memory
- Snake 
- Tetris 
- Picross (nonogram)
- SlideOut
- Quinto
- Game of Life
- SameGame
- Taquin
- Maze generator
- Bomberman

You can find some ideas of games at: 
https://inventwithpython.com/blog/2012/02/20/i-need-practice-programming-49-ideas-for-game-clones-to-code/

###Resources

<!inputFile|path=Chapters/Games/Games.md!>
<!inputFile|path=Chapters/Sokoban/Sokoban.md!>

