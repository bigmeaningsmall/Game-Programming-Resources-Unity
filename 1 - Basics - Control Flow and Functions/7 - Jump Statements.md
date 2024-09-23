---
Group: "**C - Code (Basic)**"
Index: 11
---
### Jump Statements

Jump statements allow you to control the flow of the program by jumping to other parts of the code. The main jump statements in C# are `break`, `continue`, and `return`.

#### Break
The `break` statement is used to exit the current loop or switch statement immediately, terminating the loop or case in which it resides.

**Example:**
```csharp
using UnityEngine;

public class BreakExample : MonoBehaviour
{
    private void Start()
    {
        for (int i = 0; i < 10; i++)
        {
            if (i == 5)
            {
                break;
            }
            Debug.Log("Iteration: " + i); // Code to be repeated until i is equal to 5
        }
    }
}
```

#### Continue
The `continue` statement is used to skip the rest of the current loop iteration and proceed with the next iteration of the loop.

**Example:**
```csharp
using UnityEngine;

public class ContinueExample : MonoBehaviour
{
    private void Start()
    {
        for (int i = 0; i < 10; i++)
        {
            if (i == 5)
            {
                continue;
            }
            Debug.Log("Iteration: " + i); // Code to be repeated, skipping when i is equal to 5
        }
    }
}
```

#### Return
The `return` statement is used to end the execution of the current function and optionally return a value to the function caller. In a `void` function, `return` can be used to exit the function early without returning a value.

**Example:**
```csharp
using UnityEngine;

public class ReturnExample : MonoBehaviour
{
    private void Start()
    {
        int result = Sum(3, 4);
        Debug.Log("The sum is: " + result);
    }

    // Function with return type
    int Sum(int a, int b)
    {
        return a + b;
    }
}
```

### Summary
- **Break**: Exits the current loop or switch statement immediately.
- **Continue**: Skips the rest of the current loop iteration and starts the next iteration.
- **Return**: Ends the execution of the current function and returns a value (if specified).

