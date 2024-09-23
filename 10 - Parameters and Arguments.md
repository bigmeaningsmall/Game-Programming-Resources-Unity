---
Group: "**C - Code (Basic)**"
Index: 11
---

### Parameters and Arguments

**Parameters** are variables listed as part of a function's definition. **Arguments** are the actual values passed to the function when it is called.

#### Detailed Explanation

- **Parameters**: These are the placeholders in the function definition that specify what kind of arguments the function expects. Parameters are defined within the parentheses following the function name.
  
- **Arguments**: These are the actual values supplied to the function when it is invoked. The arguments must match the parameters in type and order.

# Examples:

### Example 1: Function with Parameters and Arguments

In this example, the function `MultiplyNumbers` takes two parameters and multiplies them. The values `3` and `4` are the arguments provided during the function call.

```csharp
using UnityEngine;

public class ParametersAndArgumentsExample1 : MonoBehaviour
{
    private void Start()
    {
        int result = MultiplyNumbers(3, 4); // 3 and 4 are arguments
        Debug.Log("The product is: " + result);
    }

    // Function with parameters
    int MultiplyNumbers(int a, int b) // a and b are parameters
    {
        return a * b;
    }
}
```

### Example 2: Function with Multiple Parameters

This example demonstrates a function `DisplayPlayerStats` that takes multiple parameters of different types.

```csharp
using UnityEngine;

public class ParametersAndArgumentsExample2 : MonoBehaviour
{
    private void Start()
    {
        DisplayPlayerStats("Alice", 5, 75.5f);
    }

    // Function with multiple parameters
    void DisplayPlayerStats(string playerName, int level, float health)
    {
        Debug.Log("Player Name: " + playerName);
        Debug.Log("Level: " + level);
        Debug.Log("Health: " + health);
    }
}
```

### Example 3: Using Parameters to Perform Calculations

This example shows a function `CalculateArea` that calculates the area of a rectangle using its length and width as parameters.

```csharp
using UnityEngine;

public class ParametersAndArgumentsExample3 : MonoBehaviour
{
    private void Start()
    {
        float length = 5.0f;
        float width = 3.5f;
        float area = CalculateArea(length, width);
        Debug.Log("The area of the rectangle is: " + area);
    }

    // Function with parameters to perform a calculation
    float CalculateArea(float length, float width)
    {
        return length * width;
    }
}
```

### Key Points to Remember

1. **Parameters** are defined in the function declaration.
2. **Arguments** are the values passed to the function when it is called.
3. Parameters and arguments must match in number, type, and order.

