
### Physics: Raycasting in Unity

Raycasting is a powerful technique in Unity’s physics system that involves shooting an invisible ray (or line) from a point in space and detecting what it hits. It’s widely used for interactions such as detecting objects, line-of-sight calculations, shooting mechanics, or even determining the surface a character is standing on.

Raycasting is versatile, with versions available for both 3D and 2D physics.

#### Why Use Raycasting?

- **Line-of-sight checks**: Ensure that an object is visible or unobstructed from a particular viewpoint.
- **Interaction detection**: Detect when the player is aiming at or interacting with specific objects.
- **Physics-based interactions**: Handle more realistic object interactions such as shooting or targeting.
- **Ground detection**: Determine if a character is standing on the ground or near a ledge.

#### Basic 3D Raycasting

A simple raycast shoots an invisible ray from a starting point in a direction. If the ray hits an object, you can detect information about the object, such as its name, position, and distance from the ray’s origin.

```csharp
using UnityEngine;

public class RaycastExample : MonoBehaviour
{
    void Update()
    {
        // Define the starting point (the object's current position) and direction (forward)
        Vector3 origin = transform.position;
        Vector3 direction = transform.forward;
        float maxDistance = 100f;

        // Perform the raycast
        if (Physics.Raycast(origin, direction, out RaycastHit hit, maxDistance))
        {
            // Log the name of the object hit
            Debug.Log("Hit: " + hit.collider.gameObject.name);

            // Get additional information about the hit, such as distance and hit point
            Debug.Log("Hit Distance: " + hit.distance);
            Debug.Log("Hit Point: " + hit.point);
        }
    }
}
```

#### RaycastHit Object

When a ray hits an object, the `RaycastHit` object provides details about the hit:
- `hit.collider`: The collider that was hit.
- `hit.point`: The world position where the ray hit the object.
- `hit.normal`: The surface normal at the hit point (useful for determining angles of impact).
- `hit.distance`: The distance from the ray’s origin to the hit point.

#### Ignoring Specific Layers

You can perform raycasting that ignores certain layers of objects by using a **LayerMask**.

```csharp
LayerMask mask = LayerMask.GetMask("IgnoreLayer");
if (Physics.Raycast(origin, direction, out RaycastHit hit, maxDistance, ~mask))
{
    Debug.Log("Hit object: " + hit.collider.gameObject.name);
}
```

#### 2D Raycasting

Raycasting also works in Unity’s 2D physics system, using the `Physics2D.Raycast` function. This is useful for 2D games that involve detecting objects in 2D space.

```csharp
using UnityEngine;

public class Raycast2DExample : MonoBehaviour
{
    void Update()
    {
        // Perform the 2D raycast
        RaycastHit2D hit = Physics2D.Raycast(transform.position, Vector2.right);

        // If a 2D object was hit
        if (hit.collider != null)
        {
            Debug.Log("Hit 2D Object: " + hit.collider.gameObject.name);
        }
    }
}
```

#### Multiple Raycast Hits (RaycastAll)

You can detect multiple objects along a ray’s path using `Physics.RaycastAll`. This returns an array of `RaycastHit` objects for all the objects hit by the ray.

```csharp
RaycastHit[] hits = Physics.RaycastAll(origin, direction, maxDistance);
foreach (RaycastHit hit in hits)
{
    Debug.Log("Hit: " + hit.collider.gameObject.name);
}
```

#### Raycasting with Layers

By specifying a **LayerMask**, you can restrict raycasts to interact only with certain layers, filtering out unwanted objects.

```csharp
LayerMask layerMask = LayerMask.GetMask("Enemies", "Walls");

if (Physics.Raycast(origin, direction, out RaycastHit hit, maxDistance, layerMask))
{
    Debug.Log("Hit: " + hit.collider.gameObject.name);
}
```

#### Raycasting from the Camera

A common use case for raycasting is shooting rays from the camera (for example, detecting what the player is aiming at or clicking on). This is typically done using `Camera.main.ScreenPointToRay` to convert screen coordinates (e.g., a mouse click) into a ray.

```csharp
void Update()
{
    if (Input.GetMouseButtonDown(0)) // Left mouse click
    {
        Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

        if (Physics.Raycast(ray, out RaycastHit hit))
        {
            Debug.Log("Clicked on: " + hit.collider.gameObject.name);
        }
    }
}
```

#### Raycast Variants

1. **Physics.RaycastNonAlloc**:
   - More performance-friendly, this version fills an array of RaycastHit objects without allocating new memory.
   
   ```csharp
   RaycastHit[] results = new RaycastHit[10];
   int hits = Physics.RaycastNonAlloc(origin, direction, results, maxDistance);
   for (int i = 0; i < hits; i++)
   {
       Debug.Log("Hit: " + results[i].collider.gameObject.name);
   }
   ```

2. **SphereCast**:
   - Similar to raycasting, but with a radius. This checks for objects along the path of a sphere moving in a direction, which is useful for more forgiving object detection (e.g., detecting nearby objects).
   
   ```csharp
   float radius = 1f;
   if (Physics.SphereCast(origin, radius, direction, out RaycastHit hit, maxDistance))
   {
       Debug.Log("Sphere hit: " + hit.collider.gameObject.name);
   }
   ```

3. **BoxCast**:
   - Casts a box along a ray, useful for detecting larger areas or objects.

   ```csharp
   Vector3 halfExtents = new Vector3(1f, 1f, 1f);
   if (Physics.BoxCast(origin, halfExtents, direction, out RaycastHit hit, Quaternion.identity, maxDistance))
   {
       Debug.Log("Box hit: " + hit.collider.gameObject.name);
   }
   ```

4. **CapsuleCast**:
   - Similar to SphereCast, but shaped like a capsule, useful for characters or elongated objects.

   ```csharp
   Vector3 point1 = transform.position;
   Vector3 point2 = transform.position + Vector3.up * 2f;
   float radius = 0.5f;
   if (Physics.CapsuleCast(point1, point2, radius, direction, out RaycastHit hit, maxDistance))
   {
       Debug.Log("Capsule hit: " + hit.collider.gameObject.name);
   }
   ```

---

### Key Points

- **Raycasting** allows you to shoot an invisible ray from a point and detect what it hits, providing information such as distance, hit point, and object details.
- Raycasting can be used for detecting objects, player interactions, shooting mechanics, line-of-sight checks, and more.
- There are various raycasting methods, including 2D raycasting, multiple hits with `RaycastAll`, and specialized casts like `SphereCast` and `BoxCast`.
- Raycasting from the camera (e.g., detecting mouse clicks) is common in first-person shooters and UI interactions.
- Use **LayerMask** to limit raycasts to specific layers, ignoring unwanted objects.
