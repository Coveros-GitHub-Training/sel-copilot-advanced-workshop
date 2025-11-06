# Exercise 7 - Model Context Protocol (MCP)

#### Duration: 15 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Set up and use the GitHub MCP (Model Context Protocol) server in your IDE
- Leverage MCP to interact with GitHub repositories, issues, and pull requests through natural conversation
- Understand how MCP extends Copilot's capabilities
- Configure MCP servers for your development workflow

## 📸 Scenario: Integrating GitHub Data at PixelPerfect Gallery

Your team at PixelPerfect Gallery needs better integration with GitHub for issue management and PR workflows. You want to access GitHub data directly from your IDE without switching contexts.

Today, you'll learn how to:
- Set up GitHub MCP server for seamless GitHub integration
- Interact with issues and PRs through natural language
- Configure MCP for optimal performance
- Extend Copilot with external data sources

## 🔌 Step 1: Understanding Model Context Protocol (MCP)

> [!IMPORTANT]
> If you are using a Codespace then you will not need to install the MCP server itself. However, you will need to configure it so that you can access all of the tools for these labs. The following process will be what you have to do when working in your IDEs directly.

[Model Context Protocol](https://github.com/modelcontextprotocol) acts as a mediator between your code base and external services. By combining GitHub Copilot with various external systems, you can expand the knowledge GitHub Copilot has access to:

- **Data stores**: Files and databases
- **Communication tools**: [Slack](https://docs.slack.dev/ai/mcp-server/)
- **Design platforms**: [Figma](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Figma-MCP-server)
- **Project management**: [Jira](https://github.com/atlassian/atlassian-mcp-server) or [Azure DevOps](https://devblogs.microsoft.com/devops/azure-devops-mcp-server-public-preview/)
- **Cloud providers**: [Azure](https://learn.microsoft.com/azure/developer/azure-mcp-server/get-started)
- And many, many more!

### Why MCP Matters:
- **Unified Interface**: Access external data without leaving your IDE
- **Natural Language**: Query systems through conversation with Copilot
- **Extensibility**: Connect any service that provides an MCP server
- **Context Enhancement**: Give Copilot access to real-time data from your tools

## 📥 Step 2: Installing the GitHub MCP Server

When looking to utilize MCP Servers, there are two primary ways of connecting your GitHub Copilot Client: through the MCP Registry and through manual configuration.

### Method 1: Using the MCP Registry (Recommended)

The [GitHub MCP Registry](https://github.com/mcp) provides a list of all currently available MCP Servers that can be easily and automatically installed.

#### Instructions:

1. **Open the MCP Registry** at https://github.com/mcp in a new browser tab

2. **Find the GitHub Server**

   <img width="557" height="170" alt="GitHub MCP Server in Registry" src="https://github.com/user-attachments/assets/82e8a1b8-066f-4a8f-858f-f6161b5d0732" />

3. **Click the "Install" drop-down**, then click "Install in VS Code"

4. **Accept opening VS Code** if prompted by your browser

5. **Click "Install"** on the extension page that appears in VS Code

6. **Link your GitHub account** to your IDE as prompted

### Method 2: Manual Configuration

To manually configure an MCP connection, you will need to decide where you want to store your configuration file:

- **Repository level**: Create a `.vscode/mcp.json` file
- **User level**: Add the configuration to your `settings.json` file in Visual Studio Code

Inside the chosen file, add a configuration like this:

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

By finding and viewing the documentation for your third-party MCP Server, you will be able to retrieve any additional information that may be required for that particular configuration. The community maintains a list of common MCP servers at https://github.com/modelcontextprotocol/servers.

### ✅ Success Criteria
- [ ] GitHub MCP Server is installed
- [ ] GitHub account is linked to the IDE
- [ ] MCP Server appears in the Extensions tab

## ⚙️ Step 3: Configuring the MCP Tools List

To enable access to all of the tools available on the GitHub MCP server, you need to add a configuration to your `mcp.json`.

### Step 3.1: Access the Configuration File

**Option 1: Direct Access**
1. Open the File searcher: `Cmd+P` (Mac) or `Ctrl+P` (Windows/Linux)
2. Search for `mcp.json`

**Option 2: Through MCP Server Tab**
1. Open the `Extensions` tab
2. Click on the `MCP Servers - Installed` section at the bottom
3. Click the settings icon on the GitHub MCP
4. Click `Show Configuration (JSON)`

### Step 3.2: Update the Configuration

Once you have the `mcp.json` file opened, update it with the following:

```json
{
  "servers": {
    // Using OAuth (version 1.101 or greater)
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "X-MCP-Toolsets": "all"
      }
    }
  }
}
```

Notice the additional headers compared to what was there before. This allows us to specify additional tool sets to make available. In this case we take all tools, but in practice you would want to be more specific.

> [!IMPORTANT]
> When prompting Copilot you can only have 128 tools active at a given time. Anything beyond that will cause a degradation in performance.

### Understanding Tool Sets:

Instead of "all", you can specify specific tool sets:
- `"X-MCP-Toolsets": "issues,pull_requests"` - Only issue and PR tools
- `"X-MCP-Toolsets": "repositories,code_search"` - Only repository and search tools
- `"X-MCP-Toolsets": "all"` - All available tools

### ✅ Success Criteria
- [ ] `mcp.json` is updated with the new configuration
- [ ] Configuration includes the GitHub server with proper headers
- [ ] No syntax errors in the JSON

## 🚀 Step 4: Using GitHub MCP Effectively

The most effective way to use GitHub MCP is through natural conversation with Copilot, letting it automatically utilize the GitHub tools when needed.

Instead of explicitly calling `@github` or directly referencing a tool from the MCP, simply ask Copilot questions about your GitHub repositories in natural language. Copilot will automatically use the GitHub MCP tools when appropriate.

### Step 4.1: Enable Issues in Your Repository

> **Note:** Before testing out the MCP, ensure that you have Issues enabled in your repository
>   - Go to `Settings` > `General`
>   - Scroll to the `Features` section
>   - Check the `Issues` box (enable it)
>   - Return to the repository (refresh if needed) before proceeding

### Step 4.2: Try Natural Language Queries

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

### Step 4.3: Observe MCP in Action

When you ask these questions, observe:
- How Copilot automatically selects the right GitHub tools
- The structured data returned from GitHub
- How the response integrates GitHub data with code context
- No need to explicitly call `@github` or specific commands

## 💡 Step 5: MCP Best Practices

### Effective Prompting:
1. **Be Natural**: Ask questions in plain language
2. **Be Specific**: Include filters like labels, assignees, or status
3. **Trust Automation**: Let Copilot choose the right tools
4. **Iterate**: Refine your question if the first response isn't what you need

### Configuration Tips:
1. **Selective Tools**: Only enable tool sets you need for better performance
2. **Monitor Limits**: Stay under 128 tools for optimal performance
3. **Organization-wide**: Consider organization-level MCP configurations
4. **Security**: Review MCP server permissions and access

### Common Use Cases:
- **Issue Management**: Query, filter, and triage issues
- **PR Reviews**: Check PR status, get review feedback
- **Code Search**: Find patterns across repositories
- **Repository Info**: Get metadata, stats, and information
- **Team Collaboration**: Find work by team members

## 🌐 Step 6: Exploring Other MCP Servers

The MCP ecosystem extends far beyond GitHub. Consider adding these MCP servers based on your team's needs:

### Communication:
- **Slack MCP**: Access Slack channels, messages, and threads
- Query: "What did the team discuss about the API refactor?"

### Project Management:
- **Jira MCP**: Interact with Jira issues and projects
- Query: "Show me all high-priority tickets assigned to me"
- **Azure DevOps MCP**: Work with Azure DevOps work items
- Query: "What's the status of our current sprint?"

### Design:
- **Figma MCP**: Access Figma designs and components
- Query: "Show me the latest button component specs from Figma"

### Cloud:
- **Azure MCP**: Interact with Azure resources
- Query: "What's the current status of our production environment?"

### Development:
- **Database MCP**: Query databases directly
- **File System MCP**: Enhanced file operations
- **Git MCP**: Advanced Git operations

Visit https://github.com/modelcontextprotocol/servers for a complete list of available MCP servers.

## 🏆 Exercise Wrap-up

Excellent work! You've mastered Model Context Protocol integration:
- ✅ Installed and configured GitHub MCP server
- ✅ Used MCP to interact with GitHub repositories, issues, and PRs through natural conversation
- ✅ Learned to configure MCP tools for optimal performance
- ✅ Understood how MCP extends Copilot's capabilities
- ✅ Explored the broader MCP ecosystem

### Reflection Questions:
1. **How can GitHub MCP integration improve your development process?**
2. **What other MCP servers might benefit your team (Jira, Slack, database)?**
3. **What workflows could be streamlined with MCP integrations?**
4. **How would you balance tool availability with performance?**
5. **What security considerations should you keep in mind with MCP?**

### Key Takeaways:
- MCP extends Copilot's capabilities by connecting to external services
- Natural conversation with MCP is more effective than explicit commands
- Selective tool configuration maintains optimal performance
- The MCP ecosystem provides integrations for many popular tools
- MCP creates a unified interface for accessing diverse data sources
- Combining MCP with other Copilot features creates powerful workflows

**Ready for the next challenge? Move on to Lab 8 to learn about GitHub Copilot Spaces!**
