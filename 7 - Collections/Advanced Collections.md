---
Group: "**D - Code (Intermediate)**"
---

Certainly! Here’s an overview of some additional advanced collections in C# along with examples that can be useful in Unity programming:

### Advanced Collections

#### Queues
A Queue is a first-in, first-out (FIFO) collection of objects. It is useful for scenarios where you need to process items in the order they were added.

**Example:**

```csharp
using System.Collections.Generic;
using UnityEngine;

public class QueueExample : MonoBehaviour
{
    private void Start()
    {
        Queue<string> messages = new Queue<string>();
        messages.Enqueue("First message");
        messages.Enqueue("Second message");
        messages.Enqueue("Third message");

        while (messages.Count > 0)
        {
            string message = messages.Dequeue();
            Debug.Log("Processing: " + message);
        }
    }
}
```

#### Stacks
A Stack is a last-in, first-out (LIFO) collection of objects. It is useful for scenarios where you need to reverse the order of items or track function calls.

**Example:**

```csharp
using System.Collections.Generic;
using UnityEngine;

public class StackExample : MonoBehaviour
{
    private void Start()
    {
        Stack<string> actions = new Stack<string>();
        actions.Push("Action 1");
        actions.Push("Action 2");
        actions.Push("Action 3");

        while (actions.Count > 0)
        {
            string action = actions.Pop();
            Debug.Log("Undoing: " + action);
        }
    }
}
```

#### HashSets
A HashSet is a collection of unique elements. It is useful when you need to store a set of items and ensure there are no duplicates.

**Example:**

```csharp
using System.Collections.Generic;
using UnityEngine;

public class HashSetExample : MonoBehaviour
{
    private void Start()
    {
        HashSet<int> uniqueNumbers = new HashSet<int>();
        uniqueNumbers.Add(1);
        uniqueNumbers.Add(2);
        uniqueNumbers.Add(2); // Duplicate, will not be added
        uniqueNumbers.Add(3);

        foreach (int number in uniqueNumbers)
        {
            Debug.Log("Unique number: " + number);
        }
    }
}
```

#### LinkedLists
A LinkedList is a doubly linked list of nodes. It is useful for scenarios where you need to insert or remove elements frequently.

**Example:**

```csharp
using System.Collections.Generic;
using UnityEngine;

public class LinkedListExample : MonoBehaviour
{
    private void Start()
    {
        LinkedList<string> tasks = new LinkedList<string>();
        tasks.AddLast("Task 1");
        tasks.AddLast("Task 2");
        tasks.AddLast("Task 3");

        LinkedListNode<string> current = tasks.First;

        while (current != null)
        {
            Debug.Log("Task: " + current.Value);
            current = current.Next;
        }
    }
}
```

### Key Points

1. **Queues**:
   - First-in, first-out (FIFO) collection.
   - Useful for processing items in the order they were added.

2. **Stacks**:
   - Last-in, first-out (LIFO) collection.
   - Useful for reversing item order or tracking function calls.

3. **HashSets**:
   - Collection of unique elements.
   - Ensures no duplicates.

4. **LinkedLists**:
   - Doubly linked list of nodes.
   - Useful for frequent insertions and deletions.

These advanced collections provide additional functionality and efficiency for specific use cases in Unity programming, helping to manage data in more complex scenarios.