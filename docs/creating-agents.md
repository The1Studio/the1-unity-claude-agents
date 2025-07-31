# Creating Unity Game Dev Agents

This guide explains how to create new agents for the Unity Game Dev Agents collection.

## Agent Structure

Every agent must follow this exact structure:

```yaml
---
name: agent-name
description: |
  Agent expertise description with routing examples.
  
  Examples:
  - <example>
    Context: When this agent should be used
    user: "User request"
    assistant: "I'll use the agent-name to handle this"
    <commentary>Why this agent was selected</commentary>
  </example>
tools: Tool1, Tool2  # Optional - omit to inherit all tools
---

# Agent Name

Agent system prompt and expertise details...
```

## YAML Frontmatter

The frontmatter contains metadata used by Claude Code for agent routing:

### Required Fields

- **name**: Kebab-case identifier (e.g., `unity-shader-developer`)
- **description**: Multi-line description with routing examples

### Optional Fields

- **tools**: Comma-separated list of tools (omit to inherit all)

## Description Examples

The description MUST include XML-formatted examples showing when to use the agent:

```yaml
description: |
  Unity shader programming expert specializing in Shader Graph and HLSL. MUST BE USED for shader development, visual effects programming, or render pipeline customization.
  
  Examples:
  - <example>
    Context: Custom shader needed
    user: "Create a water shader with foam"
    assistant: "I'll use the unity-shader-developer to create this shader"
    <commentary>Shader development requires specialized knowledge</commentary>
  </example>
```

## Agent Categories

Place your agent in the appropriate directory:

### Orchestrators (`agents/orchestrators/`)
High-level coordination agents that manage workflows:
- Must have complex routing logic
- Coordinate multiple specialists
- Return structured findings

### Core (`agents/core/`)
Cross-cutting concerns that apply to all Unity projects:
- Performance optimization
- Code quality
- Build processes
- Documentation

### Specialized (`agents/specialized/`)
Domain-specific experts organized by area:
- `gameplay/` - Game mechanics, AI, physics
- `graphics/` - Rendering, shaders, VFX
- `networking/` - Multiplayer, backend
- `mobile/` - Platform-specific optimization
- `xr/` - VR/AR development

### Universal (`agents/universal/`)
Game development roles not specific to Unity:
- Game design
- Level design
- Audio design
- UI/UX design

## Writing the System Prompt

The system prompt (content after the frontmatter) should include:

### 1. Identity Statement
```markdown
You are a [specific role] specializing in [expertise areas] for Unity 6000.1. You [what you do].
```

### 2. Expertise Sections
```markdown
## Core Expertise

### Domain Area 1
- Specific skill
- Unity feature knowledge
- Best practices

### Domain Area 2
- Technical capabilities
- Tool proficiency
- Platform awareness
```

### 3. Code Examples
```markdown
## Implementation Patterns

### Pattern Name
```csharp
// Working Unity 6000.1 code example
public class Example : MonoBehaviour
{
    // Implementation
}
```
```

### 4. Best Practices
```markdown
## Best Practices

1. **Principle**: Explanation
2. **Unity-Specific**: Platform considerations
3. **Performance**: Optimization guidelines
```

### 5. Integration Points
```markdown
## Integration with Other Agents

- `related-agent-1`: How you collaborate
- `related-agent-2`: Hand-off patterns
```

## Unity-Specific Requirements

All agents must:

1. **Use Unity 6000.1 APIs**: Reference current Unity features
2. **Include Platform Considerations**: Mobile, VR, console differences
3. **Follow Unity Conventions**: Component patterns, prefabs, etc.
4. **Consider Performance**: Frame rate, memory, battery
5. **Provide Working Code**: Examples must compile

## Example: Creating a Shader Developer Agent

```yaml
---
name: unity-shader-developer
description: |
  Unity shader programming expert specializing in Shader Graph, HLSL, and render pipeline customization. MUST BE USED for custom shaders, visual effects programming, or advanced rendering techniques.
  
  Examples:
  - <example>
    Context: Custom visual effect needed
    user: "Create a hologram shader"
    assistant: "I'll use the unity-shader-developer to create the hologram effect"
    <commentary>Shader programming requires specialized expertise</commentary>
  </example>
---

# Unity Shader Developer

You are a Unity shader programming expert specializing in creating high-performance shaders for Unity 6000.1 across all render pipelines.

## Core Expertise

### Shader Languages
- Shader Graph visual programming
- HLSL shader code
- Surface shader syntax
- Compute shaders
- Shader variants and keywords

### Render Pipelines
- Universal Render Pipeline (URP)
- High Definition Render Pipeline (HDRP)
- Built-in pipeline compatibility
- Custom render features

## Implementation Examples

### URP Lit Shader Template
```hlsl
Shader "Custom/URPLitExample"
{
    Properties
    {
        _BaseMap ("Base Map", 2D) = "white" {}
        _BaseColor ("Base Color", Color) = (1,1,1,1)
    }
    
    SubShader
    {
        Tags { "RenderPipeline"="UniversalPipeline" }
        
        Pass
        {
            Name "ForwardLit"
            Tags { "LightMode"="UniversalForward" }
            
            HLSLPROGRAM
            #pragma vertex vert
            #pragma fragment frag
            
            #include "Packages/com.unity.render-pipelines.universal/ShaderLibrary/Core.hlsl"
            
            // Vertex and fragment shaders...
            ENDHLSL
        }
    }
}
```

## Best Practices

1. **Performance First**: Mobile GPU limitations
2. **Variant Reduction**: Minimize shader permutations
3. **Precision Control**: Use appropriate float precision
4. **Batching Friendly**: Enable GPU instancing

## Integration Points

- `unity-graphics-programmer`: Rendering system integration
- `unity-technical-artist`: Shader tool development
- `unity-mobile-graphics-optimizer`: Mobile shader optimization
```

## Testing Your Agent

Before submitting:

1. **Syntax Check**: Ensure valid YAML frontmatter
2. **Code Validation**: Examples must be valid Unity code
3. **Integration Test**: Works with orchestrator routing
4. **Documentation**: Clear expertise boundaries

## Quality Checklist

- [ ] Follows exact YAML format
- [ ] Includes routing examples
- [ ] Uses Unity 6000.1 features
- [ ] Provides working code
- [ ] Considers all platforms
- [ ] Integrates with other agents
- [ ] Follows naming conventions

## Submission Process

1. Create agent in appropriate category
2. Test with sample Unity project
3. Ensure orchestrator can route to it
4. Submit PR with description
5. Include usage examples