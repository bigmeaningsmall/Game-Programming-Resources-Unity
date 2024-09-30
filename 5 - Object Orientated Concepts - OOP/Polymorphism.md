---
Group: "**B - Concept**"
---


### Polymorphism

**Polymorphism** is a core concept in object-oriented programming (OOP) that allows objects of different types to be treated as objects of a common super type. It provides a way to perform a single action in different forms. In C#, polymorphism is primarily achieved through method overriding and interfaces.

### Key Concepts

- **Method Overriding**: Allows a derived class to provide a specific implementation of a method that is already defined in its base class.
- **Interfaces**: Define a contract that classes can implement. They allow different classes to be treated polymorphically if they implement the same interface.
- **Base Class Reference**: A base class reference can point to an object of any derived class.

### Examples

#### Example 1: Method Overriding

This example demonstrates polymorphism through method overriding in a class hierarchy.

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

**Step 2: Override the Method in Derived Classes**

```csharp
using UnityEngine;

public class Dog : Animal
{
    public override void Speak()
    {
        Debug.Log(name + " barks.");
    }
}

public class Cat : Animal
{
    public override void Speak()
    {
        Debug.Log(name + " meows.");
    }
}
```

**Step 3: Use Polymorphism in a Script**

```csharp
using UnityEngine;

public class PolymorphismExample : MonoBehaviour
{
    private void Start()
    {
        Animal myDog = new Dog();
        myDog.name = "Rex";
        Animal myCat = new Cat();
        myCat.name = "Whiskers";

        myDog.Speak(); // Output: Rex barks.
        myCat.Speak(); // Output: Whiskers meows.
    }
}
```

**Key Points:**
- **Virtual Method**: `Speak` method in `Animal` is marked as `virtual`.
- **Override Method**: `Speak` method in `Dog` and `Cat` overrides the base class method using the `override` keyword.
- **Base Class Reference**: `Animal` references can point to `Dog` and `Cat` objects.

#### Example 2: Polymorphism with Interfaces

This example demonstrates polymorphism using interfaces.

**Step 1: Define the Interface**

```csharp
public interface IAnimal
{
    void Speak();
}
```

**Step 2: Implement the Interface in Different Classes**

```csharp
using UnityEngine;

public class Dog : MonoBehaviour, IAnimal
{
    public string name;

    public void Speak()
    {
        Debug.Log(name + " barks.");
    }
}

public class Cat : MonoBehaviour, IAnimal
{
    public string name;

    public void Speak()
    {
        Debug.Log(name + " meows.");
    }
}
```

**Step 3: Use Polymorphism in a Script**

```csharp
using UnityEngine;

public class InterfacePolymorphismExample : MonoBehaviour
{
    private void Start()
    {
        IAnimal myDog = new Dog { name = "Rex" };
        IAnimal myCat = new Cat { name = "Whiskers" };

        myDog.Speak(); // Output: Rex barks.
        myCat.Speak(); // Output: Whiskers meows.
    }
}
```

**Key Points:**
- **Interface Declaration**: `IAnimal` interface declares the `Speak` method.
- **Interface Implementation**: `Dog` and `Cat` classes implement the `IAnimal` interface.
- **Interface Reference**: `IAnimal` references can point to `Dog` and `Cat` objects.

#### Example 3: Polymorphism in Action

This example demonstrates how polymorphism allows you to write more generic and flexible code.

```csharp
using UnityEngine;

public class PolymorphismActionExample : MonoBehaviour
{
    private void Start()
    {
        IAnimal[] animals = new IAnimal[]
        {
            new Dog { name = "Rex" },
            new Cat { name = "Whiskers" }
        };

        MakeAllAnimalsSpeak(animals);
    }

    void MakeAllAnimalsSpeak(IAnimal[] animals)
    {
        foreach (IAnimal animal in animals)
        {
            animal.Speak();
        }
    }
}
```

**Key Points:**
- **Array of Interface**: An array of `IAnimal` references can hold objects of any class that implements `IAnimal`.
- **Generic Method**: The `MakeAllAnimalsSpeak` method can accept any array of objects that implement `IAnimal`.

### Summary

- **Polymorphism**: Allows objects of different types to be treated as objects of a common super type.
- **Method Overriding**: Derived classes provide specific implementations for methods defined in a base class.
- **Interfaces**: Define a contract that multiple classes can implement, enabling polymorphic behavior.
- **Base Class Reference**: Can point to objects of any derived class, enabling flexible and reusable code.

Polymorphism enables writing more flexible and maintainable code, allowing for methods to interact with objects of various types in a unified way. This is particularly useful in scenarios where you want to handle different types of objects through a common interface or base class.