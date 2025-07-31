# Contributing to Unity Game Dev Agents

Thank you for your interest in contributing to Unity Game Dev Agents! This project aims to create the most comprehensive collection of Unity-specific AI agents for game development.

## 🚀 Quick Start for Contributors

### Setting Up Development Environment

1. **Fork and Clone**
   ```bash
   git clone https://github.com/your-username/unity-game-dev-agents.git
   cd unity-game-dev-agents
   ```

2. **Test with Claude Code**
   ```bash
   # Copy CLAUDE.md to a Unity project for testing
   cp CLAUDE.md /path/to/your/unity/project/
   ```

3. **Verify Agent Functionality**
   Open Claude Code in your Unity project and test new agents with Unity-specific tasks.

## 🎯 Types of Contributions

### 1. New Unity Agents
Create specialized agents for Unity development domains:
- **Gameplay Systems**: Inventory, combat, progression
- **Platform Specialists**: Console, WebGL, specific mobile devices
- **Tools & Pipeline**: Asset pipeline, build optimization
- **Emerging Tech**: Unity ML-Agents, Cloud Build, etc.

### 2. Agent Improvements
Enhance existing agents with:
- Updated Unity 6000.1+ APIs
- Additional code examples
- Better routing logic
- Performance optimizations

### 3. Documentation
- Workflow examples
- Best practices guides
- Integration tutorials
- Real project case studies

### 4. Testing & Quality Assurance
- Test agents with real Unity projects
- Validate code examples work correctly
- Performance benchmarking
- Cross-platform compatibility

## 📝 Creating New Unity Agents

### Agent Requirements

Every Unity agent must:
- ✅ Use Unity 6000.1+ APIs and features
- ✅ Include working C# code examples
- ✅ Follow Unity coding conventions
- ✅ Consider performance implications
- ✅ Support multiple platforms where relevant
- ✅ Integrate with existing agent ecosystem

### Agent Structure Template
```yaml
---
name: unity-[domain]-[role]
description: |
  Brief description of the agent's expertise and when to use it.
  
  Examples:
  - <example>
    Context: Specific scenario
    user: "User request example"
    assistant: "I'll use the unity-[domain]-[role] to implement..."
    <commentary>Why this agent is needed</commentary>
  </example>
---

# Unity [Domain] [Role]

You are a Unity [domain] expert specializing in [specific areas] for Unity 6000.1 projects.

## Core Expertise
- List key competencies
- Unity-specific knowledge areas
- Related technologies

## Implementation Examples

### Core System
```csharp
// Working Unity 6000.1 code example
using UnityEngine;

public class ExampleSystem : MonoBehaviour
{
    // Implementation with Unity best practices
}
```

## Best Practices
1. Unity-specific guidelines
2. Performance considerations
3. Platform compatibility

## Integration Points
- Other agents this works with
- Handoff patterns
- Coordination requirements
```

### Naming Conventions

- **Format**: `unity-[domain]-[role]`
- **Domain**: gameplay, graphics, audio, mobile, vr, etc.
- **Role**: programmer, engineer, artist, optimizer, etc.
- **Examples**: 
  - `unity-gameplay-programmer`
  - `unity-mobile-optimizer`
  - `unity-vr-developer`

### File Organization
```
agents/
├── core/                    # Cross-cutting concerns
├── specialized/
│   ├── gameplay/           # Gameplay programming
│   ├── graphics/           # Rendering and shaders
│   ├── audio/              # Audio systems
│   ├── mobile/             # Mobile development
│   ├── xr/                 # VR/AR development
│   ├── networking/         # Multiplayer
│   └── [new-domain]/       # Your new domain
└── universal/              # Framework-agnostic
```

## 🔍 Code Quality Standards

### Unity-Specific Requirements

1. **Unity Version**: All code must work with Unity 6000.1+
2. **Render Pipeline**: Support URP/HDRP where applicable
3. **Platform Support**: Consider mobile, desktop, console constraints
4. **Performance**: Include optimization considerations
5. **Best Practices**: Follow Unity's official guidelines

### Code Examples
- Must be complete and functional
- Include necessary using statements
- Add inline comments for complex logic
- Show Unity Inspector integration
- Demonstrate proper component lifecycle

### Performance Considerations
Every agent should address:
- Memory allocation patterns
- Update loop optimization
- Platform-specific constraints
- Scalability for different project sizes

## 🧪 Testing Guidelines

### Manual Testing
1. **Create Test Unity Project**: Unity 6000.1 with URP
2. **Test Agent Responses**: Use Claude Code with your agent
3. **Validate Code**: Ensure examples compile and work
4. **Check Integration**: Test with related agents

### Automated Validation
- Code examples must compile
- Follow C# and Unity naming conventions
- No deprecated Unity APIs
- Proper error handling

## 📖 Documentation Standards

### Agent Documentation
- Clear expertise description
- Practical usage examples
- Integration with other agents
- Performance considerations

### Example Workflows
When adding new agents, include:
- Common use case scenarios
- Multi-agent collaboration examples
- Real project applications

## 🔄 Review Process

### Pull Request Requirements
1. **Agent Functionality**: New/improved agent works correctly
2. **Code Quality**: Examples compile and follow standards
3. **Documentation**: Clear and comprehensive
4. **Integration**: Works with existing agent ecosystem
5. **Testing**: Validated with real Unity projects

### Review Criteria
- Unity expertise accuracy
- Code example quality
- Performance considerations
- Integration patterns
- Documentation clarity

## 🚀 Advanced Contributions

### Agent Orchestration
Help improve how agents work together:
- Better task routing logic
- Coordination patterns
- Conflict resolution
- Performance optimization

### Workflow Optimization
- Multi-agent collaboration patterns
- Complex feature implementation
- Cross-platform development flows
- Production pipeline integration

### Specialized Domains
Priority areas for new agents:
- Unity Cloud Build integration
- Console platform optimization
- WebGL performance tuning
- Unity ML-Agents implementation
- Asset pipeline automation

## 🤝 Community Guidelines

### Communication
- Be respectful and constructive
- Focus on Unity development improvement
- Share real project experiences
- Help others learn Unity best practices

### Collaboration
- Coordinate on overlapping features
- Share testing results
- Document lessons learned
- Contribute to collective knowledge

## 📋 Contribution Checklist

Before submitting your contribution:

- [ ] Agent follows naming conventions
- [ ] YAML frontmatter is properly formatted
- [ ] Code examples use Unity 6000.1+ APIs
- [ ] Examples compile without errors
- [ ] Performance implications documented
- [ ] Integration points identified
- [ ] Tested with Claude Code in Unity project
- [ ] Documentation is clear and complete
- [ ] Follows repository file organization

## 🎯 Getting Help

### Resources
- **Unity Documentation**: [docs.unity3d.com](https://docs.unity3d.com/)
- **Claude Code Docs**: [docs.anthropic.com/claude-code](https://docs.anthropic.com/claude-code)
- **Project Issues**: Use GitHub issues for questions

### Community
- Share your Unity development challenges
- Ask for agent improvement suggestions
- Collaborate on complex workflow patterns
- Test and validate each other's contributions

## 📄 License

By contributing to Unity Game Dev Agents, you agree that your contributions will be licensed under the MIT License.

---

**Let's build the future of AI-assisted Unity development together!** 🎮✨