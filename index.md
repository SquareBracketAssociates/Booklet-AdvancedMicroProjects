## Introduction




This book accompanies the _'The Advanced Object-Oriented Design and Development with Pharo'_ MOOC (AOOD) that is freely available at [https://advanced-design-mooc.pharo.org](https://advanced-design-mooc.pharo.org).
The AOOD Mooc is not about Pharo but about object-oriented design and presents a large set of topics on this subject from basic to advanced points. From this perspective, AOOD Mooc extends the Pharo Mooc [https://mooc.pharo.org](https://mooc.pharo.org). AOOD Mooc uses Pharo and readers may want to watch some videos of the Pharo Mooc to better understand the code. The module 0 of the AOOD Mocc proposes a selection of lectures to get up to speed with Pharo.

The current document contains a collection of design exercises at different levels of guidance and difficulties.

- The first part of the book is dedicated to teachers and presents different setups in which this material has been used.
- The second part proposes several little projects to exercise double dispatch, Command, and Visitor Design Patterns.
- The third part proposes some unguided extensions to the previous projects as well as some exercises that are also loosely described to give space for variations. 
- The fourth part presents some game ideas that you are invited to design and build with Bloc the new graphic layer of Pharo and that can also benefit from the micro-framework Myg. 

# Teacher corner

<!inputFile|path=Chapters/ForTeachers/forTeachers.md!>

## Module Exercises

The module is composed of 10 modules and an optional one around Pharo.
There is no direct mapping one to one mapping between the exercises and the modules. 
For example the Module 2 around tests is the second one so that the learners can try to write tests
in any of the exercises. In addition when we could all the guided exercises contained tests. 


- Chapter A basic LAN application
- Chapter *@cha:dsl@* (Crafting a simple embedded DSL with Pharo)
- Chapter *@@cha:stone@* (Stone paper scissors)
- Chapter *@cha:dsldd* (Revisiting the Die DSL: a case for double dispatch)
- A little saturn PathFinder
- Chapter *@cha:compass@* (Finding the North with Compass)
- Chapter *@cha:expressions@* (A little expression interpreter)
- Understanding visitors

- Little unguided projects
- Tamagotchi Mechanics
- Civilization
- Designing little board games



# Guided Exercices 
<!inputFile|path=Chapters/SimpleLan/Simple-LAN-Definition.md!>
<!inputFile|path=Chapters/DSL/DSL.md!>
<!inputFile|path=Chapters/PaperStoneScissor/PaperStoneScissor.md!>
 
<!inputFile|path=Chapters/DSLDoubleDispatch/DSLDoubleDispatch.md!>
<!inputFile|path=Chapters/Robots/robots.md!>
<!inputFile|path=Chapters/Compass/compass.md!>

<!inputFile|path=Chapters/Expression/Expression.md!>
<!inputFile|path=Chapters/Visitor/Visitor.md!>

# Unguided exercises

In this part, we propose multiple extensions to the previous projects.
It is fun to challenge ourselves to see how we could support the proposed variations.

<!inputFile|path=Chapters/Unguided/Unguided.md!>
<!inputFile|path=Chapters/Tamagotchi/Tamagotchi.md!>
<!inputFile|path=Chapters/Civilization/Civilization.md!>

# Unguided games

In this part, we propose you design some simple board games using the Bloc graphical framework taking as an example the games of the Myg project.

<!inputFile|path=Chapters/Games/Games.md!>



