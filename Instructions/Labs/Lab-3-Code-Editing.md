# Exercise 3 - Code Editing and Generation with GitHub Copilot

#### Duration: 30 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Master GitHub Copilot's Agent mode for multi-file code generation and modifications
- Understand when to use Agent mode vs. Edit mode in the IDE
- Generate new features and components with context-aware AI assistance
- Review and refine AI-generated code effectively
- Learn best practices for iterative AI-assisted development

## 📸 Scenario: Enhancing PixelPerfect Gallery Features

Your manager at PixelPerfect Gallery has requested several new features that will require changes across multiple files. You've been tasked with implementing these enhancements efficiently while maintaining the high quality standards of the codebase.

Your task today is to use GitHub Copilot's Agent mode to:
- Implement multi-file features with AI assistance
- Create new components and integrate them into the application
- Make context-aware changes across the codebase
- Understand best practices for AI-assisted development

## 💡 Understanding IDE Code Generation Modes

GitHub Copilot offers multiple modes in the IDE for different types of code generation:

| Mode | Trigger | Best For | Scope |
|------|---------|----------|-------|
| **Agent Mode** | Copilot Chat, select "Agent" | Complex features requiring multiple file changes | Workspace-wide |
| **Edit Mode** | Copilot Chat, select "Edit" | Quick modifications to specific code sections | Selected code or single file |
| **Ask Mode** | Copilot Chat, select "Ask" | Understanding code, getting suggestions | Read-only, no changes |

**When to use each mode:**

- **Agent Mode**: Use when implementing features that require changes across multiple files, creating new components with integrations, or making architectural improvements. Agent mode has full workspace context and can plan multi-step changes.

- **Edit Mode**: Use for targeted changes to existing code, quick refactoring of a specific function or component, or when you want more control over what gets modified.

- **Ask Mode**: Use when you need to understand code first, want suggestions before implementation, or are exploring different approaches.

> **Note**: This lab focuses on **IDE Agent mode** which works interactively within VS Code. This is different from **Coding Agent** (covered in Lab 7) which works autonomously on GitHub issues.

## 🤖 Step 1: Using Agent Mode to Add a Footer Component

Let's start by using GitHub Copilot's Agent mode to add a footer component to the application. Agent mode excels at this because it can create the component file and integrate it into the layout in one workflow.

### Instructions:

1. **Open GitHub Copilot Chat:**
   - Click the chat icon in the sidebar (or press `Ctrl+Alt+I` / `Cmd+Opt+I`)
   - Ensure you're in **Agent mode** (select "Agent" from the mode selector at the top)

2. **Provide context by opening related files:**
   - Open `src/app/layout.tsx` to show where the footer will be integrated
   - Open `src/components/ui/layout/Hero.tsx` as an example of existing component style
   - Having these files open helps Agent mode understand your project patterns

3. **Give Agent mode a clear task:**
   
   Type the following prompt in the chat:
   ```
   Create a footer component for this application and integrate it into the main layout.
   
   Requirements:
   - Create a new Footer.tsx component in src/components/ui/layout/
   - Include PixelPerfect Gallery branding/logo text
   - Add copyright information with current year
   - Include links to About, Privacy, and Terms pages
   - Style with Tailwind CSS matching the existing design system
   - Support dark mode using dark: classes
   - Add the footer to layout.tsx at line 52 where the REPLACE THIS COMMENT placeholder is
   
   Follow the patterns used in other layout components like Hero.tsx.
   ```

4. **Review Agent mode's plan:**
   - Agent mode will analyze your codebase and show you what files it plans to create or modify
   - Review the plan to ensure it matches your expectations
   - You'll see a preview of files to be created/modified
   - Click **"Accept"** to proceed or edit your prompt if needed

5. **Watch Agent mode work:**
   - Agent mode will create the Footer component file
   - It will modify layout.tsx to import and use the footer
   - Changes appear in your editor in real-time
   - You can see the progress in the chat window

6. **Review the generated code:**
   - Check the new `src/components/ui/layout/Footer.tsx` file
   - Review the changes to `src/app/layout.tsx`
   - Verify the styling matches existing components
   - Ensure proper TypeScript types are used
   - Check that imports are correct

7. **Test your changes:**
   - Save all modified files (if not auto-saved)
   - Check the browser at [http://localhost:3000](http://localhost:3000)
   - Scroll to the bottom to see your new footer
   - Toggle dark mode to verify dark mode support works

### 💡 Pro Tips for Agent Mode:
- **Open related files first**: Agent mode uses open files for context about patterns and style
- **Be specific about file locations**: Specify exact paths where new files should be created
- **Reference existing patterns**: Point Agent mode to similar components to follow
- **Use `@workspace` for broader context**: Include `@workspace` in your prompt for codebase-wide awareness
- **Review before accepting**: Always check Agent mode's plan before proceeding
- **Iterate if needed**: You can refine your prompt and try again if the plan isn't quite right

### ⚠️ Common Issues:
- **Agent mode not available**: Ensure GitHub Copilot is enabled and you have the latest VS Code version
- **Changes not appearing**: Make sure you accepted the plan and Agent mode completed its work
- **Styling doesn't match**: Reference specific components in your prompt for consistent styling
- **Files created in wrong location**: Be explicit about file paths in your requirements
- **Build errors**: Check that imports are correct and component syntax is valid

## 🎯 Step 2: Using Agent Mode for Multi-File Feature Implementation

Now let's use Agent mode for a more complex task that involves creating a new feature across multiple files. This demonstrates Agent mode's real power.

### Scenario:

The gallery needs a "Featured Photos" section on the homepage that highlights selected photos. This requires:
- Creating a new component
- Adding mock data
- Integrating it into the home page
- Ensuring consistent styling

### Instructions:

1. **Prepare the context:**
   - Open `src/app/page.tsx` (the home page where feature will be added)
   - Open `src/components/gallery/GalleryGrid.tsx` (for component pattern reference)
   - Open `src/lib/mock-photo-data.ts` (to see data structure)

2. **Prompt Agent mode with the complete requirement:**
   
   ```
   Create a Featured Photos section for the homepage.
   
   Tasks:
   1. Create a new FeaturedSection.tsx component in src/components/gallery/
   2. The component should display 3 featured photos in a hero-style layout
   3. Add a "featured" boolean field to the Photo type in src/lib/mock-photo-data.ts
   4. Update the mock data to mark 3 photos as featured
   5. Import and add FeaturedSection to the home page (src/app/page.tsx) after the Hero component
   6. Use existing components like SectionContainer and SectionTitle for consistency
   7. Style with Tailwind CSS and include dark mode support
   8. Make it responsive (different layouts for mobile/desktop)
   
   Follow patterns from GalleryGrid.tsx and other components.
   ```

3. **Review the multi-file plan:**
   - Agent mode will show all files it plans to create or modify
   - Verify it includes:
     - New `FeaturedSection.tsx` component
     - Updates to `mock-photo-data.ts` (type and data)
     - Changes to `page.tsx` (integration)
   - Accept the plan to proceed

4. **Monitor the implementation:**
   - Watch as Agent mode creates the component
   - See it update the data structure and mock data
   - Observe it integrate everything into the home page
   - Check that it follows existing patterns

5. **Review and test:**
   - Check each modified/created file
   - Verify TypeScript types are consistent
   - Test the homepage at [http://localhost:3000](http://localhost:3000)
   - Confirm the featured section appears and looks good
   - Test responsiveness by resizing the browser

### 💡 What Makes This Agent Mode-Perfect:

- **Multiple files**: Agent mode coordinates changes across several files
- **Dependencies**: It understands that the component needs data, types, and integration
- **Context awareness**: It follows patterns from files you have open
- **Consistency**: It maintains styling and architectural patterns

### 🔍 Understanding Agent Mode's Workflow:

When you accept the plan, Agent mode:
1. **Analyzes** your entire workspace and relevant files
2. **Plans** the sequence of changes needed
3. **Creates** new files with appropriate content
4. **Modifies** existing files to integrate the new feature
5. **Validates** that changes follow project patterns
6. **Applies** all changes atomically

### ⚠️ Troubleshooting:

- **Plan missing files**: Be more explicit about all required changes
- **Component doesn't appear**: Check that imports were added correctly
- **Type errors**: Review the type definitions in mock-photo-data.ts
- **Styling issues**: Reference specific components for style consistency

## 🔄 Step 3: Iterating and Refining with Agent Mode

One of Agent mode's strengths is the ability to iterate on existing code. Let's enhance the Featured Photos section we just created.

### Scenario:

After reviewing the Featured section, you want to add animations and improve the user experience. This requires iterative refinement across the component files.

### Instructions:

1. **Open the Featured section component:**
   - Navigate to `src/components/gallery/FeaturedSection.tsx` (created in Step 2)
   - Keep `src/app/page.tsx` open for context

2. **Continue the conversation in Agent mode:**
   
   Since Agent mode remembers your previous conversation, you can build on it:
   ```
   Enhance the FeaturedSection component we just created:
   
   Improvements:
   1. Add smooth fade-in animations using Framer Motion (already installed)
   2. Add hover effects on featured photos (scale and shadow)
   3. Include a "View Gallery" call-to-action button at the bottom
   4. Add loading states for when data is being fetched
   5. Improve the mobile layout to show 1 photo at a time in a carousel style
   
   Use the patterns from other components that use Framer Motion.
   ```

3. **Review the enhancement plan:**
   - Agent mode will show what files it will modify
   - It should update the FeaturedSection component
   - Possibly add new imports for Framer Motion
   - Accept the plan

4. **Test the improvements:**
   - Refresh the browser and observe the animations
   - Hover over photos to see the effects
   - Resize the browser to see responsive behavior
   - Check that dark mode still works

5. **Request additional refinements if needed:**
   
   You can continue the conversation:
   ```
   Make the animation timing slower and more elegant
   ```
   
   Or:
   ```
   Add a subtle background pattern to the featured section
   ```

### 💡 Benefits of Iterative Agent Mode:

- **Context preservation**: Agent mode remembers what it just built
- **Incremental improvements**: Make changes step-by-step rather than all at once
- **Learning opportunity**: See how to progressively enhance features
- **Safe experimentation**: Easy to ask for changes and see results immediately

### 🔍 Providing Effective Feedback to Agent Mode:

When iterating, be specific about what you want changed:

**Good iteration prompts:**
- ✅ "Make the animation duration 0.5 seconds instead of the current timing"
- ✅ "Change the hover scale from 1.05 to 1.02 for a more subtle effect"
- ✅ "Add error handling for when featured photos array is empty"

**Less effective prompts:**
- ❌ "Make it better"
- ❌ "Fix the animations"
- ❌ "Improve performance"

### 🎯 Practice Exercise:

Try one more iteration on your own:
1. Ask Agent mode to add photo captions that appear on hover
2. Request that clicking a featured photo navigates to a detail view
3. Add a smooth transition between photos on mobile

### ⚠️ When to Stop Iterating:

Watch for signs that you should start a fresh conversation:
- The conversation history becomes very long
- Agent mode starts making unrelated changes
- You're changing direction significantly from the original task
- TypeScript errors accumulate

**Tip**: Start a new Agent mode conversation for unrelated features

## 📝 Step 4: When to Use Edit Mode Instead of Agent Mode

While Agent mode is powerful for multi-file changes, Edit mode is better for quick, targeted modifications. Let's explore when and how to use Edit mode effectively.

### When to Choose Edit Mode:

**Use Edit Mode for:**
- ✅ Refactoring a single function or component
- ✅ Quick bug fixes in specific code sections
- ✅ Adding a single method or feature to an existing class
- ✅ Improving specific code blocks (performance, readability)
- ✅ When you want to see changes before they're applied

**Use Agent Mode for:**
- ✅ Creating new features that span multiple files
- ✅ Architectural changes affecting several components
- ✅ Adding new routes, pages, or major components
- ✅ Integrating new libraries or patterns across the codebase

### Exercise: Quick Refactoring with Edit Mode

Let's use Edit mode for a focused improvement to existing code.

### Instructions:

1. **Open the file** `src/components/gallery/GalleryGrid.tsx`

2. **Select lines 26-43** (the filtering logic section)

3. **Switch to Edit mode** in Copilot Chat

4. **Request a targeted improvement:**
   ```
   Refactor this filtering logic to use useMemo for better performance. Add proper TypeScript types for the filtered results.
   ```

5. **Review the changes before accepting:**
   - Edit mode shows you a diff of what will change
   - You can see exactly what code is being added/removed
   - Accept if it looks good, or refine your prompt

6. **Apply and test:**
   - Click "Apply" to make the changes
   - Save the file
   - Test that filtering still works in the browser

### 💡 Edit Mode Best Practices:

- **Select specific code**: Highlight exactly what you want to modify
- **Be surgical**: Ask for one specific improvement at a time
- **Review diffs carefully**: Edit mode shows you exactly what will change
- **Keep prompts focused**: "Add error handling to this function" not "improve everything"

### 🔍 Comparing Agent Mode vs Edit Mode:

**Example Scenario**: Adding error handling

**Agent Mode approach:**
```
Add error handling throughout the application for all API calls, 
file operations, and user inputs. Include error boundaries and 
toast notifications.
```
*Result: Multiple files modified with comprehensive error handling*

**Edit Mode approach:**
```
[Select specific function]
Add try-catch error handling to this function with user-friendly 
error messages
```
*Result: One function improved with targeted error handling*

### ⚠️ When Edit Mode Isn't Enough:

If Edit mode suggests creating new files or modifying multiple files, switch to Agent mode instead. Edit mode works best within the scope of what you have selected.

## 🎓 Step 5: Best Practices for IDE AI-Assisted Development

Let's review what makes for effective AI-assisted development in the IDE:

### ✅ Do's for Agent Mode:

1. **Start with Clear Requirements**: Define the complete scope upfront
   - ❌ "Add a footer"
   - ✅ "Create a Footer.tsx component in src/components/ui/layout/ with branding, links, and dark mode support, then integrate it into layout.tsx"

2. **Provide Rich Context**: Open relevant files before making requests
   - Open similar components for style patterns
   - Open files that will be modified or imported
   - Reference existing components: "Follow patterns in @Hero.tsx"

3. **Think Multi-File**: Use Agent mode when changes span multiple files
   - Creating components with integration
   - Adding features that need data, types, and UI
   - Architectural improvements

4. **Review Plans Before Accepting**: Always check what Agent mode intends to do
   - Verify all files to be modified are correct
   - Ensure no unintended changes
   - Confirm the approach makes sense

5. **Iterate Conversationally**: Build on previous context
   - "Now add animations to the component we just created"
   - "Enhance the Featured section with hover effects"

### ✅ Do's for Edit Mode:

1. **Select Precisely**: Highlight exactly what needs to change
   - Select specific functions, not entire files
   - Be surgical about what you want modified

2. **One Change at a Time**: Focus on single improvements
   - ✅ "Add memoization to this filter function"
   - ❌ "Improve this component" (too vague)

3. **Review Diffs**: Edit mode shows exactly what will change
   - Check additions and deletions carefully
   - Ensure functionality is preserved

### ❌ Universal Don'ts:

1. **Don't skip review**: Always understand generated code before using it
2. **Don't ignore errors**: If TypeScript complains, investigate and fix
3. **Don't forget testing**: Test all AI-generated code in the browser
4. **Don't lose context**: If conversations get long, start fresh
5. **Don't over-rely**: AI is a powerful assistant, not a replacement for thinking

### 🎯 Mode Selection Quick Guide:

| Scenario | Use This Mode | Why |
|----------|--------------|-----|
| Add new feature with multiple files | **Agent** | Coordinates changes across codebase |
| Create component and integrate it | **Agent** | Handles file creation and imports |
| Refactor single function | **Edit** | Quick, targeted change |
| Fix bug in specific code | **Edit** | Surgical precision |
| Understand code first | **Ask** | Read-only exploration |
| Major architectural change | **Agent** | Context-aware, multi-file planning |

## 🏆 Exercise Wrap-up

Excellent work! You've mastered GitHub Copilot's IDE modes for code generation:
- ✅ Used Agent mode to create multi-file features with full integration
- ✅ Implemented complex functionality across components, data, and pages
- ✅ Iterated on AI-generated code to refine and enhance features
- ✅ Applied Edit mode for targeted, surgical code improvements
- ✅ Learned when to use each mode for maximum effectiveness

### Reflection Questions:
1. **How does Agent mode's multi-file capability change your development workflow?**
2. **When would you choose Edit mode over Agent mode, and why?**
3. **What surprised you about Agent mode's understanding of your codebase?**
4. **How might you use iterative prompting to build complex features?**
5. **What strategies will you use to provide better context to Copilot?**

### Key Takeaways:
- **Agent mode is the primary tool** for feature development requiring multiple files
- **Edit mode complements Agent mode** for quick, targeted improvements
- Context is critical: open related files and reference existing patterns
- Iterative development with AI works just like with human developers
- Always review, test, and understand what AI generates
- Clear requirements and specific prompts yield better results

### 🎯 Real-World Applications:

**Agent Mode Use Cases:**
- Building new features from scratch
- Adding components with full integration
- Implementing requirements that touch multiple files
- Refactoring that affects architecture

**Edit Mode Use Cases:**
- Quick bug fixes
- Performance optimizations in specific functions
- Adding error handling to existing code
- Refining algorithms or logic

### 📚 What's Next?

- **Lab 4**: Learn engineering best practices for AI-assisted development
- **Lab 5**: Customize Copilot with prompt files and chat modes
- **Lab 7**: Explore Coding Agent for autonomous development on GitHub issues

Remember: Agent mode in the IDE (this lab) is for interactive development, while Coding Agent (Lab 7) is for autonomous work on GitHub. Both are powerful tools for different workflows!
