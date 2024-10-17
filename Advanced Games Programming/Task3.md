# Health potion tasks

We broke down the problem and likened it to other computational problems, where you use coins to get to a certain amount. 
We deduced that it would start with the potion with the highest volume and then use as many as it could before the amount left was less than that, and then go to the next smallest.
We realised that the potions were stored in a vector struct. 
As we were not completely familiar with vectors in C++, we wanted to look at the documentation.

Created a while loop to add potion health value to the current health
It went on for ever as we had not properly set up the while loop to end,
 
```
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
unfortunately if the answer gets to more than 90 (less than the 10 potion amount) it would get stuck.
We then instead calculated the lowest healing potion ( making it so its scalable for any types of potions.
Used that to make the while loop to go down to until there were no potions left to get it to exactly 100.
Then output the amount of health if it didn’t go to 100.
