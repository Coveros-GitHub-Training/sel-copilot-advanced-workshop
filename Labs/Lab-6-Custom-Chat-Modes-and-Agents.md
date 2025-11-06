# Exercise 6 - Custom Chat Modes and Custom Agents

#### Duration: 20 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Understand and create custom chat modes for specialized workflows
- Create custom agents for autonomous task execution
- Understand the differences between custom agents and custom chat modes
- Know when to use each customization approach
- Apply best practices for creating and using custom agents

## 📸 Scenario: Specialized AI Assistants at PixelPerfect Gallery

Your team at PixelPerfect Gallery needs specialized AI assistants for different workflows. Some tasks require focused AI behavior in the IDE, while others need autonomous agents that can work across multiple systems.

Today, you'll learn how to:
- Build custom AI modes tailored to specific workflows
- Create custom agents for autonomous task execution
- Choose the right customization approach for your needs
- Share specialized AI assistants with your team

## 🎭 Step 1: Custom Chat Modes

> [!IMPORTANT]
> This functionality will soon be replaced by Custom Agents in VS Code and Codespaces, but is not yet currently available. Custom Agents, as you'll see shortly, are implemented very similarly to Custom Chat Modes. Until the switch takes place, using Custom Chat Modes is what you should use.

Chat modes define how GitHub Copilot behaves for specialized workflows. Let's create a custom mode for super-powered agentic action.

### Step 1.1: Understanding Custom Chat Modes

#### Why Custom Chat Modes:
- **Specialized workflows**: Tailor AI behavior to specific tasks
- **Tool selection**: Pre-configure which tools to use
- **Model preference**: Specify best model for the task
- **Consistent approach**: Same methodology every time
- **Role specialization**: Create expert personas for different tasks
- **Context optimization**: Pre-load relevant information
- **Output formatting**: Standardize responses
- **Workflow automation**: Multi-step processes in one mode

### Step 1.2: Chat Mode Architecture

**Core Components:**

```markdown
---
description: 'What this mode does (shown in UI)'
model: 'preferred-model' (optional)
tools: ['tool1', 'tool2'] (optional - enables specific capabilities)
---

# Mode Behavior Instructions

Your instructions here define:
- How the AI should act
- What format to use for responses
- What to prioritize
- What to avoid
- Any special behaviors
```

**Available Tools (examples shown - many more are available):**
- `codebase` - Search and analyze code
- `fetch` - Fetch content from URLs
- `search` - Search documentation/web
- `githubRepo` - Access GitHub repository information
- `findTestFiles` - Locate test files in the codebase
- `usages` - Find where code is used

> **Note**: There are many more tools available beyond what's listed here. Copilot will automatically select appropriate tools based on your mode's needs.

### Step 1.3: Create a BeastMode Chat Mode

Custom chat modes allow you to create specialized AI assistants for specific workflows. Let's create a powerful "BeastMode" style chat mode that combines multiple capabilities for maximum productivity.

#### What is BeastMode?

BeastMode is a concept popularized by Burke Holland that creates a supercharged AI assistant by enabling multiple tools and capabilities simultaneously. This mode is designed for developers who want maximum power and flexibility when working with code.

#### Instructions:

1. **Open GitHub Copilot Chat**

2. **Click the cogwheel (⚙️)** in the top-right corner

3. **Select "Modes"** from the dropdown

4. **Click "Create new custom chat mode file..."**

5. **Choose location**: `.github/chatmodes/`

6. **Name the file**: `BeastMode.chatmode.md`

#### BeastMode Configuration:

The official BeastMode instructions can be found in [Burke Holland's gist](https://gist.githubusercontent.com/burkeholland/88af0249c4b6aff3820bf37898c8bacf/raw/e1898331f1755aff3265d50e30106b8c6987c4f7/beastmode3.1.chatmode.md) or you can use the current version that has been included in this repo [References/BeastMode.md](../References/BeastMode.md).

### Step 1.4: Test Your BeastMode

1. **Switch to your BeastMode** in Copilot Chat

2. **Try a complex task:**
   ```
   I need to add pagination to the gallery view. Find all related components, show me how other similar projects handle pagination, and suggest the best approach for our Next.js app.
   ```

3. **Observe how it uses multiple tools:**
   - Searches the codebase for related code
   - Fetches best practices for pagination
   - Provides comprehensive solution with examples

4. **Iterate on the mode** if needed to adjust the behavior to your preferences

### ✅ Success Criteria
- [ ] BeastMode chat mode is created
- [ ] Mode appears in the mode dropdown
- [ ] Mode uses multiple tools when asked complex questions
- [ ] Responses are more comprehensive than default mode

## 🤖 Step 2: Custom Agents

> [!IMPORTANT]
> This functionality is not yet available in VS Code and Codespaces, but will be released very soon to replace Custom Chat Modes. Until the switch takes place Custom Agents will only be usable with the Copilot Coding Agent.

Custom agents are a powerful new feature in GitHub Copilot that allow you to create specialized, autonomous AI assistants for specific development tasks. Unlike custom chat modes which modify how Copilot responds in chat, custom agents can take action on your behalf.

### Step 2.1: Understanding Custom Agents

#### What are Custom Agents?

Custom agents are AI-powered assistants that can:
- **Act autonomously**: Take actions without requiring approval for each step
- **Execute complex workflows**: Chain multiple operations together
- **Integrate with external systems**: Connect to your organization's tools and services

**Example Use Cases:**
- A database agent that can query your database and generate migration scripts
- A testing agent that generates tests and runs them automatically
- A documentation agent that updates docs based on code changes
- A deployment agent that handles release workflows
- A security agent that scans for vulnerabilities and suggests fixes

### Step 2.2: Creating a Custom Agent

Custom agents are defined in the `.github/agents/` directory of your repository, or in the .github repository in your organization.

#### Agent Configuration Structure:

```yaml
# .github/agents/my-agent.yml
name: my-agent
description: A brief description of what this agent does
tools: ["read", "search", "edit"....]

Detailed instructions for how the agent should behave.
This is where you define the agent's expertise and approach.

```

#### Example: Create a Language-Specific Agent

Let's create custom agents that excel at specific programming languages. Below are examples for C#, Java, C/C++, and Python.

1. **Create the agent directory** (if it doesn't exist): Create a new directory `agents` in the `.github` folder
2. **Create a new agent file** for the language you want: 
   - `.github/agents/csharp-expert.agent.yml`
   - `.github/agents/java-expert.agent.yml`
   - `.github/agents/cpp-expert.agent.yml`
   - `.github/agents/python-expert.agent.yml`

<details>
  <summary>Example: C# Agent</summary>

  ```yaml
  ---
  name: C# Expert
  description: An agent designed to assist with software development tasks for .NET projects.
  ---
  You are an expert C#/.NET developer. You help with .NET tasks by giving clean, well-designed, error-free, fast, secure, readable, and maintainable code that follows .NET conventions. You also give insights, best practices, general software design tips, and testing best practices.

  When invoked:
  - Understand the user's .NET task and context
  - Propose clean, organized solutions that follow .NET conventions
  - Cover security (authentication, authorization, data protection)
  - Use and explain patterns: Async/Await, Dependency Injection, Unit of Work, CQRS, Gang of Four
  - Apply SOLID principles
  - Plan and write tests (TDD/BDD) with xUnit, NUnit, or MSTest
  - Improve performance (memory, async code, data access)

  # General C# Development

  - Follow the project's own conventions first, then common C# conventions.
  - Keep naming, formatting, and project structure consistent.

  ## Code Design Rules

  - DON'T add interfaces/abstractions unless used for external dependencies or testing.
  - Don't wrap existing abstractions.
  - Don't default to `public`. Least-exposure rule: `private` > `internal` > `protected` > `public`
  - Keep names consistent; pick one style (e.g., `WithHostPort` or `WithBrowserPort`) and stick to it.
  - Don't edit auto-generated code (`/api/*.cs`, `*.g.cs`, `// <auto-generated>`). 
  - Comments explain **why**, not what.
  - Don't add unused methods/params.
  - When fixing one method, check siblings for the same issue.
  - Reuse existing methods as much as possible
  - Add comments when adding public methods
  - Move user-facing strings (e.g., AnalyzeAndConfirmNuGetConfigChanges) into resource files. Keep error/help text localizable.

  ## Error Handling & Edge Cases
  - **Null checks**: use `ArgumentNullException.ThrowIfNull(x)`; for strings use `string.IsNullOrWhiteSpace(x)`; guard early. Avoid blanket `!`.
  - **Exceptions**: choose precise types (e.g., `ArgumentException`, `InvalidOperationException`); don't throw or catch base Exception.
  - **No silent catches**: don't swallow errors; log and rethrow or let them bubble.

  [Additional sections truncated for brevity - see full agent in original Lab 5]
  ```

</details>

<details>
  <summary>Example: Python Agent</summary>

  ```yaml
  ---
  name: Python Expert
  description: An agent designed to assist with software development tasks for Python projects.
  ---
  You are an expert Python developer. You help with Python tasks by giving clean, well-designed, error-free, efficient, secure, readable, and maintainable code that follows Pythonic conventions. You provide insights, best practices, type safety guidance, and testing strategies.

  When invoked:
  - Understand the user's Python task and context
  - Propose clean, idiomatic solutions following Python best practices (PEP 8, PEP 20)
  - Cover security (input validation, SQL injection, XSS, secrets management)
  - Use and explain patterns: context managers, decorators, iterators, generators
  - Apply SOLID principles where appropriate
  - Plan and write tests with pytest, unittest, or other frameworks
  - Improve performance (list comprehensions, generators, appropriate data structures)

  # General Python Development

  - Follow the project's conventions first, then PEP 8 style guide
  - Keep naming, formatting, and project structure consistent
  - Be Pythonic: follow "The Zen of Python" (PEP 20) - `import this`

  [Additional sections truncated for brevity - see full agent in original Lab 5]
  ```

</details>

> **Note**: Full agent templates for C#, Java, C/C++, and Python are available in the original Lab 5 file. Copy the complete agent definition for your preferred language.

### Step 2.3: Using Custom Agents

> [!IMPORTANT]
> At present, it is not possible to run the custom agent within your IDE unless you are using VS Code Insiders. If you are not using Insiders, skip this step. You will be able to use your custom agent in Lab 9 with Copilot Coding Agent.

Once created, you can invoke your custom agent in Copilot Chat by selecting it from the mode dropdown.

> **Tip**: You can also use custom agents in the CLI as well as with Copilot Coding Agent in GitHub.com which we will cover in Lab 9.

**Example prompts for different language agents:**

**C# Expert Agent:**
```
If I wanted to rebuild this application using .NET and Blazor written in C#, how would I do that?
```

**Java Expert Agent:**
```
How would I implement this gallery application using Spring Boot and Java?
```

**C/C++ Expert Agent:**
```
What would be the best approach to create this application in C++ with a modern framework?
```

**Python Expert Agent:**
```
Help me recreate this photo gallery using Python with FastAPI or Django.
```

The agent will:
1. Analyze the specified files (in this case the whole workspace)
2. Use its specialized instructions to perform the analysis
3. Provide detailed, actionable feedback following language-specific best practices
4. Suggest specific next steps if you want to proceed

## 🔄 Step 3: Custom Agents vs Custom Chat Modes

Understanding when to use each customization approach is crucial for effective AI-assisted development.

### Custom Chat Modes:
- **Location**: Defined in the repos themselves, or saved in the User Data folder in the IDE
- **Usage**: Used directly in the IDE as a means to control how Copilot behaves
- **Modes**: Can be Ask, Edit, or Agent mode
- **Purpose**: Modify how Copilot responds in chat conversations
- **Best for**: Specialized questioning, focused responses, consistent formatting

### Custom Agents:
- **Location**: Also defined in the repos themselves, or saved in the User Data folder in the IDE, but can also be saved in the Organization .github repo and set to be available to all users within the Organization
- **Usage**: Can be used in the IDE, from the CLI, or with Copilot Coding Agent
- **Modes**: Always run in agent mode and are specifically geared towards autonomous agentic development
- **Purpose**: Autonomous task execution and workflow automation
- **Best for**: Multi-step workflows, autonomous code generation, external integrations

### Decision Guide:

**Use Custom Chat Modes when:**
- You need specialized responses in chat
- You want to control tool selection for specific workflows
- You're working interactively in the IDE
- You need consistent formatting or tone

**Use Custom Agents when:**
- You need autonomous task execution
- You're delegating work to Copilot Coding Agent
- You want organization-wide standardization
- You need integration with external systems

## 💡 Best Practices

### For Custom Chat Modes:
1. **Clear Purpose**: Each mode should have a specific, well-defined purpose
2. **Tool Selection**: Only include tools that are necessary
3. **Instructions**: Be explicit about behavior, format, and priorities
4. **Testing**: Test modes with various inputs before sharing

### For Custom Agents:
1. **Be Specific in Instructions**: Clear, detailed instructions lead to better agent behavior
2. **Define Clear Scope**: Each agent should have a well-defined purpose
3. **Test Thoroughly**: Test your agents with various inputs before sharing with team
4. **Document Usage**: Include examples of how to invoke and use your agents
5. **Iterate Based on Feedback**: Refine agent instructions based on team usage
6. **Consider Security**: Be cautious about what tools and permissions agents have access to

## 🏆 Exercise Wrap-up

Excellent work! You've mastered custom chat modes and custom agents:
- ✅ Built custom chat modes for specialized workflows
- ✅ Created custom agents for autonomous task execution
- ✅ Understood the differences between custom agents and custom chat modes
- ✅ Learned when to use each customization approach
- ✅ Applied best practices for creating specialized AI assistants

### Reflection Questions:
1. **What specialized modes would help your team work more efficiently?**
2. **What autonomous workflows could be handled by custom agents?**
3. **How can you leverage organization-wide custom agents?**
4. **When should you use a chat mode vs. a custom agent?**
5. **How will you share these customizations with your team?**

### Key Takeaways:
- Custom chat modes create specialized AI personas for different tasks
- Custom agents enable autonomous task execution and workflow automation
- Understanding the difference between agents and modes helps you choose the right tool
- Organization-wide agents standardize approaches across teams
- These customizations multiply productivity across your entire team

### 📚 Learn More:
- [About Custom Agents](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-custom-agents)
- [How to Create Custom Agents](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents)
- [Awesome Copilot Agents](https://github.com/github/awesome-copilot) developed by GitHub and the community

**Ready for the next challenge? Move on to Lab 7 to learn about Model Context Protocol (MCP)!**
