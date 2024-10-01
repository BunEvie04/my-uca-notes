# Task 1
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
## Alternative methods
Alternative methods may include using the ***sort*** function to automatically list them in order using the given parameters.

```cpp
std::sort(items.begin(), items.end(), [](const Item& a, 
const Item& b)
{
    return a.name < b.name;    
});
```

## Sorting by value
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

## Next steps
For the next stage I wanted the user to be able to add their own inputs into each of the catagories, with the system outputting a new list with their addition sorted within. 