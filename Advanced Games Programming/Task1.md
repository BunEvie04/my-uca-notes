# Task 1

## Research 

To start with the task, it is important to know what sorting method isand how to implement it into the project. This website was used for this purpose as it broke them down with examples to make it clearer.

https://www.simplilearn.com/tutorials/cpp-tutorial/sorting-in-cpp#:~:text=Examples%20of%20internal%20sorting%20are,sorting%20is%20the%20Merge%20sort.


The video below was used as a reference when considering alternate methods for the sorting method within this task

<iframe width="560" height="315" src="https://www.youtube.com/embed/x0uUKWJzSO4?si=HVr-AaPAjHRnAq2A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>



## Inventory sorting
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
```cpp
public:
    std::string name;
    int value;

    Item(std::string n, int v) : name(n), value(v) {}
};
```

This is completed through a bubble sort. By defining the integers n (for the size of the list), i, and j, the loops can filter out the placements for each item in the array.
```cpp
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
Alternative methods may include using the ***sort*** function to automatically list them in order using the given parameters.

```cpp
std::sort(items.begin(), items.end(), [](const Item& a, 
const Item& b)
{
    return a.name < b.name;    
});
```

### Sorting by value
The next step I want to try is to sort by the values of the items in the list, which use int v. For this, I changed the parts containing *name* and replaced it with *value*.
Before:

```
Sorted by Value (Descending):
Sword: 150
Bow: 120
Shield: 100
Helmet: 80
Potion: 50
```

### Next steps
For the next stage I wanted the user to be able to add their own inputs into each of the catagories, with the system outputting a new list with their addition sorted within. 


### Full Code
```
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

        //std::cin >>  >> std::endl;
        
        
        std::cout << "\nSorted by Name (Ascending):" << std::endl;
        SortByName(items, true); // Sort by name in ascending order
        DisplayInventory(items);
        
        std::cout << "\nSorted by Name (Descending):" << std::endl;
        SortByName(items, false); // Sort by name in ascending order
        DisplayInventory(items);

        std::cout << "\nSorted by Value (Ascending):" << std::endl;
        SortByValue(items, false); // Sort by value in descending order
        DisplayInventory(items);
        
        std::cout << "\nSorted by Value (Descending):" << std::endl;
        SortByValue(items, true); // Sort by value in descending order
        DisplayInventory(items);

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

## Bibliography

Ravikiran, A. S. (2021) What is sorting in C++: Bubble Sort, Insertion Sort & more. At: https://www.simplilearn.com/tutorials/cpp-tutorial/sorting-in-cpp (Accessed  05/12/2024).

The Cherno (s.d.) Sorting in C++. At: https://youtu.be/x0uUKWJzSO4?si=G2y8Capf5eodJ5QN (Accessed  05/12/2024).

