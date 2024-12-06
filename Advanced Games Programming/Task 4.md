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
