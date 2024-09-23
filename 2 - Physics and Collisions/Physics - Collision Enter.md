
### Physics: OnCollisionEnter

In Unity, the `OnCollisionEnter` method is used to detect collisions between two GameObjects with Rigidbody components. This method is called automatically when two colliders come into contact, allowing you to respond to physical interactions in your game, such as when a player hits a wall or an object.

To use `OnCollisionEnter`, ensure that at least one of the colliding objects has a `Rigidbody` component, and both objects must have colliders.

#### Example: Detecting Collisions

```csharp
using UnityEngine;

public class CollisionExample : MonoBehaviour
{
    // This method is called when this GameObject collides with another GameObject
    private void OnCollisionEnter(Collision collision)
    {
        // Log the name of the GameObject we collided with
        Debug.Log("Collided with: " + collision.gameObject.name);

        // Access the collision point and other details
        foreach (ContactPoint contact in collision.contacts)
        {
            Debug.Log("Collision Point: " + contact.point);
        }

        // Apply logic based on the object collided with
        if (collision.gameObject.tag == "Enemy")
        {
            Debug.Log("Hit an enemy!");
            // Example: Apply damage or destroy the enemy
        }
    }
}
```

#### Key Components of `OnCollisionEnter`:

1. **Collision Parameter**: The `Collision` object contains information about the collision, including:
   - `collision.gameObject`: The GameObject that collided with the current one.
   - `collision.contacts`: An array of `ContactPoint` objects that describe where the colliders touched.
   - `collision.relativeVelocity`: The relative speed of the collision.

2. **Tag-Based Detection**: Use `collision.gameObject.tag` to check for specific types of objects (e.g., "Enemy", "Wall", "PowerUp"). This is helpful for applying game logic based on what was hit.

3. **Rigidbody Requirement**: One or both of the GameObjects involved must have a `Rigidbody` component for `OnCollisionEnter` to trigger.

4. **Collider Requirement**: Both GameObjects must have some form of collider (BoxCollider, SphereCollider, etc.).

#### Example: Bouncing Off Walls

You can create specific behavior, such as making an object bounce off a wall or responding to damage by using logic inside `OnCollisionEnter`:

```csharp
using UnityEngine;

public class BallBounce : MonoBehaviour
{
    private Rigidbody rb;

    private void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    private void OnCollisionEnter(Collision collision)
    {
        // Check if the object collided with is tagged as "Wall"
        if (collision.gameObject.tag == "Wall")
        {
            // Invert the velocity to simulate a bounce
            Vector3 bounce = Vector3.Reflect(rb.velocity, collision.contacts[0].normal);
            rb.velocity = bounce;
        }
    }
}
```

### Key Points

- **OnCollisionEnter** is called when two colliders touch, at least one of which has a `Rigidbody`.
- The `Collision` object provides useful information like the contact points, the object collided with, and the relative speed.
- Use tags to differentiate between various objects and apply specific behaviors.
- Physics behaviors such as bouncing can be handled by manipulating the `Rigidbody` velocity after a collision.

This method is essential for creating interactions between objects in Unity’s physics system, such as detecting hits, triggering effects, or simulating responses like bouncing or destruction.
