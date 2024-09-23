---
Group: "**C - Code (Basic)**"
Index: 11
---

### Basic Programming Concepts in Unity C#

#### 1. Variables
Variables are used to store data that can be referenced and manipulated in a program. In C#, variables must be declared with a specific data type.

**Example:**

```csharp
public class VariableExample : MonoBehaviour
{
    // Variable declaration
    int score = 0;
    [SerializeField] float health = 100.0f;
    public string playerName = "John";
    private bool isGameOver = false;

    private void Start()
    {
        // Variable usage
        score = 10;
        health -= 20.5f;
        playerName = "Alice";
        isGameOver = true;

        Debug.Log("Score: " + score);
        Debug.Log("Health: " + health);
        Debug.Log("Player Name: " + playerName);
        Debug.Log("Is Game Over: " + isGameOver);
    }
}
```

