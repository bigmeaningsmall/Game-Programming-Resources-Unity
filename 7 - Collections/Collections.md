---
Group: "**D - Code (Intermediate)**"
---


### Collections

Collections are data structures that hold multiple items. In C#, common collections include Arrays, Lists, and Dictionaries. Each of these collections has its own characteristics and use cases.

#### Arrays
Arrays are fixed-size collections of elements of the same type. They are useful when you know the number of elements in advance and need fast access by index.

**Example:**

```csharp
using UnityEngine;

public class ArrayExample : MonoBehaviour
{
    private void Start()
    {
        int[] scores = new int[5]; // Array declaration with size 5
        scores[0] = 10;
        scores[1] = 20;
        scores[2] = 30;
        scores[3] = 40;
        scores[4] = 50;

        for (int i = 0; i < scores.Length; i++)
        {
            Debug.Log("Score " + i + ": " + scores[i]);
        }
    }
}
```

#### Lists
Lists are dynamic-size collections of elements of the same type. They are part of the `System.Collections.Generic` namespace and are useful when the number of elements can change dynamically.

**Example:**

```csharp
using System.Collections.Generic;
using UnityEngine;

public class ListExample : MonoBehaviour
{
    private void Start()
    {
        List<string> fruits = new List<string>(); // List declaration
        fruits.Add("Apple");
        fruits.Add("Banana");
        fruits.Add("Cherry");

        foreach (string fruit in fruits)
        {
            Debug.Log("Fruit: " + fruit);
        }
    }
}
```

#### Dictionaries
Dictionaries are collections of key-value pairs. Each key must be unique, and they provide fast lookup based on keys. Dictionaries are part of the `System.Collections.Generic` namespace.

**Example:**

```csharp
using System.Collections.Generic;
using UnityEngine;

public class DictionaryExample : MonoBehaviour
{
    private void Start()
    {
        Dictionary<string, int> ages = new Dictionary<string, int>(); // Dictionary declaration
        ages["Alice"] = 25;
        ages["Bob"] = 30;
        ages["Charlie"] = 35;

        foreach (KeyValuePair<string, int> entry in ages)
        {
            Debug.Log(entry.Key + " is " + entry.Value + " years old.");
        }
    }
}
```

### Key Points

1. **Arrays**:
   - Fixed size
   - Fast access by index
   - Suitable when the number of elements is known in advance

2. **Lists**:
   - Dynamic size
   - Part of `System.Collections.Generic`
   - Suitable when the number of elements can change dynamically

3. **Dictionaries**:
   - Key-value pairs
   - Unique keys
   - Fast lookup by key
   - Part of `System.Collections.Generic`

These examples cover the basic use cases and syntax for Arrays, Lists, and Dictionaries in C#. Each of these collections serves different purposes and is suitable for various scenarios in Unity game development.