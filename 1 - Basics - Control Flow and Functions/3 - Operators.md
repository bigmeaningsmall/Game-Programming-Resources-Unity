
#### 3. Operators
Operators are symbols that tell the compiler to perform specific mathematical, relational, or logical operations and produce a result.

**Common Operators:**
### Common Operators

#### Arithmetic Operators
- `+` (Addition)
- `-` (Subtraction)
- `*` (Multiplication)
- `/` (Division)
- `%` (Modulus)

#### Assignment Operators
- `=` (Assignment)
- `+=` (Addition Assignment)
- `-=` (Subtraction Assignment)
- `*=` (Multiplication Assignment)
- `/=` (Division Assignment)
- `%=` (Modulus Assignment)

#### Comparison Operators
- `==` (Equal to)
- `!=` (Not equal to)
- `>` (Greater than)
- `<` (Less than)
- `>=` (Greater than or equal to)
- `<=` (Less than or equal to)

#### Logical Operators
- `&&` (Logical AND)
- `||` (Logical OR)
- `!` (Logical NOT)

**Example:**

```csharp
public class OperatorExample : MonoBehaviour
{
    private void Start()
    {
        // Arithmetic operators
        int a = 10;
        int b = 3;
        int sum = a + b;
        int difference = a - b;
        int product = a * b;
        int quotient = a / b;
        int remainder = a % b;

        Debug.Log("Sum: " + sum);
        Debug.Log("Difference: " + difference);
        Debug.Log("Product: " + product);
        Debug.Log("Quotient: " + quotient);
        Debug.Log("Remainder: " + remainder);

        // Comparison operators
        bool isEqual = (a == b);
        bool isNotEqual = (a != b);
        bool isGreater = (a > b);
        bool isLess = (a < b);
        bool isGreaterOrEqual = (a >= b);
        bool isLessOrEqual = (a <= b);

        Debug.Log("Is Equal: " + isEqual);
        Debug.Log("Is Not Equal: " + isNotEqual);
        Debug.Log("Is Greater: " + isGreater);
        Debug.Log("Is Less: " + isLess);
        Debug.Log("Is Greater Or Equal: " + isGreaterOrEqual);
        Debug.Log("Is Less Or Equal: " + isLessOrEqual);

        // Logical operators
        bool andOperator = (a > 5 && b < 5);
        bool orOperator = (a > 5 || b > 5);
        bool notOperator = !(a > 5);

        Debug.Log("AND Operator: " + andOperator);
        Debug.Log("OR Operator: " + orOperator);
        Debug.Log("NOT Operator: " + notOperator);
    }
}
```

These examples cover the basics of variables, data types, and operators in Unity C#. They provide a foundation for students to understand how to store, manipulate, and evaluate data within their scripts.
