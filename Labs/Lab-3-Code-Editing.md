# Exercise 3 - Code Editing and Generation with GitHub Copilot

#### Duration: 40 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Master GitHub Copilot's Edit mode for targeted code modifications
- Understand GitHub Copilot's Agent mode for multi-file code generation and modifications
- Understand when to use Edit mode vs. Agent mode in the IDE
- Generate new features and components with context-aware AI assistance
- Review and refine AI-generated code effectively
- Learn best practices for iterative AI-assisted development

## 📸 Scenario: Enhancing PixelPerfect Gallery Features

Your manager at PixelPerfect Gallery has requested several new features that will require changes across multiple files. You've been tasked with implementing these enhancements efficiently while maintaining the high quality standards of the codebase.

Your task today is to use GitHub Copilot's Edit and Agent modes to:
- Make targeted, deliberate changes to specific files with Edit mode
- Implement multi-file features with Agent mode assistance
- Create new components and integrate them into the application
- Make context-aware changes across the codebase

## 💡 Understanding GitHub Copilot Chat Modes

Before we dive into code generation, let's understand the different ways you can interact with GitHub Copilot in VS Code. GitHub Copilot Chat offers multiple modes, each optimized for different types of tasks:

| Mode | Trigger | Best For | Scope |
|------|---------|----------|-------|
| **Ask Mode** | Copilot Chat, select "Ask" | Understanding code, getting explanations, learning concepts | Read-only, no changes |
| **Edit Mode** | Copilot Chat, select "Edit" | Deliberate, specific changes to explicitly targeted files (1 to many files) | Targeted files you specify |
| **Agent Mode** | Copilot Chat, select "Agent" | Exploratory tasks, architectural planning, complex problem-solving | Workspace-wide, autonomous |
| **Plan Mode** | Copilot Chat, select "Plan" | Previewing changes before execution, understanding impact | Shows plan without making changes |

> **You learned Ask mode in Lab 2** where you explored the codebase. Now we'll focus on **Edit Mode** and **Agent Mode** for making code changes.

### 🎯 Understanding IDE Code Generation Modes

**When to use each mode:**

- **Ask Mode**: Use when you need to understand code first, want suggestions before implementation, or are exploring different approaches.

- **Edit Mode**: Use when you know exactly what needs to change and in which files. Edit mode makes deliberate, specific modifications to 1 to many files that you explicitly target. Perfect for focused refactoring, bug fixes, or feature additions where you control the scope.

- **Agent Mode**: Use when you need AI to explore your codebase, make decisions about architecture, or solve complex problems where the solution isn't immediately clear. Agent mode autonomously plans and executes changes across your workspace.

- **Plan Mode**: Use when you want to preview what changes Copilot would make before executing them. Plan mode generates a detailed plan showing files to be modified, changes to be made, and the reasoning behind decisions—without actually applying any changes. Great for understanding impact and validating approach before committing.

### 🆕 About Plan Mode (Recently Released)

**Plan mode** is a new addition to GitHub Copilot in VS Code that helps you understand what changes will be made before they're executed. Think of it as a "dry run" for your AI-assisted changes.

**How Plan Mode Works:**
1. You describe what you want to accomplish
2. Copilot analyzes your codebase and creates a detailed plan
3. The plan shows:
   - Which files will be modified or created
   - What specific changes will be made to each file
   - The reasoning behind the changes
   - Dependencies and impacts
4. You review the plan without any code being changed
5. You can then execute the plan, modify your request, or try a different approach

**Benefits:**
- **Risk reduction**: See the impact before changes are made
- **Learning opportunity**: Understand AI's decision-making process
- **Better prompts**: Refine your request based on the preview
- **Confidence**: Proceed with changes knowing what will happen

**When to Use Plan Mode:**
- Before making significant refactoring changes
- When working with unfamiliar code sections
- To validate your approach before implementation
- When you want to understand AI's reasoning
- Before changes that might affect multiple files

> **Note**: Plan mode is currently available in VS Code Insiders and will be rolled out to stable VS Code soon. This lab focuses on **Edit and Agent modes** which are the primary modes for code generation. **IDE Agent mode** (this lab) works interactively within VS Code, different from **Coding Agent** (Lab 7) which works autonomously on GitHub issues.

## 📝 Step 1: Using Edit Mode for Targeted Code Changes

While Agent mode is powerful for exploratory and autonomous work, Edit mode is ideal when you know exactly what needs to change. Let's start with Edit mode to make focused improvements to existing code.

### Exercise: Quick Refactoring with Edit Mode

Let's use Edit mode for a focused improvement to existing code.

### Instructions:

1. **Open the file** `pixelperfect-gallery/src/components/gallery/GalleryGrid.tsx`

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

6. **Keep and test:**
   - Click "Keep" to accept the changes
   - Save the file
   - Test that filtering still works in the browser

### 💡 Edit Mode Best Practices:

- **Be explicit about files**: Specify exactly which files should be modified
- **Be deliberate**: Know what you want changed before using Edit mode
- **Use for targeted scope**: Works on 1 to many files you explicitly name
- **Review diffs carefully**: Edit mode shows you exactly what will change
- **Control the changes**: You determine the scope, not the AI

### 🔍 Comparing Agent Mode vs Edit Mode:

**Example Scenario**: Adding error handling

**Edit Mode approach:**
```
Add try-catch error handling to the following files:
- pixelperfect-gallery/src/components/gallery/GalleryGrid.tsx (in the filter function)
- pixelperfect-gallery/src/app/page.tsx (in the data loading section)
- pixelperfect-gallery/src/lib/mock-photo-data.ts (in the data export)

Use consistent error messages and logging.
```
*Result: Targeted, deliberate changes to the 3 files you specified*

**Agent Mode approach:**
```
Analyze the application and add appropriate error handling wherever needed. 
Use your judgment to determine which components need error boundaries, 
which functions need try-catch blocks, and how to handle errors gracefully.
```
*Result: AI autonomously explores, plans, and implements error handling across multiple files*

### ⚠️ Key Difference:

**Edit Mode**: You tell Copilot what to change and where (1 to many specific files)  
**Agent Mode**: Copilot explores, decides what to change, and where to make those changes

## 🤖 Step 2: Using Agent Mode to Add a Footer Component

Let's start by using GitHub Copilot's Agent mode to add a footer component to the application. Agent mode excels at exploratory tasks where AI can autonomously determine the best approach.

### Instructions:

1. **Open GitHub Copilot Chat:**
   - Click the chat icon in the sidebar (or press `Ctrl+Alt+I` / `Cmd+Ctrl+I`)
   - Ensure you're in **Agent mode** (select "Agent" from the mode selector at the top)

2. **Provide context by opening related files:**
   - Open `pixelperfect-gallery/src/app/layout.tsx` to show where the footer will be integrated. In the chat window click the `+` next to the file name to include it as context
   - Open `pixelperfect-gallery/src/components/ui/layout/Hero.tsx` as an example of existing component style. In the chat window click the `+` next to the file name to include it as context
   - Having these files open helps Agent mode understand your project patterns. You can also directly use files as context with `#fileName.xxx`

3. **Give Agent mode a clear task:**
   - Give Agent mode a prompt that clearly instructs it to add the `<footer>` section to our Gallery site. If you'd like an example of what this could look like see below
   - <details>
      <summary>Hint:</summary>
   
      Type the following prompt in the chat:
      ```
      Create a footer component for this application and integrate it into the main layout.
      
      Requirements:
      - Create a new Footer.tsx component in pixelperfect-gallery/src/components/ui/layout/
      - Include PixelPerfect Gallery branding/logo text
      - Add copyright information with current year
      - Include links to About, Privacy, and Terms pages
      - Style with Tailwind CSS matching the existing design system
      - Support dark mode using dark: classes
      - Add the footer to layout.tsx at line 52 where the REPLACE THIS COMMENT placeholder is
      
      Follow the patterns used in other layout components like Hero.tsx.
      ```

   </details>
   

4. **Watch Agent mode work:**
   - Agent mode will create the Footer component file
   - It will modify layout.tsx to import and use the footer
   - Changes appear in your editor in real-time
   - You can see the progress in the chat window

5. **Review the generated code:**
   - Check the new `pixelperfect-gallery/src/components/ui/layout/Footer.tsx` file
   - Review the changes to `pixelperfect-gallery/src/app/layout.tsx`
   - Verify the styling matches existing components
   - Ensure proper TypeScript types are used
   - Check that imports are correct

6. **Test your changes:**
   - `Keep` all of the changes and if needed save all modified files
   - Check the browser at [http://localhost:3000](http://localhost:3000)
   - Scroll to the bottom to see your new footer
   - Toggle dark mode to verify dark mode support works
      - If dark mode support wasn't achieved iterate on the prompt with Agent mode to have it implement that.

### 💡 Pro Tips for Agent Mode:
- **Be specific about file locations**: Specify exact paths where new files should be created
- **Reference existing patterns**: Point Agent mode to similar components to follow
- **Use `@workspace` for broader context**: `@workspace` should be included in agent requests automatically. However, depending on IDE version and feature it will sometimes be necessary to manually include it.
- **Review before accepting**: Always check Agent mode's output before accepting it
- **Iterate if needed**: You can refine your prompt and try again if the plan isn't quite right. You don't have to opt to `Keep` anything to iterate. Simply type a follow-up prompt to Copilot and it will continue working.

### ⚠️ Common Issues:
- **Agent mode not available**: Ensure GitHub Copilot is enabled and you have the latest VS Code version
- **Styling doesn't match**: Reference specific components in your prompt for consistent styling
- **Files created in wrong location**: Be explicit about file paths in your requirements

## 🎯 Step 3: Using Agent Mode for Multi-File Feature Implementation

Now let's use Agent mode for a more complex task that involves creating a new feature across multiple files. This demonstrates Agent mode's real power.

### Scenario:

The gallery needs a "Featured Photos" section on the homepage that highlights selected photos. This requires:
- Creating a new component
- Adding mock data
- Integrating it into the home page
- Ensuring consistent styling

### Instructions:

1. **Prepare the context:**
   - Open `pixelperfect-gallery/src/app/page.tsx` (the home page where feature will be added)
   - Open `pixelperfect-gallery/src/components/gallery/GalleryGrid.tsx` (for component pattern reference)
   - Open `pixelperfect-gallery/src/lib/mock-photo-data.ts` (to see data structure)

2. **Prompt Agent mode with the complete requirement:**

   - Come up with a prompt that covers the core requirements listed above.
   - **Hint**: Using markdown format to create lists of requirements is a very effective method when working with AI
   - <details>
      <summary>Hint:</summary>

      Type the following prompt in the chat:
      ```
      Create a Featured Photos section for the homepage.
      
      Tasks:
      1. Create a new FeaturedSection.tsx component in pixelperfect-gallery/src/components/gallery/
      2. The component should display 3 featured photos in a hero-style layout
      3. Add a "featured" boolean field to the Photo type in pixelperfect-gallery/src/lib/mock-photo-data.ts
      4. Update the mock data to mark 3 photos as featured
      5. Import and add FeaturedSection to the home page (src/app/page.tsx) after the Hero component
      6. Use existing components like SectionContainer and SectionTitle for consistency
      7. Style with Tailwind CSS and include dark mode support
      8. Make it responsive (different layouts for mobile/desktop)
      
      Follow patterns from GalleryGrid.tsx and other components.
      ```
   
      </details>

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

### 🔍 Understanding Agent Mode's Workflow:

When you accept the plan, Agent mode:
1. **Analyzes** your entire workspace and relevant files
2. **Plans** the sequence of changes needed
3. **Creates** new files with appropriate content
4. **Modifies** existing files to integrate the new feature
5. **Validates** that changes follow project patterns
6. **Applies** all changes atomically

## 🔄 Step 4: Iterating and Refining with Agent Mode

One of Agent mode's strengths is the ability to iterate on existing code. Let's practice this by enhancing an existing component or the one you created in Step 3.

### Scenario:

You want to add animations and improve the user experience for one of the components. This demonstrates iterative refinement with Agent mode.

### Instructions:

1. **Choose a component to enhance:**
   - Open `pixelperfect-gallery/src/components/gallery/FeaturedSection.tsx` or `pixelperfect-gallery/src/components/gallery/GalleryGrid.tsx`
   - Ensure the file you selected is included as context (hint: `#fileName.tsx`)
   - You'll want to use the same chat session you used in Step 3

2. **Continue the conversation in Agent mode:**
   
   Agent mode remembers your previous conversation, so you can build on it:
   
   **If enhancing FeaturedSection from Step 3:**
   - Add animations to the featured section (fade-in, hover effects, particle effects, etc.)
   - Add a View Gallery button
   - Add UI to show when image data is being loaded
   - Make improvements to mobile UI. We need to improve the way the images are shown and how you can navigate through them
   - <details>
      <summary>Hint:</summary>

      Type the following prompt in the chat:
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
      
      </details>
   
   **If enhancing GalleryGrid instead:**
   - Add animations to the featured section (fade-in, hover effects, shadowing, etc.)
   - Improve the mobile layout
   - Add loading indicators while data is being loaded
   - Add an animation for when the grid is ready and appears
   - <details>
      <summary>Hint:</summary>

      Type the following prompt in the chat:
      ```
      Enhance the GalleryGrid component in pixelperfect-gallery/src/components/gallery/GalleryGrid.tsx:
      
      Improvements:
      1. Add smooth fade-in animations when photos load using Framer Motion
      2. Add hover effects on photos (scale and shadow)
      3. Improve the mobile layout with better spacing
      4. Add loading skeletons while photos are being fetched
      5. Add a subtle entrance animation when the grid appears
      
      Use the patterns from other components that use Framer Motion.
      ```
      
   </details>

4. **Review agent modes changes:**
   - Agent mode will show what files it modifies as it works
   - Depending on which file you selected, verify that it updates that file
   - You should see new imports for Framer Motion
   - Accept the changes

5. **Test the improvements:**
   - Refresh the browser and observe the animations
   - Hover over photos to see the effects
   - Resize the browser to see responsive behavior

6. **Request additional refinements if needed:**
   
   You can continue the conversation:
   ```
   Make the animation timing slower and more elegant
   ```
   
   Or:
   ```
   Add a subtle background pattern to the featured section
   ```

   OR:
   Have Copilot refine the changes to what you think will look best. There are no wrong answers!

### 💡 Benefits of Iterating with Agent Mode:

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

**Tip**: Start a new Agent mode conversation for unrelated features

## 🎓 Step 5: Best Practices for IDE AI-Assisted Development

Let's review what makes for effective AI-assisted development in the IDE:

### ✅ Do's for Agent Mode:

1. **Let AI Explore and Decide**: Give high-level goals and let Agent mode determine the approach
   - ❌ "Modify these 3 specific files to add error handling"
   - ✅ "Add comprehensive error handling to the application where appropriate"

2. **Provide Context, Not Instructions**: Open relevant files to guide discovery
   - Open similar components for style patterns
   - Reference existing patterns: "Follow patterns in @Hero.tsx"
   - Let Agent mode decide which files to modify

3. **Use for Complex Problems**: Leverage Agent mode's autonomous capabilities
   - Architectural decisions and planning
   - Exploratory refactoring
   - Problems where the solution isn't immediately clear

4. **Review Plans Before Accepting**: Always check what Agent mode intends to do
   - Verify all files to be modified are correct
   - Ensure no unintended changes
   - Confirm the approach makes sense

5. **Iterate Conversationally**: Build on previous context
   - "Now add animations to the component we just created"
   - "Enhance the Featured section with hover effects"

### ✅ Do's for Edit Mode:

1. **Be Explicit About Files**: Tell Copilot exactly which files to modify
   - ✅ "Refactor the filter function in pixelperfect-gallery/src/components/gallery/GalleryGrid.tsx"
   - ✅ "Add error handling to auth.ts, api.ts, and database.ts"

2. **Be Deliberate and Specific**: Know what you want changed
   - ✅ "Add memoization to the filter function"
   - ❌ "Improve this component" (too vague)

3. **Control the Scope**: Use Edit mode when you want to control exactly what changes
   - Specify 1 to many files explicitly
   - Define the exact changes needed
   - Maintain control over the modification scope

4. **Review Diffs**: Edit mode shows exactly what will change
   - Check additions and deletions carefully
   - Ensure functionality is preserved

### ❌ Universal Don'ts:

1. **Don't skip review**: Always understand generated code before using it
2. **Don't ignore errors**: If TypeScript complains, investigate and fix
3. **Don't forget testing**: Test all AI-generated code in the browser
4. **Don't lose context**: If conversations get long, start fresh
5. **Don't over-rely**: AI is a powerful assistant, **not a replacement for thinking**

### 🎯 Mode Selection Quick Guide:

| Scenario | Use This Mode | Why |
|----------|--------------|-----|
| Explore codebase and decide what to change | **Agent** | Autonomous discovery and planning |
| Complex problem where solution isn't clear | **Agent** | AI determines best approach |
| Architectural planning and implementation | **Agent** | Workspace-wide context and decisions |
| Refactor specific files you identify | **Edit** | Targeted changes to 1-many files you specify |
| Fix bug in known locations | **Edit** | Deliberate modifications with explicit control |
| Add feature to specific components | **Edit** | You control which files are changed |
| Preview changes before executing | **Plan** | See impact without modifying code |
| Validate approach before committing | **Plan** | Review plan and reasoning first |
| Understand code or get suggestions | **Ask** | Read-only exploration |

## 🏆 Exercise Wrap-up

Excellent work! You've mastered GitHub Copilot's IDE modes for code generation:
- ✅ Applied Edit mode for targeted, surgical code improvements
- ✅ Used Agent mode to create multi-file features with full integration
- ✅ Implemented complex functionality across components, data, and pages
- ✅ Iterated on AI-generated code to refine and enhance features
- ✅ Learned when to use each mode for maximum effectiveness

### Reflection Questions:
1. **How does Agent mode's multi-file capability change your development workflow?**
2. **When would you choose Edit mode over Agent mode, and why?**
3. **What surprised you about Agent mode's understanding of your codebase?**
4. **How might you use iterative prompting to build complex features?**
5. **What strategies will you use to provide better context to Copilot?**

### Key Takeaways:
- **Edit mode is perfect** for targeted changes when you know exactly what to modify
- **Agent mode is the primary tool** for feature development requiring multiple files
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
