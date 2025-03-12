# Development Commentary Template

```
Key Requirements
Project Commentary of 3,500 words (LO1 & LO2)
Provide a project commentary detailing the process of developing the project. The project commentary is a piece of technical and academic writing.

Project Outcome (LO3)
Provide a build of your project (e.g., .exe, .apk) that can be run on a local machine if appropriate. The build should be made available via itch.io. Ensure the build includes all necessary files and instructions for execution.

In some situations a video demonstration alone or website link maybe applicable. You must consult with your supervisor to ensure you meet the criteria for your chosen project.

Source Code (LO3)
Provide a online repository containing all source code for the developed project. the version provided must be inline with the project outcome.

Project Schedule (LO4)
Provide a up to date schedule of works using an software package that utilises an industry standard methodology such as agile, kanban, waterfall, RAD, etc.

[Requirement 4] ([Associated Learning Outcomes])
```

## Project Outline
> - Provide a concise description of the project, including its core concept and purpose.  
> - Outline the initial goals or objectives you aim to achieve.  
> - Identify any anticipated challenges or potential issues that may arise during development.

This is a project that uses behaviour trees alongside alternative mechanics that creates a simple puzzle game with a primary focus on exploiting animal creature behaviours in order for the player to reach the destination.

The desired result is for at least a set of levels that showcase and develop the mechanics built up previously. The player would hope to learn the mechanics behind the animals alongside how items affect them in their routines.

Some difficulties that I may have with this project can be found within the design elements around the stages, as most of my ideas are around the mechanics themselves with the level design coming into play to fit in with the features. Alongside this I worry on if I will have enough time to fully flesh out the animals to a standard I would be perfectly happy with, as I want as much as possible to be perfect which cuts into the time left of the project. This, however, I will have to work on with methods such as trello boards and timelines to keep myself on track.


## Research

### Methodology  
> - Identify relevant sources for the project, including articles, documentation, talks, and games.  
> - Detail how these sources have informed your practical work and influenced your approach.

* Trello boards are used with the agile working methodology to boost the working efficiency of the project. As a solo developer it is key to not lose track of how the project is developing, so making use of short sprints with the trello boards keeping track of what has been done/needs doing is key to making sure everything is progressing smoothly. 

### Game Sources  
> - Conduct research on games that are relevant to your project. Provide a brief description of each game and the insights it offers.  
> - Analyse the game's approach, cross-referencing it with other sources such as articles or talks to support your analysis.  
> - Explain how these insights apply to your project and influence your decision-making process.

* Monster Hunter World (Capcom 2018)
  * This game became an inspiration with how the monsters behave in the environment with and without the players influence
  * It allows the environment to be interactable with many options for the player to exploit monsters

### Academic Sources  
> - Research academic papers, books, or articles that provide theoretical guidance for your project. Include a brief summary of each source.  
> - Describe how the academic research applies to your project and shapes your design and development decisions.

* Refer back to written essay with taken notes and important reflections on the topic of animal behaviours in video games
* Academic sources and pages can be found there, will be relinked and talked about in brief

### Documentation Sources  
> - Investigate relevant documentation, tutorials, or instructional videos that provide technical insights into your tasks. Summarise the content and its relevance to your project.  
> - Explain how this technical knowledge supports your project work and guides your decision-making process.

https://www.youtube.com/watch?v=9JOstDKNHJg&t=120s
https://www.youtube.com/watch?v=Ff67XtqgSxc

## Implementation

### Process
> - Provide a step-by-step breakdown of your development process, including key milestones and decisions made throughout the project.  
> - Highlight any tools, frameworks, or techniques used, and explain how they contributed to the implementation.  
> - Include screenshots, diagrams, or code snippets where relevant to showcase your progress.

#### Feedback

```
I would have expected a little more features for a prototype. While everything is functional, it is quiet bare bones.
```
```
There some tasks where it was lacking research, when tackling any problem, its important to research and understand the problem you are trying to solve.
```

#### Improvements
Based on the feedback given on the prototype project and its development journal, it is clear that the final project needs to have more research put into each mechanic alongside haveing more substance insirted for the players enjoyment.

#### Idea Generation:
> This section will focus on the ideas that will be added into the game, with new ideas being expanded upon within their relevant sections


Using the prototype, compare to similar games and research mechanics that could fit into the game, ensuring that the main idea of a puzzle game primarily utilizing the animal behaviour remains intact.
* Monster hunter
  * Monsters are used for combat, which there will be no combat present in the game
  * Interactions with items still occur however that influence the behaviour:
    * Torch pods create fire on the ground where they land that monsters shy away from
    * Other ammo when fired lure monsters to areas
    * Drugged meat can be placed that inflicts status effects including drowsiness, paralysis and poison
    * Environmental objects can be triggered to hide the player/interup the monster
* Captain Toad
  * Enemies block off areas which the player has to maneuver around/kill to progress

As well as that, looking at examples of interactions with animals irl can give insight into mechanics
* Some animals hunt and harm other beings due to needing to eat
* Being threatened can cause violent retaliation in animals
  * (Lethal Company) Baboon Hawks maintain distance constantly with the player(s) 
and attack dependant on if the player remains close for too long/holding weapons/more people
* Feeling threatened can also cause other animals to flee instead

From this I can create new mechanic ideas that have potential to fit into the game:
* Different creatures with some behaviours that are unique and some shared
* Hidden meters for features like being threatened by other entities/player
* Utilisation of fire can be used to scare animals/coherce them into/away from locations
* Moving around/avoiding certain animals to reach locations
  * Animal could be hostile(?) and player needs to avoid being caught
  * Animal might be a passive roadblock
* Other item types besides grass that create different outcomes with the environment
  * Meat only lures carnivorous animals for example

* Natural item that player has to pick up, takes animals some time to eat
 * Can ask player to collect item from area
 * Player places for animal to eat in location, can be then used as platform


#### Assets
 
Key in making everything look more polished without taking the important time away from development. If time permits then I can go back and create key assets for an extra flair.

https://www.fab.com/listings/e883b476-660a-43f3-99e8-11cfddb5cfa4 - Cat asset


#### Research points
##### Pathfinding

Research into pathfinding will be needed as the animal in the prototype moved only in a straight line, and pathfinding will allow better gameplay and prevent anything from getting stuck.

##### Better Hitboxes

Working on a better hitbox on the animal would be great as it would previously push the player on its way to its destination, this would partially fix the issue. However a fix on the stepping mechanic would be needed as its currently connected to the animal itself.

##### C++ Conversion

If felt appropriate, working on swapping some bp out for c++ would work, as it improves my knowledge on the subject and increases performance.

#### Styling and Level Design

The current plan is to focus on an isometric style of game which will be easier to view and allows for simpler level design, as slopes, plains and pits will be enough for a first level. 

Development of the first level will become crucial for the first few weeks as it allows the game to become testable as a baseline for the true game. The level should be simple with the pickup and place grass mechanic from the prototype present. Other simpler mechanics can be added to improve the lack of gameplay that was in the prototype.

#### Timeline of Events

This section will focus on the plan of events that should line up with the trello board 
https://trello.com/b/aw9D4OtI/fmp-animal-game

* Build the first level geometry using simple shapes
* Add in basic pathfinding to replace ai movement
 
>6/2


Started research into pathfinding using the epic tutorial on the basic work

Starting with the blockout for the work

>7/2
* Found out using navmodifier volume with object avioudance works to prevent the animal from taking certain paths, this may work for now but another solution may need to be found later in development that uses less processing power
* Figuring out how to address the pit shenanigans in the main game

The map will be based on a hill setting, with a basic introductory puzzle using the mechanic introduced in the prototype.
After that will be another mechanic with an item that will distract an animal for a time, allowing the player to get past for more puzzle ideas



>8/2

3 first level mechanics
* Direct grass movement
 * Prototype mechanic
 * Reserved for the first animal
* Fire avoidance
 * Placeable for most animals
 * Fire close by moves animals away from area
* Big food
 * Stops to eat
 * Looks for more before idling

Making the pit fall more consistent with a collision box that makes a platform when the animal collides with it in the pit. This is done by making the collision of the new box change when it collides with the animal, so it then prevents the player from falling through.

Next steps would be to add the encyclopedia to the game to explain the mechanic of an animal once the player is in sight of one.

>21/2

Everything was fixed with gitlfs so now work into the new systems can begin
anymal has been made, being a cat model stand-in. 
Up next is editing ui to be multipage with inventory built into the first one.
adding more behaviours for second animal to align with fruit


>22/2

Third person character can now pick up multiple items one at a time, working towards multiple later if needed but allows different items to be used within the level. When same time item pickup is needed an inventory will be added to the book as its first page.


>Week of the 24th (week3???)

This week focused on some visual features including the UI for menus, changing user settings, basic saving, and building the level mechanics for the first stage.

The help menu from the prototype was repurposed into the pause menu, which contained useful buttons like:
* Resume
  * Un-pauses the game
* Save
  * Saves the variables related to the current game state in its own spot
  * Currently only saves the player position for now
* Restart from Point
  * Returns all variables saved in savegame back into the game
* Restart Level
  * Restarts the level from scratch
  * Currently incompatible with savegame
* Title Screen
  * Returns the player to the title screen
* Quit Game
  * Closes the game
* Settings
  * Opens the settings menu

(Screenshot here)


Alongside the pause screen, a settings menu was added to allow the player to customise their experience to match their system and preferences. There are working drop-down boxes that display and select the players desired window and resolution combined with sliders for audio management on music and sound effects. Currently the graphical settings work as intended but without any audio added into the project I cannot be too sure if the audio sliders are fully functioning.

(Gifs of combobox and sliders)


The cat (a stand-in name for the second ai animal) was further developed in its behaviour. It is similar to the prototype in how it patrols and moves towards food but differs in how it goes about each task. As a second attempt on the behaviour tree it became more streamlined and readable so more events could be added if needed.  
A pawnsensing component has been added, which means the cat will roam until it sees the necessary item within its eyesight. Once this occurs it will change behaviour to move towards it and stay there (mimicking eating). This is planned to be the ai base that will be the source of most of the puzzles in future levels.


This first level being blocked out will be made to showcase the very basic mechanic of placing items and working with the animals. Split into two very short sections, the first utilises the prototype animal due to its simple nature in the pit falling mechanic seen previously in the prototype. The second area will contain a larger space with trees to spawn food items the player can use to lure the cat out of the goal area.

Reference for future efforts:
* Addition of spawners working and dropping fruit
* Working behaviour trees to activate when needed

>To be dated but other additions/workflow
>>Week 4
* Title menu
  * The title menu was updated slightly to have options for: a new game, load game, settings menu, exit button, and the option for the prototype
* Apple mechanics
  * The basic apple is similar to the grass block from the prototype but is planned to be able to be spawned in by a tree actor, alongside growing when spawned and shrinking when being eaten
  * This week was spent on getting the apple to detect when the cat is nearby alongside the destruction events for it.
* More map detail

>>Week5

* Spawning functions for apples
  * The next step for the apples would be to add the tree actor itself with an event to spawn the apples at a selected amount. This could be simply done through a spawn actor node but for the purposes of what I required, it was not the most efficient solution.
  * My first thoughts was to create an actor component that could be attached to the tree actors. Functions were added to get an array of the number of trees present in the level, alongside another to get each a location offset for where to spawn the apples. A great deal of time was spent on this, including the development and research into structs to try and get this process to work, as each tree that was in the level would have a maximum of (at the time) two apples that would spawn nearby. 
  * That plan proved futile as I had discovered that using a linked custom event connected to the spawn actor within the tree actor blueprint automatically attaches the two together, allowing each trees counter to decrease independantly when its own apple is removed from play.

* Missteps with ActorComponent, Functions and Structs
* The right answer

>>Week6

* Spawner function for inventory work


* Future in the week:
  * Object pool
    * Integer for the amount of apples currently in the level, with the eating of the apple increasing the value and the lowering of it for spawning it
    * Picking the item up would be neutral as it would add one before removing one, and vice versa for dropping it.
    * Testing will need to be done to check this would work properly
  * Proper level finishes
    * Finishing the level design and implementing developed mechanics
    * Creating a build that can be user tested.
  * Bug fixes
    * Animal destroys the object from a distance



### New Approaches  
> - Detail any innovative or new approaches you explored during the project.  
> - Explain why these approaches were chosen and how they differ from standard practices.  
> - Evaluate the success of these approaches, including any challenges faced and lessons learned.

### Testing
> - Document the user testing conducted, specifying the type of tests used (e.g., automated testing, guided user testing, blind testing).  
> - Present feedback or issues identified during testing, using graphs, tables, or visual aids to summarise results.  
> - Describe how these issues were addressed. If any issues were not resolved, provide a clear justification for leaving them unaddressed.

### Technical Difficulties
> - Identify any technical difficulties encountered during the implementation phase.  
> - Provide details on how these issues were diagnosed and resolved.  
> - If any difficulties remain unresolved, explain the impact on the project and any mitigation strategies used to minimise their effect.  
> - Reflect on what you would do differently in future projects to avoid similar issues.
>> can this be included in the process subtitle??

* Git LFS overusing its data quota, preventing me from accessing the project until it gets fixed
  * This was caused by the file structure and setup of Git LFS being incorrect, this was changed by organising the files and folders in the project into 'Dynamic' and 'Static'. From there the git ignore file was altered to only use LFS on the larger files/one of the folders.
* This created another issue when cloning the project on another device; where some of the blueprint files would not appear within the UE5 editor
  * A solution was to directly place the missing files into their respective locations, gathering the new files from an older commit where they appeared still.


## Outcomes

### Source Code/Project Files
> - Provide a link to your complete source code or project files.  
> - Ensure the link is publicly accessible or shared with the appropriate permissions.  
> - Include a brief description of the files provided, highlighting key components or any instructions required to run the project.

### Build Link
> - Share a link to a playable or executable build of your project.  
> - Ensure the build is accessible across relevant platforms and is publicly accessible.  
> - Include any necessary instructions for running the build, such as system requirements or installation steps.

### Video Demonstration
> - Embed a video or provide a link to a recorded demonstration of your project in action.  
> - The video should showcase key features, functionality, and any unique elements of your project.  
> - Include a brief commentary or text overlay in the video to explain the different aspects of your project as they are shown.

## Reflection

### Research Effectiveness  
> - Assess the usefulness of the research conducted during the project.  
> - Highlight which sources (games, academic, documentation) had the most significant impact on your work and explain why.  
> - Identify any research gaps or areas where additional information could have improved your project outcomes.

### Positive Analysis 
> - Reflect on the successful aspects of the project.  
> - Highlight specific elements that worked well, such as technical solutions, creative decisions, or user feedback.  
> - Provide evidence to support your analysis, such as test results, screenshots, or user comments.

### Negative Analysis  
> - Identify the areas of the project that did not go as planned or could have been improved.  
> - Discuss challenges you faced, whether technical, creative, or time-related, and evaluate their impact on the final product.  
> - Reflect on any mistakes or missteps and what you learned from them.

* Understanding more about how Github works with Git LFS
  * Portions of the working timeline have been cut due to having an inaccessable project
* Working with item management for puzzles
  * Linking each instance of a spawning actor with a set amount of sub actors (tree instances spawning a set amount of apples each)

### Next Time
> - Outline what you would do differently if you were to undertake a similar project again.  
> - Suggest improvements to your workflow, research methods, or implementation process based on your reflections.  
> - Consider any new tools, techniques, or approaches you would explore in future projects to achieve better results.

## Bibliography  
> - Compile a complete list of all sources referenced throughout your project. This may include articles, journals, videos, games, software, documentation, or any other materials.
> - Ensure all references are formatted according to the [university's citation method](https://mylibrary.uca.ac.uk/referencing).  
> - Organise your references in alphabetical order. Alternatively, you may separate them by type (e.g., academic sources, games, videos), but consistency is key.

To be updated properly later:
* Monster Hunter World
 * Capcom 2018
* Captain Toad

## Declared Assets
> - Provide a detailed list of any third-party assets used in the project.  
> - This includes asset packs, music, sound effects, 3D models, textures, scripts, or code from external sources.  
> - Declare any use of AI tools (e.g., ChatGPT, GitHub Copilot, Meshy) or pre-existing code. Specify the purpose of these assets/tools and how they were integrated into your work.  
> - Ensure you clearly distinguish between your original work and any external contributions to maintain academic integrity.

* Animal Variety Pack






# Next steps for the dev commentary
* Inclusion of images, gifs and videos
* Fill in research sections
* User testing
