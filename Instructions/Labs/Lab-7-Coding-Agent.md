# Exercise 7 - GitHub Copilot Coding Agent

#### Duration: 30 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Understand GitHub Copilot's Coding Agent and its autonomous capabilities
- Learn to create and assign GitHub issues to Copilot for autonomous implementation
- Experience the full autonomous development workflow from issue creation to pull request
- Monitor and interact with Copilot's development process through session logs
- Review and iterate on AI-generated code using pull request workflows
- Understand best practices and limitations for coding agents

## 📸 Scenario: Scaling Development at PixelPerfect Gallery

PixelPerfect Gallery is growing rapidly, and your development backlog is overflowing with enhancement requests:
- Users want better photo filtering capabilities
- The admin dashboard needs new analytics features
- Documentation is falling behind
- Several UI components need accessibility improvements

Your manager has heard about GitHub Copilot's Coding Agent—an autonomous AI developer that can work independently on GitHub issues, just like a human team member. Today, you'll explore this revolutionary feature by delegating tasks to Copilot and seeing how it works autonomously to implement solutions.

## 🤖 Introduction to Coding Agent

**GitHub Copilot Coding Agent** is an autonomous AI developer that works directly on GitHub issues. Unlike the interactive IDE modes (Ask, Edit, Agent), Coding Agent works independently after being assigned an issue.

### What Coding Agent Can Do:

- ✅ Fix bugs and address issues
- ✅ Implement incremental new features
- ✅ Improve test coverage
- ✅ Update documentation
- ✅ Address technical debt
- ✅ Refactor code for better maintainability

### How Coding Agent Works:

**1. Assignment & Activation:**
- Assign a GitHub issue to `@copilot` like any team member
- Copilot adds a 👀 emoji reaction to show it's working
- Spins up a secure GitHub Actions environment

**2. Autonomous Development:**
- Analyzes the codebase using advanced RAG (Retrieval Augmented Generation)
- Plans implementation approach
- Creates a new branch (always prefixed with `copilot/`)
- Writes and commits code incrementally

**3. Quality Assurance:**
- Runs existing tests and linters
- Creates new tests when appropriate
- Validates changes against repository standards
- Documents reasoning in commit messages

**4. Pull Request & Review:**
- Opens a draft pull request with detailed description
- Provides session logs showing decision-making process
- Requests review from the original issue assignor
- Responds to feedback and iterates based on comments

### Coding Agent vs. IDE Agent Mode:

| Feature | IDE Agent Mode | Coding Agent |
|---------|----------------|--------------|
| Location | VS Code | GitHub.com |
| Interaction | Interactive, conversational | Autonomous, delegated |
| Scope | Current files/workspace | Entire repository |
| Workflow | Real-time collaboration | Asynchronous task completion |
| Output | Direct code changes | Pull request with review |
| Best For | Exploratory development | Well-defined tasks |

## 📝 Step 1: Create and Assign an Issue to Copilot

Let's create a task for Copilot to work on autonomously.

### Instructions:

1. **Navigate to Issues:**
   - Go to the **Issues** tab in your GitHub repository
   - Click **"New Issue"** button

2. **Create a well-defined issue:**

   **Title**: `Add photographer profile page`

   **Description**:
   ```markdown
   ## User Story
   As a photographer using PixelPerfect Gallery, I want a dedicated profile page where I can display my bio, profile picture, and showcase my best work.

   ## Requirements
   - Create a new route at `/profile` in the Next.js app
   - Design a profile page with:
     - Profile picture display area
     - Bio/description section
     - Featured photos grid (using existing GalleryGrid component)
     - Contact information section
   - Use TypeScript for type safety
   - Style with Tailwind CSS, following existing design patterns
   - Ensure responsive design (mobile-first)
   - Include dark mode support

   ## Acceptance Criteria
   - [ ] Profile page is accessible at `/profile`
   - [ ] Page displays all required sections
   - [ ] Responsive on mobile, tablet, and desktop
   - [ ] Follows existing component patterns
   - [ ] No TypeScript errors
   - [ ] Consistent with existing design system
   ```

3. **Submit the issue** by clicking "Submit new issue"

4. **Assign to Copilot:**
   - In the issue sidebar, under **"Assignees"**, click **"Assign to Copilot"**
   - In the popup:
     - Verify the target repository is correct
     - Ensure the base branch is `main` (or your default branch)
     - Click **"Assign"**

5. **Observe the reaction:**
   - Copilot will add a 👀 emoji to indicate it's started working
   - A comment will appear showing Copilot is planning its approach

### 💡 Tips for Writing Good Issues for Coding Agent:

**DO:**
- ✅ Be specific about requirements and acceptance criteria
- ✅ Include examples or mockups when helpful
- ✅ Reference existing components or patterns to follow
- ✅ Specify technologies and frameworks to use
- ✅ Break large features into smaller, focused issues

**DON'T:**
- ❌ Make issues too vague ("make the app better")
- ❌ Combine multiple unrelated changes in one issue
- ❌ Create overly complex tasks that require architectural decisions
- ❌ Forget to specify important constraints or requirements

## 👀 Step 2: Monitor Copilot's Progress

Now let's watch as Copilot works autonomously on your issue.

### Instructions:

1. **Wait for Copilot to start:**
   - Look for the 👀 emoji reaction on the issue
   - Copilot will comment with its initial plan

2. **Find the Pull Request:**
   - In the issue sidebar, look for the **"Development"** section
   - Click the PR link (or wait a few moments and refresh if not yet available)
   - Alternatively, navigate to the **Pull Requests** tab

3. **Examine the Draft PR:**
   - Notice the PR is marked as **Draft** (work in progress)
   - Review the PR description - Copilot outlines its approach
   - The description includes a checklist of tasks

4. **View the Session Logs:**
   - In the PR timeline, click **"View Session"**
   - Explore Copilot's decision-making process:
     - Files it analyzed
     - Plans it created
     - Code it generated
     - Tests it ran
     - Any challenges it encountered

5. **Watch Progress:**
   - Return to the PR periodically to see updates
   - Copilot will check off tasks as it completes them
   - View commits to see incremental changes

6. **Wait for Completion:**
   - When Copilot finishes, the PR will show "Ready for review"
   - Copilot will request your review

**Note**: Depending on complexity, this may take 5-15 minutes. In a real workflow, you'd work on other tasks while Copilot handles this autonomously!

## 🔍 Step 3: Review Copilot's Work

Once Copilot completes the task, it's time to review the implementation.

### Instructions:

1. **Review the PR Description:**
   - Read Copilot's summary of what was implemented
   - Check that all acceptance criteria are addressed
   - Review the approach Copilot took

2. **Examine the Code Changes:**
   - Click **"Files changed"** tab
   - Review each file modification:
     - Is the code quality high?
     - Does it follow project conventions?
     - Are TypeScript types properly defined?
     - Is the styling consistent?

3. **Check the Session Details:**
   - Review the **"View Session"** logs again
   - Understand why Copilot made specific decisions
   - See what context and files it used

4. **Test the Implementation (if possible):**
   - Check out the branch locally if you want to test
   - Verify the feature works as expected
   - Test edge cases

5. **Leave Review Comments:**
   - If you find issues, leave comments on specific lines
   - Ask for improvements or clarifications
   - Suggest alternative approaches

6. **Approve or Request Changes:**
   - If satisfied, **approve** the PR
   - If changes needed, **request changes** with specific feedback
   - Copilot can iterate based on your feedback!

## 🔄 Step 4: Iterate with Copilot (Optional)

If you requested changes, Copilot can address your feedback autonomously.

### Instructions:

1. **Leave specific feedback** on the PR:
   ```markdown
   @copilot Please add error handling for when the profile data is not available.
   ```

   ```markdown
   @copilot Can you add loading states to the profile page?
   ```

2. **Copilot will respond:**
   - Address your comments
   - Make additional commits
   - Update the PR

3. **Review the iterations:**
   - Check that your feedback was addressed
   - Review the new changes

4. **Merge when satisfied:**
   - Click **"Ready for review"** if still in draft
   - Approve the PR
   - Merge using your preferred strategy

## 🎁 Optional: Become a Tech Lead - Delegate Multiple Tasks

While Copilot works on your first issue, experience what it's like to delegate tasks to your AI team member!

### Additional Task Ideas:

Create and assign additional issues to Copilot:

**1. Enhanced Filtering:**
```markdown
Title: Add advanced photo filters with multiple categories
- Add dropdown filters for date, category, and photographer
- Allow multiple simultaneous filters
- Show active filter badges
- Include "Clear all" button
```

**2. Search Functionality:**
```markdown
Title: Implement photo search feature
- Add search bar to gallery page
- Search by photo title, tags, and photographer name
- Display search results in real-time
- Show "no results" state when appropriate
```

**3. Admin Analytics:**
```markdown
Title: Add photo upload analytics to admin dashboard
- Display upload trends over time
- Show most popular photo categories
- Include total storage usage
- Add charts using a charting library
```

**4. Documentation:**
```markdown
Title: Document the component architecture
- Create architecture diagram
- Document each major component
- Add usage examples for UI components
- Include contribution guidelines
```

### Pro Tips for Effective Delegation:

- **Start small**: Begin with well-defined, focused tasks
- **Be specific**: Clear requirements = better results
- **Set acceptance criteria**: Make success measurable
- **Use labels**: Tag issues by type (bug, feature, docs, etc.)
- **Monitor progress**: Check in on session logs periodically
- **Iterate**: Provide feedback to improve results

## 🌐 Step 5: Alternative Ways to Work with Coding Agent

There are multiple ways to interact with Coding Agent beyond the GitHub Issues UI.

### Method 1: Agent Panel

The Agent Panel provides a dedicated interface for managing Copilot tasks:

1. Navigate to [https://github.com/copilot/agents](https://github.com/copilot/agents)
2. Select your repository from the dropdown
3. Describe a task in the text box
4. Click **"Start Task"** to create a PR without a formal issue

**Documentation**: [Agent Panel Guide](https://docs.github.com/copilot/how-tos/use-copilot-agents/coding-agent/create-a-pr#asking-copilot-to-create-a-pull-request-from-the-agents-panel-or-page)

### Method 2: Visual Studio Code

Delegate tasks directly from your IDE while coding:

1. Install the [GitHub Pull Request extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
2. In Copilot Chat, describe a task
3. Include `#copilotCodingAgent` in your prompt
4. Click **"Continue"** to start the autonomous task

**Documentation**: [VS Code Integration](https://docs.github.com/copilot/how-tos/use-copilot-agents/coding-agent/create-a-pr#asking-copilot-to-create-a-pull-request-from-copilot-chat-in-visual-studio-code)

### Method 3: GitHub CLI

Assign tasks from the command line:

```bash
gh agent-task create --title "Your task title" --body "Task description"
```

**Documentation**: [GitHub CLI Guide](https://docs.github.com/copilot/how-tos/use-copilot-agents/coding-agent/create-a-pr#asking-copilot-to-create-a-pull-request-from-the-github-cli)

## ⚠️ Best Practices and Limitations

### What Coding Agent Does Well:

- ✅ Incremental feature additions to existing patterns
- ✅ Bug fixes with clear reproduction steps
- ✅ Test coverage improvements
- ✅ Documentation updates
- ✅ Refactoring following established patterns
- ✅ Accessibility improvements
- ✅ Performance optimizations with specific goals

### What to Avoid:

- ❌ Major architectural changes
- ❌ Security-critical implementations without review
- ❌ Complex multi-system integrations
- ❌ Tasks requiring external system access
- ❌ Ambiguous or poorly-defined requirements
- ❌ Tasks that need human judgment or business decisions

### Security Considerations:

- **Always review** Copilot's code before merging
- **Don't blindly trust** security-related changes
- **Verify** any external dependencies added
- **Test thoroughly** before deploying to production
- **Use branch protection** rules to require human review

## 🏆 Exercise Wrap-up

Excellent work! You've experienced autonomous AI development with GitHub Copilot Coding Agent:
- ✅ Created and assigned issues to Copilot
- ✅ Monitored autonomous development through session logs
- ✅ Reviewed AI-generated pull requests
- ✅ Understood the workflow and best practices
- ✅ Learned when to use Coding Agent effectively

### Reflection Questions:
1. **How does delegating to Coding Agent differ from interactive IDE development?**
2. **What types of tasks are best suited for autonomous Coding Agent?**
3. **How would you integrate Coding Agent into your team's workflow?**
4. **What surprised you about Copilot's autonomous capabilities?**
5. **How might Coding Agent change your approach to issue management?**

### Key Takeaways:
- Coding Agent works autonomously on well-defined GitHub issues
- It follows standard pull request workflows for review and iteration
- Session logs provide transparency into AI decision-making
- Best results come from clear, specific requirements
- Human review remains essential for quality and security
- Coding Agent multiplies development capacity for routine tasks

### Real-World Applications:

**Development Teams:**
- Delegate routine bug fixes and feature additions
- Keep Copilot working on lower-priority tasks
- Free senior developers for architectural work
- Maintain velocity during code freezes or holidays

**Solo Developers:**
- Parallel development on multiple features
- Automated test coverage improvements
- Documentation kept up-to-date
- Technical debt addressed systematically

**Open Source Projects:**
- Good first issues implemented by Copilot
- Documentation improvements
- Test coverage for contributors
- Consistent code style enforcement

## 🎉 Congratulations!

You've completed all the GitHub Copilot labs! You now have hands-on experience with:

- Setting up and exploring codebases with Copilot
- Code generation and editing with multiple modes
- Engineering best practices and team collaboration
- Advanced customization with models, prompts, and chat modes
- Copilot Spaces for focused, collaborative development
- Autonomous development with Coding Agent

Continue exploring GitHub Copilot's capabilities, share your learnings with your team, and keep building amazing things with AI assistance!

For more information, check out the [official GitHub Copilot documentation](https://docs.github.com/copilot).

#### You have successfully completed all labs! 🎊

![Completion celebration](../../media/next-page.png)
