# Exercise 2 - Exploring the Codebase with GitHub Copilot

#### Duration: 30 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Use GitHub Copilot Chat in "Ask" mode to understand unfamiliar codebases
- Learn how to efficiently navigate and analyze project structure with AI assistance
- Understand how to identify build processes, frameworks, and dependencies
- Develop strategies for onboarding to new projects using GitHub Copilot

## 📸 Scenario: Your First Day at PixelPerfect Gallery

Welcome to your first day as a developer at PixelPerfect Gallery! Your manager has just given you access to the photo gallery repository, but like any new team member, you need to understand:
- What does this application actually do?
- How is the code organized and structured?
- What technologies and frameworks are being used?
- How do I build, run, and enhance the application?

As a modern developer, you'll leverage GitHub Copilot Chat to accelerate your onboarding process and get productive quickly.

## 🤖 Introduction to GitHub Copilot Chat

GitHub Copilot Chat is an AI-powered conversational interface that helps you understand code, generate implementations, and solve development challenges. There are several modes to interact with GitHub Copilot:

| Mode | Purpose | Best For |
|------|---------|----------|
| **Ask** | Get explanations and answers about code | Understanding existing code, learning new concepts |
| **Edit** | Modify existing code with AI assistance | Refactoring, bug fixes, feature additions |
| **Agent** | Delegate complex tasks to AI | Multi-file changes, architectural decisions |

For exploring an unfamiliar codebase, **Ask mode** is ideal because it allows you to:
- Query specific files or code patterns without making changes
- Get high-level explanations of project structure and purpose
- Understand dependencies, build processes, and development workflows
- Ask follow-up questions to deepen your understanding

## 🧠 Choosing the Right AI Model

GitHub Copilot Chat offers access to multiple AI models, each with different strengths and capabilities. Understanding when to use each model can significantly improve your development experience.

### Available Models

GitHub Copilot provides access to several AI models from leading providers such as OpenAI, Anthropic, Google, and others. The available options are constantly evolving. For the most up-to-date information about supported models and their capabilities, see the official documentation: [GitHub Copilot Supported Models](https://docs.github.com/copilot/reference/ai-models/supported-models)

Different models excel at different types of tasks. For detailed information about each model's strengths and ideal use cases, see the [AI Models Comparison Guide](https://docs.github.com/copilot/reference/ai-models/model-comparison):
- Some are optimized for **code understanding and analysis**
- Others excel at **complex reasoning and problem-solving**
- Some prioritize **speed for quick responses**
- Others focus on **detailed explanations and accuracy**

GitHub is now also offering a new auto model selection feature within Visual Studio Code that automatically chooses the best model for your specific task based on context and requirements. This can help streamline your workflow by ensuring you're always using the most suitable AI model without manual selection. More information can be found here: [Auto Model Selection](https://docs.github.com/copilot/concepts/auto-model-selection).

### 💰 Model Pricing and Usage Limits

**Important**: Different AI models have different pricing structures and usage limits:

- **0x Models**: Unlimited usage within your Copilot subscription
- **Other Models**: Have different cost multipliers and usage limits
- **Auto Model Selection**: Will automatically choose from a variety of models with different multipliers at a 10% discount
- **Usage Allowances**: 
    - Copilot Business: 300 requests per user per month
    - Copilot Enterprise: 1,000 requests per user per month
- **Additional Requests**: Available at $0.04 each when you exceed your monthly allowance

For complete details on model pricing and billing, see: [GitHub Copilot Billing Documentation](https://docs.github.com/copilot/concepts/billing/copilot-requests)

### 🔄 Experimenting with Different Models

Try asking the same question to different models to compare their responses! Each model may provide unique insights or different perspectives on the same problem.

**How to Switch Models:**
1. In GitHub Copilot Chat, look for the model selector (usually below the text area in which prompts can be submitted)
2. Click on the current model name to see available options
3. Select a different model and ask your question

## 🔍 Step 1: Discovering Available Copilot Features

Let's start by understanding what GitHub Copilot can do for you.

### Instructions:
1. Switch to "Ask" mode within GitHub Copilot Chat if you are not already in that mode.
2. Type the following command in the Copilot chat:

```markdown
/help
```

### 💡 What to Expect from GitHub Copilot

You'll see a list of available commands and features, including:
- **Slash commands** like `/explain`, `/fix`, `/tests`, etc.
- **Chat participants** that provide specialized assistance
- **Code actions** available through the editor

Take a moment to familiarize yourself with these options - you'll use many of them throughout these labs!

## 📚 Step 2: Understanding the Project Purpose

Let's get a high-level understanding of what this application does.

### Instructions:
1. Stay in "Ask" mode within GitHub Copilot Chat
2. Ask GitHub Copilot some questions to help you understand the application
3. **Try different models**: Start with the default model, then experiment with others to see how their explanations differ

If you get stuck, try using these sample prompts to explore the project:

<details>
  <summary>Sample Prompts</summary>
  
  ```
  What is the main purpose of this application? What does it do?
  ```

  ```
  Give me a summary of the project and give an overview of the most impactful files.
  ```

  ```
  Can you give me a high-level overview of this project's features and functionality?
  ```

  ```
  What type of application is this? Is it a web app, API, desktop app, or something else?
  ```

</details>

### 💡 What to Expect from GitHub Copilot

When you ask these questions, GitHub Copilot will analyze your workspace and provide insights such as:
- **Application Type**: Whether it's a photo gallery, portfolio site, web application, etc.
- **Core Features**: Key functionality like photo upload, gallery display, filtering, admin dashboard
- **Technology Stack**: Programming languages, frameworks, and architectural patterns in use
- **Business Domain**: The industry or use case the application serves

GitHub Copilot's responses will be based on analyzing your codebase structure, configuration files, dependencies, and code patterns. The more specific your questions, the more targeted and useful the responses will be.

## 🏗️ Step 3: Analyzing Project Structure

Now let's understand how the code is organized and what the folder structure tells us.

### Instructions:
Ask GitHub Copilot some questions to help you understand the organization of the codebase. **Experiment**: Try asking the same structural question to different models - you might get varying levels of detail or different organizational perspectives! 

If you get stuck, try using these sample prompts:

<details>
  <summary>Sample Prompts</summary>

  ```
  How is this project structured? Can you explain the main folders and their purposes?
  ```

  ```
  What are the most important files I should understand as a new developer on this project?
  ```

  ```
  Are there any configuration files I should be aware of? What do they control?
  ```

  ```
  Explain the src/components/ directory structure and the types of components used.
  ```

</details>

### 💡 What to Expect from GitHub Copilot

When you ask these questions, GitHub Copilot will analyze the files and folders in your workspace and provide a structural breakdown, including:
- **Folder Roles**: Explanations of what code lives in directories like `src/app/`, `src/components/`, `src/lib/`
- **Key Files**: Identification of critical files such as `package.json`, `README.md`, or main entry points
- **Architectural Patterns**: Insights into how the project is organized (Next.js App Router, component-driven architecture)
- **Configuration Details**: Information about configuration files like `next.config.ts`, `tailwind.config.js`, or TypeScript settings

GitHub Copilot's response helps new developers quickly orient themselves by providing a map of the codebase organization.

## 💻 Step 4: Identifying Technologies and Frameworks

Understanding the tech stack is crucial for knowing what skills you'll need and how to work effectively.

### Instructions:
Ask GitHub Copilot some questions to help you understand the technologies and frameworks used within the codebase.

If you get stuck, try using these sample prompts:

<details>
  <summary>Sample Prompts</summary>

  ```
  What programming languages are used in this project?
  ```

  ```
  What frameworks and libraries does this project depend on? Can you explain what each major one does?
  ```

  ```
  What's the package.json telling me about the dependencies?
  ```

  ```
  What is Next.js and why is it used in this project?
  ```

</details>

If GitHub Copilot mentions any technologies you're unfamiliar with, don't hesitate to ask follow-up questions! Remember, GitHub Copilot Chat isn't just for understanding your specific codebase—it's your **onboarding buddy**, **technical sounding board**, and **intelligent search engine** all rolled into one.

<details>
  <summary>Sample Follow-up Prompts</summary>

  ```
  Can you explain what [framework name] is and why it might be used in this type of project?
  ``` 

  ```
  What are the key benefits of using [library name] over other similar libraries?
  ``` 

  ```
  How does [technology name] work at a high level?
  ```

  ```
  What is Tailwind CSS and how does it differ from traditional CSS?
  ```
</details>

### 🎁 Optional Model Experimentation Challenge

Technical framework questions are great for comparing models - try asking about a complex technology stack with different available models to see different explanation styles! 

**Try This**: Pick one technology or framework from the project and ask about it using different available models. Try each of these three prompts and compare the responses.

1. "What is [technology] and how does it work?"
2. "Explain [technology] and its role in this project"
3. "Analyze the architectural benefits of using [technology] in this context"

**Questions to Consider:**
- Which model gave the most comprehensive explanation?
- Did any model provide unique insights the others missed?
- Which explanation style did you prefer and why?
- How did the depth of technical detail vary between models?

## 🔨 Step 5: Understanding Code Components

Let's explore specific components to see how they work.

### Instructions:

1. **Explore a UI component:**
   - Open the file `src/components/gallery/GalleryGrid.tsx`
   - Select lines 30-43 (or any interesting section)
   - Ask GitHub Copilot to explain the selected code

2. **Use the workspace participant:**

If you get stuck, try these sample prompts:

<details>
  <summary>Sample Prompts</summary>

  ```
  @workspace /explain
  ```

  ```
  How does the GalleryGrid component handle photo filtering?
  ```

  ```
  Explain how the UploadZone component implements drag-and-drop functionality.
  ```

  ```
  What are the UI layout components and how are they used?
  ```

</details>

### 💡 Pro Tips for Code Exploration:
- Highlight specific code sections before asking for explanations
- Use `@workspace` to get context-aware answers
- Ask about design patterns or architectural decisions
- Compare different component implementations

## 🎨 Step 6: Understanding the Component System

The PixelPerfect Gallery uses a component-driven architecture. Let's explore it:

### Instructions:

Ask GitHub Copilot about the component structure and design patterns.

<details>
  <summary>Sample Prompts</summary>

  ```
  What UI components are available in the src/components/ui/ directory?
  ```

  ```
  How does this project organize reusable components vs feature-specific components?
  ```

  ```
  Explain the purpose of the SectionContainer and SectionTitle components.
  ```

  ```
  Tell me about the improvements that can be made in this repo.
  ```

</details>

**Pro Tip:** Review the `COMPONENT_USAGE_GUIDE.md` file in the root of the repository for detailed component documentation!

## 🏆 Exercise Wrap-up

Congratulations! You've successfully used GitHub Copilot Chat in Ask mode to:
- ✅ Discover available Copilot features and commands
- ✅ Understand the purpose and functionality of the photo gallery codebase
- ✅ Analyze project structure and organization
- ✅ Identify technologies, frameworks, and dependencies
- ✅ Explore specific code components and patterns

### Reflection Questions:
1. How did using GitHub Copilot Chat change your approach to exploring a new codebase compared to manual exploration?
2. What types of questions were most effective for getting useful information?
3. Were there any areas where GitHub Copilot's explanations needed clarification or weren't accurate?
4. **Model Comparison**: Which AI models did you try, and what differences did you notice in their responses?
5. **Model Preferences**: Did you develop preferences for certain models for specific types of questions? Why?

### Key Takeaways:
- GitHub Copilot Chat can dramatically accelerate codebase onboarding
- Starting with high-level questions and drilling down works well
- The `/help` command shows you available features and slash commands
- Use `@workspace` for context-aware code explanations
- **Different AI models excel at different tasks** - experimenting with multiple models gives you a more complete picture
- **Model selection strategy** can improve both the quality and speed of your development workflow
