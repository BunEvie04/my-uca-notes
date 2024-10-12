# Prototype Ideas

## Game ideas

Puzzle platformer relying on AI behaviour and interaction within the world. With different pickupable items being able to affect the world and the creatures within. Some levels may ask the player to use the creatures habits to make a path forward, like removing the food so they eat at the unwalkable area full of bushes. Or the player could use fire from a torch item to scare/guide them away from the objective.

## Engine

UE5 
(reason)

## Language

C++
(reason)

## Possible mechanics to focus on
- AI implementation through both docile and aggressive creatures
    - The creatures themselves can have AI pathways that influence what it does
    - Interacting with the environment through its behaviours
    - Switching between a searching phase, a resting phase and an eating phase
    - Phases get cycled through from resting -> searching -> eating and so forth
- Inventory system to store and use items
    - Keys used to open doors
    - Grass that can placed in front of the player
    - Torches that can create fire on certain tiles/anywhere
    - 
- Different movement types to enable world traversal
    - Climbing
    - Jumps (possibly more than one)
- Attacks as a form of interaction
- Movable blocks within the world
- Character dialogue as in universe explanations
- Carrying mechanic
    - Larger items
    - Possibly the creatures within reason

## Level Plan

The overal plan for the prototype is to get from point A (at the bottom of a hill) to point B(at the top of the hill). This can be accomplished through puzzle solving with the different mechanics at play.  
There will be a fur coated animal which covers one to four tiles total, with it having options between different patches of tall grass to eat at, with gaps between resting.  
While this creature is resting, the player can then harvest the remaining growing crops to then place in a pit, for the animal to fall and creaete a path to the exit.

## Research

This section will cover the research made for the features present within the prototype. Primarily it will cover my findings on ai pathways and how I can implement it into the game.

> how would i first implement ai within ue5 cpp?
>

## Workings

To start with the ai I used a character blueprint class, with an ai controller attatched to it. I wanted to start this within blueprints so I can lay the groundwork before using c++ since this is the first proper time using ai within UE5. After the character was created and placed into the level, a navigation mesh was placed down across the entire stage along with basic blueprints for the character to move to random points on the level.

A behaviour tree was implemented with a blackboard planned to give the animal ai different actions/states, for now while things are being set up basic tasks named "Idle", "Searching", and "Eating" have been made. These will be expanded upon once I finish initialising the ai character with animations.
Speaking about the ai character, a free animal asset pack labelled "AnimalVarietyPack" was added into the project so that I could temporarily make the animal look like an animal. This came with the downsides of having the animations be animation sequences, alongside having to work out how to implement them into the states. Once this is in place the behaviour tree can be expanded upon to give the ai the actions it needs to function within the ideas of the game.

As I am slightly unfamiliar with animation sequences I experimented with animation blueprints to bring the sequences together, however I am currently unsure of the reasoning behind what to do.


>
> Iamge of mesh nav
>
> Talk about the issue with wall
> 
> Implemented a free asset pack named "variety animal pack" to temporarily act as the ai animal
> The animation came as animation sequences so I am having to put them together using state machines
