# Customize Copilot Demo

Welcome to the GitHub Copilot customization demo! Here you'll learn how to tailor GitHub Copilot to your specific needs and workflow preferences. This demo covers advanced features that help you optimize your AI-assisted coding experience for maximum productivity.

## What You'll Learn
By the end of this demo, you will:
- [ ] Know how to monitor your premium request usage
- [ ] Switch between AI models in Chat and Code completions (OPTIONAL)
- [ ] Use prompt files for consistent AI interactions
- [ ] Utilize Chat modes for various development tasks
- [ ] Set up custom instructions with MCP servers for personalized AI behavior

**Estimated Time:** 25-30 minutes

---

## 📊 Step 1: Monitor Premium Request

### Option A: Access the Premium Dashboard

In IDE:

1. **Open VS Code** and ensure GitHub Copilot is active
2. **Locate Copilot status:** Look for the GitHub Copilot logo in the bottom-right status bar

### Option B: Access the Premium Dashboard

In github.com:

1. **Navigate to GitHub:** Go to [https://github.com/settings/copilot/features](https://github.com/settings/copilot/features)
2. **Sign in:** Ensure you're logged into your GitHub account
3. **View dashboard:** Review your premium request usage percentage and limits

View premium request percentage to understand how many requests you have left.

---

## 🔄 Step 2: Advanced Model Switching (OPTIONAL)

Mode: edit

For this demo, try the same coding task with different models and note the differences.

### Instructions

1. Update your mode to **edit**
2. Select the model you want to try out
3. Add the following files to the GitHub Copilot Chat UI as related files. You can do so but selecting `Add Context` and typing in the name of each file. OR close out all tabs, then open these three files. Select `Add Context`, then `Open Editors` to grab all open files in your IDE. Either way will gather the below files.
```markdown
- /src/app/gallery/page.tsx
- /src/lib/mock-photo-data.ts
- /src/components/GalleryGrid.tsx
```
4. Stay on the last page: GalleryGrid and highlight lines 26 - 43
5. Add in below prompt:

Prompt
```typescript
// Ask each model: "Help me refactor this function for better performance, readability, and add TypeScript improvements"
```

Repeat steps 2-5 for two other models of your choosing.

Which answers did you like the best? which the least? Discuss in your group.

---

## 📝 Step 3: Use Prompt Files

1. Go to the `/.github/prompts` folder and look through the files.
- There are two files to choose from each in varying difficult levels.
- Look over the format of each before choosing which one.
2. Choose the file you want to test out.
3. Add in the prompt below depending on the prompt file.

**Generate mock data**
Prompt
```markdown
/generate-mock-photo-data 3
```

**Refactor UI component**
Prompt
```markdown
/generate-new-ui for the recent galleries table in the admin page. I want it to be the replacement component for the current table and be reuseable.  Place it in the layout folder.
```

**BONAS CHALLENGE:** Create your own prompt file for unit tests

Ask copilot to generate a new prompt file for unit tests. Use the following steps:

1. Go to GitHub Copilot UI
2. Click on the gear icon in the top right corner
3. Select "Prompt Files"
4. Click the plus icon that says "New prompt file"
5. Select the folder you want to save the file in i.e `.github/prompts/`
6. Name the file 'generate-unit-tests.prompt.md'
7. Create your own custom prompt file with GitHub Copilot:

```markdown
<!-- Add in related files to Ask mode -->
Related files:
- /src/components/ui/FeatureCard.tsx
- /.github/prompts/generate-new-ui.prompt.md
- /.github/prompts/generate-mock-photo-data.prompt.md

<!-- Copy/paste prompt below -->
help me create a prompt files for creating unit test generation for the UI components.
```

## 🎭 Step 4: Utilize Chat Modes

1. Look over the `Plan.chatmode.md` in the `.github/chatmodes` file to see the expected behavior of the mode
2. Go to GitHub Copilot Chat
3. Update mode to "Plan" mode
4. Add in prompt below and look over the suggestion

```markdown
help me plan out a new page for creating new galleries
```
**DISCUSSION**
Look through response. What other modes would be helpful for this repo?

**If time permits**
Try implementing the changes from the plan using a different mode to explore how the experience varies.

## 🛠️ Step 5: Custom instructions and MCP Servers

### Understanding MCP Servers

Model Context Protocol (MCP) servers allow you to extend GitHub Copilot capabilities to external data sources. Custom instructions can help guide Copilot's behavior to align with your project's coding standards and conventions. This is particularly useful for large teams or complex projects where consistency is key.

**Prerequisites**
- GitHub Copilot License
- VSCode 1.99 or later
- MCP servers in Copilot enabled

### Part One: Get familiar with custom instructions

Custom instructions let you shape GitHub Copilot’s behavior to match your team’s coding style, best practices, and project conventions. With custom instructions, Copilot can automatically follow your preferred patterns, use your naming conventions, and even adapt to your workflow. Let's see what this repos custom instructions are:

1. Go to `.github/copilot-instructions.md`
2. Look over the file. Have you noticed coding suggestions have been based around this file?

Now let's generate one with the help of GitHub Copilot.

1. Go to Copilot Chat
2. Select the gear icon on the top right
3. Click "Generate Agent Instructions"
4. Wait while Copilot makes updates to `.github/copilot-instructions.md`

Look over this file and notice how its a good starting point for this project. You can remove or add any instructions your team has in mind!

Custom instructions works in tandem with MCP to help you guide the agent.

### Part Two: MCP Authentication

> [!Note]
> While it is possible to automatically configure MCP servers through [The GitHub MCP Registry](https://github.com/mcp), this section will focus on manual configuration as it is still required for internal MCP servers your company may use as well as MCP servers not supported by GitHub yet.

1. Go to `.vscode/mcp.json` and look over the configuration file. There are two options to choose from depending on your preference and version. For OAuth, refer to `Option A` below. For PAT instructions, refer to `Option B`

**Option A:** VSCode using OAuth (Version 1.101 or greater) Instructions

2. Look for server under `// Using OAuth (version 1.101 or greater)`
3. Click `start`
4. A pop up will appear for the authentication process which will say "The MCP Server Definition 'github' wants to authenticate to GitHub."
5. Select "Allow"
6. Select the account you want to authenticate and press enter

**Option B:** VSCode using GitHub PAT Instructions

2. Follow instructions from [GitHub MCP Server Repo](https://github.com/github/github-mcp-server?tab=readme-ov-file#remote-github-mcp-server)

Now that you have authenticated via OAuth or PAT, let's confirm the tools.

1. Go to GitHub Copilot Chat
2. Select "Agent" mode
3. Click on the tools icon
4. View all of the available toolsets

### Part Three: Creating issues in this template with MCP

1. Since you are already in agent mode in VSCode, type the following prompt in chat to create an issue with MCP server

```markdown
Create an issue for this repo for a feature request to toggle between dark mode and light mode
```

2. Look over the response. Once confirmed, press "continue"
3. Go to the repository and view the issue creation!

## 📋 Advanced Exercises & Challenges

### 🎯 Challenge 1: Build a Custom Workflow

Create a complete customization package for a specific workflow.

**Task:**
```markdown
Choose a workflow:
- Feature development
- Bug fixing
- Documentation
- Testing

Create:
1. Custom chat mode for the workflow
2. 3 prompt files for common tasks
3. Custom instructions section
4. Quick reference guide

Test your customizations and refine based on results.
```

### 🎯 Challenge 2: Model Performance Analysis

Compare models systematically for your use cases.

**Task:**
```markdown
Test 3 different models on:
1. Component generation
2. Bug investigation
3. Documentation writing

For each:
- Time the response
- Rate quality (1-10)
- Note strengths/weaknesses
- Calculate cost

Create a decision matrix for your team.
```

### 🎯 Challenge 3: Prompt Engineering Contest

Who can write the most effective prompt?

**Task:**
```markdown
Scenario: Generate a photo gallery filter component

Round 1: Write your best prompt
Round 2: Test with Copilot
Round 3: Rate results:
  - Correctness
  - Completeness
  - Code quality
  - First-attempt success

Share winning prompts with team!
```

### 🎯 Challenge 4: MCP Server Creation

Build a custom MCP server for your team.

**Task:**
```markdown
Ideas:
- Internal documentation search
- Project-specific code snippets
- Team knowledge base
- Analytics dashboard access

Steps:
1. Design the server capabilities
2. Implement the server
3. Configure in VS Code
4. Test with Copilot
5. Document for team
```

## 💡 Pro Tips Collection

### Tip 1: The Context Stack
```markdown
Layer your context for best results:

Personal Instructions (You):
"I prefer functional components"

Repository Instructions (Project):
"We use Tailwind CSS exclusively"

Prompt (Specific task):
"Create a button component"

Result: Functional component with Tailwind CSS!
```

### Tip 2: The Example Pattern
```markdown
Instead of describing what you want:
"Make it look professional"

Show an example:
"Make it match @src/components/ui/Button.tsx"

Result: Consistent, accurate output
```

### Tip 3: The Iteration Technique
```markdown
Don't aim for perfection immediately:

Prompt 1: "Create basic structure"
Prompt 2: "Add error handling"
Prompt 3: "Optimize performance"
Prompt 4: "Polish and document"

Result: High-quality, well-thought-out code
```

### Tip 4: The Validation Loop
```markdown
After getting a suggestion:

1. Review the code
2. Ask: "What edge cases are we missing?"
3. Copilot identifies gaps
4. Address them
5. Repeat until confident

Result: Robust, production-ready code
```

## 🔧 Troubleshooting Common Issues

### Issue: Copilot Not Following Custom Instructions

**Symptoms:**
- Generates code in wrong style
- Ignores project conventions
- Uses deprecated patterns

**Solutions:**
1. Check file location: `.github/copilot-instructions.md`
2. Verify file syntax (Markdown format)
3. Make instructions more specific
4. Add concrete examples
5. Reload VS Code window
6. Reference instructions explicitly in prompts

**Example Fix:**
```markdown
Before (Vague):
"Use modern React patterns"

After (Specific):
"Use functional components with hooks.
Example: @src/components/ui/Button.tsx"
```

### Issue: Prompt Files Not Appearing

**Symptoms:**
- Can't see `/generate-*` commands
- Prompts not in autocomplete

**Solutions:**
1. Enable feature in settings:
   - Search "prompt files" in VS Code settings
   - Enable "GitHub Copilot: Prompt Files"
2. Check file naming: `*.prompt.md`
3. Verify YAML frontmatter format
4. Reload window
5. Check file permissions

### Issue: MCP Server Connection Failures

**Symptoms:**
- "Connection refused"
- Tools not appearing in Agent mode
- Authentication errors

**Solutions:**
1. Verify `.vscode/mcp.json` syntax
2. Check environment variables set
3. Test server independently:
   ```bash
   node path/to/server.js
   ```
4. Review server logs
5. Validate token permissions
6. Try OAuth instead of PAT (or vice versa)
7. Restart VS Code

### Issue: Slow Performance

**Symptoms:**
- Long wait times
- Timeouts
- IDE lag

**Solutions:**
1. Reduce context size:
   - Close unnecessary files
   - Limit file references
2. Use faster models for simple tasks
3. Clear Copilot cache:
   - Command Palette → "Copilot: Clear Cache"
4. Check network connection
5. Reduce prompt complexity
6. Break large prompts into steps

## 📊 Quick Reference Guide

### Customization Options Matrix

| Feature | Scope | Setup Time | Impact | Best For |
|---------|-------|------------|--------|----------|
| Personal Instructions | You | 5 min | High | Individual preferences |
| Repository Instructions | Project | 15 min | Very High | Team consistency |
| Prompt Files | Team/Project | 10 min each | High | Repeated tasks |
| Chat Modes | Workflow | 20 min | High | Specialized workflows |
| MCP Servers | Organization | 1-2 hours | Variable | External integrations |

### Command Quick Reference

```markdown
# Prompt Files
/prompt-name [arguments]

# Chat Modes
Switch mode dropdown → Select mode

# Context References
@filename - Reference specific file
@foldername/ - Reference folder contents
#symbol - Reference code symbol

# Model Selection
Click model dropdown in Copilot Chat

# Premium Usage
Click Copilot icon in status bar
```

### File Locations

```markdown
Repository Instructions:
.github/copilot-instructions.md

Prompt Files:
.github/prompts/*.prompt.md

Chat Modes:
.github/chatmodes/*.chatmode.md

MCP Configuration:
.vscode/mcp.json

Personal Settings:
https://github.com/settings/copilot
```

## 🎓 Learning Path

### Week 1: Foundations
```markdown
Day 1-2: Personal instructions and basic customization
Day 3-4: Model switching and understanding differences
Day 5: Prompt file exploration and usage
```

### Week 2: Intermediate
```markdown
Day 1-2: Create first prompt files
Day 3-4: Build custom chat mode
Day 5: Test and refine
```

### Week 3: Advanced
```markdown
Day 1-2: MCP server setup
Day 3-4: Advanced prompt engineering
Day 5: Team knowledge sharing
```

### Week 4: Mastery
```markdown
Day 1-2: Optimize all customizations
Day 3-4: Measure productivity impact
Day 5: Document and share with team
```

## ✅ Completion Checklist

Mark off each item as you complete it:

- [ ] Explored premium request monitoring and identified usage patterns
- [ ] Practiced model switching techniques
- [ ] Used project-specific prompt file
- [ ] Experimented with different chat modes
- [ ] Understood MCP servers or set up custom instruction patterns
- [ ] Applied customizations to improve your development workflow
- [ ] Created at least one custom prompt file
- [ ] Built or customized a chat mode
- [ ] Documented your learnings
- [ ] Shared knowledge with team

## 🎯 Skill Assessment

Rate yourself (1-5) on these skills:

```markdown
Understanding Customization Options: ___/5
Writing Effective Custom Instructions: ___/5
Creating Useful Prompt Files: ___/5
Building Custom Chat Modes: ___/5
Model Selection for Tasks: ___/5
MCP Server Configuration: ___/5
Troubleshooting Issues: ___/5
Team Knowledge Sharing: ___/5

Overall Readiness: ___/40

30-40: Expert - Ready to lead team adoption
20-29: Proficient - Ready for advanced usage
10-19: Competent - Ready for daily use
0-9: Beginner - Review materials and practice
```

## 🚀 What's Next?

Excellent work! You've now mastered the advanced customization features of GitHub Copilot.

**Recommended Next Steps:**

1. **Apply to Real Work**
   - Customize for your current project
   - Create team prompt library
   - Share with colleagues

2. **Continue Learning**
   - Experiment with advanced patterns
   - Build custom MCP servers
   - Optimize for your workflow

3. **Share Knowledge**
   - Document your customizations
   - Train team members
   - Contribute to community

---

👉 **[Start Copilot Spaces Demo](./copilot-spaces.md)** or **[Continue to Coding Agent Demo](./coding-agent.md)**
