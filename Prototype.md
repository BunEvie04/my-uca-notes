# Prototype Ideas

## Game ideas

Puzzle platformer relying on AI behaviour and interaction within the world. With different pickupable items being able to affect the world and the creatures within. Some levels may ask the player to use the creatures habits to make a path forward, like removing the food so they eat at the unwalkable area full of bushes. Or the player could use fire from a torch item to scare/guide them away from the objective.

Monster Hunter (Capcom, 2004-current), specifically Monster Hunter World (Capcom, 2019) is an action role-playing game that has a strong emphasis on building a world of unique animals of varying sizes. This installment into the series in particular has a heavy focus on immersing the player into the environment, which is done through the range of animals with behaviours that fit into the areas they inhabit. This has inspired me to make this style of game, which revolves around the player being able to see and interact/exploit the animals in order to get the win condition.

## Engine

UE5 

## Language

C++
Blueprints

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

Captain Toad's Treasure Tracker (Nintendo, 2014) was a good game for me to look at when it came to the level design, as this game contains enemies that fit on a smaller scaled, simplistic level. Therefore some information can be transfered onto how I should divide the world into base areas and how the main puzzle should be set up to reach the end goal. Some levels in the game rely on blocks being moved into the right location to gain access to another part of the stage, so a similar idea can be implemented into my prototype with the animal acting as the stepping stone.

![iCaptain Toad Level](https://github.com/user-attachments/assets/e2a03f01-79cc-42e5-9131-dd7a9b38bfb4)


Later in development a new level had to be made for the prototype as the default didn't work correctly with the navigation mesh. An empty map was made with simple platforms to provide the same function as the plans.

![Level Layout](https://github.com/user-attachments/assets/c5e23918-4284-4df4-aa0a-b9744992e698)


## Research

This section will cover the research made for the features present within the prototype. Primarily it will cover my findings on ai pathways and how I can implement it into the game.

As behaviour trees are something I have little information on, I gathered research on how to implement them within the project as the main mechanic. I started by experimenting with the basic nodes and seeing how it interacts with the animal, then recieved helpful insight from my peers and lecturer on more advanced features. Using the Unreal Engine documentation page on behaviour trees was useful as a base to set everything up well for the implementation within the project, as it had step by step instructions with images on how to do so.

https://dev.epicgames.com/documentation/en-us/unreal-engine/behavior-tree-in-unreal-engine---quick-start-guide

The video below was used partway through the project to fill in the gaps of knowledge where things were not going well. In conjunction with the documentation above, my knowledge of behaviour trees grew to the point where I felt more comfortable in implementing it as the main feature of the project.

<iframe width="560" height="315" src="https://www.youtube.com/embed/QJuaB2V79mU?si=swfMoPyF1oD5Vahd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Other forms of research came in looking up certain nodes within blueprints, as I know how to implement most of the mechanics it just misses that one important node/element that makes it work efficiently. Relying on Unreal Engine documentation and AI hints allowed me to find what I miss.


## Workings

### Animal Class

To start with the ai I used a character blueprint class, with an ai controller attatched to it. I wanted to start this within blueprints so I can lay the groundwork before using c++ since this is the first proper time using ai within UE5. After the character was created and placed into the level, a navigation mesh was placed down across the entire stage along with basic blueprints for the character to move to random points on the level.
Within the animal's AI Controller, it sets up the Behaviour Tree alongside some of the variables that are contained within the blackboard component. Such as the Grass block location and if its valid or not, all set up with the event tick. The AI controller doesn't hold much more information as most of the animal's behaviours come from the behaviour tree custom tasks.

![Fox Asset](https://github.com/user-attachments/assets/fe4909a7-8108-4dbd-82f2-5a3727758d69)


<iframe src="https://blueprintue.com/render/4gyp1uwq/" scrolling="no" allowfullscreen></iframe>

* A free animal asset pack labelled "AnimalVarietyPack" was added into the project
  * Allows me to temporarily make the animal look like an animal
  * This came with the downsides of having the animations be animation sequences, alongside having to work out how to implement them into the states.
  * As a result, the behaviour tree can be expanded upon to give the ai the actions it needs to function within the ideas of the game.

### Behaviour Tree

I am slowly understanding how behaviour tree tasks work, I tried to follow the Unreal Engine documentation on it and after a few attempts I stripped it all to start again with a basic move to task. This behaviour tree can be split into two different halfs, the idle activity and the active tasks. These tasks are set up so that the fox animal is constantly in a active state, dependant of a blackboard float "energy" alongside multiple other booleans.

![BlackBoard Variables](https://github.com/user-attachments/assets/f1f59444-e405-44be-b0cb-509a3a229721)

* Idle
  * Resting
    * Causes the animal to play a short sequence of animations indicating sleep
    * The energy variable increases by a set amount
  * Roaming
    * Causes the animal to move to a random location in the nav mesh
    * Decreases the energy variable by a set amount

<iframe src="https://blueprintue.com/render/z16skiv-/" scrolling="no" allowfullscreen></iframe>

<iframe src="https://blueprintue.com/render/yc3lh-en/" scrolling="no" allowfullscreen></iframe>


* Active
  * CanReach
    * A revision of a previous task
    * Detects if the block is both valid and if it is reachable to the animal
  * PitRedo
    * A second version of a task
    * Places the animal into the pit when the grass block is placed in
    * If the grass is not in the pit it continues the gameplay loop
  * MoveTo
    * A simple move to which only works if the prior tasks return successful


<iframe src="https://blueprintue.com/render/m5iox_m0/" scrolling="no" allowfullscreen></iframe> 

<iframe src="https://blueprintue.com/render/op832tcg/" scrolling="no" allowfullscreen></iframe>


<img width="1070" alt="{Final Behaviour Tree}" src="https://github.com/user-attachments/assets/092c4a22-5987-484c-a518-79fcd07a000c">


### Grass Actor

![iGrass Viewport](https://github.com/user-attachments/assets/bcd1a327-698c-4672-ba27-579f1fcb6c49)


This is an actor that will be interacted with by both the player and the animal ai. The player will be able to pick it up (by destroying the actor and storing it as a variable) and place it anywhere within the level (using spawn actor of class) using the "E" key.

The Animal ai will interact with the grass by chasing after it, causing the actor to move to another location when both it and the animal's collision box overlap. Upon moving, it had trouple not moving directly back to the location so an inclusion of overlap functions were used. Alongside this, a mechanic for the grass to grow when moved was added to make it seem more a part of the world.

<iframe src="https://blueprintue.com/render/0k-wxu6f/" scrolling="no" allowfullscreen></iframe>

<iframe src="https://blueprintue.com/render/p6cb3krn/" scrolling="no" allowfullscreen></iframe>  


* A simple actor class to be interacted with
  * Slightly translucent to seem more like the desired outcome
  * Aimed to move to a new location when the animal interacts with it
  * Will grow in size after moving to appear like a new patch of tall grass
  * Can be picked up and placed by the player for the main puzzle element
 
## Player Character

There wasn't much changed to the player character, but since they aren't the main focus it was intentional.
The only additions made towards the player was in terms of movement, as the jump mechanic was removed to prevent the player from cheezing the level by jumping to the exit.


## Extra Items

- After testing the project, I added a collision box that moves actors back onto the stage in case they get in arease which they are not meant to
- A new level was made due to a fault with the nav mesh on the prior.

## Used Widgets

* Start Screen
  * Plays when opened
  * Lists controls
  * Clickable play button  


![TitleScreen](https://github.com/user-attachments/assets/538a39ce-60c3-4d2e-836a-b75676ef62a4)


* Description Overlay
  * Appears when holding "Q"
  * Gives description in game on objective  


![GameDescription](https://github.com/user-attachments/assets/f65ebbae-74be-469b-9842-4a876c05494a)



## Testing and Feedback

At certain intervals of the development process, I had numerous individuals try the different builds of the game, below are videos of two people testing the first build of the game. This build was found to not work as intended but was tested anyway for the other features to be shown off to the public. In addition to this, the videos show off a different level from the final designs, as some of the required features like the nav mesh did not work correctly in this initial level (ie. the nav mesh would shift to a side of the level when played, compared to in editor)

<iframe width="560" height="315" src="https://www.youtube.com/embed/C_oBPP1LZJY?si=wdt-JGFCIlhTKCf9" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>  

Feedback from person 1
* Kept falling into the hole and got softlocked
* The fox did not act as intended

<iframe width="560" height="315" src="https://www.youtube.com/embed/xLCZX4QSgKA?si=D3wUm7Qu4W_Ou2m3" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Feedback from person 2
*  The behaviour of the animal was rather inconsistent
*  There was a good foundation with a lot of potential

From this, I worked on how the the animal behaved in both the editor and the project build. I found out that only certain custom tasks in the behaviour tree functioned correctly and played in teh final build. It was odd as all online answers were unable to solve this issue, including asking on web forums like reddit and the unreal engine help site. Chatgpt was asked as well, which answered with solutions that did not solve the issue at hand. This promted me to try the angle of recreating the custom tasks again but breaking them down into multiple smaller tasks, which worked and enabled me to create another build with a working animal behaviour tree.

Alongside this, I also added a collision box that will move any actor back onto the stage, so that they don't get softlocked again.

The next bits of feedback were from a group testing setting, so I have grouped them up for simplicity:
* The fox's hitbox was too large and hit like a truck, but it made sense once I realised what I needed to do
  * The animal's hitbox had been tweeked to not move the player too much
* I had no idea of what I was doing, I accidentally crashed the game
  * A menu has been added at the start of the game with listed controls
  * A help screen found by pressing "Q" can inform any confused players.
* The grass I threw off came back but the fox was softlocked.
  * A fix for this to reset the animal has been added
  * A decorator was added that aborts the move to task if it lasts enough time without success

These rounds of testing proved useful as most of these issues I had missed prior to making these builds.

## Declared Assets
* Chat GPT
  * AI Tool
* AnimalVarietyPack
  * Free asset pack

## Main build

The final build has been uploaded onto itch.io, with the link to the project below

https://bunevie.itch.io/animalpuzzleprototype

## Video Demonstration

I have recorded a video on youtube going over some of the main features in a short playthrough

https://youtu.be/l7Iq0lCPmbI


## Reflection

This prototype project has been 10 weeks worth of progress. As such, it would hope to hold work expected to be seen of similar in the same amount of time. I feel like the end result meets these expectations alongside performing the basic role it was meant to do; it is a prototype of a game and uses an animal as the main puzzle to get to the win condition. In this regard, I feel as if I had learnt a great deal of knowledge into how ai can be used within games and its implementation. I have also learnt a lot as to how teams within the games industry perform due, in part, to how this project was set up with bi-weekly stand-up meetings to talk about the project. Factors like this aid in the development process and give that understanding of the games industry. I only hope to be able to deliver a fully fleshed out game in return from this prototype.


## Bibliography

Capcom (2018) Monster Hunter World. (s.l.): (s.n.).

Nintendo (2014) Captain Toad: Treasure Tracker. (s.l.): (s.n.).

Games, E. (s.d.) Behavior Tree Quick Start Guide. At: https://dev.epicgames.com/documentation/en-us/unreal-engine/behavior-tree-in-unreal-engine---quick-start-guide (Accessed  05/12/2024a).

Games, G. (s.d.) How to Make a Simple Behavior Tree in Unreal Engine 5 - Advanced AI. At: https://www.youtube.com/embed/QJuaB2V79mU?si=swfMoPyF1oD5Vahd (Accessed  05/12/2024b).



