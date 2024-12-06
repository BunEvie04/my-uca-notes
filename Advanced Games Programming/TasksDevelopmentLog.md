# Development Log
## Task 1 - Inventory Sorting System

### Research 

To start with the task, it is important to know what sorting method isand how to implement it into the project. This website was used for this purpose as it broke them down with examples to make it clearer.

https://www.simplilearn.com/tutorials/cpp-tutorial/sorting-in-cpp#:~:text=Examples%20of%20internal%20sorting%20are,sorting%20is%20the%20Merge%20sort.


The video below was used as a reference when considering alternate methods for the sorting method within this task

<iframe width="560" height="315" src="https://www.youtube.com/embed/x0uUKWJzSO4?si=HVr-AaPAjHRnAq2A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>



### Inventory sorting
This task gives a list of items along with a starting point for me to convert into an ordered list. The original items are below contained within the main()
```cpp
std::vector<Item> items = {
        Item("Sword", 150),
        Item("Potion", 50),
        Item("Shield", 100),
        Item("Bow", 120),
        Item("Helmet", 80)
    };
```
The list is defined in the public
``` cpp
public:
    std::string name;
    int value;

    Item(std::string n, int v) : name(n), value(v) {}
};
```

This is completed through a bubble sort. By defining the integers n (for the size of the list), i, and j, the loops can filter out the placements for each item in the array.
``` cpp
    //defines n as the number of items within the list
    int n = items.size();
    if (ascending)
    {
        //loops until the end of the list has been reached
        for(int i = 0; i < n; i++)
        {
            //places the list items
            for (int j = 0; j < n - i - 1; j++)
            {
                //compares the adjacent items
                if (items[j].name > items[j + 1].name) std::swap(items[j], items[j + 1]);
            }
        }
    }
```
### Alternative methods
Alternative methods may include using the ***sort*** function to automatically list them in order using the given parameters. This also shows the next step of sorting by the values of the items in the list, which use int v. For this, I changed the parts containing *name* and replaced it with *value*.

``` cpp
std::sort(items.begin(), items.end(), [](const Item& a, 
const Item& b)
{
    return a.name < b.name;    
});
```
``` cpp
Sorted by Value (Descending):
Sword: 150
Bow: 120
Shield: 100
Helmet: 80
Potion: 50
```

By changing the outputs from true to false and by reversing the greater than into less than within the "else" part of the functions, it is possible to see the opposites of each list, allowing the user to see more sorting methods for the systems.
``` cpp
        //Descending
        for (int i = 0; i < n; i++)
        {
            //places the list items
            for (int j = 0; j < n - i - 1; j++)
            {
                //compares the adjacent items
                if (items[j].name < items[j + 1].name) std::swap(items[j], items[j + 1]);
            }
        }
    
```

### Next steps
For the next stage I wanted the user to be able to select what they want the order to be, as currently it is all displayed in full. This can be done through asking the user to select between the names and value, and then between ascending and descending. This would filter out the results to get the sorting the player requires.

``` cpp
if (Type == "Name"||Type == "name")
{
        if (Sort == "Ascending"||Sort == "ascending")
        {
                std::cout << "\nSorted by Name (Ascending):" << std::endl;
                SortByName(items, true); // Sort by name in ascending order
                DisplayInventory(items);
        }
        else
        {
                std::cout << "\nSorted by Name (Descending):" << std::endl;
                SortByName(items, false); // Sort by name in ascending order
                DisplayInventory(items);
        }
}
else
{
        if (Sort == "Ascending"||Sort == "ascending")
        {
                std::cout << "\nSorted by Value (Ascending):" << std::endl;
                SortByValue(items, false); // Sort by value in descending order
                DisplayInventory(items);
        }
        else
        {
                std::cout << "\nSorted by Value (Descending):" << std::endl;
                SortByValue(items, true); // Sort by value in descending order
                DisplayInventory(items);
        };
};
```
```
Would you like the sort to be on names, or on values?
value
Ascending or Descending order?
descending

Sorted by Value (Descending):
Sword: 150
Bow: 120
Shield: 100
Helmet: 80
Potion: 50
continue?(y/n)
```

### Bibliography

Ravikiran, A. S. (2021) What is sorting in C++: Bubble Sort, Insertion Sort & more. At: https://www.simplilearn.com/tutorials/cpp-tutorial/sorting-in-cpp (Accessed  05/12/2024).

The Cherno (s.d.) Sorting in C++. At: https://youtu.be/x0uUKWJzSO4?si=G2y8Capf5eodJ5QN (Accessed  05/12/2024).

### Full Code
``` cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>

class Item
{
public:
    std::string name;
    int value;

    Item(std::string n, int v) : name(n), value(v) {}
    
};

// Function to display the inventory
void DisplayInventory(const std::vector<Item>& items)
{
    for (const auto& item : items)
    {
        std::cout << item.name << ": " << item.value << std::endl;
    }
}

// Function to sort items by name (alphabetically)
void SortByName(std::vector<Item>& items, bool ascending = true)
{
    //defines n as the number of items within the list
    int n = items.size();
    if (ascending)
    {
        //loops until the end of the list has been reached
        for (int i = 0; i < n; i++)
        {
            //places the list items
            for (int j = 0; j < n - i - 1; j++)
            {
                //compares the adjacent items
                if (items[j].name > items[j + 1].name) std::swap(items[j], items[j + 1]);
            }
        }
    }

    else
    {
        //Descending
        for (int i = 0; i < n; i++)
        {
            //places the list items
            for (int j = 0; j < n - i - 1; j++)
            {
                //compares the adjacent items
                if (items[j].name < items[j + 1].name) std::swap(items[j], items[j + 1]);
            }
        }
    }


    //sort function automatically fits the list items using the given type
    /*std::sort(items.begin(), items.end(), [](const Item& a, const Item& b)
    {
        return a.name < b.name;
    });
    */
}

// Function to sort items by value (ascending/descending)
void SortByValue(std::vector<Item>& items, bool ascending = true)
{
    if (ascending)
    {
        std::sort(items.begin(), items.end(), [](const Item& a, const Item& b)
        {
            return a.value > b.value;
        });
    }
    
    else
    {
        std::sort(items.begin(), items.end(), [](const Item& a, const Item& b)
        {
            return a.value < b.value;
        });
    }

}

int main()
{

    char* pcontinue = new char;
    *pcontinue = 'y';

    for (; *pcontinue == 'y';) {


        std::vector<Item> items = {
            Item("Sword", 150),
            Item("Potion", 50),
            Item("Shield", 100),
            Item("Bow", 120),
            Item("Helmet", 80)
        };

        std::cout << "Original Inventory:" << std::endl;
        DisplayInventory(items);

        if (Type == "Name"||Type == "name")
        {
            if (Sort == "Ascending"||Sort == "ascending")
            {
                std::cout << "\nSorted by Name (Ascending):" << std::endl;
                SortByName(items, true); // Sort by name in ascending order
                DisplayInventory(items);
            }
            else
            {
                std::cout << "\nSorted by Name (Descending):" << std::endl;
                SortByName(items, false); // Sort by name in ascending order
                DisplayInventory(items);
            }
        }
        else
        {
            if (Sort == "Ascending"||Sort == "ascending")
            {
                std::cout << "\nSorted by Value (Ascending):" << std::endl;
                SortByValue(items, false); // Sort by value in descending order
                DisplayInventory(items);
            }
            else
            {
                std::cout << "\nSorted by Value (Descending):" << std::endl;
                SortByValue(items, true); // Sort by value in descending order
                DisplayInventory(items);
            };
        };

        std::string newname;
        int newvalue;

        //Below is unused enter new item code
        /*std::cout << "Enter another item:" << std::endl;
        std::cin >> newname;
        std::cout << "Enter the price" << std::endl;
        std::cin >> newvalue;

        items.push_back(Item(newname, newvalue));

        std::cout << "\nUpdated Items:" << std::endl;
        for (const auto& item : items) {
            std::cout << "Item: " << item.name << ", Value: " << item.value << std::endl;
        }*/
        
        //Attempts at chossing what to sort
        

        std::cout << "continue?(y/n)";
        std::cin >> pcontinue;

    }

    return 0;
}
```


## Week 2 - Educational Game Plan
### Deliverals
For this task it is asked to develop an educational maths game aimed at teaching basic arithmatic, involving addition, subtraction, multiplication and division. The target audience is primary schoolers and the time given by the client is 8 weeks of 8 sprints. This will be worked on by a group of three people with different expertise, these being:
* A general developer on coding and mechanics
* A specialist in dialogue systems and localization
* A specialist in UI/UX design
Based on this it should become simpler do divide the roles to ensure the client gets a fully implemented project within the asked amount of time.

To start off with, its better to establish a proper working plan that will efficiently incorporate each member of the team. Trello will be used as it is an online resource that everyone can access easily, and gives tools tp neatly sort each sprint and the work each member will be required to do. Within I can create the 8 different sprints on each list, with at least one job for each member of the group, alongside this an extra list can be created for all the tasks to be placed on before sorting. This is important to do as it allows me to better sort things since they are all in one place, before they get sorted in terms of impoartance for the project and how possible they would be for the different developers to work on in a given sprint.

### Research
When it comes to the planning, I had a brief look at some examples within the industry on the different types of working methodologies. However, most of the knowledge applied within this I have previously gathered from my computer science btec course. However, it is clear to see that this project will take the form of a scrum-agile working style, as it is made up of set weekly sprints with certain goals to be completed, with standups and constant communication to allow each member to get the help they may need

### Sprint Plans

This section should provide a brief overview of the planned activities across each sprint, each with a small explanation on why it was decided to do each task on this section of development.
Each sprint for this project will be lasting one week, with the group having a stand-up every other week to go over the stages of development that each member is at, to ensure that everyoone can get help if they need it. The website listed below goes into more detail on what this methodology entails.

https://www.atlassian.com/agile/scrum

![Current workings](https://github.com/user-attachments/assets/e83377c7-a747-49af-ae4c-76587461c5b4)


### Sprint 1

For this first sprint it would be wise to get the planning portion out of the way to ensure that each member of the team can decide on their goals within the project. This also allows us to gather important information and generate ideas on different elements, such as the style of the game and the levels of difficulty we aim to reach.  

Alongside this, research into other online maths games would prove useful, as some online maths games remain popular among students of that younger age group. Such websites like Sumdog are highly popular because they use simple mathematics in conjunction with background animations and sounds to simulate a game environment, to use an example.

![Sprint1Image](https://github.com/user-attachments/assets/e70fb34e-8023-44e0-88e3-3b89789fdd11)


### Sprint 2

Sprint 2 should be that start of the development process, as all of the research and pllanning should have been finished within the first week of the project. The basic plan for this stage would be to create the framework of the game, which includes the main logic behind the operations and the starting foundations of the visual design of the game aspects itself. 

For the third developer on the dialogue systems, this sprint will rely on them creating a script for the game. For this week they will focus on the general text being displayed to the player, so it'd have to, like most other things, be accommodated towards the target age.

![Sprint2Image](https://github.com/user-attachments/assets/5cdebf36-7dad-429c-a532-f9a1d5a940b9)


### Sprint 3

The third sprint will just be a continueation of the second, with a meeting at the start of the week to bring everyone up to speed, as a way to tell where everyone is with their respective jobs.

The main goal is to have the core game setup with the operations and have it all be playable, this way the project can be shown off as a full proof of concept. The script should be finished this week as it will be necessary for the next sprint. Over the course of the next couple of weeks, the UI will be developed so that it can be integrated and used with future elements.

![Sprint3Image](https://github.com/user-attachments/assets/f614cf63-235c-4986-b389-baa5e0daa92f)


### Sprint 4

Using the UI developed in the previous sprint, the developers on mechanics and dialogue will be working together on setting up and fleshing out a dialogue system. This will be a joint effort as there may be issues conncting the two areas that would be better worked on with both people simultaneously.

The UI designercan partake in ensuring the dialogue boxes are fit for purpose and work appropriately. Alongside this, the other required UI elements should be fleshed out this sprint so that the user testing (aimed to be the focus of next week) can be performed in its basic capacity.

![Sprint4Image](https://github.com/user-attachments/assets/47729965-2c08-4098-a8c1-5bb8a9960059)


### Sprint 5

As mentioned previously, this week should hopefully be focused on getting a working build ready for users to test and provide feedback. Each week will hopefully provide newer builds with revised builds using the feedback from the user testing.

During this process extra resources will be used on animations, it is still to be decided who would have the most experience with this so it will mainly fall into the UX designers job with everyone else working as extra help.

![Sprint5Image](https://github.com/user-attachments/assets/882526a6-50d3-4071-8f00-7530756fd3d3)


### Sprint 6

This week will be a little bit busier as each member will have a different role. Alongside this, the team will be recieving the first bits of feedback from users on how the testing build is, this would be vital and will need to be implemented in the upcoming sprints.

The progress tracking systems will bee implemented for teachers to be able to monitor a student's results to help teach them if they are falling a bit behind.

Since english was the default language, it will not need to be localized, instead the first decided localized language would be Spanish. As this isn't a large project it should only take less than a week to localise.

The UX designer will be focusing on sound design, as this was deemed not important enough to be in the first couple of testing builds.

![Sprint6Image](https://github.com/user-attachments/assets/c1970a29-ffde-485e-afdc-1dbd5adb9e87)


### Sprint 7

A rewards system mechanic is of least importance in comparison to the other mechanics, so it will be included in the seventh sprint. As such, this is the only inclusion along with the Korean localization that will be added in the final testing build.

![Sprint7Image](https://github.com/user-attachments/assets/22047d4e-635b-4421-836f-9fbeee5c7335)


### Sprint 8

This sprint is the final sprint with the main focus on tying up all of the loose ends of the project and implementing any important feedback as part of hte final wave of testing. The game should hopefully be at the point of full release at the middway point of the sprint with the latter half pollishing for hte client.

![Sprint8Image](https://github.com/user-attachments/assets/42d53adb-213e-49a3-b2d3-9640913b7424)


## Reflection

This task has been a great deal of insight into what goes into the head of people within the industry when it comes time to plan out a project that utilises sprints. It gives a good hint into what it will be like working as part of a smaller team of developers with different tools and skillsets, as the plans would have to stretch us out in a healthy manner to increase efficiency and avoid burnout. Trello was a wonderful tool to work with as it provided a base to plan out each sprint with cards that could be moved with ease in case a task could not be completed or had to be pushed to an earlier/later point within the development process.

## Bibliography

Atlassian (s.d.) What is scrum and how to get started. At: https://www.atlassian.com/agile/scrum (Accessed  06/12/2024).


## Task 3 - Health potion tasks
### Research
For this pair-programming task, we split the research up between us. Most of the research was spend on lists and how to push and pull items from a list. Alongside that, we found it vital to add a small bit of flow-charting to figure out how to get the sorting and healing.

https://www.w3schools.com/cpp/cpp_list.asp


### Workings
This project was worked on using pair-programming, so I had a partner helping me with the research and finding the solution to this task.

We broke down the problem and likened it to other computational problems, where you use coins to get to a certain amount. 
We deduced that it would start with the potion with the highest volume and then use as many as it could before the amount left was less than that, and then go to the next smallest.
We realised that the potions were stored in a vector struct. 
As we were not completely familiar with vectors in C++, we wanted to look at the documentation.

Created a while loop to add potion health value to the current health
It went on for ever as we had not properly set up the while loop to end,
 
``` cpp
int size = potions.size();
Potion lastIndex = potions[size - 1];
int lowestHeal = lastIndex.healingValue;
            
            
            while (player.currentHealth <= player.maxHealth - lowestHeal)
            {
                std::cout << healthNeeded << std::endl;
                while (healthNeeded >= potions[potionindex].healingValue)
                {
                    totalPotions++;
                    healthNeeded = healthNeeded - potions[potionindex].healingValue;
                    player.currentHealth = player.currentHealth + potions[potionindex].healingValue;
                    
                }
                potionindex++;
             }
```
Unfortunately if the answer gets to more than 90 (less than the 10 potion amount) it would get stuck.
We then instead calculated the lowest healing potion ( making it so its scalable for any types of potions.
Used that to make the while loop to go down to until there were no potions left to get it to exactly 100.
Then output the amount of health if it didn’t go to 100.

This worked, and the end result outputs until no more potions can be used, outputting the result, an example of this being the Rogue and Cleric, who would be left on 95 health due to potions only healing as low as 10 health.
```
Healing Cleric: Current Health = 85, Max Health = 100
15
15
15
Total number of potions for Cleric is 1
Not enough potions to fully heal Cleric!
Current health is: 95
```
Compared to the other two that heal to the solid 100. As a result of this, however, it was decided to add text to inform the player in both cases
```
Healing Knight: Current Health = 70, Max Health = 100
30
30
10
Total number of potions for Knight is 2
Knight is fully healed!
```

### Reflection
As this was my first time truly working with someone in pair-programming, I got to experience another part that is seen within the industry. Alongside this, the project explained how to use lists to order items and how to add and remove objects from them, which can come in use within my projects in the future.



### Bibliography

C++ list (s.d.) At: https://www.w3schools.com/cpp/cpp_list.asp (Accessed  06/12/2024).


### Full Code
``` cpp
#include <iostream>
#include <vector>
#include <algorithm>

class Potion
{
public:
    std::string name;
    int healingValue;

    Potion(std::string n, int h) : name(n), healingValue(h) {}
};

class Player
{
public:
    std::string name;
    int currentHealth;
    int maxHealth;

    Player(std::string n, int current, int max) : name(n), currentHealth(current), maxHealth(max) {}
};

class HealthPotionSystem
{
public:
    std::vector<Potion> potions;

    HealthPotionSystem()
    {
        // Adding multiple potions
        potions.push_back(Potion("Small Potion", 10));
        potions.push_back(Potion("Medium Potion", 20));
        potions.push_back(Potion("Large Potion", 50));
    }

    // Method to determine the optimal potions to consume for each player
    void HealPlayers(std::vector<Player>& players)
    {
        for (auto& player : players)
        {
            int totalPotions = 0;
            int potionindex = 0;
            int healthNeeded = player.maxHealth - player.currentHealth;
            if (healthNeeded <= 0)
            
            {
                std::cout << player.name << " is already at max health!" << std::endl;
                continue;
            }

            // Sort potions by their healing value in descending order
            std::sort(potions.begin(), potions.end(), [](const Potion& p1, const Potion& p2) {
                return p1.healingValue > p2.healingValue;
            });

            std::cout << "Healing " << player.name << ": Current Health = " << player.currentHealth << ", Max Health = " << player.maxHealth << std::endl;

            // Implement your solution here to consume potions optimally based on healthNeeded for each player
            int size = potions.size();
            Potion lastIndex = potions[size - 1];
            int lowestHeal = lastIndex.healingValue;
            
            
            while (player.currentHealth <= player.maxHealth - lowestHeal)
            {
                std::cout << healthNeeded << std::endl;
                while (healthNeeded >= potions[potionindex].healingValue)
                {
                    totalPotions++;
                    healthNeeded = healthNeeded - potions[potionindex].healingValue;
                    player.currentHealth = player.currentHealth + potions[potionindex].healingValue;
                    
                }
                potionindex++;
                

                
            }
            
            std::cout << "Total number of potions for " << player.name << " is " << totalPotions << std::endl;
            
            

            if (player.currentHealth < player.maxHealth)
            {
                std::cout << "Not enough potions to fully heal " << player.name << "!" << std::endl;
                std::cout << "Current health is: " << player.currentHealth << std::endl;
            }
            else
            {
                std::cout << player.name << " is fully healed!" << std::endl;
            }
        }
    }
};

int main()
{
    // List of multiple players
    std::vector<Player> players = {
        Player("Mage", 50, 100),
        Player("Knight", 70, 100),
        Player("Rogue", 65, 100),
        Player("Cleric", 85, 100)
    };

    HealthPotionSystem potionSystem;
    potionSystem.HealPlayers(players); // Heal all players optimally using available potions
    

    return 0;
}
```



## Week 4 - Branching Dialogue
### Research

For the research it was best to look at examples of how to set up C# dialogue trees from the presentation. so I can research the best way to set out the question data. I used a bit of ai so I could adapt some of my prior knowledge into the format needed, plus had assistance from websites that explained some functions that aided me.



### Workings

Created big list of the nodes with questions.
``` c#
public DialogueNode BuildDialogueTree()
    {
        // Task for student: Build the dialogue tree structure here, creating connections between nodes
        DialogueNode root = new DialogueNode("Would you kill this person?", false);
        DialogueNode first = new DialogueNode("1How would you do it?",false); // yes
        DialogueNode second = new DialogueNode("2How wonderful?",false); //  no
        root.yes = first;
        root.no = second;
        
        DialogueNode third = new DialogueNode("3?",true); // yes
        DialogueNode fourth = new DialogueNode("4",false); // no
        first.yes = third;
        first.no = fourth;
        
        DialogueNode fifth = new DialogueNode("5",false); // yes, end
        DialogueNode sixth = new DialogueNode("6",true); // no
        second.yes = fifth;
        second.no = sixth;
        
        
        DialogueNode ninth = new DialogueNode("9",true); // yes, end
        DialogueNode tenth = new DialogueNode("10",true); // no, end
        fourth.yes = ninth;
        fourth.no = tenth;
        
        DialogueNode seventh = new DialogueNode("7",true); // yes, end
        DialogueNode eighth = new DialogueNode("8",true); // no, end 
        fifth.yes = seventh;
        fifth.no = eighth;
        
        return root;
        
        
    }
```
Experimented the best way of connecting the nodes together.
Had some issue with changing the example tree code from the presentation into working for our purpose as our one, was a multi node layers. 
Had some issues with encapsulation, and getting the function to call the root node, by root being built at the start. Could then access the root and start the node traversal.
Some issues with the online compiler, but it seemed to work fine. Only the first branches have proper dialogue attached to it, but it still shows different results based on yes and no answers.
```
Would you kill this person?
no
How wonderful?
yes
5
```

### Reflection
This topic was a bit more complex than what I am used to, as I have previously done branching dialogue in Unreal Engine blueprints I had an idea on the logic but was missing the important key words in c#. Luckily I had the tools and resources to hand that enabled me to finish this task.

### Full Code
``` c#
using System;
using System.Collections.Generic;

// The DialogueNode class represents a single dialogue option in the tree
public class DialogueNode
{
    // Task for student: Define the properties or fields for the dialogue node (e.g., dialogue text, choices, success/failure status)
    public string question;
    public DialogueNode yes, no;
    public bool endingNode;

    public DialogueNode(string NewDialogue, bool end) 
    {
        question = NewDialogue;
        yes = null;
        no = null;
        endingNode = end;
    }
    
}

// The DialogueSystem class represents the overall dialogue system
public class DialogueSystem
{
    // Task for student: Define the root node of the dialogue system (the starting point of the conversation)
    
    public DialogueNode BuildDialogueTree()
    {
        // Task for student: Build the dialogue tree structure here, creating connections between nodes
        DialogueNode root = new DialogueNode("Would you kill this person?", false);
        DialogueNode first = new DialogueNode("1How would you do it?",false); // yes
        DialogueNode second = new DialogueNode("2How wonderful?",false); //  no
        root.yes = first;
        root.no = second;
        
        DialogueNode third = new DialogueNode("3?",true); // yes
        DialogueNode fourth = new DialogueNode("4",false); // no
        first.yes = third;
        first.no = fourth;
        
        DialogueNode fifth = new DialogueNode("5",false); // yes, end
        DialogueNode sixth = new DialogueNode("6",true); // no
        second.yes = fifth;
        second.no = sixth;
        
        
        DialogueNode ninth = new DialogueNode("9",true); // yes, end
        DialogueNode tenth = new DialogueNode("10",true); // no, end
        fourth.yes = ninth;
        fourth.no = tenth;
        
        DialogueNode seventh = new DialogueNode("7",true); // yes, end
        DialogueNode eighth = new DialogueNode("8",true); // no, end 
        fifth.yes = seventh;
        fifth.no = eighth;
        
        return root;
        
        
    }
    
    public void StartDialogue(DialogueNode node)
    {
        // Task for student: Implement a function to navigate through the dialogue based on player choices
        string answer = "yes";
        
        if (node != null) {
            Console.WriteLine(node.question);
            answer = Console.ReadLine(); 
            if (answer == "yes")
            {
                StartDialogue(node.yes);
            }
            else
            {
                StartDialogue(node.no);
            }
        
        }
        
        
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        DialogueSystem dialogueSystem = new DialogueSystem();

        DialogueNode root = dialogueSystem.BuildDialogueTree();
         // Build the dialogue structure
        dialogueSystem.StartDialogue(root);     // Start navigating through the dialogue
    }
}
```



## Week 5 - Spellbook Search
### Research
Most of the research contained within this project had the sole purpose of finding the help on array searches.
https://www.geeksforgeeks.org/searching-in-array/

### Workings
This task asked for a search system 
For this task, it was important to get information on how to implement a sort system, I found websites with information on sorting vectors, as the main set of spells were displayed as an array. This gave information of using both the name of the array alongside using the overarching spelltype as the key terms to be used when searching in the array.

```cpp
// Spell search
std::vector<Spell> SearchSpells(const std::vector<Spell>& spellList, const std::string& keyword)
{
    std::vector<Spell> results;
    for (const auto& spell : spellList)
    {
        std::string lowerKeyword = keyword;
        std::transform(lowerKeyword.begin(), lowerKeyword.end(), lowerKeyword.begin(), ::tolower);

        // Check if the keyword matches
        std::string lowerName = spell.name;
        std::transform(lowerName.begin(), lowerName.end(), lowerName.begin(), ::tolower);

        if (lowerName.find(lowerKeyword) != std::string::npos ||
            spell.GetTargetTypeAsString().find(keyword) != std::string::npos ||
            spell.GetSpellTypeAsString().find(keyword) != std::string::npos)
        {
            results.push_back(spell);
        }
    }
    return results;
}
```

This works and displays the right selection of spells, the example below showing the result when a heal spell is searched for.
```
Search terms: Damage, Heal, Buff, Debuff, SingleTarget, AOE, Self
Enter a search keyword:
heal
Matching Spells:
Name: Healing Aura, Mana Cost: 30, Power: 50, Target: AOE, Type: Heal
Name: Healing Rain, Mana Cost: 35, Power: 60, Target: AOE, Type: Heal
Name: Radiant Heal, Mana Cost: 30, Power: 70, Target: Single Target, Type: Heal
```


### Reflection
This task was important as it is really important to be able to be able to find the information in arrays. Plus the better the search system, the more users will enjoy the experience. This is something I will carry forward as a key function.

### Bibliography

Searching in array (2024) At: https://www.geeksforgeeks.org/searching-in-array/ (Accessed  06/12/2024).


### Full Code
``` cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

// Define the target types
enum class TargetType
{
    SingleTarget,
    AOE,
    Self
};

// Define the spell types
enum class SpellType
{
    Damage,
    Heal,
    Buff,
    Debuff
};

// The Spell class represents a single spell with attributes
class Spell
{
public:
    std::string name;
    int manaCost;
    int power;
    TargetType target;
    SpellType type;

    Spell(std::string n, int mCost, int p, TargetType t, SpellType st)
        : name(n), manaCost(mCost), power(p), target(t), type(st) {}

    void PrintSpell() const
    {
        std::cout << "Name: " << name << ", Mana Cost: " << manaCost
                  << ", Power: " << power << ", Target: " << GetTargetTypeAsString()
                  << ", Type: " << GetSpellTypeAsString() << std::endl;
    }

    std::string GetTargetTypeAsString() const
    {
        switch (target)
        {
        case TargetType::SingleTarget: return "Single Target";
        case TargetType::AOE: return "AOE";
        case TargetType::Self: return "Self";
        default: return "Unknown";
        }
    }

    std::string GetSpellTypeAsString() const
    {
        switch (type)
        {
        case SpellType::Damage: return "Damage";
        case SpellType::Heal: return "Heal";
        case SpellType::Buff: return "Buff";
        case SpellType::Debuff: return "Debuff";
        default: return "Unknown";
        }
    }
};

// Function to create a list of spells
std::vector<Spell> CreateSpells()
{
    return {
        {"Fireball", 50, 100, TargetType::SingleTarget, SpellType::Damage},
        {"Healing Aura", 30, 50, TargetType::AOE, SpellType::Heal},
        {"Shield", 20, 0, TargetType::Self, SpellType::Buff},
        {"Curse", 40, 60, TargetType::SingleTarget, SpellType::Debuff},
        {"Blizzard", 70, 80, TargetType::AOE, SpellType::Damage},
        {"Regenerate", 25, 30, TargetType::Self, SpellType::Heal},
        {"Lightning Strike", 55, 120, TargetType::SingleTarget, SpellType::Damage},
        {"Mass Shield", 60, 0, TargetType::AOE, SpellType::Buff},
        {"Flame Burst", 45, 110, TargetType::AOE, SpellType::Damage},
        {"Light Aura", 30, 0, TargetType::AOE, SpellType::Buff},
        {"Dark Curse", 40, 70, TargetType::SingleTarget, SpellType::Debuff},
        {"Water Wave", 35, 90, TargetType::AOE, SpellType::Damage},
        {"Thunderbolt", 60, 130, TargetType::SingleTarget, SpellType::Damage},
        {"Earthquake", 65, 150, TargetType::AOE, SpellType::Damage},
        {"Magic Barrier", 50, 0, TargetType::Self, SpellType::Buff},
        {"Invisibility", 30, 0, TargetType::Self, SpellType::Buff},
        {"Meteor Shower", 90, 200, TargetType::AOE, SpellType::Damage},
        {"Ice Spike", 35, 80, TargetType::SingleTarget, SpellType::Damage},
        {"Hurricane", 75, 140, TargetType::AOE, SpellType::Damage},
        {"Holy Light", 20, 40, TargetType::Self, SpellType::Heal},
        {"Lightning Storm", 80, 180, TargetType::AOE, SpellType::Damage},
        {"Sacred Flame", 60, 100, TargetType::SingleTarget, SpellType::Damage},
        {"Venom Strike", 30, 70, TargetType::SingleTarget, SpellType::Debuff},
        {"Frost Nova", 70, 90, TargetType::AOE, SpellType::Damage},
        {"Mana Shield", 40, 0, TargetType::Self, SpellType::Buff},
        {"Arcane Missiles", 45, 85, TargetType::SingleTarget, SpellType::Damage},
        {"Healing Rain", 35, 60, TargetType::AOE, SpellType::Heal},
        {"Divine Protection", 50, 0, TargetType::Self, SpellType::Buff},
        {"Poison Cloud", 50, 100, TargetType::AOE, SpellType::Debuff},
        {"Stone Skin", 25, 0, TargetType::Self, SpellType::Buff},
        {"Life Drain", 50, 70, TargetType::SingleTarget, SpellType::Debuff},
        {"Phoenix Fire", 100, 250, TargetType::AOE, SpellType::Damage},
        {"Raging Inferno", 90, 210, TargetType::AOE, SpellType::Damage},
        {"Whirlwind", 55, 85, TargetType::AOE, SpellType::Damage},
        {"Blessing of Light", 30, 0, TargetType::Self, SpellType::Buff},
        {"Shadow Bolt", 40, 90, TargetType::SingleTarget, SpellType::Damage},
        {"Serpent's Bite", 45, 65, TargetType::SingleTarget, SpellType::Debuff},
        {"Cleansing Wave", 25, 0, TargetType::AOE, SpellType::Heal},
        {"Chill Touch", 35, 50, TargetType::SingleTarget, SpellType::Damage},
        {"Blood Pact", 60, 0, TargetType::Self, SpellType::Buff},
        {"Lunar Strike", 75, 160, TargetType::SingleTarget, SpellType::Damage},
        {"Solar Flare", 65, 140, TargetType::AOE, SpellType::Damage},
        {"Nature's Grasp", 50, 80, TargetType::SingleTarget, SpellType::Buff},
        {"Wrath of the Ancients", 100, 250, TargetType::AOE, SpellType::Damage},
        {"Ethereal Form", 40, 0, TargetType::Self, SpellType::Buff},
        {"Radiant Heal", 30, 70, TargetType::SingleTarget, SpellType::Heal},
        {"Stormcall", 80, 150, TargetType::AOE, SpellType::Damage},
        {"Chain Lightning", 70, 130, TargetType::AOE, SpellType::Damage},
        // Add more spells here
    };
}

// Spell search
std::vector<Spell> SearchSpells(const std::vector<Spell>& spellList, const std::string& keyword)
{
    std::vector<Spell> results;
    for (const auto& spell : spellList)
    {
        std::string lowerKeyword = keyword;
        std::transform(lowerKeyword.begin(), lowerKeyword.end(), lowerKeyword.begin(), ::tolower);

        // Check if the keyword matches
        std::string lowerName = spell.name;
        std::transform(lowerName.begin(), lowerName.end(), lowerName.begin(), ::tolower);

        if (lowerName.find(lowerKeyword) != std::string::npos ||
            spell.GetTargetTypeAsString().find(keyword) != std::string::npos ||
            spell.GetSpellTypeAsString().find(keyword) != std::string::npos)
        {
            results.push_back(spell);
        }
    }
    return results;
}

int main()
{
    std::vector<Spell> spells = CreateSpells();

    std::string keyword;
    std::cout << "Search terms: Damage, Heal, Buff, Debuff, SingleTarget, AOE, Self" << std::endl;
    std::cout << "Enter a search keyword:" << std::endl;
    std::getline(std::cin, keyword);

    // Search for spells based on the keyword
    std::vector<Spell> matchingSpells = SearchSpells(spells, keyword);

    // Display the results
    if (!matchingSpells.empty())
    {
        std::cout << "Matching Spells:" << std::endl;
        for (const auto& spell : matchingSpells)
        {
            spell.PrintSpell();
        }
    }
    else
    {
        std::cout << "No spells matched the search criteria." << std::endl;
    }

    return 0;
}
```


## Task 6 - Data Driven Movement System

### Deliverals
This task asks for the implementation of data-oriented design (DOD) in a simple movement system. This should be done using arrays or structs insted of the standardized classes and encapsulation.
The key requirements for this task are as follows:
* Storage of data in arrays or structs
* Multiple entities should be able to be moved
* The organization of data should be efficient through this separation of storage and behaviours
* Entity positions updated by velocity or input
* All entities are processed together for performance


### Research
This article from linkedin is perfect for explaining the uses of data oriented designs in video games, this is because it shows a direct comparison in usage and displays how much more scalable data oriented design is.
https://www.linkedin.com/pulse/data-oriented-vs-object-oriented-programming-choosing-iman-irajdoost-laece/

This video from a conference goes in depth about data oriented design, with Yehonathan Sharvit speaking and explaining the principles. I found the whole talk to be intruiging while giving me a greater interest within this topic. They wrote a book about data-oriented programming with the link below connected to an excerp from said book.

https://blog.klipse.tech/dop/2022/06/22/principles-of-dop.html

<iframe width="560" height="315" src="https://www.youtube.com/embed/zSHvEAKLFJw?si=8gq-wDaz_ay75-nQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


### Workings
The fisrt step onto changin this into data oriented design is to change how the inputs are placed into the program. Compared to before, there are now vector arrays connected that display only the data associated, in this case being the positions and velocities.
``` cpp
public:
    // Arrays grouped together
    std::vector<float> positionsX;
    std::vector<float> positionsY;
    std::vector<float> positionsZ;
    std::vector<float> velocitiesX;
    std::vector<float> velocitiesY;
    std::vector<float> velocitiesZ;
```

The entities can then be created, they can be introduced in a similar array style so it is all put out in one go.
``` cpp
    // Adding entities
    void AddEntity(float posX, float posY, float posZ, float velX, float velY, float velZ)
    {
        positionsX.push_back(posX);
        positionsY.push_back(posY);
        positionsZ.push_back(posZ);
        velocitiesX.push_back(velX);
        velocitiesY.push_back(velY);
        velocitiesZ.push_back(velZ);
    }
```

This way, when the system requires the entity to have an attached position to place it on the map, it can be done simply by combining the two. This allows all of the entities to be updated simultaniously.
``` cpp
    void UpdatePositions(float deltaTime)
    {
        size_t entityCount = positionsX.size();

        // Batch processing using loop unrolling for performance
        for (size_t i = 0; i < entityCount; ++i)
        {
            positionsX[i] += velocitiesX[i] * deltaTime;
            positionsY[i] += velocitiesY[i] * deltaTime;
            positionsZ[i] += velocitiesZ[i] * deltaTime;
        }
    }
```

All before being printed off simultaniously, in a highly efficient manner due to all of the information being light and in batches.
``` cpp
    // Print the positions of all entities
    void PrintPositions()
    {
        size_t entityCount = positionsX.size();

        for (size_t i = 0; i < entityCount; ++i)
        {
            std::cout << "Entity " << i + 1 << " Position: X=" << positionsX[i]
                      << ", Y=" << positionsY[i] << ", Z=" << positionsZ[i] << std::endl;
        }
    }
```


### Reflection
This was a task that was very much out of my comfort zone. As such, I resorted to relying on many resources such as the sources referenced, alongside help from my peers and even a small portion of ai in creating a data-oriented system for the movement. I feel like I am still missing a few bits on how it all works but am happy that through lots of trial and error the end results truly show through. 


### Bibliography

Conferences, G. (2023) Reduce System Complexity with Data-Oriented Programming • Yehonathan Sharvit • GOTO 2023. At: https://youtu.be/zSHvEAKLFJw?si=IYH942ZugGuTj8Ii

Irajdoost, I. (2024) Data-oriented vs. Object-Oriented Programming: Choosing the right paradigm for your project. At: https://www.linkedin.com/pulse/data-oriented-vs-object-oriented-programming-choosing-iman-irajdoost-laece/ (Accessed  05/12/2024).

Sharvit, Y. (2022) Principles of Data-Oriented Programming. At: https://blog.klipse.tech/dop/2022/06/22/principles-of-dop.html (Accessed  06/12/2024).



### Full Code
```cpp
#include <iostream>
#include <vector>

// Struct for entity data (position and velocity)
struct EntityData
{
    float positionX;
    float positionY;
    float positionZ;
    float velocityX;
    float velocityY;
    float velocityZ;

    // Constructor for initializing the struct
    EntityData(float posX, float posY, float posZ, float velX, float velY, float velZ)
        : positionX(posX), positionY(posY), positionZ(posZ), velocityX(velX), velocityY(velY), velocityZ(velZ) {}
};

// Movement system class (data-driven design)
class MovementSystem
{
public:
    // Arrays grouped together
    std::vector<float> positionsX;
    std::vector<float> positionsY;
    std::vector<float> positionsZ;
    std::vector<float> velocitiesX;
    std::vector<float> velocitiesY;
    std::vector<float> velocitiesZ;

    // Adding entities
    void AddEntity(float posX, float posY, float posZ, float velX, float velY, float velZ)
    {
        positionsX.push_back(posX);
        positionsY.push_back(posY);
        positionsZ.push_back(posZ);
        velocitiesX.push_back(velX);
        velocitiesY.push_back(velY);
        velocitiesZ.push_back(velZ);
    }

    // Updating the positions
    void UpdatePositions(float deltaTime)
    {
        size_t entityCount = positionsX.size();

        // Batch processing using loop unrolling for performance
        for (size_t i = 0; i < entityCount; ++i)
        {
            positionsX[i] += velocitiesX[i] * deltaTime;
            positionsY[i] += velocitiesY[i] * deltaTime;
            positionsZ[i] += velocitiesZ[i] * deltaTime;
        }
    }

    // Print the positions of all entities
    void PrintPositions()
    {
        size_t entityCount = positionsX.size();

        for (size_t i = 0; i < entityCount; ++i)
        {
            std::cout << "Entity " << i + 1 << " Position: X=" << positionsX[i]
                      << ", Y=" << positionsY[i] << ", Z=" << positionsZ[i] << std::endl;
        }
    }
};

int main()
{
    // Movement system
    MovementSystem movementSystem;

    // Add entities to the system
    movementSystem.AddEntity(0, 0, 0, 1, 0, 0);
    movementSystem.AddEntity(1, 2, 3, 0, 1, 0);
    movementSystem.AddEntity(5, 5, 5, 0, 0, 1);

    // Simulate multiple frames
    for (int frame = 0; frame < 5; ++frame)
    {
        std::cout << "\nFrame " << frame + 1 << std::endl;
        movementSystem.PrintPositions();      // Print current positions
        movementSystem.UpdatePositions(0.016f);  // Update positions (16ms per frame)
    }

    return 0;
}
```



## Week 7 - Character Creator
This task asked for the implementation of a character creation system using factory patterns and decorators. The first stwps where to plan out what the expectations and end results would be.
In this case, it was asked to contain:
* Characters would hold at least one item
* Factory or alternative patterns to create the different classes for characters
* Decorator patterns being used to modify the stats when items are applied
* Editable stats for the characters that items can interact with

To start it is important to define certain stats of each class, using switches to set these class differences. This is done first as the classes and stats need to be declared for the decorators to have value.
``` cpp
public:
    static Character* CreateCharacter(const std::string& name, CharacterClass charClass)
    {
        Character* character = new Character(name, charClass);

        // Switch case implementation
        switch (charClass)
        {
            case CharacterClass::Warrior: 
            character->strength = 10;
            character->intelligence = 3;
            
            break;
            case CharacterClass::Rogue: 
            character->agility = 10;
            character->luck = 7;
            character->strength = 4;
            break;
            case CharacterClass::Mage: 
            character->agility = 4;
            character->intelligence = 8;
            
            break;
            case CharacterClass::Wizard: 
            character->agility = 3;
            character->intelligence = 10;
            break;
            case CharacterClass::Ranger: 
            character->speed = 7;
            character->intelligence = 10;
            break;
            case CharacterClass::Monk: 
            character->agility = 6;
            character->endurance = 7;
            break;
            case CharacterClass::Bard: 
            character->luck = 15;
            character->willpower = 7;
            break;
            case CharacterClass::Paladin: 
            character->willpower = 8;
            character->strength = 8;
            character->endurance = 9;
            break;
            case CharacterClass::Cleric: 
            character->willpower = 8;
            character->strength = 4;
            break;
            
            
        }
        return character;
    }
};
```

Creating a decorator class to have the items within, as this would allow the stats items and stats called in from one place for efficiency. 
A virtual function was thought to be used with this but it was decided to revert back to the decorator as a subclass of the character as this will allow the decorator to add/functions to the character. This was mainly due to the level of research necessary to understand this method, and it was deemed better to use what was better known.

With this new setup, a decorator base with an ability attached to it. A child decorator for sword was added which passed “slash” as the ability. Following this, a shield decorator could be added for further testing of the decorator function. This would then, in theory, give the player a block ability.
``` cpp
class SwordDecorator : public CharacterDecorator
{
   public:
    SwordDecorator(Character* character)
        : CharacterDecorator(character, "Slash") {} // Pass ability "Slash" to the constructor

    void changeStats() override {
        character->strength += 5;  // Increase strength by 5
    }

    void addAbility() override {
        ability = "Slash"; // Modify the ability
    }
};
```

Created examples of the different characters with items for testing to ensure it all works as necessary.   
The shield stats didn't work as intended until reimplementation, but this was fixed up so the stats and ability worked as intended.

Currently the player can see each step of the character creation, including seeing the warrior's stats get changed and abilities being added on.
``` Output
Name: GuyDude, Class: 0
Strength: 10, Agility: 5, Endurance: 5, Intelligence: 3, Willpower: 5, Speed: 5, Luck: 5
Name: GuyDude, Class: 0
Strength: 10, Agility: 5, Endurance: 10, Intelligence: 3, Willpower: 5, Speed: 5, Luck: 5
Ability: Block
Name: GuyDude, Class: 0
Strength: 15, Agility: 5, Endurance: 10, Intelligence: 3, Willpower: 5, Speed: 5, Luck: 5
Ability: Slash
Name: GuyDude, Class: 0
Strength: 15, Agility: 5, Endurance: 10, Intelligence: 3, Willpower: 5, Speed: 5, Luck: 5
Ability: Slash
Ability: Block
```

Following this, the option for the player to select their class. This allows all classes to be seen and takes in the player input.
After this the idea of an item selection  to show off the decorators was planned to be implemented, with the basic options of before combined with extras like the "hermes boots", which adds a dash ability and increases the speed of the player. The end goal of this implementation is for the player to have control over the character and the attatched items.

### Reflection
Overall I feel that this project was useful for increasing my understanding for decorators in c++. Before this, I had an idea of how switch cases can be implemented and used to alter the variables but had little knowledge of how to use decorators alongside to achieve a similar effect. The only other time I have applied decorators in my knowledge is within my final major prototype behaviour tree, but this was implemented within blueprints, which is a lot more visual and easier to recognise. After this however, I feel more comfortable using this tool as I have this point to reference as to how it can be applied and used.

### Full code below with output:
``` cpp
#include <iostream>
#include <string>

// Define the character classes
enum class CharacterClass
{
    Warrior,
    Rogue,
    Mage,
    Wizard,
    Ranger,
    Monk,
    Bard,
    Paladin,
    Cleric
};

// Character base class
class Character
{
public:
    std::string name;
    CharacterClass characterClass;
    int strength, agility, endurance, intelligence, willpower, speed, luck;

    Character(std::string n, CharacterClass c)
        : name(n), characterClass(c), strength(5), agility(5), endurance(5),
          intelligence(5), willpower(5), speed(5), luck(5) {}

    virtual void PrintCharacterInfo()
    {
        std::cout << "Name: " << name << ", Class: " << static_cast<int>(characterClass) << std::endl;
        std::cout << "Strength: " << strength << ", Agility: " << agility
                  << ", Endurance: " << endurance << ", Intelligence: " << intelligence
                  << ", Willpower: " << willpower << ", Speed: " << speed
                  << ", Luck: " << luck << std::endl;
        
    }

    virtual ~Character() = default;
};

// Factory for character creation
class CharacterFactory
{
public:
    static Character* CreateCharacter(const std::string& name, CharacterClass charClass)
    {
        Character* character = new Character(name, charClass);

        // Switch case implementation
        switch (charClass)
        {
            case CharacterClass::Warrior: 
            character->strength = 10;
            character->intelligence = 3;
            
            break;
            case CharacterClass::Rogue: 
            character->agility = 10;
            character->luck = 7;
            character->strength = 4;
            break;
            case CharacterClass::Mage: 
            character->agility = 4;
            character->intelligence = 8;
            
            break;
            case CharacterClass::Wizard: 
            character->agility = 3;
            character->intelligence = 10;
            break;
            case CharacterClass::Ranger: 
            character->speed = 7;
            character->intelligence = 10;
            break;
            case CharacterClass::Monk: 
            character->agility = 6;
            character->endurance = 7;
            break;
            case CharacterClass::Bard: 
            character->luck = 15;
            character->willpower = 7;
            break;
            case CharacterClass::Paladin: 
            character->willpower = 8;
            character->strength = 8;
            character->endurance = 9;
            break;
            case CharacterClass::Cleric: 
            character->willpower = 8;
            character->strength = 4;
            break;
            
            
        }
        return character;
    }
};

// Decorator for adding abilities or modifiers to characters
class CharacterDecorator : public Character
{
protected:
    Character* character;

public:
    std::string ability;

    CharacterDecorator(Character* c, const std::string& ab) : Character(c->name, c->characterClass), character(c), ability(ab) {}

    virtual void changeStats() {}

    virtual void addAbility() {}

    void PrintCharacterInfo() override {
        character->PrintCharacterInfo();
        std::cout << "Ability: " << ability << std::endl;
    }
    
    
    
    
};


class SwordDecorator : public CharacterDecorator
{
   public:
    SwordDecorator(Character* character)
        : CharacterDecorator(character, "Slash") {} // Pass ability "Slash" to the constructor

    void changeStats() override {
        character->strength += 5;  // Increase strength by 5
    }

    void addAbility() override {
        ability = "Slash"; // Modify the ability
    }
};

class ShieldDecorator : public CharacterDecorator {
public:
    ShieldDecorator(Character* character)
        : CharacterDecorator(character, "Block") {}

    void changeStats() override {
        character->endurance += 5;  // Increase endurance by 5
    }

    void addAbility() override {
        ability = "Block"; // Modify the ability
    }
};



// class Decorator 
// {
//     public:
//         void updateStats();
        
//         virtual void Statchange();
        
    
    
    
// }


// Implemented Decorator
int main() {
    Character* firstGuy = CharacterFactory::CreateCharacter("GuyDude", CharacterClass::Warrior);

     // Print the character info before decorating
    firstGuy->PrintCharacterInfo();

       // Now decorate the character with a sword and shield
    SwordDecorator* decoratedWithSword = new SwordDecorator(firstGuy);
    ShieldDecorator* decoratedWithShield = new ShieldDecorator(decoratedWithSword);
    ShieldDecorator* decoratedWithOnlyShield = new ShieldDecorator(firstGuy);
    
    
    decoratedWithOnlyShield->changeStats();
    decoratedWithOnlyShield->addAbility();
    decoratedWithOnlyShield->PrintCharacterInfo();
    // Apply all decorators' changes
    decoratedWithSword->changeStats();  // Apply sword stats
    decoratedWithSword->addAbility();  // Apply sword ability
    
    decoratedWithSword->PrintCharacterInfo();
    
    decoratedWithShield->changeStats();  // Apply shield stats
    decoratedWithShield->addAbility();  // Apply shield ability
        
    // Print the updated character info
    decoratedWithShield->PrintCharacterInfo();
    // Clean up memory
    delete firstGuy;
    delete decoratedWithSword;
    delete decoratedWithShield;
    delete decoratedWithOnlyShield;
    return 0;
}
```
