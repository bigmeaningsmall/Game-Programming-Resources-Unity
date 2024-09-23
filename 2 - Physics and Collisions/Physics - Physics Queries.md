
### Physics: Physics Queries in Unity

Physics queries in Unity allow you to detect objects and their properties within a specific area or along a defined path. Unlike raycasting, which shoots a single ray in a direction, physics queries such as **OverlapSphere**, **OverlapBox**, and **OverlapCapsule** let you define areas and volumes to detect all objects within them. These are useful for proximity detection, area-of-effect abilities, or identifying objects in a defined region.

Physics queries come in two main forms: **3D Physics Queries** and **2D Physics Queries**. Each has its own variants for specific shapes and areas.

### 3D Physics Queries

#### OverlapSphere

The `Physics.OverlapSphere` query detects all colliders within a spherical area. This is useful for proximity-based checks (e.g., detecting nearby enemies, area-of-effect spells, or objects within a specific range).

```csharp
using UnityEngine;

public class OverlapSphereExample : MonoBehaviour
{
    public float detectionRadius = 5f;

    void Update()
    {
        Vector3 center = transform.position;
        Collider[] hitColliders = Physics.OverlapSphere(center, detectionRadius);
        foreach (Collider hitCollider in hitColliders)
        {
            Debug.Log("Detected object: " + hitCollider.gameObject.name);
        }
    }
}
```

- **Parameters**:
  - `center`: The center of the sphere.
  - `radius`: The radius of the sphere.
  - `layerMask` (optional): Filter the query to specific layers.
  - `queryTriggerInteraction` (optional): Whether to include or ignore trigger colliders.

#### OverlapBox

The `Physics.OverlapBox` query detects all colliders within a box-shaped volume. This is useful for defining a rectangular detection area (e.g., melee weapon hits, detecting objects within a zone).

```csharp
using UnityEngine;

public class OverlapBoxExample : MonoBehaviour
{
    public Vector3 boxSize = new Vector3(2f, 2f, 2f);

    void Update()
    {
        Vector3 center = transform.position;
        Collider[] hitColliders = Physics.OverlapBox(center, boxSize / 2);
        foreach (Collider hitCollider in hitColliders)
        {
            Debug.Log("Detected object: " + hitCollider.gameObject.name);
        }
    }
}
```

- **Parameters**:
  - `center`: The center of the box.
  - `halfExtents`: The half-size of the box along each axis (i.e., half the full size).
  - `orientation` (optional): The rotation of the box.
  - `layerMask` (optional): Filter the query to specific layers.

#### OverlapCapsule

The `Physics.OverlapCapsule` query detects all colliders within a capsule-shaped volume. It is useful for detecting objects in areas such as character bodies or elongated objects.

```csharp
using UnityEngine;

public class OverlapCapsuleExample : MonoBehaviour
{
    public float height = 2f;
    public float radius = 1f;

    void Update()
    {
        Vector3 point1 = transform.position + Vector3.up * height / 2;
        Vector3 point2 = transform.position - Vector3.up * height / 2;
        Collider[] hitColliders = Physics.OverlapCapsule(point1, point2, radius);
        foreach (Collider hitCollider in hitColliders)
        {
            Debug.Log("Detected object: " + hitCollider.gameObject.name);
        }
    }
}
```

- **Parameters**:
  - `point1`: The first endpoint of the capsule.
  - `point2`: The second endpoint of the capsule.
  - `radius`: The radius of the capsule.
  - `layerMask` (optional): Filter the query to specific layers.

### 2D Physics Queries

Unity’s 2D physics system provides similar physics queries, but tailored for 2D space.

#### OverlapCircle2D

The `Physics2D.OverlapCircle` query detects all 2D colliders within a circular area. This is the 2D equivalent of `OverlapSphere`.

```csharp
using UnityEngine;

public class OverlapCircle2DExample : MonoBehaviour
{
    public float detectionRadius = 5f;

    void Update()
    {
        Vector2 center = transform.position;
        Collider2D[] hitColliders = Physics2D.OverlapCircleAll(center, detectionRadius);
        foreach (Collider2D hitCollider in hitColliders)
        {
            Debug.Log("Detected 2D object: " + hitCollider.gameObject.name);
        }
    }
}
```

- **Parameters**:
  - `point`: The center of the circle.
  - `radius`: The radius of the circle.
  - `layerMask` (optional): Filter the query to specific layers.

#### OverlapBox2D

The `Physics2D.OverlapBox` query detects all 2D colliders within a box-shaped area. It’s ideal for detecting rectangular regions in 2D games.

```csharp
using UnityEngine;

public class OverlapBox2DExample : MonoBehaviour
{
    public Vector2 boxSize = new Vector2(2f, 2f);

    void Update()
    {
        Vector2 center = transform.position;
        Collider2D[] hitColliders = Physics2D.OverlapBoxAll(center, boxSize, 0f); // No rotation
        foreach (Collider2D hitCollider in hitColliders)
        {
            Debug.Log("Detected 2D object: " + hitCollider.gameObject.name);
        }
    }
}
```

- **Parameters**:
  - `point`: The center of the box.
  - `size`: The dimensions of the box.
  - `angle` (optional): The rotation of the box in degrees.

### Advanced Physics Queries

#### Raycasting with Overlap Queries

You can combine raycasting and overlap queries to narrow down detections to objects within a defined area and along a path. For example, you can first perform an `OverlapSphere` to detect nearby objects and then use `Raycast` to determine line-of-sight.

#### Layer Filtering with Queries

Just like raycasts, all physics queries support **LayerMask** filtering. This is especially useful for limiting which objects should be detected, such as detecting only enemies or interactable objects:

```csharp
LayerMask layerMask = LayerMask.GetMask("Enemies", "Interactables");
Collider[] hitColliders = Physics.OverlapSphere(center, detectionRadius, layerMask);
```

#### Physics Queries and Trigger Colliders

By default, physics queries will include both trigger and non-trigger colliders. You can control this with the `QueryTriggerInteraction` option, which lets you include or exclude triggers in the query:

```csharp
Collider[] hitColliders = Physics.OverlapSphere(center, detectionRadius, layerMask, QueryTriggerInteraction.Ignore);
```

### Best Practices

1. **Optimize Performance**: Physics queries like `OverlapSphere` and `OverlapBox` can be performance-intensive, especially if used frequently in large scenes. Only use them when necessary, and consider limiting queries with `LayerMask` and `QueryTriggerInteraction`.
2. **Bounding Volumes**: Consider the size and shape of the bounding volume for your query. Use the smallest volume necessary to reduce unnecessary checks.
3. **Collision Detection**: Physics queries are useful for more than just detecting objects—they can also be used for dynamic collision detection, determining which objects are in an area before applying effects like explosions or damage.

---

### Key Points

- **Physics queries** are essential for detecting objects within a defined area, such as spherical, box-shaped, or capsule-shaped volumes.
- Use `Physics.OverlapSphere`, `Physics.OverlapBox`, and `Physics.OverlapCapsule` for 3D queries, and their 2D equivalents (`OverlapCircle2D`, `OverlapBox2D`) for 2D games.
- Physics queries return an array of colliders that can be iterated over to detect multiple objects in the area.
- Combine queries with **LayerMask** to filter objects based on layers and **QueryTriggerInteraction** to include or exclude triggers.
- Physics queries are useful for proximity detection, area-of-effect damage, melee combat detection, and more.
