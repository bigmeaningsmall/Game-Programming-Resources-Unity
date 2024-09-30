---
Group: "**B - Concept**"
---


### Encapsulation

**Encapsulation** is one of the fundamental principles of object-oriented programming (OOP). It refers to the bundling of data (variables) and methods (functions) that operate on the data into a single unit, typically a class. Encapsulation restricts direct access to some of an object's components, which can prevent the accidental modification of data and promote a modular and maintainable code structure.

### Key Concepts

- **Private Members**: Variables and methods that are not accessible from outside the class.
- **Public Methods**: Functions that provide controlled access to the private members.
- **Properties**: Special methods called getters and setters used to access private fields.

### Examples

#### Example 1: Basic Encapsulation

This example demonstrates the encapsulation of data within a class using private members and public methods.

**Step 1: Define a Class with Private Members**

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    // Private fields
    private string playerName;
    private int health;

    // Public method to set the player's name
    public void SetPlayerName(string name)
    {
        playerName = name;
    }

    // Public method to get the player's name
    public string GetPlayerName()
    {
        return playerName;
    }

    // Public method to set the player's health
    public void SetHealth(int healthValue)
    {
        if (healthValue >= 0)
        {
            health = healthValue;
        }
    }

    // Public method to get the player's health
    public int GetHealth()
    {
        return health;
    }
}
```

**Step 2: Use the Encapsulated Class**

```csharp
using UnityEngine;

public class EncapsulationExample : MonoBehaviour
{
    private void Start()
    {
        Player player = new Player();
        player.SetPlayerName("Alice");
        player.SetHealth(100);

        Debug.Log("Player Name: " + player.GetPlayerName());
        Debug.Log("Player Health: " + player.GetHealth());
    }
}
```

**Key Points:**
- **Private Fields**: `playerName` and `health` are private and not accessible directly from outside the class.
- **Public Methods**: Provide controlled access to the private fields.

#### Example 2: Encapsulation with Properties

This example demonstrates encapsulation using properties to provide access to private fields.

**Step 1: Define a Class with Properties**

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    // Private fields
    private string playerName;
    private int health;

    // Public property for playerName
    public string PlayerName
    {
        get { return playerName; }
        set { playerName = value; }
    }

    // Public property for health with validation in the setter
    public int Health
    {
        get { return health; }
        set
        {
            if (value >= 0)
            {
                health = value;
            }
        }
    }
}
```

**Step 2: Use the Encapsulated Class with Properties**

```csharp
using UnityEngine;

public class PropertyEncapsulationExample : MonoBehaviour
{
    private void Start()
    {
        Player player = new Player();
        player.PlayerName = "Bob";
        player.Health = 150;

        Debug.Log("Player Name: " + player.PlayerName);
        Debug.Log("Player Health: " + player.Health);
    }
}
```

**Key Points:**
- **Properties**: `PlayerName` and `Health` properties provide controlled access to the private fields.
- **Validation**: The `Health` property includes validation in the setter.

### Summary

- **Encapsulation**: Bundling data and methods that operate on that data within a single unit (class).
- **Private Members**: Variables and methods that are not accessible from outside the class, ensuring data protection.
- **Public Methods**: Functions that provide controlled access to private members.
- **Properties**: Getters and setters that provide a way to read and write private fields with optional validation.

Encapsulation helps in protecting the internal state of an object and only exposes a controlled interface, making the code more modular, maintainable, and less prone to errors. It is a key principle in achieving data hiding and abstraction in OOP.