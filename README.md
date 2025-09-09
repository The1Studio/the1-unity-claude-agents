# Unity Claude Agents - Unity Game Development AI Team 🎮

**Supercharge Claude Code with a team of specialized Unity AI agents** that work together to build complete game features, optimize performance, and handle any Unity development challenge with expert-level knowledge.

## ⚠️ Important Notice

**This project is experimental and token-intensive.** Unity game development involves complex multi-system interactions. Multi-agent orchestration can consume 10-50k tokens per complex feature. Use with caution and monitor your usage.

## 🚀 Quick Start (3 Minutes)

### Prerequisites
- **Claude Code CLI** installed and authenticated
- **Claude subscription** - required for intensive agent workflows
- **Unity 2022.3 LTS or later** (Unity 6000.1+ recommended)
- Active Unity project directory

### 1. Install the Agents
```bash
git clone https://github.com/The1Studio/the1-unity-claude-agents.git
```

#### Option A: Symlink (Recommended - auto-updates)

**macOS/Linux:**
```bash
ln -sf "$(pwd)/the1-unity-claude-agents" ~/.claude/agents
```

**Windows (PowerShell):**
```powershell
cmd /c mklink /D "$env:USERPROFILE\.claude\agents" "$(Get-Location)\the1-unity-claude-agents"
```

#### Option B: Copy (Static - no auto-updates)
```bash
cp -r the1-unity-claude-agents ~/.claude/
```

### 2. Verify Installation
```bash
claude /agents
# Should show all 40+ Unity agents.
```

### 3. Initialize Your Unity Project
**Navigate** to your **Unity project directory** (where Assets/ folder is) and run:

```bash
claude "use @unity-team-configurator and optimize my Unity project to best use the available subagents."
```

### 4. Start Building
```bash
claude "use @unity-tech-lead-orchestrator and create a player movement system with jumping"
```

Your Unity AI team will automatically detect your Unity version, render pipeline, and use the right specialists!

## 🎯 How Auto-Configuration Works

The @unity-team-configurator automatically sets up your perfect Unity development team. When invoked, it:

1. **Locates CLAUDE.md** - Finds existing project configuration in your Unity project root
2. **Detects Unity Stack** - Inspects Unity version, render pipeline (URP/HDRP/Built-in), platforms, and packages
3. **Discovers Available Agents** - Scans ~/.claude/agents/ for Unity specialists
4. **Selects Specialists** - Matches agents to your Unity setup (mobile, VR, multiplayer, etc.)
5. **Updates CLAUDE.md** - Creates a Unity-specific "AI Team Configuration" section
6. **Provides Usage Guidance** - Shows detected Unity setup and sample commands

## 👥 Meet Your Unity AI Development Team

### 🎭 Orchestrators (3 agents)
- **[Unity Tech Lead Orchestrator](agents/orchestrators/unity-tech-lead-orchestrator.md)** - Senior Unity architect who coordinates complex game development tasks
- **[Unity Project Analyst](agents/orchestrators/unity-project-analyst.md)** - Unity project analyzer for technology detection and optimization
- **[Unity Team Configurator](agents/orchestrators/unity-team-configurator.md)** - AI team setup for Unity projects with automatic stack detection

### 🎮 Core Development (6 agents)
- **[Unity Performance Optimizer](agents/core/unity-performance-optimizer.md)** - Performance profiling, optimization, and platform-specific tuning
- **[Unity Code Reviewer](agents/core/unity-code-reviewer.md)** - Unity-specific code review with best practices enforcement
- **[Unity Build Engineer](agents/core/unity-build-engineer.md)** - Build pipelines, CI/CD, and multi-platform deployment
- **[Unity QA Engineer](agents/core/unity-qa-engineer.md)** - Automated testing with Unity Test Framework
- **[Unity Analytics Engineer](agents/core/unity-analytics-engineer.md)** - Game analytics, telemetry, and player behavior tracking
- **[Unity Tools Programmer](agents/core/unity-tools-programmer.md)** - Editor tools, workflow automation, and productivity

### 💼 Specialized Experts (28 agents)

#### Gameplay Programming (4 agents)
- **[Unity Gameplay Programmer](agents/specialized/gameplay/unity-gameplay-programmer.md)** - Core game mechanics and player systems
- **[Unity Physics Programmer](agents/specialized/gameplay/unity-physics-programmer.md)** - Physics simulation, vehicles, and constraints
- **[Unity AI Programmer](agents/specialized/gameplay/unity-ai-programmer.md)** - AI behavior, pathfinding, and decision systems
- **[Unity Animation Programmer](agents/specialized/gameplay/unity-animation-programmer.md)** - Character animation, Timeline, and IK

#### Graphics & Rendering (3 agents)
- **[Unity Graphics Programmer](agents/specialized/graphics/unity-graphics-programmer.md)** - Rendering optimization and visual effects
- **[Unity Shader Programmer](agents/specialized/graphics/unity-shader-programmer.md)** - Custom shader development with HLSL
- **[Unity Technical Artist](agents/specialized/graphics/unity-technical-artist.md)** - Art pipeline and shader authoring

#### Platform Development (6 agents)
- **[Unity Mobile Developer](agents/specialized/mobile/unity-mobile-developer.md)** - iOS/Android optimization and features
- **[Unity Console Developer](agents/platforms/unity-console-developer.md)** - PlayStation, Xbox, Nintendo Switch development
- **[Unity Web Developer](agents/platforms/unity-web-developer.md)** - WebGL deployment and browser optimization
- **[Unity VR Developer](agents/specialized/xr/unity-vr-developer.md)** - Virtual reality with XR Toolkit
- **[Unity AR Developer](agents/specialized/xr/unity-ar-developer.md)** - Augmented reality with AR Foundation

#### Networking & Infrastructure (2 agents)
- **[Unity Multiplayer Engineer](agents/specialized/networking/unity-multiplayer-engineer.md)** - Netcode for GameObjects and networking
- **[Unity Cloud Engineer](agents/specialized/cloud/unity-cloud-engineer.md)** - Unity Gaming Services and cloud infrastructure

#### UI & User Experience (1 agent)
- **[Unity UI Developer](agents/specialized/ui/unity-ui-developer.md)** - UI Toolkit and uGUI implementation

#### Business & Monetization (1 agent)
- **[Unity Monetization Specialist](agents/specialized/monetization/unity-monetization-specialist.md)** - IAP, ads, and ethical monetization

#### Accessibility & Localization (2 agents)
- **[Unity Localization Specialist](agents/specialized/localization/unity-localization-specialist.md)** - Multi-language support and cultural adaptation
- **[Unity Accessibility Specialist](agents/specialized/accessibility/unity-accessibility-specialist.md)** - Inclusive game design features

#### Audio (1 agent)
- **[Unity Audio Engineer](agents/specialized/audio/unity-audio-engineer.md)** - 3D audio, music systems, and optimization

#### Data & Security (2 agents)
- **[Unity Data Engineer](agents/specialized/data/unity-data-engineer.md)** - Save systems, data persistence, and cloud sync
- **[Unity Security Engineer](agents/specialized/security/unity-security-engineer.md)** - Anti-cheat, encryption, and security

### 🌐 Universal Game Design (1 agent)
- **[Game Designer](agents/universal/game-designer.md)** - Game mechanics, balance, and monetization design

### 🛠️ Quality Assurance (4 agents)
- **[Code Archaeologist](agents/core/code-archaeologist.md)** - Legacy code exploration and documentation
- **[Code Reviewer](agents/core/code-reviewer.md)** - Comprehensive code quality assessment
- **[Documentation Specialist](agents/core/documentation-specialist.md)** - Technical documentation and guides
- **[Performance Optimizer](agents/core/performance-optimizer.md)** - System-wide performance analysis

## 🚀 Example Workflows

### Creating a Mobile Game
```bash
claude "use @unity-tech-lead-orchestrator to create a mobile puzzle game with touch controls"
# Automatically routes to: @unity-mobile-developer, @unity-ui-developer, @unity-gameplay-programmer
```

### Optimizing Performance
```bash
claude "use @unity-performance-optimizer to analyze and fix framerate issues on mobile"
# Deep performance analysis with platform-specific optimizations
```

### Multiplayer Implementation
```bash
claude "use @unity-multiplayer-engineer to add online multiplayer to my racing game"
# Complete networking setup with Netcode for GameObjects
```

## 📊 Token Usage Guidelines

Unity development workflows can be token-intensive:
- **Simple features**: 5-10k tokens (player movement, UI screens)
- **Complex systems**: 20-40k tokens (multiplayer, save systems)
- **Full features**: 40-80k tokens (complete game mechanics with optimization)

Tips to manage usage:
1. Break large features into smaller tasks
2. Use specific agents directly for focused work
3. Let orchestrators handle only complex multi-system features

## 🤝 Contributing

Want to add new Unity agents or improve existing ones? Check out our [Contributing Guide](CONTRIBUTING.md).

### Adding New Agents
1. Create agent file in appropriate category
2. Follow the YAML frontmatter format
3. Include Unity 6000.1 code examples
4. Submit PR with clear description

## 📚 Documentation

- **[Creating Agents](docs/creating-agents.md)** - Guide for creating new Unity agents
- **[Best Practices](docs/best-practices.md)** - Unity development best practices
- **[Example Workflows](docs/example-workflows.md)** - Common Unity development scenarios

## 🔧 Troubleshooting

### "Agent not found"
- Verify installation path: `ls ~/.claude/`
- Check agent names: `claude /agents | grep unity`
- Ensure proper symlink/copy

### "High token usage"
- Use specific agents instead of orchestrators for simple tasks
- Break complex features into smaller chunks
- Monitor usage with Claude's token counter

## 📄 License

MIT License - Use freely in personal and commercial projects.

## 🙏 Acknowledgments

- **Anthropic** for Claude Code and the agent system
- **Unity Technologies** for the amazing game engine
- **awesome-claude-agents** for the project structure inspiration
- The Unity development community

---

<div align="center">

**Built with ❤️ for Unity developers**

[Report Issues](https://github.com/The1Studio/the1-unity-claude-agents/issues) • [Request Features](https://github.com/The1Studio/the1-unity-claude-agents/issues/new) • [Join Discussion](https://github.com/The1Studio/the1-unity-claude-agents/discussions)

</div>