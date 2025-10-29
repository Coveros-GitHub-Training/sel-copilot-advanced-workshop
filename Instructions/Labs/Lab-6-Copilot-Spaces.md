# Exercise 6 - GitHub Copilot Spaces

#### Duration: 25 minutes

## 🎯 Learning Objectives

By the end of this exercise, you will:
- Understand what GitHub Copilot Spaces are and their benefits
- Know how to create and configure a new Copilot Space
- Be able to set up a Space with specific goals, instructions, and context
- Complete development tasks using collaborative AI assistance in Spaces
- Share and manage Spaces with team members

## 📸 Scenario: Collaborative Development at PixelPerfect Gallery

Your team at PixelPerfect Gallery is working on multiple simultaneous initiatives:
- A security audit to ensure the photo upload system is hardened against vulnerabilities
- New documentation for the API and component architecture
- Performance optimization for large photo galleries
- Accessibility improvements across the application

These are complex, multi-faceted projects that benefit from focused, dedicated AI assistance with specific context and goals. Your manager has asked you to explore GitHub Copilot Spaces as a way to organize these initiatives and collaborate more effectively with AI assistance.

## 🌟 Introduction to GitHub Copilot Spaces

**GitHub Copilot Spaces** are dedicated, persistent AI workspaces where you can:
- Define specific goals and instructions for a project or initiative
- Add relevant context files, issues, and documentation
- Have focused conversations with Copilot about a particular topic
- Collaborate with team members in a shared AI context
- Track progress on complex, multi-step tasks

### Benefits of Copilot Spaces:

- **Focused Context**: Each Space maintains its own context and conversation history
- **Persistent Memory**: Spaces remember your goals, instructions, and progress
- **Team Collaboration**: Share Spaces with teammates for coordinated AI assistance
- **Organized Workflows**: Separate concerns into different Spaces (security, features, docs, etc.)
- **Specialized Instructions**: Tailor Copilot's behavior for specific project needs

### Spaces vs. Regular Copilot Chat:

| Feature | Regular Chat | Copilot Spaces |
|---------|--------------|----------------|
| Context | Current workspace only | Custom files, repos, issues, docs |
| Persistence | Session-based | Persistent across sessions |
| Instructions | General + repo instructions | Custom instructions per Space |
| Collaboration | Individual conversations | Shared team Spaces |
| Organization | Single chat thread | Multiple focused Spaces |

## 🎯 Step 1: Create Your First Copilot Space

Let's create a dedicated Space for working on security improvements for the PixelPerfect Gallery.

### Instructions:

1. **Navigate to Copilot Spaces:**
   - Go to [https://github.com/copilot/spaces](https://github.com/copilot/spaces)
   - Sign in to your GitHub account if needed

2. **Create a new Space:**
   - Click **"Create Space"** button

3. **Configure basic Space settings:**

   **Choose an option below based on your interest:**

### Option A: Security Analysis & Hardening

**Purpose**: Analyze and improve the security posture of the photo gallery application.

1. **Space name**: `Photo Gallery - Security Assessment`
2. **Owner**: Select your username or organization
3. **Description**: `Implement security best practices for the photo gallery application`
4. **Click "Save"**

**Add Instructions:**

5. Click **"Instructions"**
6. Add the following instructions:

```markdown
You are a security expert helping to analyze and improve the security posture of a Next.js 15 photo gallery application. Focus on:

- File upload security vulnerabilities and mitigations
- Input validation and sanitization
- Authentication and authorization patterns
- XSS prevention in user-generated content
- Secure image processing and storage
- OWASP Top 10 web application security risks
- Next.js specific security best practices

Provide specific code examples and security recommendations that follow industry standards and OWASP guidelines. Consider both client-side and server-side security measures.
```

7. Click **"Save"**

**Add Source Files:**

8. Click **"Add sources"** → **"Add files and repositories"**
9. Add the following files:
   ```
   src/components/upload/UploadZone.tsx
   src/lib/mock-photo-data.ts
   src/app/layout.tsx
   next.config.ts
   ```
10. Click **"Save"**

**Add Issue Context:**

11. Click **"Add sources"** → **"Link files, pull requests, and issues"**
12. Add a relevant issue URL if available, or skip this step
13. Click **"Save"**

**Add Security Documentation:**

14. Click **"Add sources"** → **"Add text content"**
15. Add the following security reference:

```markdown
## OWASP Top 10 2021 - Key Security Risks for Web Applications

1. **A01 Broken Access Control** - Users can act outside of their intended permissions
2. **A02 Cryptographic Failures** - Failures related to cryptography leading to sensitive data exposure
3. **A03 Injection** - User-supplied data is not validated, filtered, or sanitized
4. **A04 Insecure Design** - Risks related to design and architectural flaws
5. **A05 Security Misconfiguration** - Missing appropriate security hardening
6. **A06 Vulnerable and Outdated Components** - Using components with known vulnerabilities
7. **A07 Identification and Authentication Failures** - Authentication and session management issues
8. **A08 Software and Data Integrity Failures** - Code and infrastructure integrity violations
9. **A09 Security Logging and Monitoring Failures** - Insufficient logging and monitoring
10. **A10 Server-Side Request Forgery** - SSRF flaws in fetching remote resources

## Next.js Security Headers
- Content Security Policy (CSP)
- X-Frame-Options
- X-Content-Type-Options
- Referrer-Policy
- Permissions-Policy

## File Upload Security Considerations
- File type validation
- File size limits
- Malware scanning
- Secure file storage
- Image processing vulnerabilities
```

16. Click **"Save"**

### Option B: Documentation Generation & API Design

**Purpose**: Create comprehensive documentation and API design for the gallery application.

1. **Space name**: `Photo Gallery - Documentation Hub`
2. **Owner**: Select your username or organization
3. **Description**: `Create comprehensive documentation and API design documentation for the photo gallery application`
4. **Click "Save"**

**Add Instructions:**

5. Click **"Instructions"**
6. Add the following instructions:

```markdown
You are a technical documentation expert and API designer helping to create comprehensive documentation for a Next.js 15 photo gallery application. Focus on:

- Clear, beginner-friendly component documentation
- API design and endpoint specifications
- Architecture decision records (ADRs)
- Code examples and usage patterns
- JSDoc comments for functions and components
- README and getting started guides
- Accessibility documentation
- Performance considerations

Provide well-structured, maintainable documentation that follows industry best practices. Use clear examples and diagrams where appropriate.
```

7. Click **"Save"**

**Add Source Files:**

8. Click **"Add sources"** → **"Add files and repositories"**
9. Add the following files:
   ```
   src/components/ui/layout/SectionContainer.tsx
   src/components/gallery/GalleryGrid.tsx
   src/app/page.tsx
   COMPONENT_USAGE_GUIDE.md
   ```
10. Click **"Save"**

**Add Documentation Templates:**

11. Click **"Add sources"** → **"Add text content"**
12. Add the following documentation template:

```markdown
## Component Documentation Template

### ComponentName

**Purpose**: [One sentence describing what this component does]

**Location**: `src/components/[path]/ComponentName.tsx`

#### Props

| Prop | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| propName | type | Yes/No | value | Description |

#### Usage Example

\`\`\`tsx
<ComponentName prop="value" />
\`\`\`

#### Accessibility

- [ARIA attributes used]
- [Keyboard navigation]
- [Screen reader considerations]

#### Styling

- Uses Tailwind CSS
- Supports dark mode via `dark:` classes
- Responsive breakpoints: mobile-first

#### Related Components

- [Component 1]
- [Component 2]
```

13. Click **"Save"**

### Option C: Performance Optimization

**Purpose**: Optimize the photo gallery for better performance with large image collections.

1. **Space name**: `Photo Gallery - Performance Optimization`
2. **Owner**: Select your username or organization
3. **Description**: `Optimize photo gallery performance for large image collections and improve user experience`
4. **Click "Save"**

**Add Instructions:**

5. Click **"Instructions"**
6. Add optimization-focused instructions and context
7. Add relevant source files related to gallery rendering and image loading

## 💬 Step 2: Work Within Your Copilot Space

Now that your Space is configured, let's use it to accomplish some goals.

### Instructions:

1. **Open your Space** from the Copilot Spaces dashboard

2. **Start a conversation** with Copilot about your Space's focus area

**For Security Space:**

<details>
  <summary>Sample Security Prompts</summary>

  ```
  Analyze the UploadZone component for potential security vulnerabilities. What risks should we address?
  ```

  ```
  How can we implement file type validation and size restrictions for uploaded images?
  ```

  ```
  Review the mock data handling - are there any XSS vulnerabilities we should prevent?
  ```

  ```
  What security headers should we configure in next.config.ts for this application?
  ```

  ```
  Create a security checklist for the photo upload feature based on OWASP Top 10.
  ```

</details>

**For Documentation Space:**

<details>
  <summary>Sample Documentation Prompts</summary>

  ```
  Generate comprehensive JSDoc comments for the GalleryGrid component.
  ```

  ```
  Create an API specification document for the photo data structure used in this application.
  ```

  ```
  Write a component usage guide for the SectionContainer layout component.
  ```

  ```
  Generate an architecture decision record (ADR) for using Next.js App Router in this project.
  ```

  ```
  Create a getting started guide for new developers joining the photo gallery project.
  ```

</details>

**For Performance Space:**

<details>
  <summary>Sample Performance Prompts</summary>

  ```
  Analyze the GalleryGrid component for performance bottlenecks with large photo collections.
  ```

  ```
  How can we implement lazy loading and infinite scroll for the photo gallery?
  ```

  ```
  What image optimization strategies should we use for faster loading?
  ```

  ```
  Suggest React optimization techniques (memoization, useMemo, etc.) for the gallery components.
  ```

</details>

3. **Review the responses** - notice how Copilot uses the context and instructions from your Space

4. **Have a multi-turn conversation** - ask follow-up questions, request code examples, iterate on solutions

5. **Implement suggestions** - copy code examples to your IDE and test them

## 🤝 Step 3: Collaborate in Spaces

Spaces become even more powerful when used for team collaboration.

### Sharing Your Space:

1. **In your Space**, look for sharing options (typically a "Share" button or in Space settings)

2. **Invite team members:**
   - Add collaborators by GitHub username or email
   - Set appropriate permissions (view, edit, admin)

3. **Share the Space link** with your team

### Collaborative Use Cases:

- **Code Reviews**: Create a Space for reviewing a specific feature or PR
- **Bug Investigation**: Dedicated Space for diagnosing and fixing a complex bug
- **Architecture Planning**: Space for designing new features or refactoring
- **Onboarding**: Space with curated context for new team members
- **Knowledge Sharing**: Document solutions and share the Space

## 📝 Step 4: Manage and Organize Your Spaces

As you create more Spaces, organization becomes important.

### Best Practices:

1. **Use clear, descriptive names:**
   - ✅ "Photo Upload - Security Hardening"
   - ❌ "Project A"

2. **Add comprehensive descriptions:**
   - Explain the Space's purpose
   - Include goals or success criteria
   - Note any specific constraints

3. **Keep instructions focused:**
   - Each Space should have a clear, specific purpose
   - Don't try to cover everything in one Space
   - Instructions should guide Copilot toward your specific needs

4. **Curate sources carefully:**
   - Add only relevant files and documentation
   - Too much context can dilute focus
   - Update sources as the project evolves

5. **Archive completed Spaces:**
   - Keep your active list manageable
   - Archived Spaces remain accessible for reference

## 🔍 Step 5: Advanced Space Features

### Setting Goals:

Many Spaces allow you to define specific goals or objectives:

1. **Open Space settings**
2. **Add goals or objectives** (if available)
3. **Track progress** toward those goals

### Using Spaces for Different Workflows:

**Feature Development:**
- Create a Space for each major feature
- Include design docs, related issues, and affected files
- Track implementation progress

**Bug Fixes:**
- Dedicated Space for complex bugs
- Add error logs, affected code, and investigation notes
- Document the solution for future reference

**Learning & Exploration:**
- Create Spaces for learning new technologies
- Add tutorials, documentation, and practice code
- Build a personal knowledge base

**Code Migration:**
- Space for migrating to new frameworks or libraries
- Include migration guides and both old and new code examples
- Track which files have been migrated

## 🏆 Exercise Wrap-up

Excellent work! You've learned how to use GitHub Copilot Spaces:
- ✅ Created a dedicated Copilot Space with custom instructions
- ✅ Added relevant context files and documentation to a Space
- ✅ Used Spaces for focused, goal-oriented AI assistance
- ✅ Understood collaboration features and best practices
- ✅ Learned to organize and manage multiple Spaces

### Reflection Questions:
1. **How do Spaces differ from regular Copilot Chat in your workflow?**
2. **What types of projects or tasks would benefit most from dedicated Spaces?**
3. **How might your team use Spaces for collaboration?**
4. **What instructions and context were most effective in your Space?**
5. **How would you organize Spaces for your current projects?**

### Key Takeaways:
- Spaces provide persistent, focused AI assistance for complex projects
- Custom instructions and curated context improve AI responses
- Spaces enable better team collaboration and knowledge sharing
- Different Spaces can serve different purposes (security, docs, features, etc.)
- Spaces are particularly valuable for long-running, complex initiatives

### When to Use Spaces vs. Regular Chat:

**Use Regular Chat for:**
- Quick questions
- One-off code generation
- General exploration
- Simple refactoring

**Use Copilot Spaces for:**
- Long-running projects
- Focused initiatives (security, performance, etc.)
- Team collaboration
- Complex, multi-step tasks
- Building specialized knowledge bases

## 🚀 Next Steps

In Exercise 7, we'll explore GitHub Copilot's Coding Agent feature, which allows you to assign entire issues or tasks to Copilot for automated implementation!

#### You have successfully completed the lab. Click on **Next >>** to continue to the next lab.

![Next page navigation](../../media/next-page.png)
