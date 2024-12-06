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
