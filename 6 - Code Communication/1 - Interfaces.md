---
Group: "**D - Code (Intermediate)**"
---


### Interfaces

#### Revision

**Interfaces** in C# define a contract that classes can implement. They specify methods, properties, events, and indexers without implementing them. Classes and structs that implement an interface must provide an implementation for all its members. Interfaces enable polymorphism, allowing objects to be used interchangeably if they implement the same interface.

### Key Concepts

- **Interface Declaration**: Use the `interface` keyword to declare an interface.
- **Interface Implementation**: Use the `: InterfaceName` syntax to implement an interface in a class or struct.
- **Multiple Inheritance**: A class or struct can implement multiple interfaces.
- **Polymorphism**: Interfaces allow objects to be treated polymorphically.

### Examples

#### Example 1: Basic Interface

This example demonstrates how to declare and implement a basic interface.

**Step 1: Define the Interface**

```csharp
public interface IMovable
{
    void Move();
}
```

**Step 2: Implement the Interface in a Class**

```csharp
using UnityEngine;

public class Player : MonoBehaviour, IMovable
{
    public void Move()
    {
        Debug.Log("Player is moving");
    }
}
```

**Step 3: Use the Interface**

```csharp
using UnityEngine;

public class InterfaceExample : MonoBehaviour
{
    private void Start()
    {
        IMovable movable = new Player();
        movable.Move(); // Output: Player is moving
    }
}
```

**Key Points:**
- **Interface Declaration**: `public interface IMovable { void Move(); }`
- **Interface Implementation**: `public class Player : MonoBehaviour, IMovable`
- **Polymorphism**: `IMovable movable = new Player();`

#### Example 2: Interface with Properties

This example demonstrates how to declare and implement an interface with properties.

**Step 1: Define the Interface**

```csharp
public interface IDamageable
{
    int Health { get; set; }
    void TakeDamage(int damage);
}
```

**Step 2: Implement the Interface in a Class**

```csharp
using UnityEngine;

public class Enemy : MonoBehaviour, IDamageable
{
    public int Health { get; set; }

    public void TakeDamage(int damage)
    {
        Health -= damage;
        if (Health <= 0)
        {
            Debug.Log("Enemy is dead");
        }
        else
        {
            Debug.Log("Enemy took damage, health is now: " + Health);
        }
    }
}
```

**Step 3: Use the Interface**

```csharp
using UnityEngine;

public class DamageExample : MonoBehaviour
{
    private void Start()
    {
        IDamageable damageable = new Enemy { Health = 100 };
        damageable.TakeDamage(20); // Output: Enemy took damage, health is now: 80
        damageable.TakeDamage(90); // Output: Enemy is dead
    }
}
```

**Key Points:**
- **Interface with Properties**: `int Health { get; set; }`
- **Interface Implementation**: Implementing both the property and the method in `Enemy` class.
- **Using Interface**: Creating an `IDamageable` reference to an `Enemy` instance.

#### Example 3: Multiple Interfaces

This example demonstrates how a class can implement multiple interfaces.

**Step 1: Define the Interfaces**

```csharp
public interface IMovable
{
    void Move();
}

public interface IDamageable
{
    int Health { get; set; }
    void TakeDamage(int damage);
}
```

**Step 2: Implement Multiple Interfaces in a Class**

```csharp
using UnityEngine;

public class NPC : MonoBehaviour, IMovable, IDamageable
{
    public int Health { get; set; }

    public void Move()
    {
        Debug.Log("NPC is moving");
    }

    public void TakeDamage(int damage)
    {
        Health -= damage;
        if (Health <= 0)
        {
            Debug.Log("NPC is dead");
        }
        else
        {
            Debug.Log("NPC took damage, health is now: " + Health);
        }
    }
}
```

**Step 3: Use the Multiple Interfaces**

```csharp
using UnityEngine;

public class MultipleInterfacesExample : MonoBehaviour
{
    private void Start()
    {
        NPC npc = new NPC { Health = 100 };
        
        IMovable movable = npc;
        IDamageable damageable = npc;

        movable.Move();           // Output: NPC is moving
        damageable.TakeDamage(20); // Output: NPC took damage, health is now: 80
    }
}
```

**Key Points:**
- **Multiple Interfaces**: `public class NPC : MonoBehaviour, IMovable, IDamageable`
- **Using Interface References**: `IMovable movable = npc;` and `IDamageable damageable = npc;`

### Summary

- **Interface**: Defines a contract with methods, properties, events, and indexers.
- **Implementation**: Classes and structs must implement all members of the interface.
- **Polymorphism**: Interfaces enable treating objects of different classes uniformly.
- **Multiple Inheritance**: A class or struct can implement multiple interfaces, allowing for more flexible and modular code design.

Interfaces are a powerful feature in C# that allow for the design of flexible and reusable code. They help define clear contracts that implementing classes must follow, promoting consistency and reliability in your codebase.