# Exercise 4 - Engineering Practices and Copilot Instructions

#### Duration: XX minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Understand how to debug and inspect Copilot's decision-making process using the Debug Panel
- Configure personal instructions for consistent code generation across all your projects
- Create and manage repository-specific instructions for team standardization
- Monitor premium request usage to manage costs effectively
- Switch between AI models for different tasks and understand their strengths
- Master the custom instructions hierarchy (personal, repository, organization)
- Apply best practices for instruction file creation in real-world projects

## 📸 Scenario: Standardizing Development at PixelPerfect Gallery

Your team at PixelPerfect Gallery has been using GitHub Copilot for a few weeks now, and developers are getting great results. However, your manager has noticed some challenges:

- Different developers get varying code styles from Copilot for similar tasks
- Some developers get better results than others with similar prompts
- Team members aren't sure why Copilot makes certain suggestions
- The team needs to ensure consistent code patterns across the project
- Team members aren't sure which AI model to use for different scenarios

Today, you'll learn professional engineering practices for using GitHub Copilot effectively and explore instruction customization to:
- Understand AI decision-making through the Debug Panel
- Standardize code generation across the team with instruction files
- Optimize AI model usage for cost and efficiency
- Create effective instruction files that guide Copilot to produce high-quality, consistent code

## 🔍 Step 1: Understanding Copilot's Decision-Making

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

## 🎛️ Step 2: Personal Instructions and Custom Configuration

Personal instructions define how Copilot behaves across all repositories you work on. They're powerful for maintaining consistent coding standards and preferences.

### Step 2.1: Configure Personal Instructions

#### Why This Matters:
- **Consistency**: Get similar code style across all your projects
- **Efficiency**: Don't repeat common preferences in every chat
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

## 📊 Step 3: Managing Model Usage and Costs

Understanding premium request usage and model costs is essential for optimizing your GitHub Copilot experience. GitHub Copilot offers different AI models—some with unlimited usage (0x models) and others that count against a monthly request allowance (premium models). Learning to monitor your usage, select the right model for each task, and manage costs effectively will help you work more efficiently. For comprehensive information about pricing structures, advanced monitoring strategies, cost optimization techniques, and model selection guidelines by task type, see the **[Premium Request Usage Guide](../References/Premium-Request-Usage.md)**.

### Step 3.1: Experiment with Model Switching

Different AI models excel at different tasks. Learning which models work best for specific scenarios helps you work more efficiently.

#### Available Models:

GitHub Copilot provides access to models from:
- **OpenAI** (GPT series)
- **Anthropic** (Claude series)
- **Google** (Gemini series)
- **Auto** - Automatically selects the best model for your task at a 10% discount
- **Others** (constantly evolving)

For current models: [Supported Models Documentation](https://docs.github.com/copilot/reference/ai-models/supported-models)

#### About Auto Model Selection:

The **Auto** option intelligently selects the most appropriate model for your specific task:
- **Cost Savings**: Automatically get a 10% discount on premium request usage
- **Smart Selection**: GitHub analyzes your prompt and selects the optimal model
- **Simplified Workflow**: No need to manually choose between models for different tasks
- **Best Practice**: Ideal when you're unsure which model is best suited for your task

When to use Auto:
- When you want cost optimization without manual model selection
- For varied tasks where different models might be optimal
- When you're new to Copilot and learning which models work best
- For general development work without specific model requirements

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

7. **Repeat steps 4-6 with two other models** (including trying the Auto option)

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

## 📋 Step 4: Understanding Repository Custom Instructions

Repository custom instructions guide Copilot's behavior for your specific project. Understanding how these work and interact with other instruction levels helps you use them effectively.

### Step 4.1: Repository Instructions Overview

#### Two Types of Repository Instructions:

**1. Repository-Wide Instructions** (`.github/copilot-instructions.md`)
- Single file that applies to ALL files in the repository
- Contains universal standards, tech stack, and project patterns
- Foundation for all Copilot suggestions in this project

**2. Path-Specific Instructions** (`.github/instructions/*.instructions.md`)
- Multiple files in the `.github/instructions/` directory
- Each applies only to files matching its `applyTo` patterns
- Provides specialized guidance for specific areas (frontend, backend, tests, etc.)

#### 🔄 How Repository Instructions Work with Other Levels

**Important Research Finding**: All relevant instructions (personal, repository, organization) are provided to Copilot as context. They merge together rather than following a strict priority hierarchy.

**Instruction Levels:**

1. **Personal Instructions** (Your GitHub settings)
   - Your personal preferences across all projects
   - Example: "I prefer functional programming patterns"

2. **Repository-Wide Instructions** (`.github/copilot-instructions.md`)
   - Project-specific standards for the whole codebase
   - Example: "Use Next.js 15 App Router with TypeScript strict mode"

3. **Path-Specific Instructions** (`.github/instructions/*.instructions.md`)
   - Area-specific guidance within the repository
   - Example: "For test files, use Arrange-Act-Assert pattern"

4. **Organization Instructions** (Enterprise settings)
   - Company-wide standards across all organization repos
   - Example: "All code must pass security scanning before merge"

**Best Practices:**
- Repository instructions should be the "source of truth" for project standards
- Ensure instructions at different levels complement, not conflict
- Personal instructions should be general, repository instructions specific
- Path-specific instructions should extend, not contradict, repository-wide instructions

**Example of Good Layering:**
- **Personal**: "I prefer descriptive variable names"
- **Repository-Wide**: "Use Next.js 15 with TypeScript strict mode"
- **Path-Specific (tests)**: "Use data-testid attributes for test queries"
- **Organization**: "All API keys must be in environment variables"

These work together to provide comprehensive guidance.

### Step 4.2: Review Repository Instructions

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

### Step 4.3: Auto-Generate Repository Instructions

Use the Copilot Chat "Generate Chat Instructions" feature to automatically create (or refine) the repository’s `copilot-instructions.md`, then compare and improve it.

1. Open Copilot Chat  
2. Click the gear icon (Configure Chat) → choose **Generate Chat Instructions**
3. Look through the changes that Copilot has suggested making to the instructions file
4. Accept the changes that you think add value to the instructions, and `Undo` the ones that don't

> Tip: You should repeat this process routinely to ensure that the instructions always stay up to date with the codebase. This ensures that Copilot gets the best context possible when working within your code.

## 💎 Step 5: Best Practices for Creating Effective Instruction Files

Creating high-quality instruction files is essential for maximizing Copilot's effectiveness in production environments. Well-crafted instructions help teams maintain consistency, enforce standards, and guide AI-assisted development.

### Why Instruction Files Matter in Real Projects

In real-world development scenarios, instruction files serve several critical purposes:

- **Team Consistency**: Ensure all team members receive similar guidance from Copilot, regardless of their experience level
- **Code Quality**: Automatically enforce architectural patterns and coding standards across the project
- **Faster Onboarding**: Help new developers understand project conventions quickly without extensive documentation reviews
- **Enhanced Copilot Output**: Copilot is tuned to your repository specifics, and as such is much more accurate with its output

### Understanding Repository Custom Instructions

Repository custom instructions provide project-specific guidance to Copilot. There are two types within a repository:

**Repository-Wide Instructions** (`.github/copilot-instructions.md`):
- Single file that applies to all files in the repository
- Defines universal standards, tech stack, and patterns for the entire project
- Examples: Project overview, technology stack, architecture patterns, coding standards

**Path-Specific Instructions** (`.github/instructions/*.instructions.md`):
- Multiple files in `.github/instructions/` directory
- Each applies only to files matching specified `applyTo` patterns
- Examples: Frontend-specific React patterns, backend API conventions, test file requirements

**How They Work Together:**
Both types work through context merging - Copilot uses the repository-wide instructions plus any matching path-specific instructions to inform its suggestions.

### Key Elements of Repository-Wide Instructions (`.github/copilot-instructions.md`)

When creating the repository-wide instruction file, focus on these essential elements:

1. **Project Overview**: Clear description of what the project does, who it's for, and core functionality
2. **Technology Stack**: Explicitly define frameworks, libraries, and versions (including what NOT to use)
3. **Architecture Patterns**: Be specific about folder structure, design patterns, and code organization
4. **Code Style Standards**: Specify naming conventions, file structure, and formatting preferences
5. **Security Requirements**: Specify security practices that must be followed
6. **Deprecated Patterns**: Explicitly document what patterns to avoid
7. **Code Examples**: Provide concrete examples of correct patterns

### When to Use Path-Specific Instructions (`.github/instructions/*.instructions.md`)

Path-specific instructions are valuable for:
- **Different areas with different needs**: Frontend vs Backend, Tests, Security-sensitive files
- **Monorepos**: Different standards for different sub-projects
- **Legacy code**: Modernization guidance for specific directories
- **Specialized requirements**: Stricter patterns for certain file types

### 📖 Complete Guide with Research-Backed Best Practices

For comprehensive, evidence-based best practices with detailed real-world examples and implementation strategies for creating effective repository custom instructions, see:

**[Copilot Instruction Best Practices Guide](../References/Copilot-Instruction-Best-Practices.md)**

This reference guide covers:
- **Clear distinction** between Repository-Wide (`.github/copilot-instructions.md`) and Path-Specific (`.github/instructions/*.instructions.md`) instructions
- **Research-backed impact**: 50%+ productivity increase, 3-4x faster feature delivery, 60% code review reduction
- **Evidence-based best practices** for both repository instruction types
- **Critical limitations** you need to understand (token limits, non-deterministic behavior, legacy code influence)
- **Common mistakes** identified through real-world case studies (wrong glob patterns, missing `applyTo`, conflicts)
- **Path-specific instruction techniques** with `applyTo` pattern examples
- **Measuring effectiveness** with qualitative and quantitative metrics
- **Implementation strategies** for new and existing projects with phased rollout plans

## 🏆 Exercise Wrap-up

Excellent work! You've learned professional engineering practices and instruction customization for GitHub Copilot:
- ✅ Debugged and inspected Copilot's decision-making process using the Debug Panel
- ✅ Configured personal instructions for consistent code generation
- ✅ Monitored premium request usage to optimize costs
- ✅ Experimented with different AI models for various tasks
- ✅ Understood custom instructions hierarchy (personal, repository, organization)
- ✅ Learned best practices for creating effective instruction files

### Reflection Questions:
1. **How can the debug view help you write better prompts?**
2. **How might personal instructions improve your daily workflow?**
3. **What standards or preferences would you include in personal instructions?**
4. **How can monitoring usage help you make better model choices?**
5. **What differences did you notice between AI models?**
6. **What should go in personal vs. repository vs. organization instructions?**
7. **How can well-crafted instructions improve team productivity?**

### Key Takeaways:
- The Debug Panel provides transparency into AI decision-making
- Personal instructions maintain consistency across all your projects
- Repository instructions ensure team-wide coding standards
- Different AI models have different strengths and costs - choose wisely
- Instructions at different levels provide appropriate context (personal, repository, organization)
- These practices make AI-assisted development more professional and reliable
- Well-crafted instruction files multiply Copilot's effectiveness

**Ready for the next challenge? Move on to Lab 5 to learn about Prompt Files, Custom Chat Modes, and MCP!**
