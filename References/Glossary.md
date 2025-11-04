# GitHub Copilot Workshop Glossary

**Quick Reference Guide for All Terms, Tools, and Features**

This glossary provides clear definitions and explanations for all GitHub Copilot terms, tools, and features covered in the workshop labs. Use this as a quick reference when you encounter unfamiliar terminology or need clarification on Copilot capabilities.

---

## Table of Contents

- [Core Copilot Features](#core-copilot-features)
- [Chat Modes](#chat-modes)
- [Customization & Configuration](#customization--configuration)
- [Coding Agent & Autonomous Development](#coding-agent--autonomous-development)
- [GitHub Copilot Spaces](#github-copilot-spaces)
- [Model Context Protocol (MCP)](#model-context-protocol-mcp)
- [AI Models & Usage](#ai-models--usage)
- [Development Tools & Features](#development-tools--features)
- [Quality & Review](#quality--review)
- [File Types & Configuration](#file-types--configuration)

---

## Core Copilot Features

### GitHub Copilot
An AI-powered coding assistant that provides code suggestions, explanations, and development assistance directly within your IDE and throughout the GitHub platform.

**Key Capabilities**: Code completion, chat assistance, autonomous coding, code review

### GitHub Copilot Chat
An interactive conversational interface that allows you to ask questions, request explanations, and get AI assistance with coding tasks. Available in VS Code, Visual Studio, and on GitHub.com.

**Key Capabilities**: Ask questions, explain code, generate implementations, refactor code

### Code Completions
Real-time AI-powered suggestions that appear as "ghost text" while you type in your IDE. These suggestions help you write code faster by predicting what you want to write next.

### Inline Chat
A chat interface that appears directly in your code editor at the cursor position, allowing you to ask questions or request changes without leaving your code.

**Trigger**: `Ctrl+I` (Windows/Linux) or `Cmd+I` (Mac)

### Slash Commands
Special commands in Copilot Chat that start with `/` and trigger specific AI behaviors or actions.

**Where It's Used**: Lab 2  
**Examples**: 
- `/explain` - Explain selected code
- `/fix` - Suggest fixes for problems
- `/tests` - Generate test cases
- `/help` - Show available commands

### Chat Participants
Special prefixes that scope Copilot's responses to specific contexts or enable specialized capabilities.

**Examples**:
- `@workspace` - Provides context about your entire workspace
- `@terminal` - Help with terminal commands
- `@github` - GitHub-specific operations (via MCP)

---

## Chat Modes

### Ask Mode
A read-only chat mode for understanding code, getting explanations, and exploring options without making any changes to your files.

**Best For**: Exploring codebases, learning concepts, getting suggestions  
**Output**: Explanations and suggestions only - no code changes

### Edit Mode
A chat mode that makes targeted, deliberate changes to one or more specific files that you explicitly identify.

**Best For**: Focused refactoring, bug fixes, specific file modifications  
**Output**: Proposed changes with diffs you can review and accept

### Agent Mode (IDE)
A chat mode where Copilot works autonomously within your IDE to explore your workspace, make decisions about what to change, and implement solutions across multiple files.

**Best For**: Complex features, exploratory tasks, multi-file implementations  
**Output**: Autonomous changes across workspace files  
**Note**: Different from Coding Agent (which works on GitHub.com)

### Plan Mode
A chat mode that shows you what changes Copilot would make without actually applying them, allowing you to review the approach before execution.

**Best For**: Understanding impact, validating approach, risk reduction  
**Output**: Detailed plan of proposed changes without modifying files
**Note**: Currently only available in VS Code Insiders

---

## Customization & Configuration

### Personal Instructions
User-level configuration that defines how Copilot behaves across all repositories you work on. Set on github.com/copilot.

**Location**: https://github.com/copilot (Personal instructions section)  
**Scope**: All your repositories  
**Examples**: Coding style preferences, comment standards, preferred frameworks

### Repository Instructions
Project-specific configuration that guides Copilot to follow your repository's patterns, conventions, and requirements.

**Location**: `.github/copilot-instructions.md`  
**Scope**: Single repository  
**Examples**: Architecture patterns, component structure, team coding standards

### Custom Instructions
Specific instructions that cover things like language specific syntax standards or design patters that affect only certain file types. Use `applyTo` pattern logic to target specific file types.

**Location**: `.github/instructions/*.instructions.md`  
**Scope**: Single repository  
**Examples**: C# syntax patterns, UI styling, 3rd party package usage

### Organization Instructions
Company-wide standards set by organization administrators that apply to all repositories in the organization.

**Set By**: Organization administrators  
**Scope**: All organization repositories  
**Examples**: Security policies, compliance requirements, company standards

### Instruction Hierarchy
The priority order when multiple instruction levels exist: Personal (highest) → Repository → Organization (lowest). Higher priority instructions override lower ones when they conflict.

**Order**: Personal > Repository > Organization

### Prompt Files
Reusable, parameterized templates for common AI interactions that can be invoked with a slash command.

**Location**: `.github/prompts/*.prompt.md`  
**Format**: Markdown with YAML frontmatter  
**Usage**: Type `/prompt-name` in Copilot Chat  
**Examples**: `/generate-mock-photo-data`, `/generate-new-ui`

### Custom Chat Modes
Specialized AI personas created for specific workflows, with custom instructions and tool configurations.

**Location**: `.github/chatmodes/*.chatmode.md`  
**Format**: Markdown with YAML frontmatter  
**Examples**: BeastMode, Security Review Mode, Documentation Mode

### Custom Agents
Autonomous AI assistants with specialized instructions and capabilities that can be used in the IDE, CLI, or with Coding Agent.

**Location**: `.github/agents/*.agent.yml`  
**Format**: YAML with markdown instructions  
**Usage**: Select from agent dropdown or reference in agent assignments  
**Scope**: IDE, CLI, and Coding Agent  
**Examples**: C# Expert agent, Testing agent, Security agent

### BeastMode
A community-created custom chat mode that combines multiple tools and capabilities for maximum AI power and flexibility, popularized by Burke Holland.

**Features**: Multi-tool access, comprehensive code search, web access  
**Best For**: Complex problems requiring multiple capabilities

---

## Coding Agent & Autonomous Development

### Coding Agent (GitHub Copilot Coding Agent)
An autonomous AI developer that works on GitHub issues independently, creating pull requests without human intervention during implementation.

**Where It's Used**: Lab 7  
**Location**: GitHub.com (issues and pull requests)  
**Assignment**: Assign GitHub issue to `@copilot`  
**Output**: Pull request with implementation  
**Duration**: Typically 10-15 minutes per task

### Session Logs
Detailed records of Coding Agent's decision-making process, showing what files were analyzed, what approaches were considered, and why specific decisions were made.

**Where It's Used**: Lab 7  
**Access**: "View Session" link in pull request timeline  
**Contents**: Context gathering, planning, implementation steps, testing results

### Code Review Agent
An AI agent that automatically reviews pull requests and provides inline comments on code quality, security, performance, and best practices.

**Where It's Used**: Lab 7  
**Assignment**: Assign `@copilot` as a reviewer on any PR  
**Output**: Inline comments and summary of findings  
**Checks**: Security, performance, test coverage, accessibility, style

### Draft Pull Request
A work-in-progress pull request that Coding Agent creates while working on an issue. Marked as "Draft" until the agent completes its work.

**Where It's Used**: Lab 7  
**Status**: Automatically changes to "Ready for review" when complete  
**Purpose**: Shows progress and allows early feedback

### Session Steering
The ability to guide Coding Agent mid-session by adding prompts to influence its approach while it's working.

**Where It's Used**: Lab 7  
**Access**: Active session page on github.com/copilot/agents  
**Purpose**: Correct course without waiting for completion  
**Example**: "Use Tailwind CSS instead of custom CSS files"

### Iteration with @copilot
The process of requesting changes to a pull request by mentioning `@copilot` in comments, allowing the agent to make updates autonomously.

**Where It's Used**: Lab 7  
**Works On**: Any PR (Copilot-created or human-created)  
**Usage**: Comment on PR with `@copilot` followed by requested changes  
**Example**: `@copilot Please add error handling for null values`

---

## GitHub Copilot Spaces

### Copilot Spaces
Dedicated, persistent AI workspaces where you can define specific goals, add custom context, and have focused conversations with Copilot about particular projects or initiatives.

**Where It's Used**: Lab 6  
**Location**: https://github.com/copilot/spaces  
**Key Features**: Custom instructions, curated source files, collaborative workspace  
**Best For**: Long-running projects, specialized tasks, team collaboration

### Space Instructions
Custom guidance specific to a Copilot Space that defines how the AI should behave for that particular workspace or project.

**Where It's Used**: Lab 6  
**Location**: Within Space configuration  
**Scope**: Single Space  
**Examples**: "Focus on security best practices", "Document for beginners"

### Space Sources
Files, documentation, issues, or text content added to a Space to provide context for AI assistance.

**Where It's Used**: Lab 6  
**Types**: Repository files, text content, issues, external documentation  
**Purpose**: Give Copilot relevant context for focused assistance

---

## Model Context Protocol (MCP)

### Model Context Protocol (MCP)
A standardized protocol that allows AI assistants like Copilot to connect to external services and data sources, expanding their knowledge and capabilities.

**Where It's Used**: Labs 5-6  
**Purpose**: Integrate external systems (GitHub, Slack, databases, etc.)  
**Official Site**: https://github.com/modelcontextprotocol  
**Server List**: https://github.com/modelcontextprotocol/servers

### MCP Server
A service that implements the Model Context Protocol to expose data or functionality to AI assistants.

**Where It's Used**: Lab 5  
**Examples**: GitHub MCP Server, Slack MCP, Figma MCP, Azure MCP  
**Location**: Community list at https://github.com/modelcontextprotocol/servers

### MCP Registry
A centralized directory of available MCP servers that can be easily installed into your development environment.

**Where It's Used**: Lab 5  
**Location**: https://github.com/mcp (GitHub's registry interface)  
**Community List**: https://github.com/modelcontextprotocol/servers  
**Purpose**: Discover and install MCP servers with one click

### GitHub MCP Server
An MCP server that connects Copilot to GitHub's data, enabling queries about repositories, issues, pull requests, and more through natural conversation.

**Where It's Used**: Labs 5-6  
**Capabilities**: Query issues, search repositories, analyze PRs, access organization data  
**Installation**: Via MCP Registry or manual configuration

### MCP Configuration
The setup file that defines which MCP servers are available to your IDE and how they should be configured.

**Where It's Used**: Lab 5  
**Location**: `.vscode/mcp.json` (repository) or VS Code settings.json (user)  
**Format**: JSON configuration with server definitions

---

## AI Models & Usage

### AI Models
The underlying machine learning models that power GitHub Copilot's capabilities. Different models have different strengths, speeds, and costs.

**Where It's Used**: Lab 4  
**Providers**: OpenAI (GPT), Anthropic (Claude), Google (Gemini)  
**Documentation**: https://docs.github.com/copilot/reference/ai-models/supported-models

### Premium Models
AI models that count against your monthly request allowance. Generally more powerful but limited in usage.

**Where It's Used**: Lab 4  
**Examples**: GPT-4, Claude Sonnet, advanced models  
**Cost**: Counts against monthly premium request quota

### 0x Models (Unlimited)
AI models with unlimited usage that don't count against your premium request allowance. Optimized for common tasks.

**Where It's Used**: Lab 4  
**Examples**: Base GPT models, standard Claude models  
**Cost**: Unlimited, no request counting

### Auto Model Selection
A feature that automatically selects the most appropriate AI model for your task while providing a 10% discount on premium requests.

**Where It's Used**: Lab 4  
**Benefit**: Cost savings + optimal model selection  
**Best For**: Users who want automation without manual model selection

### Premium Request Usage
Tracking and management of your monthly allowance of premium model requests.

**Where It's Used**: Lab 4  
**Monitor At**: GitHub Copilot settings page  
**Reference Guide**: [Premium Request Usage Guide](Premium-Request-Usage.md)

### Model Switching
The ability to select different AI models for different tasks based on their strengths and your needs.

**Where It's Used**: Lab 4  
**Location**: Model selector dropdown in Copilot Chat  
**Purpose**: Match model capabilities to task requirements

---

## Development Tools & Features

### Debug Panel (Chat Debug View)
A transparency feature that shows exactly what context, prompts, and system instructions Copilot is using for its responses.

**Where It's Used**: Lab 4  
**Access**: Command Palette → "Copilot Chat Debug: Focus on Copilot Chat Debug View"  
**Shows**: Prompts, system instructions, context files, token usage  
**Purpose**: Understand AI decision-making, improve prompts, debug issues

### RAG (Retrieval Augmented Generation)
A technique where AI retrieves relevant information from your codebase before generating responses, ensuring context-aware and project-consistent outputs.

**Where It's Used**: Throughout (underlying technology)  
**How It Works**: AI searches codebase → finds relevant patterns → generates matching code  
**Benefit**: Code that matches your project's style and patterns

### Workspace Context
The set of files, folders, and project information that Copilot can access and analyze in your current development environment.

**Where It's Used**: Throughout all labs  
**Triggered By**: `@workspace` participant  
**Scope**: All files in your opened workspace/repository

### File References
A way to explicitly include specific files in your Copilot Chat context to ensure relevant information is considered.

**Where It's Used**: Labs 3, 5  
**Syntax**: `#filename.tsx` or `@filename.tsx`  
**Purpose**: Ensure specific files are considered in AI responses

### Context Files
Files that have been added to a chat conversation to provide relevant information for AI assistance.

**Where It's Used**: Throughout labs  
**How to Add**: Click `+` in chat, use `#filename`, or reference with `@`  
**Examples**: Related components, configuration files, documentation

---

## Quality & Review

### Linting
Automated code quality checking that identifies style issues, potential bugs, and code that doesn't follow project standards.

**Where It's Used**: Labs 1, 4  
**Command**: `npm run lint`  
**Purpose**: Ensure code quality and consistency

### TypeScript
A programming language that adds static types to JavaScript, providing better tooling, error detection, and code quality.

**Where It's Used**: Throughout (PixelPerfect Gallery is built with TypeScript)  
**Files**: `.ts`, `.tsx`  
**Benefits**: Type safety, better IDE support, fewer runtime errors

### Test Coverage
The percentage of your code that is executed by automated tests, indicating how well-tested your application is.

**Where It's Used**: Labs 4, 7  
**Goal**: High coverage for critical features  
**Types**: Unit tests, integration tests, end-to-end tests

### Acceptance Criteria
Specific, measurable conditions that must be met for a feature or task to be considered complete.

**Where It's Used**: Lab 7  
**Format**: Checklist in issue description  
**Example**: "User can filter photos by category"  
**Purpose**: Clear success metrics for Coding Agent

### Code Review
The process of examining code changes to ensure quality, security, and adherence to standards before merging.

**Where It's Used**: Lab 7  
**Participants**: Humans and/or Code Review Agent  
**Purpose**: Catch issues, improve quality, share knowledge

---

## File Types & Configuration

### `.github/copilot-instructions.md`
The repository-level instructions file that guides Copilot's behavior for a specific project.

**Where It's Used**: Lab 4  
**Format**: Markdown  
**Contains**: Architecture patterns, coding standards, project context  
**Scope**: Single repository

### `.github/prompts/*.prompt.md`
Directory containing reusable prompt templates that can be invoked as slash commands.

**Where It's Used**: Lab 5  
**Format**: Markdown with YAML frontmatter  
**Naming**: `filename.prompt.md`  
**Usage**: `/filename` in chat

### `.github/chatmodes/*.chatmode.md`
Directory containing custom chat mode definitions for specialized AI behaviors.

**Where It's Used**: Lab 5  
**Format**: Markdown with YAML frontmatter  
**Naming**: `filename.chatmode.md`  
**Usage**: Select from mode dropdown

### `.github/agents/*.agent.yml`
Directory containing custom agent definitions for autonomous task execution.

**Where It's Used**: Lab 5  
**Format**: YAML with markdown instructions  
**Naming**: `filename.agent.yml`  
**Usage**: Select from agent dropdown or reference in assignments

### `.vscode/mcp.json`
Repository-level MCP server configuration file.

**Where It's Used**: Lab 5  
**Format**: JSON  
**Contains**: Server definitions and configurations  
**Scope**: Single repository

### `next.config.ts`
Configuration file for Next.js applications, defining build options, routing, and framework behavior.

**Where It's Used**: Lab 1  
**Framework**: Next.js  
**Purpose**: Project configuration and build settings

### `package.json`
Node.js project configuration file listing dependencies, scripts, and project metadata.

**Where It's Used**: Lab 1  
**Contains**: Dependencies, scripts, project information  
**Purpose**: Define project setup and available commands

---

## Quick Comparison Tables

### Chat Modes Comparison

| Mode | Changes Code? | Scope | Best For |
|------|---------------|-------|----------|
| **Ask** | No | Read-only | Understanding, exploring, learning |
| **Edit** | Yes | Files you specify | Targeted changes, refactoring |
| **Agent** | Yes | Autonomous decision | Complex features, exploration |
| **Plan** | No | Preview only | Understanding impact before changes |

### Agent Types Comparison

| Feature | IDE Agent Mode | Coding Agent | Custom Agents |
|---------|----------------|--------------|---------------|
| **Location** | VS Code | GitHub.com | IDE, CLI, or GitHub |
| **Interaction** | Interactive | Autonomous | Context-dependent |
| **Output** | Direct changes | Pull Request | Varies by context |
| **Best For** | Real-time development | Delegated tasks | Specialized workflows |

### Instruction Hierarchy

| Level | Scope | Set By | Priority |
|-------|-------|--------|----------|
| **Personal** | All your repos | You (on github.com/copilot) | Highest |
| **Repository** | Single repo | Repo file (`.github/copilot-instructions.md`) | Medium |
| **Organization** | All org repos | Org admins | Lowest |

---

## Related Documentation

For more detailed information on specific topics, see these reference guides:

- **[Premium Request Usage Guide](Premium-Request-Usage.md)** - Comprehensive model pricing and usage optimization
- **[Copilot Instruction Best Practices](Copilot-Instruction-Best-Practices.md)** - How to write effective instruction files
- **[Coding Agent Best Practices](Coding-Agent-Best-Practices.md)** - Advanced patterns for autonomous development
- **[BeastMode](BeastMode.md)** - Full BeastMode custom chat mode configuration

---

## Lab Cross-Reference

### By Lab

**Lab 1 - Getting Started**
- GitHub Copilot, Code Completions, Basic Setup

**Lab 2 - Exploring the Codebase**
- Copilot Chat, Ask Mode, Slash Commands, Chat Participants, `@workspace`

**Lab 3 - Code Editing & Generation**
- Edit Mode, Agent Mode (IDE), Plan Mode, Multi-file Changes, Context Files

**Lab 4 - Engineering Practices**
- Personal Instructions, Repository Instructions, Organization Instructions, Debug Panel, AI Models, Premium Models, Model Switching, Linting

**Lab 5 - Enhancing Copilot**
- Prompt Files, Custom Chat Modes, Custom Agents, BeastMode, MCP, MCP Servers, GitHub MCP Server

**Lab 6 - Copilot Spaces**
- Copilot Spaces, Space Instructions, Space Sources, MCP Integration

**Lab 7 - Coding Agent**
- Coding Agent, Session Logs, Code Review Agent, Draft Pull Request, Session Steering, Iteration with @copilot, Acceptance Criteria

---

## Quick Tips

### When You're Confused About...

**"What mode should I use?"**
- Understanding code → Ask Mode
- Specific file changes → Edit Mode  
- Complex features → Agent Mode (IDE)
- Delegated tasks → Coding Agent (GitHub)

**"Where do I configure this?"**
- Your preferences → Personal Instructions (github.com/copilot)
- Project patterns → Repository Instructions (`.github/copilot-instructions.md`)
- Reusable prompts → Prompt Files (`.github/prompts/`)
- Specialized modes → Custom Chat Modes (`.github/chatmodes/`)

**"What's the difference between Agent Mode and Coding Agent?"**
- Agent Mode (IDE) → Interactive in VS Code, real-time collaboration
- Coding Agent → Autonomous on GitHub, works independently on issues

**"When should I use Spaces?"**
- Long-running projects with specific focus areas
- Security reviews, documentation projects, feature development
- Team collaboration with shared context

**"How do I control costs?"**
- Use 0x models for routine tasks
- Enable Auto selection for 10% discount
- Monitor usage at github.com/copilot settings
- See [Premium Request Usage Guide](Premium-Request-Usage.md)

---

**Last Updated**: Reference for GitHub Copilot Advanced Workshop  
**For Questions**: Use GitHub Copilot Chat with this glossary as context!

*Tip: Press `Ctrl+F` (or `Cmd+F` on Mac) to search for specific terms on this page.*
