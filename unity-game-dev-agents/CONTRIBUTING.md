# Contributing to Unity Game Dev Agents

Thank you for your interest in improving the Unity Game Dev Agents collection! This guide will help you contribute effectively.

## 🎯 How to Contribute

### Ways to Contribute

1. **Add New Agents**: Create specialists for uncovered Unity domains
2. **Improve Existing Agents**: Enhance expertise or add examples
3. **Fix Issues**: Correct errors or outdated information
4. **Add Workflows**: Document agent collaboration patterns
5. **Improve Documentation**: Clarify usage or add guides

### Before You Start

- Check existing agents to avoid duplication
- Ensure your contribution uses Unity 6000.1 features
- Test your changes with Claude Code
- Follow the established patterns

## 📝 Agent Contribution Process

### 1. Choose Agent Type

Determine where your agent belongs:

- **Orchestrators** (`agents/orchestrators/`): High-level coordination
- **Core** (`agents/core/`): Cross-cutting concerns
- **Specialized** (`agents/specialized/`): Domain experts
  - `gameplay/`: Game mechanics, AI, physics
  - `graphics/`: Rendering, shaders, VFX
  - `networking/`: Multiplayer, backend
  - `mobile/`: Platform optimization
  - `xr/`: VR/AR development
- **Universal** (`agents/universal/`): Non-Unity specific

### 2. Follow the Format

Use this exact structure:

```yaml
---
name: agent-kebab-case-name
description: |
  Clear description of expertise. MUST BE USED for [specific scenarios].
  
  Examples:
  - <example>
    Context: When to use this agent
    user: "User request example"
    assistant: "I'll use the agent-name for this"
    <commentary>Why this agent was selected</commentary>
  </example>
tools: Tool1, Tool2  # Optional - omit to inherit all
---

# Agent Name

You are a [role] specializing in [expertise] for Unity 6000.1. You [what you do].

## Core Expertise

### Domain Area
- Specific skills
- Unity features
- Best practices

## Implementation Patterns

[Code examples with Unity 6000.1 APIs]

## Integration with Other Agents

- `related-agent`: How you collaborate
```

### 3. Include Quality Examples

Provide working Unity code:

```csharp
// ✅ Good: Complete, working example
public class HealthSystem : MonoBehaviour
{
    [SerializeField] private int maxHealth = 100;
    private int currentHealth;
    
    public event System.Action<int> OnHealthChanged;
    public event System.Action OnDeath;
    
    void Start()
    {
        currentHealth = maxHealth;
    }
    
    public void TakeDamage(int amount)
    {
        currentHealth = Mathf.Max(0, currentHealth - amount);
        OnHealthChanged?.Invoke(currentHealth);
        
        if (currentHealth == 0)
            OnDeath?.Invoke();
    }
}

// ❌ Bad: Incomplete or pseudo-code
class Health {
    // TODO: implement
}
```

### 4. Test Your Agent

Before submitting:

1. Place in correct directory
2. Validate YAML syntax
3. Test with Claude Code
4. Ensure examples compile
5. Check integration with orchestrator

## 🔄 Pull Request Process

### 1. Fork and Branch

```bash
# Fork the repository on GitHub
git clone https://github.com/yourusername/unity-game-dev-agents.git
cd unity-game-dev-agents
git checkout -b add-unity-shader-artist
```

### 2. Make Your Changes

- Add/modify agent files
- Update documentation if needed
- Follow existing patterns

### 3. Commit Guidelines

Write clear commit messages:

```bash
# ✅ Good commits
git commit -m "Add Unity Shader Artist agent for visual effects"
git commit -m "Fix Unity Multiplayer Engineer connection handling"
git commit -m "Update Unity Mobile Developer for iOS 17 support"

# ❌ Bad commits
git commit -m "Update"
git commit -m "Fix stuff"
```

### 4. Submit PR

Include in your PR description:

- **What**: What agent/change you're adding
- **Why**: Why it's needed
- **How**: How it works
- **Testing**: How you tested it

Example PR:

```markdown
## Add Unity Shader Artist Agent

### What
Adds a specialized agent for shader development and visual effects.

### Why
Currently no dedicated shader specialist exists, but shader development 
is a complex domain requiring specific expertise.

### How
- Expert in Shader Graph and HLSL
- Covers all render pipelines
- Includes mobile optimization

### Testing
Tested with:
- Creating water shaders
- Mobile shader optimization
- Custom post-processing effects
```

## 🎨 Style Guidelines

### Language and Tone

- Professional but approachable
- Clear and concise
- Focus on practical solutions
- Avoid unnecessary jargon

### Code Standards

Follow Unity conventions:

```csharp
// ✅ Unity conventions
public class PlayerController : MonoBehaviour
{
    [SerializeField] private float moveSpeed = 5f;
    
    private CharacterController controller;
    
    private void Awake()
    {
        controller = GetComponent<CharacterController>();
    }
}

// ❌ Non-Unity style
public class player_controller : MonoBehaviour
{
    public float MoveSpeed = 5f;
    
    CharacterController cc;
    
    void Start() {
        cc = gameObject.GetComponent<CharacterController>();
    }
}
```

### Documentation

- Use clear headers
- Provide context
- Include examples
- Explain integration

## ✅ Contribution Checklist

Before submitting, ensure:

- [ ] Agent follows exact YAML format
- [ ] Name uses kebab-case convention
- [ ] Description includes routing examples
- [ ] Code uses Unity 6000.1 APIs
- [ ] Examples are complete and working
- [ ] Placed in correct directory
- [ ] Integration points documented
- [ ] Tested with Claude Code

## 🚫 What Not to Do

- Don't duplicate existing agents
- Don't use outdated Unity APIs
- Don't include broken code examples
- Don't forget platform considerations
- Don't skip testing

## 💡 Ideas for Contributions

### Needed Agents

- Unity Shader Artist (VFX, custom shaders)
- Unity Terrain Specialist (world building)
- Unity Localization Expert (multi-language)
- Unity Console Developer (PlayStation, Xbox)
- Unity WebGL Optimizer (browser games)

### Workflow Documentation

- RPG game development workflow
- Racing game optimization workflow
- Battle royale architecture workflow

### Improvements

- Add more examples to existing agents
- Update for new Unity features
- Add platform-specific optimizations

## 🙋 Getting Help

If you need help:

1. Check existing agents for patterns
2. Review documentation
3. Open an issue for discussion
4. Ask in PR comments

## 🎉 Recognition

Contributors will be:
- Listed in agent metadata
- Mentioned in release notes
- Part of the Unity game dev community

Thank you for helping make Unity game development with AI better! 🎮