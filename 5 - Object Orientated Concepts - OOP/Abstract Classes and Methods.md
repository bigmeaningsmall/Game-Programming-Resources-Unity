---
Group: "**D - Code (Intermediate)**"
---


### Abstract Classes and Methods

#### Revision

**Abstract classes** and **abstract methods** are fundamental concepts in object-oriented programming (OOP) that allow you to define classes and methods that are incomplete and must be implemented by derived classes. Abstract classes provide a base for other classes to build upon, but cannot be instantiated themselves.

### Key Concepts

- **Abstract Class**: A class that cannot be instantiated and is intended to be subclassed. It can contain both abstract methods (without implementation) and concrete methods (with implementation).
- **Abstract Method**: A method declared in an abstract class without any implementation. Derived classes must override and provide an implementation for abstract methods.

### Examples

#### Example 1: Basic Abstract Class and Method

This example demonstrates how to define and use an abstract class with an abstract method.

**Step 1: Define the Abstract Class**

```csharp
using UnityEngine;

public abstract class Animal : MonoBehaviour
{
    public string name;

    // Abstract method (no implementation)
    public abstract void Speak();

    // Concrete method (with implementation)
    public void SetName(string newName)
    {
        name = newName;
    }
}
```

**Step 2: Implement the Abstract Class in a Derived Class**

```csharp
using UnityEngine;

public class Dog : Animal
{
    // Override and provide implementation for the abstract method
    public override void Speak()
    {
        Debug.Log(name + " barks.");
    }
}

public class Cat : Animal
{
    // Override and provide implementation for the abstract method
    public override void Speak()
    {
        Debug.Log(name + " meows.");
    }
}
```

**Step 3: Use the Abstract Class and Derived Classes**

```csharp
using UnityEngine;

public class AbstractExample : MonoBehaviour
{
    private void Start()
    {
        Animal myDog = new Dog();
        myDog.SetName("Rex");
        myDog.Speak(); // Output: Rex barks.

        Animal myCat = new Cat();
        myCat.SetName("Whiskers");
        myCat.Speak(); // Output: Whiskers meows.
    }
}
```

**Key Points:**
- **Abstract Class**: `public abstract class Animal`
- **Abstract Method**: `public abstract void Speak();`
- **Concrete Method**: `public void SetName(string newName)`
- **Implementation**: Derived classes (`Dog`, `Cat`) must override the `Speak` method.

#### Example 2: Abstract Class with Properties

This example demonstrates using properties in an abstract class.

**Step 1: Define the Abstract Class with Properties**

```csharp
using UnityEngine;

public abstract class Shape : MonoBehaviour
{
    public abstract float Area { get; }

    public abstract float Perimeter { get; }
}
```

**Step 2: Implement the Abstract Class in a Derived Class**

```csharp
using UnityEngine;

public class Circle : Shape
{
    public float radius;

    public override float Area
    {
        get { return Mathf.PI * radius * radius; }
    }

    public override float Perimeter
    {
        get { return 2 * Mathf.PI * radius; }
    }
}
```

**Step 3: Use the Abstract Class and Derived Classes**

```csharp
using UnityEngine;

public class AbstractPropertiesExample : MonoBehaviour
{
    private void Start()
    {
        Circle myCircle = new Circle();
        myCircle.radius = 5;
        Debug.Log("Circle Area: " + myCircle.Area); // Output: Circle Area: 78.54
        Debug.Log("Circle Perimeter: " + myCircle.Perimeter); // Output: Circle Perimeter: 31.42
    }
}
```

**Key Points:**
- **Abstract Properties**: `public abstract float Area { get; }`
- **Property Implementation**: Derived class (`Circle`) must provide the implementation for `Area` and `Perimeter` properties.

### Summary

- **Abstract Class**: A class that serves as a base for other classes and cannot be instantiated. It can contain both abstract methods (without implementation) and concrete methods (with implementation).
- **Abstract Method**: A method declared in an abstract class without any implementation. Derived classes must override and implement abstract methods.
- **Properties**: Abstract classes can also declare properties that derived classes must implement.
- **Polymorphism**: Abstract classes enable polymorphism, allowing you to use derived classes through a common base class interface.

Abstract classes and methods are powerful tools for creating a well-structured and extendable codebase. They allow you to define a common interface for a group of related classes while leaving the specific implementation details to the derived classes. This promotes code reuse and flexibility in your applications.