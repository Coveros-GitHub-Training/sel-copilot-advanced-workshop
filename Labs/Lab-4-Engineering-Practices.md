# Exercise 4 - Engineering Best Practices with GitHub Copilot

#### Duration: 15 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Understand how to debug and inspect Copilot's decision-making process
- Explore personal instructions and how they influence code generation

## 📸 Scenario: Improving Team Collaboration at PixelPerfect Gallery

Your team at PixelPerfect Gallery has been using GitHub Copilot for a few weeks now, and developers are getting great results. However, your manager has noticed that:
- Some developers get better results than others with similar prompts
- Team members aren't sure why Copilot makes certain suggestions
- There's inconsistency in the code being generated

Today, you'll learn professional engineering practices for using GitHub Copilot effectively. These practices will help you understand AI decision-making and maintain code quality standards through personal configuration.

## 🔍 Introduction to Engineering Best Practices

When using AI-assisted development in a professional environment, it's crucial to:
- **Understand the AI's reasoning** - Know why suggestions are made
- **Maintain standards** - Ensure consistent code quality across the team
- **Debug effectively** - Investigate when suggestions don't meet expectations

GitHub Copilot provides features specifically designed for professional engineers to address these needs.

## 🐛 Step 1: Inspect Copilot's Decision-Making Process

Understanding how Copilot makes suggestions helps you write better prompts and trust the AI's recommendations. The debug view shows you exactly what context Copilot is using and how it formulates responses.

### Why This Matters:
- **Improve prompts**: See what context Copilot has access to
- **Debug issues**: Understand why unexpected suggestions appear
- **Build trust**: Transparency in AI decision-making
- **Learn patterns**: Discover what makes effective prompts

### Instructions:

**Method 1: Using Keyboard Shortcut**
1. Press `Ctrl + Shift + P` (Windows/Linux) or `Cmd + Shift + P` (Mac)
2. Type "Copilot Chat Debug"
3. Select **"Copilot Chat Debug: Focus on Copilot Chat Debug View"**

**Method 2: Through the Copilot Chat Window**
1. Open GitHub Copilot Chat
2. At the top of the Copilot Chat window, click the 3 ellipses `...`
3. Click **"Show Chat Debug View"**

### What You'll See:

Once the debug panel opens, you can explore:

- **Prompts**: The actual prompts sent to the AI model
- **System Prompts**: Background instructions given to Copilot (from custom instructions, repository context, etc.)
- **Metadata**: Context information, model settings, and parameters
- **Response Details**: How Copilot formulated its suggestions, including tokens used

### 🔬 Try This Experiment:

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

### 💡 Pro Tips:
- Use this when Copilot's suggestions seem unexpected - you can see exactly what context it's using
- Check the debug view if you're not getting relevant suggestions - you might need to add more context
- Review system prompts to understand what standards Copilot is following
- Look at token usage to optimize your prompts for efficiency

## 🎛️ Step 2: Explore and Configure Personal Instructions

Personal instructions define how Copilot behaves across all repositories you work on. They're powerful for maintaining consistent coding standards and preferences.

### Why This Matters:
- **Consistency**: Get similar code style across all your projects
- **Efficiency**: Don't repeat common preferences in every chat
- **Standards**: Enforce your team's or personal coding guidelines
- **Customization**: Tailor Copilot to your specific needs and workflows

### Access Personal Instructions

1. **Navigate to GitHub Copilot**: Go to [https://github.com/copilot](https://github.com/copilot)

2. **Open settings**: Click **Your profile icon** in the bottom left of the screen

3. **Open personal instructions**: Select **"Personal instructions"**

4. **Review existing instructions** (if any are already configured)

### Create or Modify Personal Instructions

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

### Test Your Personal Instructions

1. **After adding instructions**, return to VS Code

2. **Ask Copilot to generate some code:**
   ```
   Create a new component for displaying photo metadata
   ```

3. **Observe how the generated code** reflects your personal instructions

4. **Experiment with different instructions** to see how they affect output

### 🔍 Things to Explore:

- How do personal instructions influence code style?
- What coding standards are enforced?
- How do the instructions interact with repository-level instructions?
- Do instructions apply consistently across different file types?

### ⚖️ Balancing Personal vs Repository Instructions

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

## 🏆 Exercise Wrap-up

Excellent work! You've learned professional engineering practices for using GitHub Copilot:
- ✅ Debugged and inspected Copilot's decision-making process
- ✅ Configured personal instructions for consistent code generation

### Reflection Questions:
1. **How can the debug view help you write better prompts?**
2. **How might personal instructions improve your daily workflow?**
3. **What standards or preferences would you include in personal instructions?**

### Key Takeaways:
- The debug view provides transparency into AI decision-making
- Personal instructions maintain consistency across your work
- These practices make AI-assisted development more professional and reliable
