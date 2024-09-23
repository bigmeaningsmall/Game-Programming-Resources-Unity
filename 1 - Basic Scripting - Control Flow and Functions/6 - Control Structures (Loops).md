
#### Loops
Loops allow you to execute a block of code repeatedly.

**For Loop Example:**

```csharp
public class ForLoopExample : MonoBehaviour
{
    private void Start()
    {
        for (int i = 0; i < 5; i++)
        {
            Debug.Log("For Loop iteration: " + i);
        }
    }
}
```

**While Loop Example:**

```csharp
public class WhileLoopExample : MonoBehaviour
{
    private void Start()
    {
        int i = 0;
        while (i < 5)
        {
            Debug.Log("While Loop iteration: " + i);
            i++;
        }
    }
}
```

**Do-While Loop Example:**

```csharp
public class DoWhileLoopExample : MonoBehaviour
{
    private void Start()
    {
        int i = 0;
        do
        {
            Debug.Log("Do-While Loop iteration: " + i);
            i++;
        }
        while (i < 5);
    }
}
```

