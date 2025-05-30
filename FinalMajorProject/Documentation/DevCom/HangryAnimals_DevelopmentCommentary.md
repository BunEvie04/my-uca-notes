# DevelopmentCommentary_HangryAnimals  

## Project Outline  
The desired result is to develop the mechanics used in the prototype so that the player can learn the mechanics behind the animals alongside how items affect them in their routines.  


My goals for this project include:
* Multiple animals present with different actions relating to them
* Player actions such as placeable items that interacts with the animals
* Different levels and goals for the player to complete  

The development process will be set up and divided into sprints that will manage my time to effectively negate most work build-up. This maintains the agile methodology of working in short bursts with time to reflect and manage the current stages of a project during development. Being flexible will assist in any events of emergencies.  


Some difficulties that I may have with this project can be found within the design elements around the stages, as most of my ideas are around the mechanics themselves with the level design coming into play to fit in with the features. Alongside this I worry if I will have enough time to flesh out the animals, which I will have to work on with methods such as trello boards and timelines.  



## Research  

### Methodology   
Whilst researching for my game, core points behind the prototypes development were looked at to see if they can be expanded upon. This mainly came from Monster Hunter World (Capcom 2018), where the primary goal besides slaying the large creatures is to capture and study the world and how the monsters interact with it. This laid the groundwork for the ideas that would be used such as trapping and luring of monsters with tools.  
From here, I wanted to look at other games on the separate side of the spectrum of animals in games; from being creatures, to being tools and obstacles the player uses to move forward. This was an idea founded from 'Towards a Categorization of Animals in Video Games' (Jański, K. 2016), where they talk about how the usage of animals differs between games depending on the author's intent.  
The example that came to mind is Captain Toad: Treasure Tracker (Nintendo 2014) where the enemy encounters mainly consist of manoeuvring around them to get to the goal. I wanted to look at animals as tools as it may help with designing some puzzles and areas in game, especially as the fox in the prototype acted as such in its utilization as a platform. Since the game's premise is all about utilising animal behaviours in puzzles, I figured it'd be another good starting point for the main game.  


### Game Sources  
#### Monster Hunter World (Capcom 2018)  
This game became an inspiration with regards to how monsters behave in an environment uninterupted or otherwise. The environment is intractable with many options for the player to exploit monsters to capture or slay them. I talk about this specific entry in the series due to the increased development time and developed hardware which allowed the team behind the game to implement more behaviours into the monsters that inhabit the environment.  
   
Such examples of this can include each monster having a cycle of activities they perform, from finding and eating food, to marking their territory, to fighting with other monsters over resources. One of my favourite monsters, named Vaal-Hazaak, displays this to a higher degree due to its symbiotic relationship with gasses released from the rotting flesh in its habitat, where it draws in small monsters when nearby.  

Other parts of the game intrigue me with mechanics that I'd like to include in the final product, that being the hunter's notebook that the player would use to research the locations of the monsters and give hints on how to fight them. I'd like to include such an idea as a helpful guide book as a more diegetic way for the player to receive information on the animals in game.  

![MonsterHunterWorldHuntersNotes](https://github.com/user-attachments/assets/ef4e862e-c2c9-493a-a38a-9268f818705c)    
*Image of the notebook - Displaying the useful information about one of the monsters*

This is a key point that I want to include within this developing game, that being animals that take have a loop of actions they perform whilst being reflexive around the players actions.  

#### Captain Toad's Treasure Tracker (Nintendo 2014)  
As part of the Super Mario series developed by Nintendo, this game is developed with the intention to be user friendly with a focus on putting the player first. The game revolves around using manoeuvring around enemies located within small scaled geometric levels alongside solving simple puzzles to collect items and reach the goal   

![446984647-317f55c5-3082-4b0d-a1dd-d9c0dbdad8a0](https://github.com/user-attachments/assets/3a0dd0ba-c4ca-4836-9bcd-ba2c71fe574c)  
*Image containing the creatures in the protagonists path*

This game is another of my inspirations during development since I have the decision between the visual and the gameplay elements of the animals. This is something I have previously talked about (and will in the next section) but after looking at this game and performing some self-reflection on my skills as a developer, I have decided that focusing on the gameplay elements of the animals should come first and extra behaviours could come later as extra flourishes.  



#### Nintendogs (Nintendo 2005)  
The third game that struck out to me to research was Nintendogs, as this game, compared to the other two, has the animals as the primary focal point. The dogs behave as close to 1-1 as they would outside the digital space, as this is a virtual pet simulation. The game gives the player methods to interact with the dogs, either through caring for them with bath time and brushing, or through playing and joyful interactions. Perhaps through more personal interactions with the animals will the player truly get a feel for how they behave and give back to the game's world. Alternatively, for the short term, simply using tools that provide feeding and other interactive methods would work all the same.  

![Care2](https://github.com/user-attachments/assets/626f4c92-ddcf-44a6-b4f5-f2215e023dc1)  
*Image containing a fould beast being cleansed at bathtime*




### Academic Sources  
Previously I wrote an essay titled "How would Animal Behaviour translate into game formulas?", where I looked into numerous sources to talk about how animals can be utilised in video games and to what degree are they implemented to real world behaviours. The goal of this was to research into the topic to try and find that middle ground where the player can still become immersed into the animals behaviours and actions but don't take away from player actions/still allows the player to utilise them as game mechanics within the game itself.  

Relating to the direct topic of animal behaviours doesn't appear often within academic papers. However, during my research I found a paper 'Towards a Categorization of Animals in Video Games' (Jański, K. 2016). One of the primary issue brought up within this work was the different "categorizations: one functional, one visual", with this relating to my work in how the different potential animals present would have to balance the line of how gamified it would be with its behaviours contrasting how it would outside of the screen.  

Alternatively, when looking at 'Animals Video Games and Humanity (Tyler, T. 2022), they refer to how many video games use animals as interchangeable set pieces that are "confined to a restricted range of stereotypical movements" (pg 9). For the topic animals in games it rings true for a lot of games on the market, as it is quicker to have one set of motions for all the animals in a game when they aren't the main point. It wouldn't be a bad idea to incorporate this philosophy into the game with regards to similar activity shared between different animals. An example of this would be in how the animals could all search for food and divert the behaviours from there.  



### Documentation Sources  
Helpful tutorials and videos can assist down the line as my knowledge of a lot of unreal systems isn't the best. Using some tools to assist the process is always a good idea as this prevents slowdown due to lack of knowledge.

The main offenders when it came to needing tips were the menus and working with behaviour trees. Behaviour trees and everything attached (decorators, blackboard variables) are complex to understand for a first time use, so I have been using videos and tutorials to gather the basics of this to then expand upon through my own experimentation.

https://dev.epicgames.com/documentation/en-us/unreal-engine/behavior-tree-in-unreal-engine---quick-start-guide


<iframe width="560" height="315" src="https://www.youtube.com/embed/hbHqv9ov8IM?si=dMjicFJYwJh9R0zu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>  

<iframe width="560" height="315" src="https://www.youtube.com/embed/9JOstDKNHJg?si=ICzexVAbo8yJUDD2" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>  

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ff67XtqgSxc?si=T3e0L7erMuvsNa84" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>  

<iframe width="560" height="315" src="https://www.youtube.com/embed/deUc7FnGvQo?si=CnUCmeoez22qDuuu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>    


## Implementation  

### Process  
#### Developing the Animals/Behaviour Trees  
Development of the game started with the main focus on the animals, as there wouldn't be much of a gameplay loop without them. From the prototype build I had a half working Fox animal with its associating grass food block and basic behaviour tree logic. Even if it took a bit more work to incorporate, I still wanted to include these components in the final build as they were the face of what would become "Hangry Animals". 

Before that, however, it was decided to start on another animal, the Kibby, as it would be a fresh look into the process. This was ultimately useful as its resulting actions and behaviours allowed it heavy usage across both the levels present in the final build. The Kibby would cycle between roaming spots and looking around. If it spotted its primary food source, the fruit, it would activate a boolean variable set in the behaviour tree's blackboard that would switch the tree's logic via a decorator. The resulting action being the Kibby moving towards and eating the food it spotted. Learning to set this up was a struggle as the blackboard variables would be unique to each instance, and it wasn't until I realised that they should be accessed through the AI Controller that everything fell into place.  
For the longest part of this project there was an issue that the animal would be activated to a fruit when it shouldn't when there were multiple, this was an error due to the "instance sync" tickbox being ticked, meaning any change to the blackboard variable affected everything using that blackboard. It wasn't until the topic was further researched that the solution was found.  
This Kibby animal was the first fleshed out animal to be included into the main project, with a focus on cycling the basic behaviours for the player to quickly pick up on. In addition, I decided to add a function to control whether or not the Kibby can move, with this being changable by the Kibby seeing food.  
The only other alteration the Kibby has compared to the other animals is its fear of fire, and item the player can use to scare them away. This gives the Kibby a unique behaviour that causes puzzles only it can be a part of.  

![alt text](Gamelogo.png)
*The initial Kibby model during the games development*  

![Cat](https://github.com/user-attachments/assets/1173b300-a8a0-4eae-86e2-3abaf523d440)  
*The final design of the Kibby, changed to have animations work on the mesh*  

<iframe src="https://blueprintue.com/render/agl932rl/" scrolling="no" allowfullscreen></iframe>  
*This covers the main logic behind seeing the food and changing the variable to change the cycle*  

<iframe src="https://blueprintue.com/render/j0ilssz_/" scrolling="no" allowfullscreen></iframe>   
<iframe src="https://blueprintue.com/render/7-df7dv5/" scrolling="no" allowfullscreen></iframe>  
*These go over the Kibby's behaviour tree, with the main cycle of roaming until food is spotted*  

![ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/05b6a54b-d064-46c0-a8ee-a8a421801903)  
*Another example of the Kibby moving once food is spotted*  

Now that the Kibby is set up as the normal reusable animal, I felt it safe to continue work on optimising the Fox into the new version of the game, as there is a base to the game and the Fox would fit right in. To optimize them, I neatened the connections between nodes and cross referenced with the Kibby to make the Foxling more consistent, whilst keeping the Foxling's behaviour tree and tasks unique to it alone.  
The goal of it will stay the same, with the cycle being continuously followed. The Foxling has an internal meter that will be spent by existing and even more so by performing actions, with roaming being one of such actions. Eating the grass block will restore the energy meter but if it gets too low the Foxling will rest instead of roaming the next time it is on that part of the execution tree.  
The Foxling has been expanded in versatility however, as the Foxling becoming a platform in the prototype was not very apparent and would bug out quite often. To fix this issue I first opted to have an invisible platform become solid in place of the bridge gap, which would become an issue when improperly interacted with. So I wanted to visually indicate the Fox filling in the space for the player to cross, which turned into the creature growing a cube to indicate it soaking water through its fur like a sponge.  

![Fox](https://github.com/user-attachments/assets/b3588492-4ba8-4704-9666-3aa06b9f9b93)  
*The image of the Fox in its normal form/unpoofed*  

<iframe src="https://blueprintue.com/render/f88kl818/" scrolling="no" allowfullscreen></iframe>  
<iframe src="https://blueprintue.com/render/6bjlcl9i/" scrolling="no" allowfullscreen></iframe>  
*The Fox AI controller setting up and interacting with its behaviour tree*  

![ezgif com-optimize](https://github.com/user-attachments/assets/cd716b99-894d-451d-b879-83bc6790d34c)  
<iframe src="https://blueprintue.com/render/rip5llyi/" scrolling="no" allowfullscreen></iframe>  
*For the poofing/water absorbtion when the Fox touches the water*  



The last animal that was developed with the intention of being used within the main game was the Sheep. This would be an animal that followed the Kibby in its setup but be altered in the execution, as the Sheep was primarily designed around being the central goal of the player in the second level.  
Multiple areas for the Sheep to inhabit existed, with the main one being a group of Sheep as the big set piece of the level: they needed to be guided back to the village. This includes the one that the player returns back to the flock.  
Sheep were designed to be captured in the cage mechanic, to be moved about this way by the player for puzzle solving. Alongside this, the Sheep had a collision sphere placed on it to detect when the Kibby were close to move away from them.  
Nothing much else important to note aside from the model being from a deer, as it was the closest it could be for the project. Steps had been made to try and remedy this as best as possible.  

![Deer](https://github.com/user-attachments/assets/781e76fc-bf70-4545-9045-545ca74693c8)   
*The Sheep's look in game using the clostest model that was available with some adjustments to the materials used*  

<iframe src="https://blueprintue.com/render/0hos9wr7/" scrolling="no" allowfullscreen></iframe>  
*For the Sheep's fear of the Kibby*  

<iframe src="https://blueprintue.com/render/2l9l413q/" scrolling="no" allowfullscreen></iframe>  
*For the capturing of the Sheep*  

![2025-05-2315-22-35-ezgif com-optimize (1)](https://github.com/user-attachments/assets/de398d79-5bb6-404f-8cea-8bb551c811ff)  
*A gif of the sheep moving along a spline to reach the exit in segment2*

Behaviour trees are an integral part of the project, as they've been explained to be previously. I wanted to explain in a bit more detail as to how they were developed for this game.  
They started at a very rudimentary point in the prototype, where they could only execute very basic commands with little leeway. From working on this project they've been expanded with custom decorators and tasks to perform most tasks I need the animals to do. 
Custom decorators are additions that can be added to selector and sequence nodes that I can use to determine if the behaviour tree flow should go this way, an example of this being used in the project is with the Kibby and its relation to fire. The fire gets spotted by the actor, which then is passed through the controller into the blackboard instance to tell the decorator that the fire has been spotted, which then reroutes the tree away from that branch.  


#### Player character  
Players will notice when they start the game that they have a unique set of tools to work with
* They cannot jump
* Collects and places items with matches being the ability to place fire once unlocked  
The player character is the main link between many of the systems in the game that are unrelated to the animals:
* The save system
* UI work
* Inventory
* Unique items
These are all handled inside of the player character due to the player being a constant with one instance to refer back to. It has easy access to the other components to manage connections.  

![Player](https://github.com/user-attachments/assets/f203b20f-6c91-473e-bdc3-ee609a683721)  
*The player model, using a free asset with animations*  


#### Item Mechanics  
Items and components play a big role in the game as they are what the player and animals interact with, listed below are each with a short description of what role they perform:
* Grass block
  * For the Foxling to grab as part of its cycle
  * Respawns within the specific small areas
  * It used to struggle with bouncing in different directions but the axis were restricted to prevent this from occurring in the future  

![Grass](https://github.com/user-attachments/assets/1b8092b8-6b32-4728-abdc-d991c4a838cf)  
*The grass block that respawns once eaten*  


* Fruit
  * Berries are the main fruit the player will see in the game
  * They respawn by their corresponding tree actor when they get destroyed
  * Apples are a subclass that have a longer time to eat than berried, to give players more time with the monster not doing anything
  * The apples remain unused currently  
  
![Berry](https://github.com/user-attachments/assets/e0510c17-0c8e-486a-be72-153cebb47fe1)  
*The Berry fruit item that spawns from any Berry Tree*  

![BerryTree](https://github.com/user-attachments/assets/bbe1cd70-c8f7-4fb6-b393-423298f5ee3e)  
*The Berry Tree that has an internal counter on the number of currently spawned fruits, and doesn't spawn another until a slot is free*  


* Item Basket
  * Obtained after completing the 2nd segment of the 2nd level
  * Gives the player a maximum of 5 berry items to place in front of them
  * Fruit will disappear after a certain amount of time using a delay node within the character
  * When destroyed, it goes back to the player to place again, utilising the OnDestroyed node from the spawned actor.  


* Fire mechanic
  * Obtained after completing the 1st segment of the 2nd level
  * Places in front of the player while playing a sound effect
  * When overlapping a Kibby, it spooks them and sends them moving away from the source  


* Activator
  * An invisible collision box that relies on an enum to get the node pathways it needs
  * Present in level 2 with the purpose of moving the player between segments and setting everything up to align with that movement
  * Prevents the player from being out of the cycle and in the boundaries of the game  
    


* Cage
  * A box with holes in the sides to see through
  * To be called down when the associating buttons have been pressed
  * can be pushed by the player and stepped on top of for puzzle purposes
  * When surrounding a Sheep, it will simulate the physics of the Sheep to allow them to be pushed around  

![ActivatorButtons](https://github.com/user-attachments/assets/c1212400-3ded-44b4-a102-5653ecadee15)  
*A set of buttons that spawn and despawn the cage, also used to count the sheep at the end of level 2*  

* Fences
  * Restricts the player until the prerequisites have been met
  * This typically involves the player figuring out the puzzle of the area
  * Upon completing the puzzle the gate will open  

* Splines
  * Provided specialised movement to the sheep for its own puzzle in shooing the Kibby away
  * The sheep reverses when Kibby come near  
    

#### Levels  
The levels were designed around the ideas and mechanics of the animals that were made:  

* The 1st has a mix of the Fox and the Kibby, I wanted to try and develop an area around each that demonstrated the basic goals and controls of the game. This was done by having a lower area for the player to mess around with the Fox, before moving to higher ground and moving the Kibby with food. It is simple and showcases the intent of the animals before pushing the player into the action.
* The 2nd level is designed around the Sheep being this creature you have to work around to be able to bring it back to the main area and finish the game. As such, the level is split into 3 segments that explore different mechanics such as direct moving and scaring away the Kibby. I thought it was best to divide the areas before combining them for the final push.  


#### Extra Features  
The game features basic saving. Due to time constraints it can only save the player position and whether it can use the fire.  

The user interface was a big factor of this game, as there was an overlay that displayed keybindings, objectives and current usable items. This allows the player to always be in the know as to their current status.    

![MainMenu](https://github.com/user-attachments/assets/dd23bc3c-2e68-4920-8d3e-c53cd090c330)  
![LevelSelect](https://github.com/user-attachments/assets/12b9ceb2-f2b6-44cd-a5af-5152ee5e0c5d)  
![Settings](https://github.com/user-attachments/assets/d6096aff-7aee-4d12-b505-9e0ac05c548b)  
![PauseMenu](https://github.com/user-attachments/assets/934d0747-fbda-481e-8707-ca643b029565)  
*Main menu, Level select, Settings, Pause Menu*  


![UI overlay2](https://github.com/user-attachments/assets/06481b88-e0cd-4c9f-a71a-6b200ba5e355)  
![UIExample](https://github.com/user-attachments/assets/3ce53c75-9bf9-43e2-b9fb-e77b605c2869)  
*The UI overlay changes depending on the players held item/where the are in the game*  

![NotepadUI](https://github.com/user-attachments/assets/43e86d2d-caab-4d6a-956d-a0d920a6b993)  
*NotepadUI that appears in the second level as a way to give information to the player dependant on the level segment*  

#### Polish    
For polish on the game itself, the game uses a post-processing volume with associated materials to apply a cell shaded style with black outlines.  
Free assets fill in the music, sound effects, meshes and animations, with modification to the sound effects by an outside help.  
That same outside help also designed the UI widget sprites that would be used for the overlay.  

![ShaderAndOutline](https://github.com/user-attachments/assets/0d6d9a9f-9738-45ed-ad93-9511d532d5dc)  
*The cel-shaded style with the black outline*  

### New Approach  
New approaches taken to this project include the whole concept behind behaviour trees, as this was a first for me to take on. I took this task towards my AI creatures as it would allow me to truly tackle something new within the realm of UE5 developing, and as a result I've learnt more than I would've had I just researched. This hands-on experience was really useful moving forwards.  



### Testing  
Through numerous testing iterations I have been figuring out what works best for the game. From the most recent testing phase I found out what the rough playtime is for the game alongside how people feel towards it. 


Most people played for around 10 minutes and the responses averaged out to an average playing experience.  

![TestTime](https://github.com/user-attachments/assets/ef7f42f0-61c1-48b7-95eb-7af1412dbca5)  
*The time taken, containing an error as I did not set the time to be the right answer type*  

Thankfully, they gave their thoughts on the game for me to improve upon alongside the current bugs present within that build of the game.  

![TestGraph](https://github.com/user-attachments/assets/98756461-4342-433b-93ad-f6ec8885ebba)  
![TestThoughts](https://github.com/user-attachments/assets/55792014-b5c6-4695-9edb-7bf06afb6380)  
![TestBugs](https://github.com/user-attachments/assets/67de650c-511a-48db-a437-28d19aa43b4f)  
*Graphs of user experience folowed up by their thoughts and helpful bug finding*    

The biggest response talked about the game being unplayable due to the gate locking off the later exits, the issue was found quickly due to how differently the default editor viewport and the build handles certain relationships between actors. This error was quickly fixed to allow the level to become complete.  



### Technical Difficulties   
* Git LFS overusing its data quota, preventing me from accessing the project until it gets 
  fixed
  * This was caused by the file structure and setup of Git LFS being incorrect, this was 
    changed by organising the files and folders in the project into 'Dynamic' and 'Static'. From there the git ignore file was altered to only use LFS on the larger files/one of the folders.
* This created another issue when cloning the project on another device; where some of the 
  blueprint files would not appear within the UE5 editor
  * A solution was to directly place the missing files into their respective locations, 
    gathering the new files from an older commit where they appeared still.
* Behaviour tree logic was not corrisponding to the correct actors
  * This caused seperate instances of the same actor to perform tasks they weren't meant  
    to perform. Solved by having the relationships to the AIController looked at closer  

## Outcomes  

### Source Code/Project Files  
https://github.com/BunEvie04/Hangry-Animals  

This is the repository of the project, inlcuding all source files and a readME.  


### Build Link  
https://bunevie.itch.io/hangry-animals  



### Video Demonstration  
https://www.youtube.com/watch?v=-aIkyifli6I  
<iframe width="560" height="315" src="https://www.youtube.com/embed/-aIkyifli6I?si=x5N2pnzpJFu4MgZS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>  

## Reflection  

### Research Effectiveness    
Research provided essential information that could be used in the project itself, finding the balance between the visual and gameplay of the animals was a line that was crossed, as the animals moved into the gameplay side with flourishes for the visual behavioural side.

Other areas of research also helped in the idea generation side, such as the idea of the pushing cages and the notebook to study the behaviours, coming as an offshoot of the ideas present in Monster Hunter World (Capcom 2016)


### Positive Analysis  
Positives of working on this project are the new ideas that come forward as I have a newfound understanding of how to utilise AI behaviour trees in Unreal Engine. The more practice and experience I get, the more confident I feel towards larger scale projects in the future.


### Negative Analysis   
What I found to be the bad sides of my project was how everything interconnected. I felt that everything could get tangled really easily and that didn't make the repairs simple. A lot of the time spent on this project was working on fixing the connections and casts to different actors/components. This would be remedied in the future by ensuring that there is a dedicated way to connect multiple entities while keeping the blueprints tidy.



### Next Time  
Next time I would account for the time taken for the repairs and fixes a lot better. Especially now that I know a lot more about how behaviour tree tasks and actors work, most of the pitfalls should be avoidable on future versions of projects with similar premises. Perhaps I could have a universal entity to manage links between actors and perform actions, or just any more experimentation to expand my knowledge on the subject. But overall, this project was a wonderful experience experimenting with AI animals.


## Bibliography   
> - Compile a complete list of all sources referenced throughout your project. This may include articles, journals, videos, games, software, documentation, or any other materials.
> - Ensure all references are formatted according to the [university's citation method](https://mylibrary.uca.ac.uk/referencing).  
> - Organise your references in alphabetical order. Alternatively, you may separate them by type (e.g., academic sources, games, videos), but consistency is key.

Alireza, U. A. W. (2022) Unreal Engine 5 Beginner tutorial - How to make things rotate and move using blueprints. At: https://www.youtube.com/watch?v=9JOstDKNHJg&t=120s

ANIMAL VARIETY PACK (s.d.) At: https://www.fab.com/listings/2dd7964c-a601-4264-a53d-465dcae1644c

Capcom (2018) Monster Hunter World. (s.l.): (s.n.).

Cat Animation Pack (s.d.) At: https://www.fab.com/sellers/MotionDezire

Games, E. (s.d.) Behavior Tree Quick Start Guide. At: https://dev.epicgames.com/documentation/en-us/unreal-engine/behavior-tree-in-unreal-engine---quick-start-guide (Accessed  05/12/2024).

Jański, K. (2016) 'Towards a Catagorisation of Animals in Video Games' In: Homo Ludens At: https://www.ptbg.org.pl/wp-content/uploads/2020/05/Krzysztof-JAŃSKI-Towards-a-Categorisation-of-Animals-in-Video-Games.pdf

Lowpoly Toon Characters (Free Demo + Animations) (s.d.) At: https://www.fab.com/listings/a8b4f49d-acd2-495e-b831-de27ff7c89ae 

Nintendo (2005) Nintendogs. (s.l.): (s.n.).

Nintendo (2014) Captain Toad: Treasure Tracker. (s.l.): (s.n.).

Royalty Free Music (s.d.) At: https://incompetech.com/music/royalty-free/index.html?isrc=USUAN1700075&Search=Search 

Studios, E. (2024) How to Create a Outline Shader in UE5. At: https://www.youtube.com/watch?v=deUc7FnGvQo

Tyler, T. (2022) Game: Animals, video games, and humanity. Minneapolis, MN: University of Minnesota Press

Unreal University (2023) How To Make An Options Menu - Unreal Engine 5 Tutorial. At: https://www.youtube.com/watch?v=Ff67XtqgSxc






## Declared Assets  
> - Provide a detailed list of any third-party assets used in the project.  
> - This includes asset packs, music, sound effects, 3D models, textures, scripts, or code from external sources.  
> - Declare any use of AI tools (e.g., ChatGPT, GitHub Copilot, Meshy) or pre-existing code. Specify the purpose of these assets/tools and how they were integrated into your work.  
> - Ensure you clearly distinguish between your original work and any external contributions to maintain academic integrity.

Cryshlie's 2D assets
* 2D images used for the logo and for the UI overlay

Animal Variety Pack
* Meshes, textures and animations used for the Fox and the Sheep animals
  * Fox and Deer of each

Cat Animation Pack
* Meshes, textures and animations used for the Kibby in game

Lowpoly Toon Characters (Free Demo + Animations)
* Meshes, textures and animations used for the player character
  * Just a basic character so the unreal default is not used

Level Music
Long Stroll - Kevin MacLeod (incompetech.com)
Deuces - Kevin MacLeod (incompetech.com)
Airport Lounge Kevin MacLeod (incompetech.com)
George Street Shuffle Kevin MacLeod (incompetech.com)
Shades of Spring Kevin MacLeod (incompetech.com)
* Used for the menus and for the level music

Sound effects
https://drive.google.com/file/d/1zLpu9vscsQWiEhEZzl0tKs5ZbuElYD_D/view?usp=sharing
* This is the google drive folder containing all of the sound effects used within the game
* Contained is the sfx for the Kibby, Foxling, Sheepy, buttons, item placements, fire, and eating sound effects


Starter Content
* Most of the environment and textures

Chat GPT was used for assistance with the cell shading post processing blueprints.
