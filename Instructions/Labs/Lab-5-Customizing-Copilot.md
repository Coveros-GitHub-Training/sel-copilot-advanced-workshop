# Exercise 5 - Customizing GitHub Copilot

#### Duration: 30 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Explain what custom instructions are and how they shape GitHub Copilot's behavior
- Monitor premium request usage to manage costs
- Switch between AI models for different tasks (optional)
- Use prompt files for consistent, reusable AI interactions
- Create and utilize custom chat modes for specialized workflows
- Understand how to optimize GitHub Copilot for your specific needs

## 📸 Scenario: Streamlining Workflows at PixelPerfect Gallery

Things are going well at PixelPerfect Gallery. Your team is using GitHub Copilot to efficiently build new features and fix bugs. However, you've noticed some inefficiencies:

- Different developers get varying code styles from Copilot for similar tasks
- You keep repeating the same complex prompts for common operations
- Some tasks would benefit from a specialized AI workflow
- Team members aren't sure which AI model to use for different scenarios

Your manager has asked you to explore GitHub Copilot's customization features to:
- Standardize code generation across the team
- Create reusable prompts for common tasks
- Optimize AI model usage for cost and efficiency
- Build custom workflows tailored to your development process

## 📊 Step 1: Monitor Premium Request Usage

Understanding your usage helps you make informed decisions about which AI models to use and when.

### Why This Matters:
- **Cost awareness**: Different models have different costs
- **Usage planning**: Know when you're approaching limits
- **Model selection**: Choose appropriate models based on remaining allowance
- **Team management**: Track usage patterns across your organization

### Option A: View Usage in VS Code

1. **Open VS Code** and ensure GitHub Copilot is active

2. **Locate Copilot status:**
   - Look for the GitHub Copilot logo in the bottom-right status bar
   - Click on it to see current status and usage information

3. **Review information displayed:**
   - Current model being used
   - Premium request count (if applicable)
   - Subscription status

### Option B: Access the Premium Dashboard on GitHub.com

1. **Navigate to GitHub**: Go to [https://github.com/settings/copilot/features](https://github.com/settings/copilot/features)

2. **Sign in**: Ensure you're logged into your GitHub account

3. **View dashboard**: Review your premium request usage

**What to Look For:**
- Usage percentage and limits
- Requests used vs. remaining this month
- Model usage breakdown (which models you've used most)
- Billing cycle reset date

### 💰 Understanding Model Costs:

Different AI models have different pricing structures:

- **0x Models**: Unlimited usage within your Copilot subscription
- **Premium Models**: Count against your monthly request allowance
  - Different cost multipliers per model
  - Some consume more requests per use than others
- **Auto Model Selection**: Automatic model choice at 10% discount
- **Usage Allowances**:
  - Copilot Business: 300 requests per user per month
  - Copilot Enterprise: 1,000 requests per user per month
- **Overage**: Additional requests at $0.04 each

For complete details: [GitHub Copilot Billing Documentation](https://docs.github.com/copilot/concepts/billing/copilot-requests)

## 🔄 Step 2: Experiment with Model Switching (Optional)

Different AI models excel at different tasks. Learning which models work best for specific scenarios helps you work more efficiently.

### Available Models:

GitHub Copilot provides access to models from:
- **OpenAI** (GPT series)
- **Anthropic** (Claude series)
- **Google** (Gemini series)
- **Others** (constantly evolving)

For current models: [Supported Models Documentation](https://docs.github.com/copilot/reference/ai-models/supported-models)

### Instructions:

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

### 💡 Comparison Questions:

After trying multiple models, discuss or consider:
- Which model gave the most comprehensive explanation?
- Which provided the best code quality?
- Which was fastest to respond?
- Which model's approach did you prefer and why?
- How did performance recommendations differ?
- Were TypeScript improvements consistent across models?

### When to Use Different Models:

Based on typical strengths (check current docs for specifics):
- **Quick code completions**: Fast, efficient models
- **Complex refactoring**: Models good at reasoning
- **Explanations**: Models with detailed communication
- **Performance optimization**: Models with deep analysis

## 📝 Step 3: Use Prompt Files for Consistent Generation

Prompt files allow you to create reusable, standardized prompts that maintain consistency across your team and save time on repetitive tasks.

### Why Prompt Files Matter:
- **Consistency**: Same prompt structure every time
- **Efficiency**: No need to retype complex prompts
- **Standardization**: Team uses the same approaches
- **Parameterization**: Customize with input variables
- **Documentation**: Self-documenting common workflows

### Explore Existing Prompt Files:

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

### Use a Prompt File:

**Generate Mock Data:**
```
/generate-mock-photo-data 3
```

**Generate UI Component:**
```
/generate-new-ui for a photo card component that displays a photo thumbnail with title and photographer name. Place it in the gallery folder.
```

### Understanding Prompt File Components:

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

## 🎨 Step 4: Create Your Own Prompt File

Let's create a custom prompt file for a common task in the PixelPerfect Gallery project.

### Option A: Enable Prompt Files (if needed)

1. Open VS Code Settings: `Cmd+,` (Mac) or `Ctrl+,` (Windows/Linux)
2. Search for "Prompt file"
3. Ensure "Chat: Prompt Files" is enabled

### Option B: Create the Prompt File

**Method 1: Using Copilot Chat UI**
1. Open GitHub Copilot Chat
2. Click the cogwheel (⚙️) in the top-right corner
3. Select "Prompt Files"
4. Click "New prompt file..."
5. Choose `.github/prompts/` as the location
6. Name it `generate-photo-component.prompt.md`

**Method 2: Create Manually**
Create a new file at `.github/prompts/generate-photo-component.prompt.md`

### Sample Prompt File to Create:

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

### 🎁 Bonus Challenge: Create a Test Generation Prompt

Create another prompt file for generating tests:

1. Name it `generate-component-tests.prompt.md`
2. Include parameters for:
   - Component name
   - Test scenarios to cover
   - Testing framework preferences
3. Specify it should follow existing test patterns

<details>
  <summary>Example: Test Generation Prompt</summary>

  ```markdown
  ---
  description: 'Generate comprehensive tests for a React component'
  mode: 'agent'
  ---
  
  Generate comprehensive tests for the following component:
  
  Component: ${input:component:src/components/ComponentName.tsx}
  Test scenarios: ${input:scenarios:happy path, edge cases, error handling}
  
  Requirements:
  - Use React Testing Library
  - Include TypeScript types for test utilities
  - Test props, state, and user interactions
  - Include accessibility tests
  - Add descriptive test names
  - Follow AAA pattern (Arrange, Act, Assert)
  - Mock external dependencies appropriately
  
  Generate tests that cover: ${input:scenarios}
  ```

</details>

### Test Your Prompt File:

1. In Copilot Chat, type `/` followed by your prompt file name
2. Press Enter
3. Fill in any requested input variables
4. Review the generated code

## 🎭 Step 5: Create a Custom Chat Mode

Chat modes define how GitHub Copilot behaves for specialized workflows. Let's create a custom mode for planning new features.

### Why Custom Chat Modes:
- **Specialized workflows**: Tailor AI behavior to specific tasks
- **Tool selection**: Pre-configure which tools to use
- **Model preference**: Specify best model for the task
- **Consistent approach**: Same methodology every time

### Instructions:

1. **Open GitHub Copilot Chat**

2. **Click the cogwheel (⚙️)** in the top-right corner

3. **Select "Modes"** from the dropdown

4. **Click "Create new custom chat mode file..."**

5. **Choose location**: `.github/chatmodes/`

6. **Name the file**: `Plan.chatmode.md`

### Create a Planning Mode:

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

### Test Your Custom Chat Mode:

1. **Switch to your Plan mode** in Copilot Chat

2. **Ask it to plan a feature:**
   ```
   Plan a new feature for allowing users to organize photos into custom albums with drag-and-drop functionality
   ```

3. **Review the plan generated** - does it follow your template structure?

4. **Iterate on the mode** if needed to improve results

## 📋 Step 6: Understanding Custom Instructions Files

Custom instructions are rules that apply to every Copilot interaction in a context (personal, repository, or organization level).

### Instructions Hierarchy:

1. **Personal Instructions** (highest priority)
   - Your individual preferences across all repos
   - Set at: https://github.com/copilot

2. **Repository Instructions** (medium priority)
   - Project-specific requirements
   - File: `.github/copilot-instructions.md`

3. **Organization Instructions** (lowest priority)
   - Company-wide standards
   - Set by org admins

### Review Repository Instructions:

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

### Example Instructions in This Repo:

The copilot-instructions.md file includes:
- Project structure overview
- Component usage patterns
- Technology stack information
- Styling conventions
- Best practices for this specific project

These instructions help Copilot generate code that fits seamlessly into the existing codebase.

## 🏆 Exercise Wrap-up

Excellent work! You've learned advanced customization techniques for GitHub Copilot:
- ✅ Monitored premium request usage
- ✅ Experimented with different AI models
- ✅ Used existing prompt files
- ✅ Created custom prompt files
- ✅ Built a custom chat mode
- ✅ Understood custom instructions hierarchy

### Reflection Questions:
1. **How can monitoring usage help you make better model choices?**
2. **What differences did you notice between AI models?**
3. **What common tasks in your workflow could benefit from prompt files?**
4. **How might custom chat modes improve your team's productivity?**
5. **What should go in personal vs. repository vs. organization instructions?**

### Key Takeaways:
- Different AI models have different strengths and costs
- Prompt files save time and ensure consistency
- Custom chat modes optimize workflows for specific tasks
- Instructions at different levels provide appropriate context
- Customization makes GitHub Copilot work better for your specific needs

## 🚀 Next Steps

In Exercise 6, we'll explore GitHub Copilot Spaces - a unique feature for collaborative development that allows you to create dedicated workspaces for specific projects or goals!

#### You have successfully completed the lab. Click on **Next >>** to continue to the next lab.

![Next page navigation](../../media/next-page.png)
