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
- **Parameterization**: Customize with input variables
- **Documentation**: Self-documenting common workflows
- **Knowledge sharing**: Capture expert prompting techniques
- **Onboarding**: New team members use proven patterns
- **Quality control**: Enforce best practices automatically

### Step 1.2: Explore Existing Prompt Files

#### Why Prompt Files Matter:
- **Consistency**: Same prompt structure every time
- **Efficiency**: No need to retype complex prompts
- **Standardization**: Team uses the same approaches
- **Parameterization**: Customize with input variables
- **Documentation**: Self-documenting common workflows
- **Knowledge sharing**: Capture expert prompting techniques
- **Onboarding**: New team members use proven patterns
- **Quality control**: Enforce best practices automatically

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
  mode: 'edit'
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
2. Press Enter
3. Fill in any requested input variables
4. Review the generated code

## 🎭 Step 2: Custom Chat Modes

Chat modes define how GitHub Copilot behaves for specialized workflows. Let's create a custom mode for planning new features.

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

<details>
  <summary>Example: BeastMode Chat Mode</summary>

  ```markdown
  ---
  description: Maximum power mode with all tools enabled for complex development tasks
  tools: ['codebase', 'fetch', 'search', 'githubRepo', 'findTestFiles', 'usages']
  ---
  
  # BeastMode Instructions
  
  You are in BeastMode - a supercharged development assistant with maximum capabilities enabled. You have access to all available tools to help solve complex development challenges efficiently.
  
  ## Your Capabilities
  
  With all tools at your disposal, you can:
  - Search and analyze the entire codebase
  - Fetch content from external URLs and documentation
  - Search the web for solutions and best practices
  - Access GitHub repository information
  - Locate and analyze test files
  - Find usages of code across the project
  
  ## Your Approach
  
  When assisting with development tasks:
  
  1. **Understand Context First**: Use codebase analysis to understand the existing patterns and architecture
  2. **Research Best Practices**: Leverage search and fetch to find current best practices
  3. **Find Related Code**: Use usages and codebase tools to identify related implementations
  4. **Consider Tests**: Check test files to understand testing patterns
  5. **Provide Complete Solutions**: Offer comprehensive answers with code examples, explanations, and alternatives
  
  ## Response Style
  
  - Be direct and actionable
  - Provide working code examples
  - Explain your reasoning
  - Suggest optimizations and improvements
  - Point out potential issues or edge cases
  - Reference relevant documentation when helpful
  
  ## When to Suggest Tools
  
  - Recommend specific tools when they would help solve the problem
  - Explain how to use different Copilot features effectively
  - Share keyboard shortcuts and productivity tips
  
  You're here to maximize developer productivity and solve complex problems efficiently.
  ```

</details>

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
- **Use specialized tools**: Access specific APIs, databases, or services
- **Execute complex workflows**: Chain multiple operations together
- **Maintain context**: Remember information across interactions
- **Integrate with external systems**: Connect to your organization's tools and services

#### Why Use Custom Agents?

**Custom agents excel at:**
- **Repetitive workflows**: Automating multi-step processes
- **Specialized tasks**: Domain-specific operations (database queries, API testing, deployment)
- **Integration tasks**: Connecting different systems and tools
- **Code generation with validation**: Generating and testing code automatically
- **Research and analysis**: Gathering information from multiple sources

**Example Use Cases:**
- A database agent that can query your database and generate migration scripts
- A testing agent that generates tests and runs them automatically
- A documentation agent that updates docs based on code changes
- A deployment agent that handles release workflows
- A security agent that scans for vulnerabilities and suggests fixes

### Step 3.2: Creating a Custom Agent

Custom agents are defined in the `.github/agents/` directory of your repository.

#### Agent Configuration Structure:

```yaml
# .github/agents/my-agent.yml
name: my-agent
description: A brief description of what this agent does
instructions: |
  Detailed instructions for how the agent should behave.
  This is where you define the agent's expertise and approach.
  
tools:
  - name: tool-name
    description: What this tool does
    configuration:
      # Tool-specific configuration
```

#### Example: Create a Code Review Agent

Let's create a custom agent that performs focused code reviews.

1. **Create the agent directory** (if it doesn't exist):
   ```bash
   mkdir -p .github/agents
   ```

2. **Create a new agent file**: `.github/agents/code-reviewer.yml`

<details>
  <summary>Example: Code Review Agent</summary>

  ```yaml
  name: code-reviewer
  description: Performs thorough code reviews with focus on best practices and potential issues
  instructions: |
    You are a senior code reviewer for the PixelPerfect Gallery project. Your role is to:
    
    1. **Review code quality**:
       - Check for code smells and anti-patterns
       - Verify adherence to project conventions
       - Identify potential bugs or edge cases
       - Suggest performance improvements
    
    2. **Verify best practices**:
       - TypeScript usage and type safety
       - React/Next.js best practices
       - Accessibility compliance
       - Security considerations
    
    3. **Check consistency**:
       - Naming conventions
       - Code style and formatting
       - Component patterns
       - Import organization
    
    4. **Provide actionable feedback**:
       - Explain why something should be changed
       - Suggest specific improvements
       - Prioritize critical issues
       - Offer alternatives when appropriate
    
    Always be constructive and educational in your reviews.
    
  tools:
    - codebase
    - search
  ```

</details>

#### Step 3.3: Using Custom Agents

Once created, you can invoke your custom agent in Copilot Chat:

```
@code-reviewer Please review the changes in src/components/gallery/GalleryGrid.tsx
```

The agent will:
1. Analyze the specified file(s)
2. Use its specialized instructions to perform the review
3. Provide detailed, actionable feedback
4. Suggest specific improvements

### Step 3.4: Custom Agents vs Custom Chat Modes

Understanding when to use custom agents versus custom chat modes is important:

| Feature | Custom Chat Modes | Custom Agents |
|---------|------------------|---------------|
| **Purpose** | Change how Copilot responds in chat | Create specialized autonomous assistants |
| **Interaction** | Conversational, requires user guidance | Can act autonomously with specific tools |
| **Scope** | Affects chat behavior and response style | Executes specific tasks and workflows |
| **Tools** | Limited to built-in Copilot tools | Can use custom integrations and APIs |
| **Use Case** | Specialized response formats, context-aware conversations | Automated workflows, system integrations, complex multi-step tasks |
| **Configuration** | `.github/chatmodes/*.chatmode.md` | `.github/agents/*.yml` |

**Choose Custom Chat Modes when you want to:**
- Change how Copilot formats responses
- Add specialized context to conversations
- Enable specific built-in tools
- Create different "personalities" for different workflows

**Choose Custom Agents when you want to:**
- Automate complex multi-step workflows
- Integrate with external systems and APIs
- Create task-specific autonomous assistants
- Execute actions without constant user approval

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

## 🔌 Step 4: Model Context Protocol (MCP) with GitHub

MCP (Model Context Protocol) is a powerful way to extend Copilot's capabilities by connecting it to external data sources and tools. Let's set up the GitHub MCP server to interact with GitHub directly from your IDE.

### Step 4.1: Understanding MCP

#### What is MCP?

Model Context Protocol is an open standard that allows AI models to securely connect to:
- External data sources (databases, APIs, file systems)
- Tools and services (GitHub, Jira, Slack, etc.)
- Custom integrations you build

#### Why Use MCP with GitHub?

The GitHub MCP server allows Copilot to:
- **Search repositories**: Find code, issues, PRs across all your repos
- **Read issues**: Get issue details, comments, labels
- **View pull requests**: See PR content, reviews, status
- **Check workflows**: Monitor CI/CD status, view logs
- **Search code**: Find examples across GitHub
- **Explore repository structure**: Understand project organization

This means you can ask Copilot questions like:
- "Show me all open issues labeled 'bug' in this repo"
- "What's the status of PR #123?"
- "Find examples of authentication middleware in my organization's repositories"
- "Show me the latest CI/CD run results"

### Step 4.2: Install and Configure GitHub MCP

#### Prerequisites:

- Node.js 18+ installed
- GitHub account with appropriate permissions
- GitHub Personal Access Token (PAT)

#### Installation Steps:

**1. Install the GitHub MCP Server**

```bash
npm install -g @modelcontextprotocol/server-github
```

**2. Create a GitHub Personal Access Token**

1. Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Click "Generate new token" → "Generate new token (classic)"
3. Give it a descriptive name: "Copilot MCP Server"
4. Select scopes:
   - `repo` (Full control of private repositories)
   - `read:org` (Read org and team membership)
   - `workflow` (Update GitHub Action workflows)
5. Click "Generate token"
6. **Copy the token** - you won't see it again!

**3. Configure MCP in VS Code**

Create or edit your VS Code settings for Copilot MCP:

**Location**: `~/.vscode/settings.json` or workspace `.vscode/settings.json`

```json
{
  "github.copilot.chat.mcp.servers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your-github-token-here"
      }
    }
  }
}
```

**Security Note**: For production use, store the token in a secure environment variable:

```json
{
  "github.copilot.chat.mcp.servers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${env:GITHUB_MCP_TOKEN}"
      }
    }
  }
}
```

Then set the environment variable:
```bash
# On macOS/Linux
export GITHUB_MCP_TOKEN="your-token-here"

# On Windows PowerShell
$env:GITHUB_MCP_TOKEN="your-token-here"
```

**4. Reload VS Code**

1. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Type "Reload Window"
3. Press Enter

**5. Verify MCP Connection**

1. Open GitHub Copilot Chat
2. Type `@github` to see if the GitHub MCP server is available
3. You should see GitHub as an available context source

### Step 4.3: Using GitHub MCP Effectively

The most effective way to use GitHub MCP is through natural conversation with Copilot, letting it automatically utilize the GitHub tools when needed.

#### Best Practice: Natural Conversational Approach

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

**Monitoring CI/CD:**
```
Did the latest build pass?
```
or
```
Why did the main branch workflow fail?
```

#### How It Works:

1. **Copilot analyzes your question** and determines if GitHub data would help answer it
2. **Automatically selects appropriate tools** from the MCP server
3. **Retrieves the information** from GitHub's API
4. **Presents results** in a clear, actionable format

#### When to Be More Specific:

If Copilot isn't using the GitHub MCP tools when you expect it to, you can be more explicit:

```
Use GitHub API to find all issues labeled "high-priority" in the pixelperfect-gallery repository
```

#### Example Workflow: Investigating a Build Failure

**You:** "The main branch build is failing. What happened?"

**Copilot will:**
1. Check the latest workflow runs using GitHub MCP
2. Identify which job failed
3. Retrieve relevant error logs
4. Explain the cause
5. Suggest fixes based on the error

**You can then ask:** "Show me the changes in the commits from that run"

**Copilot will:**
1. Find the commits associated with the workflow run
2. Show you the relevant code changes
3. Help identify which change likely caused the failure

### 💡 MCP Best Practices:

**Security:**
- ✅ Use environment variables for tokens
- ✅ Limit token permissions to what you need
- ✅ Rotate tokens regularly
- ✅ Never commit tokens to version control
- ✅ Use fine-grained tokens when possible

**Performance:**
- ✅ Be specific in your queries to reduce API calls
- ✅ Be mindful of GitHub API rate limits
- ✅ Use pagination for large result sets

**Usage:**
- ✅ Use natural language questions - Copilot will automatically use MCP when appropriate
- ✅ Be specific in your questions to get better results
- ✅ Combine MCP with custom modes for powerful workflows
- ✅ Verify MCP responses against GitHub UI when needed

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
