---
Group: "**D - Code (Intermediate)**"
---


### Events

**Events** in C# are a way to provide notifications when something happens. They are built on top of delegates and allow for a more controlled and flexible approach to implementing the observer pattern. Events are used extensively in frameworks like Unity to handle various interactions and game logic.

### Key Concepts

- **Event Declaration**: Defines an event using a delegate type.
- **Event Subscription**: Allows methods to be added to or removed from the event's invocation list.
- **Event Invocation**: Triggers the event, calling all subscribed methods.

### Examples

#### Example 1: Basic Event

This example demonstrates how to declare, subscribe to, and invoke an event.

**Step 1: Declare a Delegate and Event**

Declare a delegate and an event based on that delegate.

```csharp
using UnityEngine;

public class BasicEventExample : MonoBehaviour
{
    // Delegate declaration
    public delegate void SimpleEventHandler();
    // Event declaration
    public event SimpleEventHandler OnSimpleEvent;

    private void Start()
    {
        // Subscribe to the event
        OnSimpleEvent += HandleSimpleEvent;

        // Invoke the event
        OnSimpleEvent?.Invoke();
    }

    // Event handler method
    private void HandleSimpleEvent()
    {
        Debug.Log("Simple event handled");
    }
}
```

**Key Points:**
- **Delegate Declaration**: `public delegate void SimpleEventHandler();`
- **Event Declaration**: `public event SimpleEventHandler OnSimpleEvent;`
- **Event Subscription**: `OnSimpleEvent += HandleSimpleEvent;`
- **Event Invocation**: `OnSimpleEvent?.Invoke();`

#### Example 2: Event with Parameters

This example demonstrates an event with parameters.

```csharp
using UnityEngine;

public class EventWithParametersExample : MonoBehaviour
{
    // Delegate declaration
    public delegate void ParameterEventHandler(int value);
    // Event declaration
    public event ParameterEventHandler OnParameterEvent;

    private void Start()
    {
        // Subscribe to the event
        OnParameterEvent += HandleParameterEvent;

        // Invoke the event
        OnParameterEvent?.Invoke(42);
    }

    // Event handler method
    private void HandleParameterEvent(int value)
    {
        Debug.Log("Parameter event handled with value: " + value);
    }
}
```

**Key Points:**
- **Delegate with Parameters**: `public delegate void ParameterEventHandler(int value);`
- **Event with Parameters**: `public event ParameterEventHandler OnParameterEvent;`
- **Event Invocation with Parameters**: `OnParameterEvent?.Invoke(42);`

#### Example 3: Using Events in a Class

This example demonstrates using events within a class to notify subscribers of changes.

**Step 1: Define a Class with an Event**

Define a class that raises an event when a value changes.

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    // Delegate and event declaration
    public delegate void HealthChangedEventHandler(int newHealth);
    public event HealthChangedEventHandler OnHealthChanged;

    private int health;

    public int Health
    {
        get { return health; }
        set
        {
            health = value;
            OnHealthChanged?.Invoke(health); // Invoke the event when health changes
        }
    }

    private void Start()
    {
        Health = 100;
    }
}
```

**Step 2: Subscribe to the Event**

Create another script to subscribe to the `OnHealthChanged` event.

```csharp
using UnityEngine;

public class HealthDisplay : MonoBehaviour
{
    public Player player;

    private void OnEnable()
    {
        player.OnHealthChanged += UpdateHealthDisplay; // Subscribe to the event
    }

    private void OnDisable()
    {
        player.OnHealthChanged -= UpdateHealthDisplay; // Unsubscribe from the event
    }

    private void UpdateHealthDisplay(int newHealth)
    {
        Debug.Log("Health updated: " + newHealth);
        // Update UI or other elements to reflect new health value
    }
}
```

**Key Points:**
- **Event in Class**: The `Player` class has an event `OnHealthChanged`.
- **Event Subscription**: The `HealthDisplay` class subscribes to the `OnHealthChanged` event.
- **Event Unsubscription**: The `HealthDisplay` class unsubscribes from the `OnHealthChanged` event to prevent memory leaks.

### Summary

- **Events**: Provide a way to notify multiple subscribers when something happens.
- **Event Declaration**: Defined using a delegate type.
- **Event Subscription**: Methods can be added or removed from the event's invocation list.
- **Event Invocation**: Triggers the event, calling all subscribed methods.
- **Memory Management**: Always unsubscribe from events to prevent memory leaks.

By using events, you can implement the observer pattern in a type-safe and flexible manner, allowing for decoupled communication between different parts of your application. This is especially useful in game development for handling user interactions, game state changes, and other dynamic behaviors.