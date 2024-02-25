## About Pharo and Moocs

In this short chapter we want to stress some key properties about Pharo and the teaching material available. 

### A truly excellent and pedagocial language

Pharo is an truly excellent language and environment to teach object-oriented programming. 
Here are some reasons you will certainly recognize if you ever programmed or taught Pharo.

- **Tiny Syntax**. The full syntax of Pharo fits on half of a postcard (see Listing *@fullsyntax@*). Good element can learn Pharo syntax in a couple of hours and productive in a couple of days. 
- **A uniform object model without any exception**. Everything is an object and there is not a single exception. The execution model is the same at all level. There is no special rules for class methods.
- **Ready to use out of the box**. Pharo is ready to use in 2 min. There is no need to configure Eclipse. The SUnit framework is ready to use. 
- **Highly immersive IDE**. Developers get immersed in a sea of objects. They can interact with live objects and this is a huge win to deeply understanding the object-oriented metaphor. They talk to their objects.
- **Gorgeous TDD support**. Pharo is the best environment to develop following Test-Driven Design. In addition Pharo supports eXtreme Test-Driven Design that take full advantage of Test-Driven Design and liveness of Pharo. You literally develop in your debugger in the context of a test execution.
- **Advanced integrated tools**. Pharo comes out of the box with a large set of tools: It offers refactorings, code critics, test coverage. It supports microcommits: all the changes and versions of all compiled methods are one click away. Developers can navigate back in their history, run the tests to validate a change revert. It has a full integration with Git. 


```caption=The full syntax of Pharo&label=fullsyntax
exampleWithNumber: x
	"This method illustrates the complete syntax."
	<aMethodAnnotation>
	| y |
	true & false not & (nil isNil)
		ifFalse: [ self halt ].
	y := self size + super size. 
	#($a #a 'a' 1 1.0)
		do: [ :each | Transcript
			show: (each class name); 
			show: (each printString); show:''].
	^ x<y
```


### Some testimonies
While this book is the companion exercise for the _Advanced Object-Oriented Design_, it reuses a couple of concepts from the Pharo mooc. The Pharo Mooc is of high quality and received excellent feedback. 

Here are some testimonies of the Pharo mooc. 

#### In french 
_J'ai trouvé ça très intéressant, beaucoup plus que prévu ! je regrette de ne pas m'y être mis plus tôt. J'ai enfin l'impression de vraiment faire de la POO ! Ou à l'inverse je me rend que je n'en faisais pas vraiment... - Anonymous, 2019_

Mooc absolument remarquable. Superbe voyage autour de Pharo. Le paradigme objet qui (re)prend enfin du sens ! - Anonymous - 01/03/2019

#### In English

I have just completed week seven of the Pharo Mooc (beginner and object oriented tracks) I am starting a redo of the Mooc with the web track (TinyBlog project). I have already learned so much ! I have spent the last 20 years or so in software development and, following this Mooc, I realized I hadn’t really grasped the essence of object oriented design. - Anonymous

_Really one of the best mooc I have ever attended. And I have attended quite a few (openSAP, openHPI). As an old fashioned ABAP developer I want to be reborn as Pharo developer in my next life :-) - Anonymous_

Hi! I finished the MOOC some weeks ago and I would like to congratulate everybody involved! After a decade+ of Python programming I think I found my new favorite language :). I'm making a small Teapot server for Slack command bots, I'm goona push it to Github (yay Iceberg), if anyone is interested. - EduardoPadoan

_I just completed the @pharoproject Mooc the best investment I have ever made of my time. MAQBOOL
Hey all - I've just finished the Mooc - thanks for an excellent course and a thouroughly interesting look at a new way to program :smile: Looking forward to starting to play with Pharo on some upcoming ideas I've had. - Tieryn_

As much as I thought I understand object-orientation, it is very clear NOW that without a truly useable Smalltalk, which Pharo is, it is impossible to really understand and exercise object-orientation. Thank you all soooo much. - Mike D. 06/12/2020

_Hey all - I've just finished the Mooc - thanks for an excellent course and a thouroughly interesting look at a new way to program :smile: Looking forward to starting to play with Pharo on some upcoming ideas I've had - Anonymous_

A general comment I wanted to make is that the MOOC so far has been great. Impressed with the quality and content, and grateful that it is available and free. Many thanks! - Aryeh

_IMHO the videos were very well done. I would even say shockingly well done… for a bunch of programmers who are supposed to be clueless about design - SeanDeNigris - 10/26/2017_

The more I learning about @pharoproject the more I appreciate it's beauty and simplicity, finally, object-oriented programming is done right - MAQBOOL




## Lectures 

Add here one testimony of the summer school student

The material of the _'Advanced Object-Oriented Design'_ MOOC available at [http://advanced-mooc.pharo.org](http://advanced-mooc.pharo.org) has been refined over several years. It has been used for many successful lectures at different levels and configurations.

We describe some possible pedagogical objectives, some key insights, and different setups to take advantage of such a material.
The conventions to refers to the slides and videos of the two Moocs follow the one of the original names:
- W (which stands for Week) is used in the Pharo Mooc and
- M (which stands for Module) is used in the Advanced Object-Oriented Mooc.

### Possible pedagogical objectives

The material proposed by the MOOC can be used to give lectures on the following topics:

- Basic object-oriented programming (excluding for example Law of Demeter, Typing, Design Patterns)
- Test-Driven Design
- Basic Object-Oriented Design (creating hooks and template, designing reusable objects)
- Advanced object-oriented design (including Design Patterns and type consideration)

In addition and as we will show below, such goals can be easily enriched with soft skills such as:

- How to find information?
- How to report activity?
- How to get some help by asking questions in forums or online chat?
- How to report problems?

The _'Advanced Object-Oriented Design'_ Mooc complements the Pharo Mooc available at [http://mooc.pharo.org](http://mooc.pharo.org)


### Essence of OO Design from 1/2 to 1 Day Lecture

For a lecture of three hours we usually present the essence of dispatch, key points about inheritance and core extension mechanism.
We use the following material from  [http://advanced-mooc.pharo.org](http://advanced-mooc.pharo.org):

- M1-1 LectureEssence of Dispatch: Taking Pharo Booleans as Example
- M1-2 LectureEssence of Dispatch: Let the receiver decide
- M1-3 LectureInheritance Basics
- M1-4 LectureInheritance and Lookup: Self - Understand lookup once for all
- M1-5 LectureAbout super
- M3-2 LectureMessage Sends are Plans for Reuse
- M3-3 LectureHooks and Template: One of the cornerstones of OOP


### Pharo in 1 Day Lecture

Even if this is not directed supported that the Mooc [http://advanced-mooc.pharo.org](http://advanced-mooc.pharo.org), the Pharo Mooc [http://mooc.pharo.org](http://mooc.pharo.org) can be used and combined to produce a simple introduction to Pharo.

Here is the material that we use.

- W1S01-What is Pharo?
- W1S05-PharoSyntaxInANutshell
- W1S06-Blocks
- W1S07-Basic-Blocks-Loops
- W1S07-BasicBooleansAndCondition
- W1S08-Loops
- W1S10-ClassAndMethodDefinition
- W2S01-Messages
- W2S02-Messages-ForTheJavaProgrammers
- W2S03-Basic-Variables
- W2S03-Messages-Precedence
- W2S04-Messages-Sequence
- W2S07-CharacterStringSymbol
- W2S08-Basic-ArraySetOrderedCollection
- W2S10-Iterators
-  W2S11-Streams

Here are some extra lectures students may want to follow
- W2S05-ParenthesisVsSquareBrackets
- W2S06-Yourself
- W2S09-UnderstandingMistakes
- W3S00-TeapotAsAPretext

We often also present some knowledge about tests:

- M2-1 LectureTest 101: The minimum you should know
- M2-3 LectureTest-Driven Development
- M2-4 LectureXtreme Test Driven Development: Getting a productivity boost

### Basic OOP in 1/2 to 1 day


- W3S01-WhatisAnObject
- W3S02-WhatisAClass
- W3S03-MethodVsMessages
- W3S04-OOParadigm


### Pharo and OOD in 2 Days

Often we start by one day on Pharo and we take another day to show the essence of OOD. 



more here.



### Advanced object-oriented design lecture example

During several years we used and developed around this material the following lecture whose description is available at [https://github.com/pharo-mooc/AdvancedOODesignWithTDD](https://github.com/pharo-mooc/AdvancedOODesignWithTDD)

The lectures length is around 10 slots of 4 hours covering a mix of lectures and labs.
The level of the students was Master 1. Their level is heterogeneous. 

The objectives of the lectures were: 

- Revisiting basic object-oriented programming 
- Test-Driven Design
- Advanced object-oriented design 
- Reverse engineering
- Test quality with mutation testing
- Soft skills:
	- reporting: how to report activities?
	- how to ask help, how to find information?
	- how to learn fast a new language?
	- how to report problems?

#### Setup 

During the first two weeks they had to learn Pharo and report how they are learning, what were their strategies.
We gave no lectures on Pharo. We listed some resources but gave no indication.

- [http://mooc.pharo.org](the mooc on pharo)
- [https://discord.gg/QewZMZa](Pharo discord channel)
- [http://books.pharo.org](Pharo by Example)
- [http://books.pharo.org](Pharo with Style)
- [https://scg.unibe.ch/download/oorp/OORP.pdf](Object-Oriented Reengineering Patterns)


Each week the students have to watch a couple of videos and one or two lectures are given by us.
During the first 6 weeks, each week they had to do some exercises following some scripts.

#### Calendar 
Our calendar is the following one: basically

#### One glance schedule

- 01 Week:  Test introduction
- 02 Week:  OOP refresh
- 03 Week:  Reverse engineering
- 04 Week: Test Quality
- 05 Week: Presentation -- *Presentations on Learning and data structure analysis*
- 06 Week: Hook and templates
- 07 Week: Double dispatch -- Examen
Break
- 08 Week Visitor
- 09 Week Composite 
- 10 Week Inheritance
- 11 Week Types
-- Exam






