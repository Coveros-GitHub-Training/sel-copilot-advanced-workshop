# Exercise 4 - Engineering Practices and Customizing GitHub Copilot

#### Duration: 60 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Understand how to debug and inspect Copilot's decision-making process
- Configure personal instructions for consistent code generation
- Monitor premium request usage to manage costs
- Switch between AI models for different tasks
- Use prompt files for consistent, reusable AI interactions
- Create and utilize custom chat modes for specialized workflows
- Master custom instructions hierarchy (personal, repository, organization)
- Optimize GitHub Copilot for your specific workflow needs

## 📸 Scenario: Improving Team Collaboration at PixelPerfect Gallery

Your team at PixelPerfect Gallery has been using GitHub Copilot for a few weeks now, and developers are getting great results. However, your manager has noticed some challenges:

- Different developers get varying code styles from Copilot for similar tasks
- Some developers get better results than others with similar prompts
- Team members aren't sure why Copilot makes certain suggestions
- You keep repeating the same complex prompts for common operations
- Some tasks would benefit from a specialized AI workflow
- Team members aren't sure which AI model to use for different scenarios

Today, you'll learn professional engineering practices for using GitHub Copilot effectively and explore its customization features to:
- Understand AI decision-making and maintain code quality standards
- Standardize code generation across the team
- Create reusable prompts for common tasks
- Optimize AI model usage for cost and efficiency
- Build custom workflows tailored to your development process

## 🔍 Part 1: Understanding Copilot's Decision-Making

When using AI-assisted development in a professional environment, it's crucial to:
- **Understand the AI's reasoning** - Know why suggestions are made
- **Maintain standards** - Ensure consistent code quality across the team
- **Debug effectively** - Investigate when suggestions don't meet expectations

GitHub Copilot provides features specifically designed for professional engineers to address these needs.

### Step 1.1: Inspect Copilot's Decision-Making Process

Understanding how Copilot makes suggestions helps you write better prompts and trust the AI's recommendations. The debug view shows you exactly what context Copilot is using and how it formulates responses.

#### Why This Matters:
- **Improve prompts**: See what context Copilot has access to
- **Debug issues**: Understand why unexpected suggestions appear
- **Build trust**: Transparency in AI decision-making
- **Learn patterns**: Discover what makes effective prompts

#### Instructions:

**Method 1: Using Keyboard Shortcut**
1. Press `Ctrl + Shift + P` (Windows/Linux) or `Cmd + Shift + P` (Mac)
2. Type "Copilot Chat Debug"
3. Select **"Copilot Chat Debug: Focus on Copilot Chat Debug View"**

**Method 2: Through the Copilot Chat Window**
1. Open GitHub Copilot Chat
2. At the top of the Copilot Chat window, click the 3 ellipses `...`
3. Click **"Show Chat Debug View"**

#### What You'll See:

Once the debug panel opens, you can explore:

- **Prompts**: The actual prompts sent to the AI model
- **System Prompts**: Background instructions given to Copilot (from custom instructions, repository context, etc.)
- **Metadata**: Context information, model settings, and parameters
- **Response Details**: How Copilot formulated its suggestions, including tokens used

#### 🔬 Try This Experiment:

1. **Ask a simple question in Copilot Chat:**
   ```
   How does the GalleryGrid component handle filtering?
   ```

2. **Open the debug view** to see:
   - What files were included in the context
   - What system prompts were applied
   - How the query was processed

3. **Ask a more complex question:**
   ```
   @workspace Refactor the UploadZone component to use a custom hook for file handling
   ```

4. **Compare the debug information:**
   - Notice the difference in context files used
   - See how workspace references affect the prompt
   - Observe the system instructions that guide behavior

#### 💡 Pro Tips:
- Use this when Copilot's suggestions seem unexpected - you can see exactly what context it's using
- Check the debug view if you're not getting relevant suggestions - you might need to add more context
- Review system prompts to understand what standards Copilot is following
- Look at token usage to optimize your prompts for efficiency

## 🎛️ Part 2: Personal Instructions and Custom Configuration

Personal instructions define how Copilot behaves across all repositories you work on. They're powerful for maintaining consistent coding standards and preferences.

### Step 2.1: Configure Personal Instructions

#### Why This Matters:
- **Consistency**: Get similar code style across all your projects
- **Efficiency**: Don't repeat common preferences in every chat
- **Standards**: Enforce your team's or personal coding guidelines
- **Customization**: Tailor Copilot to your specific needs and workflows

#### Access Personal Instructions

1. **Navigate to GitHub Copilot**: Go to [https://github.com/copilot](https://github.com/copilot)

2. **Open settings**: Click **Your profile icon** in the bottom left of the screen

3. **Open personal instructions**: Select **"Personal instructions"**

4. **Review existing instructions** (if any are already configured)

#### Create or Modify Personal Instructions

**Add a new personal instruction** that you'd like to test for this class.

<details>
  <summary>Example Personal Instructions</summary>

  **For TypeScript Development:**
  ```
  Always use TypeScript with strict mode. Prefer interfaces over types for object definitions. 
  Use descriptive variable names and include JSDoc comments for public functions.
  ```

  **For React/Next.js:**
  ```
  Follow React best practices: use functional components with hooks, avoid prop drilling, 
  use proper TypeScript types for props and state. Follow Next.js 15 App Router patterns.
  ```

  **For Styling:**
  ```
  Use Tailwind CSS for all styling. Follow mobile-first responsive design. 
  Include dark mode variants using Tailwind's dark: prefix. Keep components accessible.
  ```

  **For Code Quality:**
  ```
  Write clean, maintainable code with single responsibility principle. 
  Include error handling and input validation. Add comments only when needed for clarity.
  ```

</details>

**💡 Help Creating Personal Instructions:**
If you're stuck, click the **lightbulb icon** in the bottom right of the textbox to insert a pre-built instruction template.

#### Test Your Personal Instructions

1. **After adding instructions**, return to VS Code

2. **Ask Copilot to generate some code:**
   ```
   Create a new component for displaying photo metadata
   ```

3. **Observe how the generated code** reflects your personal instructions

4. **Experiment with different instructions** to see how they affect output

#### 🔍 Things to Explore:

- How do personal instructions influence code style?
- What coding standards are enforced?
- How do the instructions interact with repository-level instructions?
- Do instructions apply consistently across different file types?

## 📊 Part 3: Managing Model Usage and Costs

Understanding your usage helps you make informed decisions about which AI models to use and when. This section will show you how to monitor usage and understand the basics.

### Step 3.1: Monitor Premium Request Usage

#### Quick Check Your Usage

**Option A: View Usage in VS Code**

1. **Open VS Code** and ensure GitHub Copilot is active
2. **Locate Copilot status:**
   - Look for the GitHub Copilot logo in the bottom-right status bar
   - Click on it to see current status and usage information
3. **Review information displayed:**
   - Current model being used
   - Premium request count (if applicable)
   - Subscription status

**Option B: Access the Premium Dashboard on GitHub.com**

1. **Navigate to**: [https://github.com/settings/copilot/features](https://github.com/settings/copilot/features)
2. **Sign in** and view your dashboard
3. **Review**: Usage percentage, requests remaining, and billing cycle reset date

#### Key Things to Know

- **0x Models**: Unlimited usage within your Copilot subscription
- **Premium Models**: Count against your monthly request allowance
  - Copilot Business: 300 requests per user per month
  - Copilot Enterprise: 1,000 requests per user per month
- **Best Practice**: Use premium models for complex, high-value tasks; use 0x models for routine work

> 📚 **For Detailed Information**: See the [Premium Request Usage Guide](../References/Premium-Request-Usage.md) for comprehensive information about:
> - Advanced monitoring strategies
> - Cost optimization techniques
> - Model selection by task type
> - Team usage policies and best practices
> - Monthly budget planning strategies

### Step 3.2: Experiment with Model Switching

Different AI models excel at different tasks. Learning which models work best for specific scenarios helps you work more efficiently.

#### Available Models:

GitHub Copilot provides access to models from:
- **OpenAI** (GPT series)
- **Anthropic** (Claude series)
- **Google** (Gemini series)
- **Others** (constantly evolving)

For current models: [Supported Models Documentation](https://docs.github.com/copilot/reference/ai-models/supported-models)

#### Instructions:

Let's try the same coding task with different models and compare results.

1. **Update your mode to Edit**

2. **Add context files:**
   - Click `Add Context` in GitHub Copilot Chat
   - Add these files:
     - `/src/app/gallery/page.tsx`
     - `/src/lib/mock-photo-data.ts`
     - `/src/components/gallery/GalleryGrid.tsx`
   
   **Alternative method:**
   - Close all tabs
   - Open only these three files
   - Click `Add Context` → `Open Editors`

3. **Stay on GalleryGrid.tsx and highlight lines 26-43**

4. **Select Model #1** from the model selector in Copilot Chat

5. **Ask this refactoring question:**
   ```
   Help me refactor this function for better performance, readability, and add TypeScript improvements
   ```

6. **Note the response** - save or copy it for comparison

7. **Repeat steps 4-6 with two other models**

#### 💡 Comparison Questions:

After trying multiple models, discuss or consider:
- Which model gave the most comprehensive explanation?
- Which provided the best code quality?
- Which was fastest to respond?
- Which model's approach did you prefer and why?
- How did performance recommendations differ?
- Were TypeScript improvements consistent across models?

#### When to Use Different Models:

Based on typical strengths (check current docs for specifics):
- **Quick code completions**: Fast, efficient models
- **Complex refactoring**: Models good at reasoning
- **Explanations**: Models with detailed communication
- **Performance optimization**: Models with deep analysis

## 📝 Part 4: Prompt Files for Consistent Generation

Prompt files allow you to create reusable, standardized prompts that maintain consistency across your team and save time on repetitive tasks.

### Step 4.1: Explore Existing Prompt Files

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

### Step 4.2: Create Your Own Prompt File

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

## 🎭 Part 5: Custom Chat Modes

Chat modes define how GitHub Copilot behaves for specialized workflows. Let's create a custom mode for planning new features.

### Step 5.1: Understanding Custom Chat Modes

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

### Step 5.2: Create Your Own Custom Chat Mode

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

## 📋 Part 6: Understanding Custom Instructions Hierarchy

Custom instructions are rules that apply to every Copilot interaction in a context (personal, repository, or organization level).

### Step 6.1: Instructions Hierarchy

#### Hierarchy Levels:

1. **Personal Instructions** (highest priority)
   - Your individual preferences across all repos
   - Set at: https://github.com/copilot

2. **Repository Instructions** (medium priority)
   - Project-specific requirements
   - File: `.github/copilot-instructions.md`

3. **Organization Instructions** (lowest priority)
   - Company-wide standards
   - Set by org admins

#### ⚖️ Balancing Different Instruction Levels

**Personal Instructions**: Your individual preferences across all repositories
- Language-specific preferences
- General coding style
- Comment and documentation preferences

**Repository Instructions**: Project-specific requirements (in `.github/copilot-instructions.md`)
- Project architecture patterns
- Specific libraries or frameworks to use
- Team coding standards

**Priority Order:**
1. Personal instructions (highest)
2. Repository instructions
3. Organization instructions (lowest)

When instructions conflict, higher priority ones take precedence.

### Step 6.2: Review Repository Instructions

1. **Open** `.github/copilot-instructions.md` in this repository

2. **Notice how it defines:**
   - Project overview and architecture
   - Component patterns
   - Styling conventions
   - Development workflow

3. **Understand how these instructions:**
   - Automatically apply to all Copilot interactions
   - Guide code generation to follow project patterns
   - Maintain consistency across the codebase

#### Example Instructions in This Repo:

The copilot-instructions.md file includes:
- Project structure overview
- Component usage patterns
- Technology stack information
- Styling conventions
- Best practices for this specific project

These instructions help Copilot generate code that fits seamlessly into the existing codebase.

## 🏆 Exercise Wrap-up

Excellent work! You've learned professional engineering practices and advanced customization techniques for GitHub Copilot:
- ✅ Debugged and inspected Copilot's decision-making process
- ✅ Configured personal instructions for consistent code generation
- ✅ Monitored premium request usage
- ✅ Experimented with different AI models
- ✅ Used existing prompt files
- ✅ Created custom prompt files
- ✅ Built a custom chat mode
- ✅ Understood custom instructions hierarchy

### Reflection Questions:
1. **How can the debug view help you write better prompts?**
2. **How might personal instructions improve your daily workflow?**
3. **What standards or preferences would you include in personal instructions?**
4. **How can monitoring usage help you make better model choices?**
5. **What differences did you notice between AI models?**
6. **What common tasks in your workflow could benefit from prompt files?**
7. **How might custom chat modes improve your team's productivity?**
8. **What should go in personal vs. repository vs. organization instructions?**

### Key Takeaways:
- The debug view provides transparency into AI decision-making
- Personal instructions maintain consistency across your work
- Different AI models have different strengths and costs
- Prompt files save time and ensure consistency
- Custom chat modes optimize workflows for specific tasks
- Instructions at different levels provide appropriate context
- These practices make AI-assisted development more professional and reliable
- Customization makes GitHub Copilot work better for your specific needs

## 🚀 Next Steps

Now that you've mastered engineering practices and customization:

1. **Apply to Your Work**
   - Create instructions for your project
   - Build prompt files for common tasks
   - Share with your team

2. **Measure Impact**
   - Track time savings
   - Monitor quality improvements
   - Calculate ROI

3. **Iterate and Improve**
   - Refine based on usage
   - Add new prompts as needed
   - Update instructions regularly

4. **Share Knowledge**
   - Document what works
   - Train team members
   - Contribute to community

**Ready for the next challenge? Move on to Lab 5 to learn about GitHub Copilot Spaces!**
