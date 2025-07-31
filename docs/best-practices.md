# Unity Game Dev Agents Best Practices

This guide outlines best practices for using and developing Unity Game Dev Agents.

## Using Agents Effectively

### 1. Always Start with the Orchestrator

For any multi-step task, begin with `unity-tech-lead-orchestrator`:

```
❌ Wrong: "unity-gameplay-programmer, implement multiplayer"
✅ Right: "Implement multiplayer for my racing game"
         (Tech lead will coordinate multiple specialists)
```

### 2. Provide Context

Agents work best with clear context about your Unity project:

```
❌ Vague: "Optimize my game"
✅ Clear: "Optimize my mobile puzzle game running at 20 FPS on iPhone 12"
```

### 3. Let Agents Collaborate

Don't try to assign specialists manually. The orchestrator knows optimal routing:

```
❌ Manual: "Use unity-graphics-programmer for shaders, then unity-mobile-developer"
✅ Auto: "Create a stylized water effect for mobile"
         (Orchestrator routes to appropriate specialists)
```

## Unity Development Standards

### 1. Unity Version Compatibility

All agents assume Unity 6000.1 (Unity 6) features:

```csharp
// ✅ Unity 6 Awaitable API
private async Awaitable DelayAsync()
{
    await Awaitable.WaitForSecondsAsync(1f);
}

// ❌ Older Unity coroutine pattern
private IEnumerator DelayCoroutine()
{
    yield return new WaitForSeconds(1f);
}
```

### 2. Platform Awareness

Always consider target platforms:

```csharp
public class PlatformOptimizedRenderer : MonoBehaviour
{
    void Start()
    {
        #if UNITY_IOS || UNITY_ANDROID
        QualitySettings.vSyncCount = 0;
        Application.targetFrameRate = 30;
        #else
        Application.targetFrameRate = 60;
        #endif
    }
}
```

### 3. Performance Budget

Follow platform-specific performance targets:

| Platform | Target FPS | Draw Calls | Triangles |
|----------|------------|------------|-----------|
| Mobile   | 30-60      | <100       | <100k     |
| VR       | 72-90      | <50        | <50k      |
| PC       | 60+        | <1000      | <1M       |

## Code Quality Standards

### 1. Component Architecture

Use Unity's component-based design:

```csharp
// ✅ Good: Modular components
public class PlayerHealth : MonoBehaviour { }
public class PlayerMovement : MonoBehaviour { }
public class PlayerInventory : MonoBehaviour { }

// ❌ Bad: Monolithic player class
public class Player : MonoBehaviour 
{
    // Health logic
    // Movement logic  
    // Inventory logic
}
```

### 2. ScriptableObject Usage

Leverage ScriptableObjects for data:

```csharp
// ✅ Data-driven design
[CreateAssetMenu(menuName = "Game/Enemy")]
public class EnemyData : ScriptableObject
{
    public float health;
    public float speed;
    public GameObject prefab;
}

// ❌ Hardcoded values
public class Enemy : MonoBehaviour
{
    private float health = 100f; // Hardcoded
    private float speed = 5f;    // Hardcoded
}
```

### 3. Object Pooling

Always pool frequently instantiated objects:

```csharp
// ✅ Pooled projectiles
public class ProjectilePool : MonoBehaviour
{
    private Queue<Projectile> pool = new Queue<Projectile>();
    
    public Projectile Get()
    {
        if (pool.Count > 0)
            return pool.Dequeue();
        return Instantiate(projectilePrefab);
    }
}

// ❌ Instantiate/Destroy pattern
void Fire()
{
    var bullet = Instantiate(bulletPrefab);
    Destroy(bullet, 2f); // Bad for performance
}
```

## Optimization Guidelines

### 1. Profile First

Never optimize without profiling:

```csharp
// Use Unity Profiler markers
using Unity.Profiling;

public class GameSystem : MonoBehaviour
{
    static readonly ProfilerMarker s_UpdateMarker = new ProfilerMarker("GameSystem.Update");
    
    void Update()
    {
        using (s_UpdateMarker.Auto())
        {
            // Code to profile
        }
    }
}
```

### 2. Mobile-First Development

Design for mobile constraints:

```csharp
public class MobileOptimizedEffect : MonoBehaviour
{
    [SerializeField] private ParticleSystem particles;
    
    void Start()
    {
        #if UNITY_IOS || UNITY_ANDROID
        // Reduce particle count for mobile
        var main = particles.main;
        main.maxParticles = 50;
        
        // Disable expensive features
        var collision = particles.collision;
        collision.enabled = false;
        #endif
    }
}
```

### 3. Texture Optimization

Follow platform-specific texture guidelines:

| Platform | Format    | Max Size | Compression |
|----------|-----------|----------|-------------|
| iOS      | ASTC 6x6  | 2048     | High        |
| Android  | ASTC 6x6  | 2048     | High        |
| PC       | DXT5      | 4096     | Normal      |

## Multiplayer Best Practices

### 1. Server Authority

Always validate on server:

```csharp
[ServerRpc]
void MoveServerRpc(Vector3 newPosition)
{
    // ✅ Validate movement on server
    if (IsValidPosition(newPosition))
    {
        transform.position = newPosition;
    }
    
    // ❌ Never trust client directly
    // transform.position = newPosition;
}
```

### 2. Network Optimization

Minimize network traffic:

```csharp
// ✅ Send only when changed
if (Vector3.Distance(lastSentPos, currentPos) > 0.1f)
{
    SendPositionUpdate(currentPos);
    lastSentPos = currentPos;
}

// ❌ Send every frame
void Update()
{
    SendPositionUpdate(transform.position); // Too frequent
}
```

## Asset Pipeline

### 1. Folder Structure

Maintain clean project organization:

```
Assets/
├── _Project/          # Your project files
│   ├── Scripts/
│   ├── Prefabs/
│   └── Materials/
├── _ThirdParty/       # External assets
└── StreamingAssets/   # Runtime loaded content
```

### 2. Naming Conventions

Use consistent naming:

- **Scripts**: PascalCase (PlayerController.cs)
- **Prefabs**: PascalCase (PlayerCharacter.prefab)
- **Materials**: PascalCase_Purpose (Metal_Shiny.mat)
- **Textures**: PascalCase_Type (Metal_Albedo.png)

### 3. Assembly Definitions

Organize code with assembly definitions:

```json
{
    "name": "Game.Gameplay",
    "references": ["Game.Core", "Unity.Netcode.Runtime"],
    "includePlatforms": [],
    "excludePlatforms": [],
    "allowUnsafeCode": false
}
```

## Testing Practices

### 1. Unity Test Framework

Write tests for game logic:

```csharp
[Test]
public void PlayerTakesDamage_HealthDecreases()
{
    var player = new GameObject().AddComponent<PlayerHealth>();
    player.Initialize(100);
    
    player.TakeDamage(30);
    
    Assert.AreEqual(70, player.CurrentHealth);
}
```

### 2. Integration Testing

Test in real scenarios:

```csharp
[UnityTest]
public IEnumerator PlayerMovement_ReachesDestination()
{
    var player = Object.Instantiate(playerPrefab);
    var movement = player.GetComponent<PlayerMovement>();
    
    movement.MoveTo(new Vector3(10, 0, 0));
    
    yield return new WaitForSeconds(2f);
    
    Assert.AreEqual(10f, player.transform.position.x, 0.1f);
}
```

## Documentation Standards

### 1. Code Documentation

Document complex systems:

```csharp
/// <summary>
/// Manages player inventory with stack support and weight limits.
/// </summary>
/// <remarks>
/// Uses ScriptableObject items for data-driven design.
/// Supports save/load through JSON serialization.
/// </remarks>
public class InventorySystem : MonoBehaviour
{
    /// <summary>
    /// Adds an item to the inventory if space available.
    /// </summary>
    /// <param name="item">Item to add</param>
    /// <param name="quantity">Amount to add</param>
    /// <returns>True if successfully added</returns>
    public bool AddItem(ItemData item, int quantity) { }
}
```

### 2. Architecture Documentation

Document system interactions:

```markdown
## Save System Architecture

The save system uses a three-layer approach:

1. **Data Layer**: ScriptableObjects define saveable data
2. **Serialization Layer**: JSON conversion with Unity.JsonUtility
3. **Storage Layer**: Platform-specific file I/O

### Data Flow
Player Action → SaveManager → Serializer → FileSystem
```

## Performance Monitoring

### 1. Runtime Metrics

Monitor key metrics:

```csharp
public class PerformanceMonitor : MonoBehaviour
{
    void OnGUI()
    {
        GUILayout.Label($"FPS: {1f / Time.deltaTime:F1}");
        GUILayout.Label($"Draw Calls: {UnityStats.drawCalls}");
        GUILayout.Label($"Heap: {System.GC.GetTotalMemory(false) / 1048576}MB");
    }
}
```

### 2. Build-Time Validation

Validate before building:

```csharp
[InitializeOnLoad]
public class BuildValidator
{
    static BuildValidator()
    {
        BuildPlayerWindow.RegisterBuildPlayerHandler(OnBuild);
    }
    
    static void OnBuild(BuildPlayerOptions options)
    {
        // Check texture sizes
        // Validate quality settings
        // Ensure optimization flags
    }
}
```

## Summary

Following these best practices ensures:
- High-performance Unity games
- Maintainable codebases
- Smooth multiplayer experiences
- Optimal player experience across platforms

Remember: The agents embody these practices and will guide you toward them naturally.