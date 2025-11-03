# Exercise 5 - Prompt Files, Custom Chat Modes, Custom Agents, and Model Context Protocol (MCP)

#### Duration: 60 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Create and use prompt files for consistent, reusable AI interactions
- Understand and create custom chat modes for specialized workflows
- Create custom agents for autonomous task execution
- Understand the differences between custom agents and custom chat modes
- Set up and use the GitHub MCP (Model Context Protocol) server in your IDE
- Leverage MCP to interact with GitHub repositories, issues, and pull requests through natural conversation
- Build efficient workflows combining prompt files, custom modes, custom agents, and MCP

## 📸 Scenario: Advanced Workflows at PixelPerfect Gallery

Your team at PixelPerfect Gallery is becoming more sophisticated with GitHub Copilot. You've noticed that:

- Developers repeat similar complex prompts for common operations
- Some workflows would benefit from specialized AI behavior
- The team needs better integration with GitHub for issue management and PR workflows
- You want to standardize how the team interacts with Copilot for specific tasks

Today, you'll learn advanced customization techniques to:
- Create reusable prompts that capture team knowledge
- Build custom AI modes tailored to specific workflows
- Create custom agents for autonomous task execution
- Integrate GitHub data directly into your IDE using MCP
- Streamline repetitive development tasks

## 📝 Step 1: Prompt Files for Consistent Generation

Prompt files allow you to create reusable, standardized prompts that maintain consistency across your team and save time on repetitive tasks.

### Step 1.1: Understanding Prompt Files

#### Why Prompt Files Matter:
- **Consistency**: Same prompt structure every time
- **Efficiency**: No need to retype complex prompts
- **Standardization**: Team uses the same approaches
- **Knowledge sharing**: Capture expert prompting techniques

### Step 1.2: Explore Existing Prompt Files

#### Explore Existing Prompt Files:

1. **Navigate to `.github/prompts/` folder**

2. **Open and review the existing prompt files:**
   - `generate-mock-photo-data.prompt.md`
   - `generate-new-ui.prompt.md`
   - `create-copilot-demo.prompt.md`

3. **Notice the format:**
   ```markdown
   ---
   description: 'What this prompt does'
   mode: 'edit'
   model: 'optional-specific-model'
   ---
   
   Your prompt template here with ${input:variableName:placeholder}
   ```

#### Use a Prompt File:

**Generate Mock Data:**
```
/generate-mock-photo-data 3
```

**Generate UI Component:**
```
/generate-new-ui for a photo card component that displays a photo thumbnail with title and photographer name. Place it in the gallery folder.
```

#### Understanding Prompt File Components:

**Header (YAML):**
- `description`: What the prompt does
- `mode`: 'ask', 'edit', or 'agent'
- `model`: (optional) Specific AI model to use
- `tools`: (optional) Specific tools to enable

**Body (Markdown):**
- Natural language instructions
- Variables: `${input:variableName:placeholder}`
- Workspace variables: `${workspaceFolder}`, `${file}`, etc.
- Context references: `@filename` or specific file paths

**Available Variables:**
- `${workspaceFolder}` - Current workspace path
- `${file}` - Current file path
- `${selection}` - Selected text
- `${input:name:placeholder}` - User input with placeholder

### Step 1.3: Create Your Own Prompt File

Let's create a custom prompt file for a common task in the PixelPerfect Gallery project. You'll create a prompt file that generates a new photo-related React component with TypeScript, following the project's conventions for styling and structure.

#### Enable Prompt Files (if needed)

1. Open VS Code Settings: `Cmd+,` (Mac) or `Ctrl+,` (Windows/Linux)
2. Search for "Prompt file"
3. Ensure "Chat: Prompt Files" is enabled

#### Create the Prompt File

**Method 1: Using Copilot Chat UI**
1. Open GitHub Copilot Chat
2. Click the cogwheel (⚙️) in the top-right corner
3. Select "Prompt Files"
4. Click "New prompt file..."
5. Choose `.github/prompts/` as the location
6. Name it `generate-photo-component.prompt.md`

**Method 2: Create Manually**

Create a new file at `.github/prompts/generate-photo-component.prompt.md`

#### Sample Prompt File to Create:

<details>
  <summary>Example: Generate Photo Component Prompt</summary>

  ```markdown
  ---
  description: 'Generate a new photo-related React component with TypeScript'
  agent: 'edit'
  ---
  
  Create a new React component for the PixelPerfect Gallery photo application.
  
  Component name: ${input:componentName:PhotoCard}
  Component purpose: ${input:purpose:Display a photo with metadata}
  Location: src/components/gallery/${input:componentName}.tsx
  
  Requirements:
  - Use TypeScript with proper interface definitions
  - Use Tailwind CSS for styling with dark mode support
  - Follow Next.js 15 best practices
  - Make it responsive (mobile-first)
  - Include proper accessibility attributes
  - Export as default
  - Follow the existing component patterns in src/components/ui/
  
  The component should be reusable and maintainable.
  ```

</details>

#### Test Your Prompt File:

1. In Copilot Chat, type `/` followed by your prompt file name
2. Provide the values for the input variables specified. I.e. `/generate-photo-component with componentName newComponent`
3. Press Enter
4. Review the generated code

## 🎭 Step 2: Custom Chat Modes

Chat modes define how GitHub Copilot behaves for specialized workflows. Let's create a custom mode for super powered agnetic action.

### Step 2.1: Understanding Custom Chat Modes

#### Why Custom Chat Modes:
- **Specialized workflows**: Tailor AI behavior to specific tasks
- **Tool selection**: Pre-configure which tools to use
- **Model preference**: Specify best model for the task
- **Consistent approach**: Same methodology every time
- **Role specialization**: Create expert personas for different tasks
- **Context optimization**: Pre-load relevant information
- **Output formatting**: Standardize responses
- **Workflow automation**: Multi-step processes in one mode

#### Understanding Chat Mode Architecture

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

### Step 2.2: Create Your Own Custom Chat Mode

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

#### Create a BeastMode Chat Mode:

The official BeastMode instructions can be found in [Burke Hollands](https://gist.githubusercontent.com/burkeholland/88af0249c4b6aff3820bf37898c8bacf/raw/e1898331f1755aff3265d50e30106b8c6987c4f7/beastmode3.1.chatmode.md) repo or you can use the current version that has been included in this repo [References/BeastMode.md](../References/BeastMode.md).

#### Test Your BeastMode:

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

## 🤖 Step 3: Custom Agents

Custom agents are a powerful new feature in GitHub Copilot that allow you to create specialized, autonomous AI assistants for specific development tasks. Unlike custom chat modes which modify how Copilot responds in chat, custom agents can take action on your behalf.

### Step 3.1: Understanding Custom Agents

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

### Step 3.2: Creating a Custom Agent

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

#### Example: Create a language specific agent

Let's create a custom agent that excels at C#

1. **Create the agent directory** (if it doesn't exist):
   ```bash
   mkdir -p .github/agents
   ```

2. **Create a new agent file**: `.github/agents/csharp-expert.yml`

<details>
  <summary>Example: C# Agent</summary>

  ```yaml
  ---
  name: C# Expert
  description: An agent designed to assist with software development tasks for .NET projects.
  # version: 2025-10-27a
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


  ## Goals for .NET Applications

  ### Productivity
  - Prefer modern C# (file-scoped ns, raw """ strings, switch expr, ranges/indices, async streams) when TFM allows.
  - Keep diffs small; reuse code; avoid new layers unless needed.
  - Be IDE-friendly (go-to-def, rename, quick fixes work).

  ### Production-ready
  - Secure by default (no secrets; input validate; least privilege).
  - Resilient I/O (timeouts; retry with backoff when it fits).
  - Structured logging with scopes; useful context; no log spam.
  - Use precise exceptions; don’t swallow; keep cause/context.

  ### Performance
  - Simple first; optimize hot paths when measured.
  - Stream large payloads; avoid extra allocs.
  - Use Span/Memory/pooling when it matters.
  - Async end-to-end; no sync-over-async.

  ### Cloud-native / cloud-ready
  - Cross-platform; guard OS-specific APIs.
  - Diagnostics: health/ready when it fits; metrics + traces.
  - Observability: ILogger + OpenTelemetry hooks.
  - 12-factor: config from env; avoid stateful singletons.

  # .NET quick checklist

  ## Do first

  * Read TFM + C# version.
  * Check `global.json` SDK.

  ## Initial check

  * App type: web / desktop / console / lib.
  * Packages (and multi-targeting).
  * Nullable on? (`<Nullable>enable</Nullable>` / `#nullable enable`)
  * Repo config: `Directory.Build.*`, `Directory.Packages.props`.

  ## C# version

  * **Don't** set C# newer than TFM default.
  * C# 14 (NET 10+): extension members; `field` accessor; implicit `Span<T>` conv; `?.=`; `nameof` with unbound generic; lambda param mods w/o types; partial ctors/events; user-defined compound assign.

  ## Build

  * .NET 5+: `dotnet build`, `dotnet publish`.
  * .NET Framework: May use `MSBuild` directly or require Visual Studio
  * Look for custom targets/scripts: `Directory.Build.targets`, `build.cmd/.sh`, `Build.ps1`.

  ## Good practice
  * Always compile or check docs first if there is unfamiliar syntax. Don't try to correct the syntax if code can compile.
  * Don't change TFM, SDK, or `<LangVersion>` unless asked.


  # Async Programming Best Practices

  * **Naming:** all async methods end with `Async` (incl. CLI handlers).
  * **Always await:** no fire-and-forget; if timing out, **cancel the work**.
  * **Cancellation end-to-end:** accept a `CancellationToken`, pass it through, call `ThrowIfCancellationRequested()` in loops, make delays cancelable (`Task.Delay(ms, ct)`).
  * **Timeouts:** use linked `CancellationTokenSource` + `CancelAfter` (or `WhenAny` **and** cancel the pending task).
  * **Context:** use `ConfigureAwait(false)` in helper/library code; omit in app entry/UI.
  * **Stream JSON:** `GetAsync(..., ResponseHeadersRead)` → `ReadAsStreamAsync` → `JsonDocument.ParseAsync`; avoid `ReadAsStringAsync` when large.
  * **Exit code on cancel:** return non-zero (e.g., `130`).
  * **`ValueTask`:** use only when measured to help; default to `Task`.
  * **Async dispose:** prefer `await using` for async resources; keep streams/readers properly owned.
  * **No pointless wrappers:** don’t add `async/await` if you just return the task.

  ## Immutability
  - Prefer records to classes for DTOs

  # Testing best practices

  ## Test structure

  - Separate test project: **`[ProjectName].Tests`**.
  - Mirror classes: `CatDoor` -> `CatDoorTests`.
  - Name tests by behavior: `WhenCatMeowsThenCatDoorOpens`.
  - Follow existing naming conventions.
  - Use **public instance** classes; avoid **static** fields.
  - No branching/conditionals inside tests.

  ## Unit Tests

  - One behavior per test;
  - Avoid Unicode symbols.
  - Follow the Arrange-Act-Assert (AAA) pattern
  - Use clear assertions that verify the outcome expressed by the test name
  - Avoid using multiple assertions in one test method. In this case, prefer multiple tests.
  - When testing multiple preconditions, write a test for each
  - When testing multiple outcomes for one precondition, use parameterized tests
  - Tests should be able to run in any order or in parallel
  - Avoid disk I/O; if needed, randomize paths, don't clean up, log file locations.
  - Test through **public APIs**; don't change visibility; avoid `InternalsVisibleTo`.
  - Require tests for new/changed **public APIs**.
  - Assert specific values and edge cases, not vague outcomes.

  ## Test workflow

  ### Run Test Command
  - Look for custom targets/scripts: `Directory.Build.targets`, `test.ps1/.cmd/.sh`
  - .NET Framework: May use `vstest.console.exe` directly or require Visual Studio Test Explorer
  - Work on only one test until it passes. Then run other tests to ensure nothing has been broken.

  ### Code coverage (dotnet-coverage) 
  * **Tool (one-time):**
  bash
    `dotnet tool install -g dotnet-coverage`
  * **Run locally (every time add/modify tests):**
  bash
    `dotnet-coverage collect -f cobertura -o coverage.cobertura.xml dotnet test`

  ## Test framework-specific guidance

  - **Use the framework already in the solution** (xUnit/NUnit/MSTest) for new tests.

  ### xUnit

  * Packages: `Microsoft.NET.Test.Sdk`, `xunit`, `xunit.runner.visualstudio`
  * No class attribute; use `[Fact]`
  * Parameterized tests: `[Theory]` with `[InlineData]`
  * Setup/teardown: constructor and `IDisposable`

  ### xUnit v3

  * Packages: `xunit.v3`, `xunit.runner.visualstudio` 3.x, `Microsoft.NET.Test.Sdk`
  * `ITestOutputHelper` and `[Theory]` are in `Xunit`

  ### NUnit

  * Packages: `Microsoft.NET.Test.Sdk`, `NUnit`, `NUnit3TestAdapter`
  * Class `[TestFixture]`, test `[Test]`
  * Parameterized tests: **use `[TestCase]`**

  ### MSTest

  * Class `[TestClass]`, test `[TestMethod]`
  * Setup/teardown: `[TestInitialize]`, `[TestCleanup]`
  * Parameterized tests: **use `[TestMethod]` + `[DataRow]`**

  ### Assertions

  * If **FluentAssertions/AwesomeAssertions** are already used, prefer them.
  * Otherwise, use the framework’s asserts.
  * Use `Throws/ThrowsAsync` (or MSTest `Assert.ThrowsException`) for exceptions.

  ## Mocking

  - Avoid mocks/Fakes if possible
  - External dependencies can be mocked. Never mock code whose implementation is part of the solution under test.
  - Try to verify that the outputs (e.g. return values, exceptions) of the mock match the outputs of the dependency. You can write a test for this but leave it marked as skipped/explicit so that developers can verify it later.
  ```

</details>

#### Step 3.3: Using Custom Agents

Once created, you can invoke your custom agent in Copilot Chat by selecting it from the mode dropdown:

> Tip: You can also use custom agents in the CLI as well as with Copilot Coding Agent in GitHub.com which we will cover in Lab 7

```
If I wanted to rebuild this application using .NET and blazor and written in C# how would I do that?
```

The agent will:
1. Analyze the specified files
2. Use its specialized instructions to perform the analysis
3. Provide detailed, actionable feedback
4. Suggest specific next steps if you want to proceed

### Step 3.4: Custom Agents vs Custom Chat Modes

Custom Agents and Custom Chat Modes have a lot in common but they differ in where you should use them.

Custom Chat Modes:
- Defined in the repos themselves, or saved in the User Data folder in the IDE
- Are used directly in the IDE as a means to control how Copilot behaves
- Can be Ask, Edit, or Agent mode

Custom Agents:
- Aslo defined in the repos themselves, or saved in the User Data folder in the IDE, but can also be saved in the Organization .github repo and set to be available to all users within the Organization
- Can be used in the IDE, from the CLI, or with Copilot Coding Agent
- Always run in agent mode and are specifically geared towards autonomous agentic development

### 💡 Custom Agent Best Practices:

1. **Be Specific in Instructions**: Clear, detailed instructions lead to better agent behavior
2. **Define Clear Scope**: Each agent should have a well-defined purpose
3. **Test Thoroughly**: Test your agents with various inputs before sharing with team
4. **Document Usage**: Include examples of how to invoke and use your agents
5. **Iterate Based on Feedback**: Refine agent instructions based on team usage
6. **Consider Security**: Be cautious about what tools and permissions agents have access to

### 📚 Learn More:

- [About Custom Agents](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-custom-agents)
- [How to Create Custom Agents](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents)
- [Awesome Copilot Agents](https://github.com/github/awesome-copilot) developed by GitHub and the community

## 🔌 Step 4: Model Context Protocol (MCP) with GitHub

[Model Context Protocol](https://github.com/modelcontextprotocol) acts as a mediator between your code base and external services. By combining GitHub Copilot with various external systems, you can expand the knowledge GitHub Copilot has access to:

- **Data stores**: Files and databases
- **Communication tools**: [Slack](https://docs.slack.dev/ai/mcp-server/)
- **Design platforms**: [Figma](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Figma-MCP-server)
- **Project management**: [Jira](https://github.com/atlassian/atlassian-mcp-server) or [Azure DevOps](https://devblogs.microsoft.com/devops/azure-devops-mcp-server-public-preview/)
- **Cloud providers**: [Azure](https://learn.microsoft.com/azure/developer/azure-mcp-server/get-started)
- And many, many more!  

### Step 4.1: Getting the GitHub MCP Server up and running

When looking to utilize MCP Servers, there are two primary ways of connecting your GitHub Copilot Client: through the MCP Registry and through manual configuration.

The [GitHub MCP Registry](https://github.com/mcp) provides a list of all currently available MCP Servers that can be easily and automatically installed. Simply find the MCP Server you need, click the appropriate "Install" drop-down menu, then choose the version of VS Code for which you would like to install that Server.

To manually configure an MCP connection, you will need to decide where you want to store your configuration file:

- To store the configuration at the repository level, create a `.vscode/mcp.json` file
- To store the configuration for your local device across workspaces, add the configuration to your `settings.json` file in Visual Studio Code

Inside the chosen file, you will add a configuration such as this template below...

```json
{
"inputs": [
  // The "inputs" section defines the inputs required for the MCP server configuration.
  {
    "type": "promptString"
  }
],
"servers": {
  // The "servers" section defines the MCP servers you want to use.
  "fetch": {
    "command": "uvx",
    "args": ["mcp-server-fetch"]
  }
 }
}
```

By finding and viewing the documentation for your third-party MCP Server, you will be able to retrieve any additional information that may be required for that particular configuration. The communuity maintains a list of common MCP servers at https://github.com/modelcontextprotocol/servers.

1. Start by opening up [the MCP Registry](https://github.com/mcp) in a new browser tab or window.
2. Find the GitHub Server

<img width="557" height="170" alt="image" src="https://github.com/user-attachments/assets/82e8a1b8-066f-4a8f-858f-f6161b5d0732" />

3. Click the "Install" drop-down, then click "Install in VS Code"
4. If prompted by your browser, accept opening VS Code
5. In your IDE, an extension page for the GitHub MCP Server should be displayed. Click "Install".
6. Link your GitHub account to your IDE as prompted

With that, you should be all set to begin work with the MCP Server.

### Step 4.2: Using GitHub MCP Effectively

The most effective way to use GitHub MCP is through natural conversation with Copilot, letting it automatically utilize the GitHub tools when needed.

Instead of explicitly calling `@github`, simply ask Copilot questions about your GitHub repositories in natural language. Copilot will automatically use the GitHub MCP tools when appropriate.

**Examples of Effective Prompts:**

**Finding Issues:**
```
What open issues are labeled "bug" in this repository?
```
or
```
Show me all enhancement requests that haven't been assigned yet
```

**Working with Pull Requests:**
```
What's the current status of pull request #42?
```
or
```
Are there any PRs that need review?
```

**Analyzing Code Across Repositories:**
```
Find examples of authentication middleware in my organization's repos
```
or
```
How do other projects in my org handle error logging?
```

## 🏆 Exercise Wrap-up

Excellent work! You've learned advanced GitHub Copilot customization techniques:
- ✅ Created and used prompt files for reusable, consistent interactions
- ✅ Built custom chat modes for specialized workflows
- ✅ Created custom agents for autonomous task execution
- ✅ Understood the differences between custom agents and custom chat modes
- ✅ Installed and configured GitHub MCP server
- ✅ Used MCP to interact with GitHub repositories, issues, and PRs through natural conversation
- ✅ Combined prompt files, custom modes, custom agents, and MCP for powerful workflows

### Reflection Questions:
1. **What repetitive tasks in your workflow could benefit from prompt files?**
2. **What specialized modes would help your team work more efficiently?**
3. **What autonomous workflows could be handled by custom agents?**
4. **How can GitHub MCP integration improve your development process?**
5. **What other MCP servers might benefit your team (Jira, Slack, database)?**
6. **How will you share these customizations with your team?**

### Key Takeaways:
- Prompt files capture team knowledge and ensure consistency
- Custom chat modes create specialized AI personas for different tasks
- Custom agents enable autonomous task execution and workflow automation
- Understanding the difference between agents and modes helps you choose the right tool
- MCP extends Copilot's capabilities by connecting to external services
- Natural conversation with MCP is more effective than explicit commands
- Combining these features creates powerful, automated workflows
- These customizations multiply productivity across your entire team

**Ready for the next challenge? Move on to Lab 6 to learn about GitHub Copilot Spaces!**
