## Tamagotchi Mechanics
@cha:tama

### Problem Context

Bandai, the creator of the Tamagotchi game hires us to create a new version of the game.
We have to implement the behavior logic behind the simulated pets. 
In this new version, we are going to have two Tamagotchis interacting with each other and performing some basic activities together.

Our virtual pet can be sad, hungry, or happy. And its behavior depends on its state.
The state of the virtual pet changes only when an action is performed.

A new pet starts with a happiness level of 0 and it is in a happy state. 
If a pet is already in a given state, nothing should happen if it is required to change to that state (e.g., if it is happy, and I tell the pet to be happy, nothing should change in its state).

### Behavior 

You will have to implement the following behavior.

#### Eating.
A pet can eat then:
- If it is hungry, it gets happy.
- If it is happy, it increases its happiness level by one.
- If it is sad, it will not eat, and an error should happen.

#### Playing Alone.
A pet can play with itself then: 
- If it is hungry, its happiness level is reduced by 4.
- If it is happy, it increases its happy level by two. If it plays two times since eating,
it gets hungry.
- If it is sad, it gets happy.

#### Playing With Other Pets.
A pet can play with another pet then: 
- If any of them is hungry, they don’t play and nothing changes.
- If the pet is happy, it increases its happy level by four. If it plays two times since
eating, it gets hungry.
- If any of them is sad, it gets happy.

### Extensions
As the game got so popular, we have to add new mechanics to it. We are going to add
two additional types of Pets. 

#### Dog.
- Whenever it eats, its happiness level rises to 5, then it rises normally by 1. 

#### Lonely Cat.
- Whenever it plays with another pet, it gets sad.

### Tests
It is required to implement a set of test cases covering all features. It is important to select what test cases to write, having an excessive number of dummy or uninteresting tests is not good.
Test cases should cover the different states and the possible actions.
For the added extensions is only needed to test the variation of behavior, e.g., for the Lonely Cat is only needed to make it play.


### About behavior description
All the rules, descriptions, and requirements are open to different understanding. If a point is unclear or it raises different alternatives, you are free to choose the one that better suits you. The only condition is to explain it and that test cases cover the variation.
