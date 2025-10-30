# Exercise 3 - Code Editing and Generation with GitHub Copilot

#### Duration: 30 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Understand how to use GitHub Copilot's Autocomplete feature for code generation
- Learn to use GitHub Copilot's Edit mode for code modifications
- Generate new UI components and features with AI assistance
- Review and refine AI-generated code effectively

## 📸 Scenario: Enhancing PixelPerfect Gallery Features

Your manager at PixelPerfect Gallery has noticed that the application is missing a footer component and could benefit from some UI enhancements. You've been tasked with adding these features quickly while maintaining the high quality standards of the codebase.

Your task today is to use GitHub Copilot to:
- Add a footer component to the main layout
- Generate new UI components for the gallery
- Understand best practices for AI-assisted code generation
- Review and iterate on AI-generated code

## 💡 Understanding Code Generation Modes

GitHub Copilot offers several ways to generate code:

| Feature | Trigger | Best For |
|---------|---------|----------|
| **Autocomplete** | Type naturally in the editor | Quick, inline code suggestions as you type |
| **Edit Mode** | Open Copilot Chat, select "Edit" | Modifying existing code, refactoring, feature additions |
| **Generate Code** | Right-click → Copilot → Generate | Creating new functions, classes, or components |
| **Slash Commands** | `/new`, `/fix`, `/tests` in chat | Specific code generation tasks |

## ✨ Step 1: Using Autocomplete to Generate a Footer Component

Let's start by adding a footer to the main layout using GitHub Copilot's autocomplete feature.

### Instructions:

1. **Navigate to the layout file:**
   - Open `src/app/layout.tsx`

2. **Find the location to add the footer:**
   - Go to line 52 where you see `{/* REPLACE THIS COMMENT */}`

3. **Remove the comment and add a descriptive comment:**
   - Delete the existing comment on line 52
   - Type the following comment:
   ```tsx
   {/* Create a footer for this section. It should contain the logo and copyright information. */}
   ```

4. **Wait for GitHub Copilot's suggestion:**
   - After typing the comment, press `Enter` to go to a new line
   - GitHub Copilot will start suggesting code (you'll see ghost text in gray)
   - Press `Tab` to accept the suggestion
   - Continue pressing `Enter` and `Tab` to build the complete footer
   - Press `Esc` when the footer is complete or when Copilot starts suggesting unrelated code

5. **Review the generated code:**
   - Make sure the footer includes appropriate elements
   - Check that the styling matches the rest of the application
   - Verify that the component structure makes sense

6. **Test your changes:**
   - Save the file
   - Refresh [http://localhost:3000](http://localhost:3000) in your browser
   - Scroll to the bottom of the page to see your new footer

### 💡 Pro Tips for Autocomplete:
- **Be descriptive in comments**: The more specific your comment, the better the suggestions
- **Use consistent naming**: Follow the project's naming conventions in your prompts
- **Accept partially**: You can accept part of a suggestion and modify the rest
- **Iterate**: If the first suggestion isn't perfect, try rephrasing your comment

### ⚠️ Common Issues:
- **Suggestion not appearing**: Make sure GitHub Copilot is enabled (check the status bar)
- **Wrong suggestion**: Press `Esc` and rephrase your comment more specifically
- **Too much generated**: Press `Esc` to stop generation and clean up manually

## 🎨 Step 2: Reviewing AI-Generated Code

Before we move forward, it's important to understand how to review and improve AI-generated code.

### Option A: AI-Powered Review (Premium Feature)

If you have premium access to advanced models:

1. **Select the generated footer code**
2. **Right-click** on the selection
3. **Select "Copilot" → "Review and Comment"** (or similar option)
4. **Review the feedback** provided by GitHub Copilot
5. **Apply suggested improvements** as needed

### Option B: Manual Review (Always Available)

Use these criteria to review any AI-generated code:

**Code Quality Checklist:**
- [ ] Does the code follow the project's style and conventions?
- [ ] Are TypeScript types properly defined?
- [ ] Does it use appropriate Tailwind CSS classes for styling?
- [ ] Is the code accessible (proper semantic HTML)?
- [ ] Does it handle edge cases and potential errors?
- [ ] Is the component reusable and well-structured?

**Ask GitHub Copilot for help reviewing:**

<details>
  <summary>Sample Review Prompts</summary>

  ```
  Review this footer component for best practices and suggest improvements.
  ```

  ```
  Does this component follow React and Next.js best practices?
  ```

  ```
  Check if this code is accessible and suggest improvements.
  ```

  ```
  Is there a more efficient way to write this component?
  ```

</details>

## 💭 Step 3: Using Edit Mode to Generate New Components

Now let's use GitHub Copilot's Edit mode to create more substantial features. Edit mode is more powerful for complex changes because it:
- Understands the full context of your files
- Can make multi-line modifications
- Follows your project's patterns more consistently
- Allows for iterative refinement

### 🔍 Providing Context for Better Code Generation

GitHub Copilot automatically gathers context from several sources:
- **Active editor**: The currently open file and cursor position
- **Selection**: Any highlighted/selected code
- **Open tabs**: Files you have open in VS Code
- **Workspace**: Your project structure and related files

**Best Practices for Context:**
1. **Open related files**: Have related components or utilities open in tabs
2. **Use file references**: Include `@filename` in your prompts
3. **Highlight relevant code**: Select sections you want to reference or modify
4. **Reference documentation**: Point to README or component guides

**Learn More:** [VS Code Copilot Chat Context Documentation](https://code.visualstudio.com/docs/copilot/chat/copilot-chat-context)

### Instructions:

1. **Open GitHub Copilot Chat** (click the chat icon in the sidebar)

2. **Switch to Edit mode** (select "Edit" at the top of the chat panel)

3. **Choose a component to create:**

   **Option A: Photo Stats Component**
   ```
   Create a new component in src/components/gallery/ called PhotoStats.tsx that displays statistics about a photo (views, likes, date uploaded). Use TypeScript interfaces and Tailwind CSS for styling. Follow the existing component patterns in this project.
   ```

   **Option B: Filter Bar Component**
   ```
   Create a FilterBar component in src/components/gallery/ that allows users to filter photos by category and date. Include dropdown selects for both filters. Use Radix UI components if appropriate, and Tailwind CSS for styling.
   ```

   **Option C: Custom Component**
   - Think of a component that would be useful for the photo gallery
   - Describe it clearly to GitHub Copilot
   - Specify the file location, technologies to use, and styling approach

4. **Review the generated component:**
   - Check that it follows TypeScript best practices
   - Verify it uses appropriate styling
   - Ensure it matches the project's component patterns
   - Test that it compiles without errors

5. **Iterate if needed:**
   - Ask for specific improvements
   - Request additional features
   - Refine the styling or structure

<details>
  <summary>Sample Iteration Prompts</summary>

  ```
  Add TypeScript type definitions for the component props.
  ```

  ```
  Make this component more accessible by adding ARIA labels.
  ```

  ```
  Add dark mode support using Tailwind's dark: prefix.
  ```

  ```
  Improve the component's responsive design for mobile devices.
  ```

</details>

## 🛠️ Step 4: Using Prompt Files for Consistent Generation

PixelPerfect Gallery includes custom prompt files that help generate consistent code. Let's try using one!

### Instructions:

1. **Explore existing prompt files:**
   - Navigate to `.github/prompts/` folder
   - Look through the available prompt files
   - Notice the format: header with metadata, then the prompt body

2. **Use a prompt file to generate mock data:**

   In GitHub Copilot Chat, try this command:
   ```
   /generate-mock-photo-data 5
   ```

   This uses the custom prompt file to generate mock photo data following the project's data structure.

3. **Try the UI generation prompt:**
   ```
   /generate-new-ui for a photo card component that displays a photo thumbnail with title and photographer name. Place it in the gallery folder.
   ```

### 💡 Understanding Prompt Files:

Prompt files allow you to:
- **Standardize** common code generation tasks
- **Include context** specific to your project
- **Specify parameters** that can be customized each time
- **Maintain consistency** across your team

**Format:**
```markdown
---
description: 'What this prompt does'
mode: 'edit' or 'ask' or 'agent'
---
Your prompt template here with ${variables}
```

### 🎁 Optional Challenge: Create Your Own Prompt File

Try creating a custom prompt file for a common task:

1. **Create a new file** in `.github/prompts/`
2. **Name it descriptively**, e.g., `create-test-component.prompt.md`
3. **Use this template:**
   ```markdown
   ---
   description: 'Generate a test component with sample data'
   ---
   Create a new React component in ${input:location} called ${input:componentName}.
   The component should ${input:functionality}.
   Use TypeScript, Tailwind CSS, and follow Next.js 15 best practices.
   Include proper type definitions and export the component as default.
   ```

4. **Test your prompt file** by using it in Copilot Chat

## 🔄 Step 5: Refactoring Existing Code

Let's use Edit mode to improve existing code. We'll refactor the GalleryGrid component for better performance and readability.

### Instructions:

1. **Open the file** `src/components/gallery/GalleryGrid.tsx`

2. **Select lines 26-43** (the filtering logic)

3. **Open Copilot Chat in Edit mode**

4. **Ask for refactoring:**

<details>
  <summary>Sample Refactoring Prompts</summary>

  ```
  Refactor this filtering logic for better performance and readability. Add TypeScript type improvements.
  ```

  ```
  Extract the filtering logic into a separate utility function with proper TypeScript types.
  ```

  ```
  Optimize this component to reduce unnecessary re-renders.
  ```

  ```
  Add memoization to improve performance of this filtering logic.
  ```

</details>

5. **Review the suggestions:**
   - Compare the refactored code to the original
   - Understand what improvements were made
   - Check if the changes maintain the same functionality

6. **Test the refactored code:**
   - Run `npm run dev` to ensure no errors
   - Test the filtering functionality in the browser
   - Verify performance improvements if applicable

## 🎓 Step 6: Best Practices for AI-Assisted Code Generation

Let's review what makes for effective AI-assisted development:

### ✅ Do's:

1. **Be Specific**: Clear, detailed prompts get better results
   - ❌ "Make a button"
   - ✅ "Create a primary button component with hover and active states using Tailwind CSS"

2. **Provide Context**: Reference related files and patterns
   - ✅ "Follow the pattern used in @SectionContainer.tsx"
   - ✅ "Use the same styling approach as the existing components"

3. **Iterate**: Refine the generated code through conversation
   - Generate → Review → Request improvements → Repeat

4. **Review Critically**: Always review AI-generated code
   - Check for correctness and completeness
   - Verify it follows project conventions
   - Test thoroughly

### ❌ Don'ts:

1. **Don't blindly accept**: Always understand what code does before using it
2. **Don't skip testing**: AI-generated code needs testing just like human-written code
3. **Don't ignore patterns**: Make sure generated code follows your project's conventions
4. **Don't over-rely**: Use AI as a tool, not a replacement for understanding

## 🏆 Exercise Wrap-up

Great work! You've successfully used GitHub Copilot to:
- ✅ Generate code using Autocomplete
- ✅ Create new components with Edit mode
- ✅ Use custom prompt files for consistent generation
- ✅ Refactor existing code for improvements
- ✅ Review and iterate on AI-generated code

### Reflection Questions:
1. **How did Autocomplete compare to Edit mode for different tasks?**
2. **What types of code generation did GitHub Copilot excel at?**
3. **Where did you need to provide additional guidance or corrections?**
4. **How might prompt files improve team consistency?**
5. **What best practices will you adopt for AI-assisted coding?**

### Key Takeaways:
- Different generation methods (Autocomplete, Edit mode, prompts) suit different tasks
- Clear, specific prompts produce better results
- Always review and test AI-generated code
- Iterative refinement improves code quality
- Custom prompt files help maintain consistency
