# Character Creator
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
A virtual function was thought to be used with this but it was decided to revert back to the decorator as a subclass of the character as this will allow the decorator to add/functions to the character.

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


Full code below with output:
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
