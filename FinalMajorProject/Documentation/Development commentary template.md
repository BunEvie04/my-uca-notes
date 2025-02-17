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

## Implementation

#### Process
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

#### Ideas:
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



#### Key Points
This section focuses on the important parts that will be added into the main game, through feedback or other research, and will help build stronger foundations

##### Free Assets
 
Key in making everything look more polished without taking the important time away from development. If time permits then I can go back and create key assets for an extra flair.

##### Pathfinding

Research into pathfinding will be needed as the animal in the prototype moved only in a straight line, and pathfinding will allow better gameplay and prevent anything from getting stuck.

##### Better Hitboxes

Working on a better hitbox on the animal would be great as it would previously push the player on its way to its destination, this would partially fix the issue. However a fix on the stepping mechanic would be needed as its currently connected to the animal itself.

##### C++ Conversion

If time permits and I should feel inclined, working on swapping some bp out for c++ would work, as it improves my knowledge on the subject and increases performance.

##### Styling and Level Design

The current plan is to focus on an isometric style of game which will be easier to view and allows for simpler level design, as slopes, plains and pits will be enough for a first level. 

Development of the first level will become crucial for the first few weeks as it allows the game to become testable as a baseline for the true game. The level should be simple with the pickup and place grass mechanic from the prototype present. Other simpler mechanics can be added to improve the lack of gameplay that was in the prototype.

#### Roadmap

This section will focus on the plan of events that should line up with the trello board 
https://trello.com/b/aw9D4OtI/fmp-animal-game

* Build the first level geometry using simple shapes
* Add in basic pathfinding to replace ai movement
* 

#### wk1 
##### 6/2

Started research into pathfinding using the epic tutorial on the basic work

Starting with the blockout for hte work

##### 7/2
* Found out using navmodifier volume with object avioudance works to prevent the animal from taking certain paths, this may work for now but another solution may need to be found later in development that uses less processing power
* Figuring out how to address the pit shenanigans in the main game

The map will be based on a hill setting, with a basic introductory puzzle using the mechanic introduced in the prototype.
After that will be another mechanic with an item that will distract an animal for a time, allowing the player to get past for more puzzle ideas


##### 8/2

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

##### New Approaches  
> - Detail any innovative or new approaches you explored during the project.  
> - Explain why these approaches were chosen and how they differ from standard practices.  
> - Evaluate the success of these approaches, including any challenges faced and lessons learned.

##### Testing
> - Document the user testing conducted, specifying the type of tests used (e.g., automated testing, guided user testing, blind testing).  
> - Present feedback or issues identified during testing, using graphs, tables, or visual aids to summarise results.  
> - Describe how these issues were addressed. If any issues were not resolved, provide a clear justification for leaving them unaddressed.

##### Technical Difficulties
> - Identify any technical difficulties encountered during the implementation phase.  
> - Provide details on how these issues were diagnosed and resolved.  
> - If any difficulties remain unresolved, explain the impact on the project and any mitigation strategies used to minimise their effect.  
> - Reflect on what you would do differently in future projects to avoid similar issues.
>> can this be included in the process subtitle??

* Git LFS overusing its data quota, preventing me from accessing the project until it gets fixed


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
