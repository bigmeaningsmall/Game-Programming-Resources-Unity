---
Group: "**C - Code (Basic)**"
Index: 11
---
### Return Types

#### Revision

In C#, the **return type** of a function specifies the type of value that the function returns to its caller. The return type is declared before the function name. If a function does not return any value, its return type is `void`.

**Key Concepts:**
- **Void Return Type**: Indicates that the function does not return a value.
- **Non-Void Return Types**: Indicates that the function returns a value of a specified type (e.g., `int`, `float`, `string`, `bool`, etc.).

### Examples

#### Example 1: Void Return Type
A function with a `void` return type does not return any value. It simply performs an action.

```csharp
using UnityEngine;

public class VoidReturnTypeExample : MonoBehaviour
{
    private void Start()
    {
        PrintMessage();
    }

    // Function with void return type
    void PrintMessage()
    {
        Debug.Log("Hello, World!");
    }
}
```

#### Example 2: Int Return Type
A function with an `int` return type returns an integer value to the caller.

```csharp
using UnityEngine;

public class IntReturnTypeExample : MonoBehaviour
{
    private void Start()
    {
        int result = AddNumbers(3, 4);
        Debug.Log("The sum is: " + result);
    }

    // Function with int return type
    int AddNumbers(int a, int b)
    {
        return a + b;
    }
}
```

#### Example 3: Float Return Type
A function with a `float` return type returns a floating-point number to the caller.

```csharp
using UnityEngine;

public class FloatReturnTypeExample : MonoBehaviour
{
    private void Start()
    {
        float area = CalculateArea(5.0f, 3.5f);
        Debug.Log("The area is: " + area);
    }

    // Function with float return type
    float CalculateArea(float length, float width)
    {
        return length * width;
    }
}
```

#### Example 4: String Return Type
A function with a `string` return type returns a sequence of characters to the caller.

```csharp
using UnityEngine;

public class StringReturnTypeExample : MonoBehaviour
{
    private void Start()
    {
        string message = GetGreeting("Alice");
        Debug.Log(message);
    }

    // Function with string return type
    string GetGreeting(string name)
    {
        return "Hello, " + name + "!";
    }
}
```

#### Example 5: Bool Return Type
A function with a `bool` return type returns a boolean value (true or false) to the caller.

```csharp
using UnityEngine;

public class BoolReturnTypeExample : MonoBehaviour
{
    private void Start()
    {
        bool isEven = IsEvenNumber(4);
        Debug.Log("Is the number even? " + isEven);
    }

    // Function with bool return type
    bool IsEvenNumber(int number)
    {
        return number % 2 == 0;
    }
}
```

### Key Points to Remember
1. The return type specifies what type of value the function will return.
2. The return type is declared before the function name.
3. If a function does not return any value, use `void` as the return type.
4. The `return` statement is used to return a value from the function to the caller.

By understanding return types, you can design functions that either perform actions or compute and return values, enhancing the modularity and reusability of your code.
