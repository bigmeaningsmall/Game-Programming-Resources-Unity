

### Inheritance

**Inheritance** is a fundamental concept in object-oriented programming (OOP) that allows a class to inherit properties and methods from another class. This promotes code reuse and establishes a hierarchical relationship between classes. The class that is inherited from is called the **base class** (or **parent class**), and the class that inherits is called the **derived class** (or **child class**).

### Key Concepts

- **Base Class**: The class being inherited from.
- **Derived Class**: The class that inherits from the base class.
- **`protected` Access Modifier**: Allows members to be accessible within the base class and derived classes.
- **Overriding Methods**: Derived classes can override methods from the base class to provide specific implementations.
- **Polymorphism**: Allows methods to be used interchangeably with objects of different but related types.

### Examples

#### Example 1: Basic Inheritance

This example demonstrates a simple inheritance relationship where a derived class inherits properties and methods from a base class.

**Step 1: Define the Base Class**

```csharp
using UnityEngine;

public class Animal : MonoBehaviour
{
    public string name;

    public void Speak()
    {
        Debug.Log(name + " makes a sound.");
    }
}
```

**Step 2: Define the Derived Class**

```csharp
using UnityEngine;

public class Dog : Animal
{
    public void Bark()
    {
        Debug.Log(name + " barks.");
    }
}
```

**Step 3: Use the Derived Class**

```csharp
using UnityEngine;

public class InheritanceExample : MonoBehaviour
{
    private void Start()
    {
        Dog myDog = new Dog();
        myDog.name = "Rex";
        myDog.Speak(); // Inherited method
        myDog.Bark();  // Derived class method
    }
}
```

**Key Points:**
- **Base Class**: `Animal` class with a `name` property and a `Speak` method.
- **Derived Class**: `Dog` class inherits from `Animal` and adds a `Bark` method.
- **Instantiation**: Create an instance of the `Dog` class and use both inherited and derived methods.

#### Example 2: Overriding Methods

This example demonstrates how a derived class can override a method from the base class to provide a specific implementation.

**Step 1: Define the Base Class with a Virtual Method**

```csharp
using UnityEngine;

public class Animal : MonoBehaviour
{
    public string name;

    public virtual void Speak()
    {
        Debug.Log(name + " makes a sound.");
    }
}
```

**Step 2: Override the Method in the Derived Class**

```csharp
using UnityEngine;

public class Dog : Animal
{
    public override void Speak()
    {
        Debug.Log(name + " barks.");
    }
}
```

**Step 3: Use the Derived Class**

```csharp
using UnityEngine;

public class OverridingExample : MonoBehaviour
{
    private void Start()
    {
        Dog myDog = new Dog();
        myDog.name = "Rex";
        myDog.Speak(); // Calls the overridden method in Dog
    }
}
```

**Key Points:**
- **Virtual Method**: `Speak` method in `Animal` is marked as `virtual`.
- **Override Method**: `Speak` method in `Dog` overrides the base class method using the `override` keyword.
- **Polymorphism**: The `Dog` class provides a specific implementation of the `Speak` method.

#### Example 3: Protected Members

This example demonstrates the use of the `protected` access modifier to allow derived classes to access base class members.

**Step 1: Define the Base Class with Protected Members**

```csharp
using UnityEngine;

public class Animal : MonoBehaviour
{
    protected string name;

    protected void SetName(string newName)
    {
        name = newName;
    }
}
```

**Step 2: Access Protected Members in the Derived Class**

```csharp
using UnityEngine;

public class Dog : Animal
{
    public void AssignName(string newName)
    {
        SetName(newName); // Accessing protected method from the base class
    }

    public void Speak()
    {
        Debug.Log(name + " barks.");
    }
}
```

**Step 3: Use the Derived Class**

```csharp
using UnityEngine;

public class ProtectedExample : MonoBehaviour
{
    private void Start()
    {
        Dog myDog = new Dog();
        myDog.AssignName("Rex");
        myDog.Speak(); // Output: Rex barks.
    }
}
```

**Key Points:**
- **Protected Members**: `name` and `SetName` are protected in the `Animal` class.
- **Access in Derived Class**: The `Dog` class can access and use protected members from the `Animal` class.

### Summary

- **Inheritance**: Allows a class to inherit properties and methods from another class.
- **Base Class**: The class being inherited from.
- **Derived Class**: The class that inherits from the base class.
- **Protected Members**: Accessible within the base class and derived classes.
- **Overriding Methods**: Derived classes can provide specific implementations for methods defined in the base class.
- **Polymorphism**: Allows for methods to be used interchangeably with objects of different but related types.

Inheritance promotes code reuse and establishes a hierarchical relationship between classes, enabling more flexible and maintainable code.
