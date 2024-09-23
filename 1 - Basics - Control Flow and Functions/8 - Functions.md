---
Group: "**C - Code (Basic)**"
Index: 11
---

### Functions (Methods)

#### Revision

**Functions (Methods)** are blocks of code designed to perform a particular task. They are defined once and can be called multiple times throughout your program. In C#, functions are defined within classes, and they encapsulate code for better modularity and reusability.

**Key Concepts:**
- **Declaration**: Defining the function's name, return type, and parameters.
- **Return Type**: The type of value the function returns (e.g., `void` for no return, `int` for an integer return).
- **Parameters**: Values you pass into the function to be used within its body.
- **Calling a Function**: Executing the function's code by using its name followed by parentheses.

#### Examples

### Example 1: Basic Function
A simple function that prints a message to the console.

```csharp
using UnityEngine;

public class FunctionExample1 : MonoBehaviour
{
    private void Start()
    {
        PrintMessage();
    }

    // Function declaration
    void PrintMessage()
    {
        Debug.Log("Hello, World!");
    }
}
```

### Example 2: Function with Parameters
A function that takes parameters and uses them within its body.

```csharp
using UnityEngine;

public class FunctionExample2 : MonoBehaviour
{
    private void Start()
    {
        PrintCustomMessage("Welcome to Unity!", 3);
    }

    // Function with parameters
    void PrintCustomMessage(string message, int times)
    {
        for (int i = 0; i < times; i++)
        {
            Debug.Log(message);
        }
    }
}
```

### Example 3: Function with Return Type
A function that performs a calculation and returns a value.

```csharp
using UnityEngine;

public class FunctionExample3 : MonoBehaviour
{
    private void Start()
    {
        int result = AddNumbers(5, 7);
        Debug.Log("The sum is: " + result);
    }

    // Function with return type
    int AddNumbers(int a, int b)
    {
        int sum = a + b;
        return sum;
    }
}
```

### Example 4: Using Functions for Reusability
A more practical example showing how functions can help in avoiding code duplication.

```csharp
using UnityEngine;

public class FunctionExample4 : MonoBehaviour
{
    private void Start()
    {
        int health1 = 75;
        int health2 = 45;

        Debug.Log("Player 1 Status: " + GetHealthStatus(health1));
        Debug.Log("Player 2 Status: " + GetHealthStatus(health2));
    }

    // Function for determining health status
    string GetHealthStatus(int health)
    {
        if (health > 70)
        {
            return "Healthy";
        }
        else if (health > 30)
        {
            return "Injured";
        }
        else
        {
            return "Critical";
        }
    }
}
```

