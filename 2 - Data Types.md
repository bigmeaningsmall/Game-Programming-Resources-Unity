---
Group: "**C - Code (Basic)**"
Index: 11
---

#### 2. Data Types
Data types specify the type of data that a variable can hold. C# is a strongly-typed language, meaning that the type of a variable is known at compile time.

### Common Data Types

#### int
- Integer type
- Examples: 1, -5, 100
#### float
- Floating-point type
- Examples: 1.0f, -5.5f, 100.25f
#### string
- Sequence of characters
- Example: "Hello, World!"
#### bool
- Boolean type
- Examples: true, false

**Example:**

```csharp
public class DataTypeExample : MonoBehaviour
{
    // Data type examples
    int level = 1;
    float speed = 5.5f;
    string message = "Welcome to Unity!";
    bool isActive = true;

    private void Start()
    {
        Debug.Log("Level: " + level);
        Debug.Log("Speed: " + speed);
        Debug.Log("Message: " + message);
        Debug.Log("Is Active: " + isActive);
    }
}
```

