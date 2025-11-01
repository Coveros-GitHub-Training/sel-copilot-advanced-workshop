# Exercise 5 - Prompt Files, Custom Chat Modes, and Model Context Protocol (MCP)

#### Duration: 45 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Create and use prompt files for consistent, reusable AI interactions
- Understand and create custom chat modes for specialized workflows  
- Set up and use the GitHub MCP (Model Context Protocol) server in your IDE
- Leverage MCP to interact with GitHub repositories, issues, and pull requests
- Build efficient workflows combining prompt files, custom modes, and MCP

## 📸 Scenario: Advanced Workflows at PixelPerfect Gallery

Your team at PixelPerfect Gallery is becoming more sophisticated with GitHub Copilot. You've noticed that:

- Developers repeat similar complex prompts for common operations
- Some workflows would benefit from specialized AI behavior
- The team needs better integration with GitHub for issue management and PR workflows
- You want to standardize how the team interacts with Copilot for specific tasks

Today, you'll learn advanced customization techniques to:
- Create reusable prompts that capture team knowledge
- Build custom AI modes tailored to specific workflows
- Integrate GitHub data directly into your IDE using MCP
- Streamline repetitive development tasks

## 📝 Part 1: Prompt Files for Consistent Generation

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

Let's create a custom prompt file for a common task in the PixelPerfect Gallery project.

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

## 🎭 Part 2: Custom Chat Modes

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
temperature: 0.7 (optional - controls creativity)
---

# Mode Behavior Instructions

Your instructions here define:
- How the AI should act
- What format to use for responses
- What to prioritize
- What to avoid
- Any special behaviors
```

**Available Tools:**
- `codebase` - Search and analyze code
- `editFiles` - Make file changes
- `search` - Search documentation/web
- `terminal` - Execute commands

### Step 2.2: Create Your Own Custom Chat Mode

Custom chat modes allow you to create specialized AI assistants for specific workflows. Let's create a simple planning mode for the PixelPerfect Gallery project.

#### Instructions:

1. **Open GitHub Copilot Chat**

2. **Click the cogwheel (⚙️)** in the top-right corner

3. **Select "Modes"** from the dropdown

4. **Click "Create new custom chat mode file..."**

5. **Choose location**: `.github/chatmodes/`

6. **Name the file**: `Plan.chatmode.md`

#### Create a Planning Mode:

Review the existing Plan.chatmode.md file in the repository, or create one with this structure:

<details>
  <summary>Example: Planning Chat Mode</summary>

  ```markdown
  ---
  description: Generate an implementation plan for new features
  tools: ['fetch', 'search']
  ---
  
  # Planning Mode Instructions
  
  You are in planning mode for the PixelPerfect Gallery application. Your task is to generate detailed implementation plans for new features or refactoring tasks.
  
  **Do not make any code edits** - just generate a comprehensive plan.
  
  ## Plan Structure
  
  Every plan should include:
  
  ### 1. Overview
  - Brief description of the feature or refactoring task
  - Business value and user benefit
  - Success criteria
  
  ### 2. Requirements
  - Functional requirements
  - Non-functional requirements (performance, accessibility, etc.)
  - Dependencies and constraints
  
  ### 3. Technical Approach
  - Architecture decisions
  - Technologies and libraries to use
  - Component structure
  - Data flow
  
  ### 4. Implementation Steps
  - Detailed, numbered steps
  - File changes required
  - Order of implementation
  - Potential challenges
  
  ### 5. Testing Strategy
  - Unit tests needed
  - Integration tests
  - Manual testing scenarios
  - Accessibility testing
  
  ### 6. Documentation
  - README updates
  - Component documentation
  - API documentation (if applicable)
  
  Consider the existing codebase structure, component patterns, and technology stack when creating plans.
  ```

</details>

#### Test Your Custom Chat Mode:

1. **Switch to your Plan mode** in Copilot Chat

2. **Ask it to plan a feature:**
   ```
   Plan a new feature for allowing users to organize photos into custom albums with drag-and-drop functionality
   ```

3. **Review the plan generated** - does it follow your template structure?

4. **Iterate on the mode** if needed to improve results

## 🔌 Part 3: Model Context Protocol (MCP) with GitHub

MCP (Model Context Protocol) is a powerful way to extend Copilot's capabilities by connecting it to external data sources and tools. Let's set up the GitHub MCP server to interact with GitHub directly from your IDE.

### Step 3.1: Understanding MCP

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

### Step 3.2: Install and Configure GitHub MCP

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

### Step 3.3: Using GitHub MCP in Your Workflow

Now that GitHub MCP is configured, let's explore practical use cases.

#### Example 1: Searching for Issues

**Ask Copilot:**
```
@github Find all open issues in this repository labeled "enhancement"
```

**What Copilot Can Do:**
- Query GitHub's API
- Filter by label, state, assignee
- Show issue titles, numbers, and descriptions
- Provide direct links

#### Example 2: Analyzing Pull Requests

**Ask Copilot:**
```
@github Show me details of PR #42 including review status and CI checks
```

**What You Get:**
- PR title and description
- Reviewer comments
- CI/CD status
- Merge conflicts (if any)
- Approval status

#### Example 3: Finding Code Examples

**Ask Copilot:**
```
@github Search for examples of React Server Components in repositories owned by vercel
```

**Benefits:**
- Learn from real-world examples
- Find established patterns
- Discover best practices

#### Example 4: Monitoring Workflows

**Ask Copilot:**
```
@github Show me the status of the latest workflow runs for this repository
```

**What You See:**
- Workflow names
- Run status (success, failure, in progress)
- Links to logs
- Failure reasons

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
- ✅ Combine MCP with custom modes for powerful workflows
- ✅ Use @github context explicitly in your prompts
- ✅ Verify MCP responses against GitHub UI when needed

## 🏆 Exercise Wrap-up

Excellent work! You've learned advanced GitHub Copilot customization techniques:
- ✅ Created and used prompt files for reusable, consistent interactions
- ✅ Built custom chat modes for specialized workflows
- ✅ Installed and configured GitHub MCP server
- ✅ Used MCP to interact with GitHub repositories, issues, and PRs
- ✅ Combined prompt files, custom modes, and MCP for powerful workflows

### Reflection Questions:
1. **What repetitive tasks in your workflow could benefit from prompt files?**
2. **What specialized modes would help your team work more efficiently?**
3. **How can GitHub MCP integration improve your development process?**
4. **What other MCP servers might benefit your team (Jira, Slack, database)?**
5. **How will you share these customizations with your team?**

### Key Takeaways:
- Prompt files capture team knowledge and ensure consistency
- Custom chat modes create specialized AI personas for different tasks
- MCP extends Copilot's capabilities by connecting to external services
- Combining these features creates powerful, automated workflows
- These customizations multiply productivity across your entire team

## 🚀 Next Steps

Now that you've mastered advanced customization:

1. **Build Your Library**
   - Create prompt files for common tasks
   - Design custom modes for your team's workflow
   - Document what works best

2. **Expand MCP Integration**
   - Explore other MCP servers (Jira, Slack, database)
   - Build custom MCP servers for internal tools
   - Automate routine tasks

3. **Share with Your Team**
   - Commit prompt files and custom modes to repo
   - Document usage in team wiki
   - Train team members on effective use

4. **Measure Impact**
   - Track time savings
   - Monitor consistency improvements
   - Gather team feedback
   - Iterate and improve

**Ready for the next challenge? Move on to Lab 6 to learn about GitHub Copilot Spaces!**
