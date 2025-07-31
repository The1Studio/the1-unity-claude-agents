# Unity Game Development AI Team Configuration

This repository contains specialized AI agents for Unity 6000.1 game development. Each agent represents a domain expert in game development, working together as a cohesive team to help you build high-quality Unity games.

## Working with Unity Game Dev Agents

When using these agents with Claude Code, the system will automatically select the most appropriate specialist for your task. For complex multi-step development tasks, the Unity Tech Lead Orchestrator coordinates the team's efforts.

### Key Orchestration Pattern

**CRITICAL**: For any multi-step Unity development task (implementing features, optimizing performance, setting up systems), you should ALWAYS start with the **unity-tech-lead-orchestrator**. This agent will:

1. Analyze your Unity project requirements
2. Break down the work into specialized tasks
3. Route each task to the appropriate Unity specialist
4. Coordinate the overall implementation

Only skip the orchestrator for simple, single-domain questions that clearly fall under one specialist's expertise.

## Agent Organization

Agents are organized hierarchically by their scope and specialization:

### 1. **Orchestrators** (agents/orchestrators/)
High-level coordinators that manage complex Unity development workflows:
- `unity-tech-lead-orchestrator` - Technical leadership and task routing
- `unity-project-analyst` - Unity project analysis and technology detection
- `unity-team-configurator` - Team setup based on project needs

### 2. **Core** (agents/core/)
Cross-cutting concerns that apply to all Unity projects:
- `unity-performance-optimizer` - Performance profiling and optimization
- `unity-code-reviewer` - Unity-specific code review and best practices
- `unity-build-engineer` - Build pipeline and CI/CD
- `unity-documentation-specialist` - Technical documentation

### 3. **Specialized** (agents/specialized/)
Unity domain experts organized by specialization:

#### Gameplay (agents/specialized/gameplay/)
- `unity-gameplay-programmer` - Core gameplay systems
- `unity-physics-programmer` - Physics and collision systems
- `unity-ai-programmer` - AI and behavior systems
- `unity-animation-programmer` - Animation and Timeline

#### Graphics (agents/specialized/graphics/)
- `unity-graphics-programmer` - Rendering and shaders
- `unity-technical-artist` - Art pipeline and tools
- `unity-vfx-artist` - Visual effects and particles
- `unity-lighting-artist` - Lighting and post-processing

#### Networking (agents/specialized/networking/)
- `unity-multiplayer-engineer` - Netcode and multiplayer
- `unity-backend-engineer` - Server infrastructure
- `unity-networking-optimizer` - Network performance

#### Mobile (agents/specialized/mobile/)
- `unity-mobile-developer` - iOS/Android optimization
- `unity-mobile-graphics-optimizer` - Mobile GPU optimization
- `unity-mobile-monetization` - IAP and ads integration

#### XR (agents/specialized/xr/)
- `unity-vr-developer` - Virtual reality
- `unity-ar-developer` - Augmented reality
- `unity-xr-interaction-designer` - XR interactions

### 4. **Universal** (agents/universal/)
Framework-agnostic game development specialists:
- `game-designer` - Game mechanics and systems design
- `level-designer` - Level design and world building
- `ui-ux-designer` - User interface and experience
- `audio-designer` - Sound and music implementation

## Three-Phase Unity Development Workflow

The Unity Tech Lead Orchestrator follows a structured approach:

### Phase 1: Research & Analysis
- Analyze Unity project structure and version
- Identify render pipeline (Built-in/URP/HDRP)
- Detect platforms and build targets
- Review existing systems and dependencies

### Phase 2: Planning & Architecture
- Design technical approach
- Select appropriate Unity features
- Plan performance budgets
- Identify required specialists

### Phase 3: Implementation & Optimization
- Coordinate specialist implementations
- Ensure Unity best practices
- Optimize for target platforms
- Validate performance metrics

## Agent Communication Protocol

Agents communicate through structured handoffs:

```typescript
interface AgentHandoff {
  from: string;           // Source agent
  to: string;            // Target agent
  task: string;          // Specific task description
  context: {
    unityVersion: string;      // "6000.1"
    renderPipeline: string;    // "URP" | "HDRP" | "Built-in"
    platforms: string[];       // ["iOS", "Android", "PC"]
    constraints: string[];     // Performance or technical constraints
  };
  findings: any;         // Structured findings from analysis
}
```

## Example Orchestration Flow

When you request: "Create a multiplayer racing game for mobile"

1. **unity-tech-lead-orchestrator** receives the request
2. Breaks down into specialized tasks:
   - Mobile performance requirements
   - Multiplayer architecture
   - Physics and vehicle controls
   - Touch input system
3. Routes to specialists:
   - `unity-mobile-developer` for platform setup
   - `unity-multiplayer-engineer` for networking
   - `unity-physics-programmer` for vehicle physics
   - `unity-mobile-graphics-optimizer` for rendering
4. Coordinates integration and optimization

## Unity-Specific Considerations

All agents are aware of:
- Unity 6000.1 features and APIs
- Platform-specific requirements
- Performance constraints
- Unity best practices
- Asset pipeline workflows
- Package dependencies

## Development Guidelines

### Creating New Unity Agents

1. Identify specific Unity domain expertise needed
2. Place in appropriate category folder
3. Use YAML frontmatter format
4. Include Unity 6000.1 code examples
5. Define clear integration patterns
6. Test with real Unity projects

### Agent Quality Standards

- Must use Unity 6000.1 APIs and features
- Include platform-specific considerations
- Provide working code examples
- Follow Unity coding conventions
- Consider performance implications
- Document Unity-specific gotchas

## Getting Started

1. Copy this CLAUDE.md to your Unity project root
2. The unity-tech-lead-orchestrator will analyze your project
3. Specialists will be assigned based on your needs
4. Follow the three-phase workflow for complex tasks

The Unity Game Dev AI Team is designed to accelerate your game development while maintaining high quality standards and optimal performance across all target platforms.