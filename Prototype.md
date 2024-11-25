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

I am slowly understanding how they work, after failing over and over I followed a guide which proved unhelpful and then stripped it all up to get to the basics of moveing to a desired location. This works and lays the groundwork which I can develop off of. This is also bringing me up to date with why the previous ones didn't work, as when I switched the 'move to' from a predone vector to the grass object the animal actor refused to move, so my thoughts are to translate the object's location into a readable vector for the behaviour tree. The end goal of this commit is to do this and upload onto the github website.
The level has been arranged to something more similar to the puzzle that's going to be used in the prototype, with a gap in the middle for the animal (when finished) to fall down to provide passage for the player to access the other side. 

### Recent Updates - 18/10
* The animal now moves according to the behaviour tree, so it currently moves towards the grass actor.
* Grass actor detects when its collision touches the animal and moves to another spot, creating the food collection cycle
Next steps based on this would be to add more onto the animals tree for a rest cycle and prowling/searching.
Giving the animal more believability would be nice as an extra step, such as turning manually and animations on its movements
Alongside this I would need to add an item pickup to allow the player to pickup the grass to have the animal seek it out after being placed.

The main issue of why the unique tasks made were not working have been found to be because the node used to initiate them was "Event Receive Execute" instead of "Event Receive Excecute AI", this has been fixed so the behaviour trees can be simplified.

### Recent Updates - 26/10
The behaviour tree has been edited with branches for:
* Looking at the object
* Moving towards the object and plays animation for eating
* Moving towards the pit as a last resort (a placeholder while the function is being worked out)

Adding a grab system for the item, but theres an issue with the item not spawning with the players at their location.

Overall the recent additions added to the behaviour trees, with there now being a wider range of options connected to the main sequences. The fox animal now has a rotation tool towards a selected area that needs fixing as it doesn't go towards the item smoothly as a rotation. Alongside this there is a constant issue with the new grab feature, where the actor that is being picked up is returned back to where it was destroyed. 

Moving on I need to fix the issues with the grab feature and simplify the foxes behaviour so it becomes easier to read and edit.
The navigation mesh needs to be better implemented so the object doesn't spawn within the walls.
I also could add an inventory system for the picked up item alongside a win condition for when the player reaches the other side.
Once these have been implemented I will be able to create the protoprototype for other users to experiment with.

### Animal searching/Grass location change tests
* Moved twice then grass spawned right next to animal, preventing it from being overlapped again
* Didn't appear to move when overlapped with animal
* Had a perfect change of location up to 5 times before staying in the same spot
* Grass object moved inside a wall.

> Was given advice and shown how to add a function library for the "getrandomlocationinnavigableradius" labelled as the random location function
> Used a "nearly equal" to compare the transformed location and the original, so it can try and recorrect the move.
> I tried adding a secondary smaller collision box for primarily the animal but it only works half the time
* Animal now moves towards it, but the issues of a close move still occurs
> Solution found was to loop the random location finder and setter until the grass block leaves the animals collision.
* Grass block checks for the animal, if its still collided it performs another random move

Next steps are to add gravity and make the grass spawn in front of player rather than inside.
Edit the ai to only go in the pit if the grass is there
Add celebratory text
Extras...
Create playable build.

### 31/10
Currently trying to fix the grass block and its collision, as in order to fall when dropped I made it a physical object. This caused an infinite loop when the animal interacted with it, which I theorise is to be caused by the animal not being able to fully complete the goal of reaching the origin of the grass block. To solve this I fiddled with the collision types in the project editor, adding a "grass" type that can be transferred to other items of similar needs.
>Image of error screen
The only other issues occurring with this now is the cube appearance stays in place while the object moves. I can tell based on how the animal moves towards empty spaces each time the behaviour tree loops, while the block appears to remain in the same location. I tried adding a shpere mesh to see if this would move whilst the others stayed in the same location, which is exactly what happened. When comparing the differences I noticed it could be due to the simulate physics being ticked, which when unticked allowed the box to move but stopped the box from falling.
>Image of new grass hierachy
This has been solved by changing the heirachy to have the mesh become the root node with the collision box attached to that, now when the grass block moves, everything is grabbed with it with an extra detail of it growing out of the ground
>Image of before and after growing
The placement of the block had to be fixed again so its placed at a distance, so a "getforwardvector" was used and added to the players location to get the placement location.

The next step that needs to be implemented before the prototype level is fully playable is to alter the animal behaviour to recognise when the grass block is in the bit and proceed to follow it in. As an extra challenge.

>Current thoughts:
>> Add behaviours for the animal to detect where the object is
>> Resting nature to be added
>> Split ideas of either getting the animal to naturally fall down or a behaviour to only do so when the block is noted to be down there.

### 3/11
 This is a small update for me to alter where the grass spawns, as the grass block needed a bit of extra tweeking to get it to respawn where is fully needed.

### 5/11
The behaviour of roaming was implemented. 
This would get the animal to move to a random location inbetween the food seeking
Using the same getrandomlocationinnavigablearea worked as there wasn't a real need for the animal to go to a specific location, I just wanted to have the animal behave in more manners than just eat.

I also added a second secondary behaviour that can alternate with the walking on a selector branch of the tree, this would be the sleeping behaviour where the animal lays down. This would activate when a new float "energy" depletes past a certain point, being depleted through actions like roaming. decoratiors.......

This created an issue where upon activating the sleep function, instead of moving to the eating immediately, the animal would start the lying animation and then move as part of the roaming, getting stuck in the process.

### 


# What to include in dev log:
* Editing where the grass spawns
* Adding the roaming bahaviours
* Attempting to solve the sleepwalking
* Giving the animal branching on the Initial behaviours
* Getting assistance on fixing the sleepwalking and merging the two changes together
* Editing the numbers for energy
* Adding in the proper pit solution for the animal controller bp
* Finishing the gameplay loop

# Extra steps:
* Title, pause and win screen
* User testing
* Polishing
* Unique player character



> Iamge of mesh nav
>
> Talk about the issue with wall
> 
> Implemented a free asset pack named "variety animal pack" to temporarily act as the ai animal
> The animation came as animation sequences so I am having to put them together using state machines
![alt text](image.png)
