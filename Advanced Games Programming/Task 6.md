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
```


### Reflection
This was a task that was very much out of my comfort zone. As such, I resorted to relying on many resources such as the sources referenced, alongside help from my peers and even a small portion of ai in creating a data-oriented system for the movement. I feel like I am still missing a few bits on how it all works but am happy that through lots of trial and error the end results truly show through. 


### Bibliography

Conferences, G. (2023) Reduce System Complexity with Data-Oriented Programming • Yehonathan Sharvit • GOTO 2023. At: https://youtu.be/zSHvEAKLFJw?si=IYH942ZugGuTj8Ii

Irajdoost, I. (2024) Data-oriented vs. Object-Oriented Programming: Choosing the right paradigm for your project. At: https://www.linkedin.com/pulse/data-oriented-vs-object-oriented-programming-choosing-iman-irajdoost-laece/ (Accessed  05/12/2024).

Sharvit, Y. (2022) Principles of Data-Oriented Programming. At: https://blog.klipse.tech/dop/2022/06/22/principles-of-dop.html (Accessed  06/12/2024).



### Full Code below
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
