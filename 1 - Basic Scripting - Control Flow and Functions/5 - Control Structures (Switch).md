

## Switch Statements
Switch statements allow you to select one of many code blocks to be executed.

**Example:**

```csharp

public class SwitchStatementExample : MonoBehaviour
{
	int playerLevel = 3;
	
    private void Start()
    {
		switch (playerLevel)
		{
		    case 1:
		        // Code for level 1
		        break;
		    case 2:
		        // Code for level 2
		        break;
		    case 3:
		        // Code for level 3
		        break;
		    case 4:
		        // Code for level 4
		        break;
		    default:
		        // Code for unknown levels
		        break;
		}

        Debug.Log("Level: " + playerLevel);
    }
}
```
