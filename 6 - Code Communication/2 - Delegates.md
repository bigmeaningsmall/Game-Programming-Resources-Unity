---
Group: "**D - Code (Intermediate)**"
---


### Delegates

**Delegates** in C# are a type that represents references to methods with a specific parameter list and return type. They are similar to function pointers in C++ but are type-safe and secure. Delegates are used to pass methods as arguments to other methods, define callback methods, and implement event handling.

### Key Concepts

- **Delegate Declaration**: Defines the type signature of methods that the delegate can reference.
- **Delegate Instantiation**: Creates an instance of the delegate, referencing a specific method.
- **Delegate Invocation**: Calls the method(s) referenced by the delegate.
- **Multicast Delegates**: Delegates that can reference more than one method at a time.

### Examples

#### Example 1: Basic Delegate

This example demonstrates how to declare, instantiate, and invoke a delegate.

**Step 1: Declare a Delegate**

Declare a delegate that takes an integer and returns void.

```csharp
using UnityEngine;

public class BasicDelegateExample : MonoBehaviour
{
    // Delegate declaration
    public delegate void PrintDelegate(int number);

    private void Start()
    {
        // Instantiate the delegate
        PrintDelegate print = PrintNumber;

        // Invoke the delegate
        print(100);
    }

    // Method that matches the delegate signature
    private void PrintNumber(int number)
    {
        Debug.Log("Number: " + number);
    }
}
```

**Key Points:**
- **Delegate Declaration**: `public delegate void PrintDelegate(int number);`
- **Delegate Instantiation**: `PrintDelegate print = PrintNumber;`
- **Delegate Invocation**: `print(100);`

#### Example 2: Multicast Delegate

This example demonstrates a multicast delegate, which can reference multiple methods.

```csharp
using UnityEngine;

public class MulticastDelegateExample : MonoBehaviour
{
    // Delegate declaration
    public delegate void PrintDelegate(int number);

    private void Start()
    {
        // Instantiate the delegate and add methods
        PrintDelegate print = PrintNumber;
        print += PrintNumberTwice;

        // Invoke the delegate
        print(100);
    }

    // Method that matches the delegate signature
    private void PrintNumber(int number)
    {
        Debug.Log("Number: " + number);
    }

    // Another method that matches the delegate signature
    private void PrintNumberTwice(int number)
    {
        Debug.Log("Number twice: " + (number * 2));
    }
}
```

**Key Points:**
- **Multicast Delegate**: `print += PrintNumberTwice;` adds another method to the delegate invocation list.
- **Delegate Invocation**: Calls both `PrintNumber` and `PrintNumberTwice`.

#### Example 3: Delegate as a Callback

This example demonstrates using a delegate as a callback method.

```csharp
using UnityEngine;

public class DelegateCallbackExample : MonoBehaviour
{
    // Delegate declaration
    public delegate void ResultDelegate(int result);

    private void Start()
    {
        // Perform a calculation and use a callback to handle the result
        PerformCalculation(10, 20, HandleResult);
    }

    // Method that performs a calculation and calls the callback
    private void PerformCalculation(int a, int b, ResultDelegate callback)
    {
        int result = a + b;
        callback(result);
    }

    // Callback method
    private void HandleResult(int result)
    {
        Debug.Log("Calculation result: " + result);
    }
}
```

**Key Points:**
- **Callback Mechanism**: Pass a delegate as an argument to a method.
- **Callback Invocation**: Call the delegate within the method to invoke the callback.

### Summary

- **Delegates**: A type that references methods with a specific parameter list and return type.
- **Declaration**: Defines the type signature of methods that the delegate can reference.
- **Instantiation**: Creates an instance of the delegate, referencing a specific method.
- **Invocation**: Calls the method(s) referenced by the delegate.
- **Multicast Delegates**: Delegates that can reference more than one method at a time.
- **Callback Methods**: Delegates can be used to define callback methods, providing a way to pass methods as arguments to other methods.

By using delegates, you can create flexible and reusable code that allows methods to be passed as parameters, enabling callback mechanisms and event handling in a type-safe manner.