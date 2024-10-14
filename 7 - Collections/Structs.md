---
Group: "**E - Code (Advanced)**"
---

### Advanced Collections: Structs

In C#, structs (short for structures) are value types that can be used to encapsulate small groups of related variables. Unlike classes, structs are typically used for lightweight objects that do not require inheritance or reference semantics. They are useful for improving performance in certain scenarios, such as when dealing with collections of simple data types.

#### Structs in Collections

Structs can be used within collections like arrays, lists, and dictionaries to group related data together. Here are some examples to illustrate how structs can be used in collections:

### Example 1: Structs in Arrays

```csharp
using UnityEngine;

public class StructArrayExample : MonoBehaviour
{
    // Define a struct to represent a point in 2D space
    public struct Point
    {
        public float x;
        public float y;

        public Point(float x, float y)
        {
            this.x = x;
            this.y = y;
        }
    }

    private void Start()
    {
        // Create an array of points
        Point[] points = new Point[3];
        points[0] = new Point(1.0f, 2.0f);
        points[1] = new Point(3.0f, 4.0f);
        points[2] = new Point(5.0f, 6.0f);

        foreach (Point point in points)
        {
            Debug.Log("Point: (" + point.x + ", " + point.y + ")");
        }
    }
}
```

### Example 2: Structs in Lists

```csharp
using System.Collections.Generic;
using UnityEngine;

public class StructListExample : MonoBehaviour
{
    // Define a struct to represent a player with an ID and name
    public struct Player
    {
        public int id;
        public string name;

        public Player(int id, string name)
        {
            this.id = id;
            this.name = name;
        }
    }

    private void Start()
    {
        // Create a list of players
        List<Player> players = new List<Player>();
        players.Add(new Player(1, "Alice"));
        players.Add(new Player(2, "Bob"));
        players.Add(new Player(3, "Charlie"));

        foreach (Player player in players)
        {
            Debug.Log("Player ID: " + player.id + ", Name: " + player.name);
        }
    }
}
```

### Example 3: Structs in Dictionaries

```csharp
using System.Collections.Generic;
using UnityEngine;

public class StructDictionaryExample : MonoBehaviour
{
    // Define a struct to represent an item with a name and value
    public struct Item
    {
        public string name;
        public int value;

        public Item(string name, int value)
        {
            this.name = name;
            this.value = value;
        }
    }

    private void Start()
    {
        // Create a dictionary to store items by their IDs
        Dictionary<int, Item> items = new Dictionary<int, Item>();
        items[101] = new Item("Sword", 150);
        items[102] = new Item("Shield", 100);
        items[103] = new Item("Potion", 50);

        foreach (KeyValuePair<int, Item> entry in items)
        {
            Debug.Log("Item ID: " + entry.Key + ", Name: " + entry.Value.name + ", Value: " + entry.Value.value);
        }
    }
}
```

### Key Points

1. **Structs**:
   - Value types, stored on the stack
   - Typically used for lightweight objects
   - Do not support inheritance

2. **Using Structs in Collections**:
   - Can encapsulate related data
   - Improve performance by avoiding heap allocation
   - Useful in arrays, lists, and dictionaries

By using structs in collections, you can efficiently group related data and improve performance in certain scenarios. Structs are particularly beneficial when you need to handle simple, lightweight objects in a performant manner.