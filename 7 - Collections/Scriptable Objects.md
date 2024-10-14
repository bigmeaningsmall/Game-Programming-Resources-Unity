---
Group: "**E - Code (Advanced)**"
---

### Scriptable Objects

**Scriptable Objects** in Unity are a powerful way to create data containers that can be used to store large amounts of data independent of class instances. They are assets that allow you to manage data in a more modular and decoupled manner, making your code cleaner and more manageable.

### Key Concepts

- **Scriptable Object**: A class that derives from `ScriptableObject`, used to create custom assets.
- **Asset Creation**: Scriptable Objects can be created and managed through the Unity Editor.
- **Data Storage**: Ideal for storing configuration data, game settings, and other types of data that need to persist independently of game objects.

### Example

#### Example 1: Creating a Scriptable Object

This example demonstrates how to create a Scriptable Object to store item data.

**Step 1: Define the Scriptable Object**

Create a new script to define the Scriptable Object.

```csharp
using UnityEngine;

[CreateAssetMenu(fileName = "NewItem", menuName = "Inventory/Item")]
public class Item : ScriptableObject
{
    public string itemName;
    public string description;
    public Sprite icon;
    public int value;
}
```

**Key Points:**
- **[CreateAssetMenu]**: Attribute to allow creating an instance of the Scriptable Object from the Unity Editor.
- **Public Fields**: Fields to store item data, which will be exposed in the Unity Editor.

**Step 2: Create an Instance of the Scriptable Object**

1. In Unity, go to the **Project** window.
2. Right-click and select **Create > Inventory > Item**.
3. A new asset is created. You can now fill in the details in the Inspector.

#### Example 2: Using Scriptable Objects in a Script

This example demonstrates how to use the created Scriptable Object in a MonoBehaviour script.

**Step 1: Create a MonoBehaviour Script**

Create a new script to use the Item Scriptable Object.

```csharp
using UnityEngine;

public class Inventory : MonoBehaviour
{
    public Item[] items; // Array to hold multiple Item Scriptable Objects

    private void Start()
    {
        foreach (Item item in items)
        {
            Debug.Log("Item: " + item.itemName + ", Description: " + item.description + ", Value: " + item.value);
        }
    }
}
```

**Key Points:**
- **Public Array**: A public array of `Item` objects to hold multiple Scriptable Objects.
- **Start Method**: Iterate through the array and log the item details.

**Step 2: Assign Scriptable Objects to the MonoBehaviour Script**

1. Attach the `Inventory` script to a GameObject in your scene.
2. In the Inspector, assign the created `Item` assets to the `items` array.

#### Example 3: Scriptable Object for Game Configuration

This example demonstrates using a Scriptable Object for storing game configuration settings.

**Step 1: Define the Scriptable Object**

Create a new script to define the configuration settings.

```csharp
using UnityEngine;

[CreateAssetMenu(fileName = "GameConfig", menuName = "Config/GameConfig")]
public class GameConfig : ScriptableObject
{
    public string gameName;
    public int maxPlayers;
    public float gameDuration;
}
```

**Step 2: Create and Use the Game Configuration**

1. Create an instance of the `GameConfig` Scriptable Object in the Unity Editor.
2. Assign values to the fields in the Inspector.

**Step 3: Access the Configuration in a Script**

Create a script to access and use the configuration settings.

```csharp
using UnityEngine;

public class GameManager : MonoBehaviour
{
    public GameConfig config; // Reference to the GameConfig Scriptable Object

    private void Start()
    {
        Debug.Log("Game Name: " + config.gameName);
        Debug.Log("Max Players: " + config.maxPlayers);
        Debug.Log("Game Duration: " + config.gameDuration);
    }
}
```

**Key Points:**
- **Public Reference**: A public reference to the `GameConfig` Scriptable Object.
- **Start Method**: Access and use the configuration settings.

### Summary

- **Scriptable Object**:
  - A data container that derives from `ScriptableObject`.
  - Used to store data independently of MonoBehaviour instances.
  
- **Asset Creation**:
  - Use the `[CreateAssetMenu]` attribute to create Scriptable Objects from the Unity Editor.
  - Scriptable Objects can be created and edited in the Project window.

- **Usage**:
  - Scriptable Objects can be used to store configuration data, game settings, item data, and more.
  - They help keep data modular and decoupled from specific game objects.

By leveraging Scriptable Objects, you can manage and organize your game's data more effectively, leading to cleaner and more maintainable code.