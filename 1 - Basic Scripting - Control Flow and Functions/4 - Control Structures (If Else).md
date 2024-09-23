
### Control Structures

#### If Statements
If statements allow you to execute a block of code based on a condition.

**Examples:**
##### Example 1: Basic If Statement
```csharp
using UnityEngine;

public class IfStatementExample1 : MonoBehaviour
{

	int health = 100;

    private void Start()
    {
        if (health > 0)
        {
            // Code to continue the game
            Debug.Log("Game continues. Health is greater than 0.");
        }
    }
}
```

##### Example 2: If-Else If Statement
```csharp
using UnityEngine;

public class IfStatementExample2 : MonoBehaviour
{
	int health = 100;
	
    private void Start()
    {
        if (health > 70)
        {
            // Code for 'Healthy' status
            Debug.Log("Status: Healthy");
        }
        else if (health > 30)
        {
            // Code for 'Injured' status
            Debug.Log("Status: Injured");
        }
    }
}
```

##### Example 3: If-Else If-Else Statement
```csharp
using UnityEngine;

public class IfStatementExample3 : MonoBehaviour
{

	int health = 100;
	
    private void Start()
    {
        if (health > 70)
        {
            // Code for 'Healthy' status
            Debug.Log("Status: Healthy");
        }
        else if (health > 30)
        {
            // Code for 'Injured' status
            Debug.Log("Status: Injured");
        }
        else
        {
            // Code for 'Critical' status
            Debug.Log("Status: Critical");
        }
    }
}
```



