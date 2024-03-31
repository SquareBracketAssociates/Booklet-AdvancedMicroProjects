## Civilization
@cha:civilization

In this chapter you will design a simplified version of the combat mechanics in
turn-based strategy games such as Civilization or FreeCiv [https://en.wikipedia.org/wiki/Freeciv](https://en.wikipedia.org/wiki/Freeciv) as an open-source alternative.

### General Rules
Here are some general rules:

- We have a game board made of a grid of tiles, each tile may contain (or not) one unit.
- Each unit has a given type (e.g. Archer, Marine, Pikeman, Knight, etc), a health and experience level.
- The health level is a percentage and goes from 0% to 100%.
- The experience level is a value from 1 to 3.
- Units in neighbor tiles can attack each other.
- The attacking unit will provoke damage to the defending unit and also it will receive damage from it.
- The amount of damage received from each of the units is calculated independently using two math formulas, one for the attacker and one for the defender.
- After the battle, the health of the attacker will be reduced by the amount calculated
and the same will happen to the defending unit.
- If the attacking unit gets to zero or lower health, it should be removed from the board.
- If the defending unit gets to zero or lower health it should be removed from the board.
- If the defending unit is removed from the board, the attacking unit will move into the tile occupied by the defending unit.

### Defending Unit Damage Formula

The calculation of the impact on the defending unit is calculated by the formula by the following formulae: `Dd = Ap * Atm + Dti`

##### Defending Unit Damage (Dd). 
It is the impact on the health of the defending unit. This value is calculated by the formula Figure 1 and depends on the attacking unit’s offensive power, the attacking unit’s type and the terrain occupied by the defending unit.

##### Attacking Unit Power (Ap). 
It is the power of the attacking unit type multiplied by the factor of experience. The factor of experience is equal to 1 for level 1, 1.5 for level 2, and 2 for level 3.

##### Defending / Attacking Unit Types Combination Modifier (Atm).
This value depends on the combination of the types of defending and attacking units. Some units have benefits when fighting against other units. For example, If a Knight attacks a Warrior unit, the Knight has a modifier of 2, as the Knight can charge a Warrior unit. If a Knight attacks a Pikeman unit, the Knight has a modifier of 1 as the Pikeman can repeal the charge of the knight. For a complete list, see the table of units (Section 3).

##### Defending Unit Terrain Impact (Dti).
The combat is performed in the tile occupied by the defending unit. Each tile has a given type of terrain, and each type of terrain provides its own Defending Unit Terrain Impact value. For a complete list, see the table of terrains (Section 4).


### Attacking Unit Damage Formula

 The calculation of the impact on the attacking unit is calculated by the formula: `Ad = Dp * Dtm + Ati`
 
##### tacking Unit Damage (Ad). 
It is the impact on the health of the attacking unit. This value is calculated by the formula Figure 2 and depends on the defending unit’s defensive power, the defending unit’s type and the terrain occupied by the defending unit.

##### Defending Unit Power (Dp).
It is the power of the defending unit type multiplied by the factor of experience. The factor of experience is equal to 1 for level 1, 1.75 for level 2, and 2.5 for level 3.

##### Defending / Attacking Unit Types Combination Modifier (Dtm).
 This value depends on the combination of the types of defending and attacking units. Some units have benefits when fighting against other units. For example, if a Knight attacks a Pikeman unit, the Pikeman has a modifier of 2 as it can repeal the charge of the knights. If a Knight attacks a Warrior unit, the warrior has a modifier of 1, as it does not have any advantage in the defense. For a complete list, see the table of units (Section 3).

##### Attacking Unit Terrain Impact (Ati).
The combat is performed in the case occupied by the defending unit. Each case has a given type of terrain, and each type of terrain provides its own Attacking Unit Terrain Impact value. For a complete list, see the table of terrains (Section 4).

### Units

We consider the following units: warrior, archer, pikeman, and knight.

##### Warrior. 
A basic foot soldier holding a sword
- Attacking Unit Power: 10
- Defense Unit Power: 10
- Relations with other units: N/A

##### Archer.
 A basic foot soldier with a bow and arrows.
- Attacking Unit Power: 20
- Defense Unit Power: 5
- Relations with other units: N/A

##### Pikeman. 
A soldier armed with a Pike. Effective against charges from the Knights.
- Attacking Unit Power: 5
- Defense Unit Power: 20
- Relations with other units: When it is attacked by a knight, it has a Dtm
value of 2.

##### Knight.
 The Knight is a heavy cavalry unit.
- Attacking Unit Power: 20
- Defense Unit Power: 5
- Relations with other units: When charging on any non-Pikeman unit, it has a Atm value of 2.

### Terrains

We consider the following terrains:

##### Flat Terrain.
This terrain does not have an impact on the combat. It has Ati and Dti equals to 0.

##### Hilly Terrain. 
This terrain makes it easier for the attacking part. It has an Ati of 0 and a Dti of 10. If the attacking unit is a Knight, the Dti is doubled.


### Tests

You should at least implement tests for the following use cases. Note that there should be asserts for the health of the units, and the discounted points for each of them.

- Make combat two warrior units of level 1 in a flat terrain.
- Make a Knight (level 2) attack a Warrior (level 3) in hilly terrain.
- Make a Knight (level 2) attack a Pikeman (level 3) in hilly terrain.
- Make a Knight (level 2) attack a Pikeman (level 3) in a flat terrain.
- Make an Archer (level 1) attack a Pikeman (level 3) in a flat terrain.
- Make an Archer (level 1) attack a Pikeman (level 3) in a hilly terrain.