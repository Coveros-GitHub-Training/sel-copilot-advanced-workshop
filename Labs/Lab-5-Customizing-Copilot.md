# Exercise 5 - Customizing GitHub Copilot

#### Duration: 45 minutes

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

Understanding your usage helps you make informed decisions about which AI models to use and when. This exercise will show you how to quickly check your usage and understand the basics.

### Quick Check Your Usage

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

### Key Things to Know

- **0x Models**: Unlimited usage within your Copilot subscription
- **Premium Models**: Count against your monthly request allowance
  - Copilot Business: 300 requests per user per month
  - Copilot Enterprise: 1,000 requests per user per month
- **Best Practice**: Use premium models for complex, high-value tasks; use 0x models for routine work

> 📚 **For Detailed Information**: See the [Premium Request Usage Guide](../Reference/Premium-Request-Usage.md) for comprehensive information about:
> - Advanced monitoring strategies
> - Cost optimization techniques
> - Model selection by task type
> - Team usage policies and best practices
> - Monthly budget planning strategies

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

### 🎯 Advanced Model Selection Decision Matrix

Use this comprehensive guide to choose the right model for your task:

#### **Task Type**: Code Generation
| Complexity | Best Choice | Why |
|------------|-------------|-----|
| Simple components | 0x models | Fast, sufficient for patterns |
| Complex logic | Premium reasoning models | Better architecture decisions |
| Performance-critical | Premium analysis models | Deeper optimization insights |

#### **Task Type**: Debugging & Problem Solving
| Scenario | Best Choice | Reasoning |
|----------|-------------|-----------|
| Syntax errors | 0x models | Quick fixes |
| Logic bugs | Premium models | Deep analysis needed |
| Performance issues | Premium with strong reasoning | Complex root cause analysis |
| Security vulnerabilities | Premium with security focus | Critical accuracy required |

#### **Task Type**: Documentation
| Content | Best Choice | Reason |
|---------|-------------|--------|
| Code comments | 0x models | Straightforward explanations |
| API documentation | Premium models | Comprehensive, detailed |
| Architecture docs | Premium reasoning models | Deep understanding needed |
| Tutorial content | Premium communication models | Clear, detailed explanations |

### 🔬 Model Experimentation Framework

When evaluating models for your specific use case:

**Step 1: Define Success Criteria**
```markdown
For this task, the ideal response should:
- [ ] Accuracy: Solves the problem correctly
- [ ] Clarity: Easy to understand
- [ ] Completeness: Addresses all requirements
- [ ] Efficiency: Optimal solution
- [ ] Style: Matches project conventions
```

**Step 2: Test Consistently**
Use the same:
- Input prompt
- Context files
- Code selection
- Task description

**Step 3: Document Results**
Create a comparison table:
```markdown
| Model | Speed | Quality | Explanation | Code Style | Score |
|-------|-------|---------|-------------|------------|-------|
| Model A | Fast | 8/10 | Detailed | Good | 9/10 |
| Model B | Medium | 9/10 | Excellent | Perfect | 10/10 |
| Model C | Slow | 7/10 | Adequate | Fair | 7/10 |
```

**Step 4: Build Model Preferences**
Document your findings:
```markdown
For PixelPerfect Gallery project:
- TypeScript refactoring: Model B (best type inference)
- React components: Model A (fastest, good enough)
- Performance optimization: Model C (best algorithms)
- Documentation: Model B (clearest explanations)
```

### 🎨 Practical Model Switching Scenarios

**Scenario 1: Feature Development Sprint**
```markdown
Monday (Planning):
- Use premium reasoning model for architecture planning
- Get comprehensive implementation strategy

Tuesday-Thursday (Implementation):
- Use 0x model for routine code completions
- Switch to premium for complex business logic

Friday (Review & Polish):
- Use premium for code review insights
- Use 0x for formatting and simple fixes
```

**Scenario 2: Bug Investigation**
```markdown
Step 1 (Understanding):
- Premium model: Analyze error logs and stack traces
- Build comprehensive understanding

Step 2 (Fixing):
- 0x model: Simple syntax fixes
- Premium model: Complex logic corrections

Step 3 (Testing):
- Premium model: Generate comprehensive test cases
- Ensure bug doesn't reoccur
```

**Scenario 3: Documentation Day**
```markdown
API Documentation:
- Premium model with strong communication
- Detailed, accurate descriptions needed

Code Comments:
- 0x model sufficient
- Quick inline explanations

Tutorial Content:
- Premium model
- Step-by-step, beginner-friendly needed
```

## 📝 Step 3: Use Prompt Files for Consistent Generation

Prompt files allow you to create reusable, standardized prompts that maintain consistency across your team and save time on repetitive tasks.

### Why Prompt Files Matter:
- **Consistency**: Same prompt structure every time
- **Efficiency**: No need to retype complex prompts
- **Standardization**: Team uses the same approaches
- **Parameterization**: Customize with input variables
- **Documentation**: Self-documenting common workflows
- **Knowledge sharing**: Capture expert prompting techniques
- **Onboarding**: New team members use proven patterns
- **Quality control**: Enforce best practices automatically

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

## 🎭 Step 5: Understanding Custom Chat Modes

Chat modes define how GitHub Copilot behaves for specialized workflows. Let's create a custom mode for planning new features.

### Why Custom Chat Modes:
- **Specialized workflows**: Tailor AI behavior to specific tasks
- **Tool selection**: Pre-configure which tools to use
- **Model preference**: Specify best model for the task
- **Consistent approach**: Same methodology every time
- **Role specialization**: Create expert personas for different tasks
- **Context optimization**: Pre-load relevant information
- **Output formatting**: Standardize responses
- **Workflow automation**: Multi-step processes in one mode

### 🎯 Understanding Chat Mode Architecture

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

## 💬 Step 6: Create Your Own Custom Chat Mode

Custom chat modes allow you to create specialized AI assistants for specific workflows. Let's create a simple planning mode for the PixelPerfect Gallery project.

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

## 📋 Step 7: Understanding Custom Instructions Files

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

### 🎯 Mastering Custom Instructions

#### **The Power of Context**

Custom instructions give Copilot deep context about your project, dramatically improving:
- Code quality and consistency
- Adherence to team standards
- Understanding of domain concepts
- Appropriate technology choices
- Alignment with architecture

#### **Instructions Hierarchy Strategy**

**Personal Instructions** - Your Individual Style
```markdown
Use for:
- Language preferences (e.g., "Prefer TypeScript over JavaScript")
- Coding style (e.g., "Use functional components only")
- Comment style (e.g., "JSDoc for all public functions")
- Testing preferences (e.g., "Always suggest tests with code")
- Accessibility focus (e.g., "Always include ARIA labels")

Example Personal Instructions:
---
# My Coding Preferences

## Language & Style
- Use TypeScript with strict mode
- Prefer functional programming patterns
- Use arrow functions for consistency
- Destructure props in components

## Testing
- Suggest tests with every function
- Use Jest + Testing Library
- Aim for 80% coverage minimum

## Documentation
- JSDoc for all exported functions
- Inline comments for complex logic
- README updates for new features

## Accessibility
- ARIA labels on interactive elements
- Keyboard navigation support
- Screen reader friendly
```

**Repository Instructions** - Project Standards
```markdown
Use for:
- Tech stack specifics
- Project architecture
- Component patterns
- File structure
- Domain concepts
- API conventions

Example Repository Instructions:
---
# PixelPerfect Gallery Project

## Architecture
Next.js 15 App Router with TypeScript and Tailwind CSS

## Component Patterns
- Use SectionContainer for page sections
- Use SectionTitle for headers
- Follow layout/ui/feature structure

## Domain Concepts
- Photo: Main entity with metadata
- Gallery: Collection of photos
- Photographer: User who uploads photos
- Album: User-created photo collection

## Styling Rules
- Use Tailwind CSS only
- Include dark mode variants
- Mobile-first responsive
- Follow existing color scheme

## Code Practices
- Strict TypeScript types
- Props interfaces required
- Export types with components
- Use existing utility functions
```

**Organization Instructions** - Company Standards
```markdown
Use for:
- Security requirements
- Compliance needs
- Company coding standards
- Approved libraries
- Deployment practices
- Documentation standards

Example Organization Instructions:
---
# Acme Corp Development Standards

## Security
- Never commit secrets
- Always sanitize user input
- Use parameterized queries
- Implement rate limiting
- Require authentication for sensitive endpoints

## Compliance
- GDPR: Include data deletion
- CCPA: Support data export
- SOC2: Log all data access

## Approved Technologies
- React 18+ for frontend
- Node.js 20+ for backend
- PostgreSQL for primary database
- Redis for caching
- AWS for infrastructure

## Code Quality
- Minimum 80% test coverage
- No security vulnerabilities allowed
- Pass all linting rules
- Code review required for all PRs
```

### 📝 Writing Effective Custom Instructions

#### **Structure Template**

```markdown
# [Project Name] Instructions

## Project Overview
Brief description of what the project does and its purpose.

## Technology Stack
List all major technologies:
- Framework: Next.js 15
- Language: TypeScript 5.3
- Styling: Tailwind CSS
- State: React hooks
- Testing: Jest + RTL

## Architecture
Explain the high-level structure:
- File organization
- Component hierarchy
- Data flow patterns
- API structure

## Coding Standards

### TypeScript
- Use strict mode
- Define interfaces for all data structures
- Prefer type inference where clear
- Avoid 'any' type

### React
- Functional components only
- Hooks for state management
- Props destructuring
- Memo for expensive renders

### Styling
- Tailwind classes only
- Dark mode support required
- Mobile-first approach
- Use existing color tokens

## Domain Concepts
Define key terms and concepts specific to your domain.

## Common Patterns
Show examples of how to do common tasks in your project.

## What to Avoid
List anti-patterns and things not to do.

## References
Link to important documentation files.
```

#### **Advanced Instruction Techniques**

**Technique 1: Example-Driven Instructions**
```markdown
## Component Creation Pattern

✅ DO THIS:
```tsx
interface PhotoCardProps {
  photo: Photo
  onSelect?: (id: string) => void
}

export function PhotoCard({ photo, onSelect }: PhotoCardProps) {
  return (
    <div className="rounded-lg bg-white dark:bg-slate-800">
      {/* implementation */}
    </div>
  )
}
```

❌ NOT THIS:
```tsx
export default function PhotoCard(props: any) {
  return <div>{/* implementation */}</div>
}
```
```

**Technique 2: Decision Trees**
```markdown
## Choosing the Right Component

When creating a new UI element, decide:

1. Is it layout-related?
   → Place in src/components/ui/layout/
   → Use SectionContainer, Hero patterns

2. Is it gallery-specific?
   → Place in src/components/gallery/
   → May use Photo interface

3. Is it upload-specific?
   → Place in src/components/upload/
   → Handle File types

4. Is it generic UI?
   → Place in src/components/ui/
   → Make it reusable
```

**Technique 3: Context References**
```markdown
## File References

When working on features, always reference:

- Architecture: @ARCHITECTURE.md
- Component patterns: @COMPONENT_USAGE_GUIDE.md
- Existing similar code: @src/components/gallery/GalleryGrid.tsx
- Type definitions: @src/lib/mock-photo-data.ts
- Styling examples: @src/app/page.tsx

This ensures consistency with existing code.
```

**Technique 4: Quality Gates**
```markdown
## Before Suggesting Code

Verify the suggestion:
- [ ] Follows TypeScript strict mode
- [ ] Includes proper types/interfaces
- [ ] Has dark mode support
- [ ] Is responsive (mobile-first)
- [ ] Includes error handling
- [ ] Follows existing patterns
- [ ] Has accessibility attributes
- [ ] Includes helpful comments

If any item is missing, add it to the suggestion.
```

### 🔬 Instructions for Different Scenarios

#### **For New Projects**
```markdown
Focus on:
- Tech stack choices
- Architecture decisions
- Initial patterns
- Basic standards

Keep flexible:
- Allow exploration
- Don't over-constrain
- Refine as you go
```

#### **For Established Projects**
```markdown
Focus on:
- Existing patterns
- Consistency
- Migration paths
- Technical debt

Be specific:
- Reference actual files
- Show exact patterns
- List anti-patterns
- Define terms
```

#### **For Team Projects**
```markdown
Focus on:
- Collaboration patterns
- Code review standards
- Documentation needs
- Onboarding support

Include:
- Team conventions
- Communication style
- Review checklists
- Common questions
```

### 🎓 Advanced MCP Server Integration

#### **What are MCP Servers?**

Model Context Protocol (MCP) servers extend Copilot's capabilities to external systems:
- Database access
- API integrations
- Cloud services
- Internal tools
- Documentation systems
- Analytics platforms

#### **MCP Configuration Deep Dive**

**Basic Configuration** (`.vscode/mcp.json`):
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@github/mcp-server"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

**Advanced Configuration**:
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@github/mcp-server"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}",
        "GITHUB_REPO": "owner/repo"
      },
      "timeout": 30000,
      "retries": 3
    },
    "database": {
      "command": "node",
      "args": ["./mcp-servers/database-server.js"],
      "env": {
        "DB_HOST": "${DB_HOST}",
        "DB_PORT": "${DB_PORT}",
        "DB_NAME": "${DB_NAME}"
      }
    },
    "docs": {
      "command": "python",
      "args": ["./mcp-servers/docs_server.py"],
      "cwd": "${workspaceFolder}/mcp-servers"
    }
  }
}
```

#### **Building Custom MCP Servers**

**Use Case 1: Internal Documentation Server**
```javascript
// mcp-servers/docs-server.js
const { Server } = require('@modelcontextprotocol/sdk/server');
const { StdioServerTransport } = require('@modelcontextprotocol/sdk/server/stdio');

const server = new Server({
  name: 'internal-docs',
  version: '1.0.0'
}, {
  capabilities: {
    tools: {}
  }
});

// Register tool: search internal docs
server.setRequestHandler('tools/call', async (request) => {
  if (request.params.name === 'search_docs') {
    const query = request.params.arguments.query;
    // Search your internal documentation
    const results = await searchInternalDocs(query);
    return { content: [{ type: 'text', text: results }] };
  }
});

const transport = new StdioServerTransport();
server.connect(transport);
```

**Use Case 2: Database Query Server**
```python
# mcp-servers/database-server.py
from mcp.server import Server
from mcp.server.stdio import stdio_server
import psycopg2

server = Server("database-server")

@server.call_tool()
async def query_analytics(sql_query: str):
    """Execute read-only analytics queries"""
    # Validate query is SELECT only
    if not sql_query.strip().upper().startswith('SELECT'):
        raise ValueError("Only SELECT queries allowed")
    
    # Execute query
    conn = psycopg2.connect(database="analytics")
    cursor = conn.cursor()
    cursor.execute(sql_query)
    results = cursor.fetchall()
    conn.close()
    
    return {"results": results}

if __name__ == "__main__":
    stdio_server(server)
```

#### **MCP Best Practices**

**Security:**
```markdown
- Never expose sensitive operations
- Validate all inputs
- Use read-only connections where possible
- Implement rate limiting
- Log all access
- Use environment variables for credentials
- Restrict tool capabilities
```

**Performance:**
```markdown
- Cache frequent requests
- Set appropriate timeouts
- Implement retry logic
- Use connection pooling
- Monitor resource usage
- Limit response sizes
```

**Reliability:**
```markdown
- Handle errors gracefully
- Provide clear error messages
- Implement health checks
- Log debugging information
- Version your servers
- Document capabilities
```

### 🔧 Troubleshooting Custom Instructions

**Problem**: Copilot ignores instructions
```markdown
Solutions:
1. Make instructions more specific
2. Use examples to clarify
3. Put most important rules first
4. Check instruction hierarchy
5. Verify file location (.github/copilot-instructions.md)
```

**Problem**: Instructions conflict with each other
```markdown
Solutions:
1. Review hierarchy (personal > repo > org)
2. Make preferences explicit
3. Use "prefer X over Y" language
4. Remove contradictory rules
5. Test in isolation
```

**Problem**: Instructions too restrictive
```markdown
Solutions:
1. Use "prefer" instead of "must"
2. Allow flexibility for edge cases
3. Provide alternative approaches
4. Balance standards with practicality
```

**Problem**: Copilot suggests outdated patterns
```markdown
Solutions:
1. Update instructions with current patterns
2. Reference latest examples
3. Explicitly mark old patterns as deprecated
4. Show migration path to new patterns
```

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

## 🚀 Advanced Topics & Further Learning

### 🎯 Optimization Strategies

#### **1. The Customization Maturity Model**

**Level 1: Basic Usage (Week 1)**
- Use default settings
- Learn keyboard shortcuts
- Try different modes
- Explore basic features

**Level 2: Personalization (Week 2-4)**
- Set personal instructions
- Experiment with models
- Create first prompt file
- Configure IDE settings

**Level 3: Team Optimization (Month 2-3)**
- Create repository instructions
- Build prompt file library
- Develop custom chat modes
- Share team best practices

**Level 4: Advanced Customization (Month 4+)**
- Set up MCP servers
- Create custom tools
- Build automation workflows
- Optimize cost/performance
- Measure productivity gains

#### **2. ROI Measurement Framework**

Track these metrics to measure customization impact:

**Time Savings:**
```markdown
Before Customization:
- Average time to create component: 30 minutes
- Average time to write tests: 45 minutes
- Average time to document: 20 minutes

After Customization:
- Average time to create component: 10 minutes (67% faster)
- Average time to write tests: 15 minutes (67% faster)
- Average time to document: 5 minutes (75% faster)

Weekly time saved per developer: ~8 hours
```

**Quality Improvements:**
```markdown
Metrics to track:
- Code review cycles reduced
- Bug density decreased
- Test coverage increased
- Documentation completeness improved
- Style consistency enhanced
```

**Team Metrics:**
```markdown
- Onboarding time reduced
- Knowledge sharing improved
- Code consistency increased
- Technical debt decreased
- Developer satisfaction increased
```

### 📚 Customization Recipe Book

#### **Recipe 1: The "Quick Start" Setup**
*Goal: Get 80% of benefits in 20% of time*

**Step 1:** Add basic repository instructions (5 min)
```markdown
- Project overview
- Tech stack
- File structure
- Key patterns
```

**Step 2:** Create 3 essential prompt files (15 min)
```markdown
- generate-component.prompt.md
- generate-tests.prompt.md
- review-code.prompt.md
```

**Step 3:** Set personal preferences (5 min)
```markdown
- Coding style
- Testing approach
- Documentation level
```

**Total: 25 minutes for immediate productivity boost**

#### **Recipe 2: The "Team Onboarding" Package**
*Goal: Help new team members be productive day one*

**Create:**
1. Comprehensive repository instructions
2. Prompt file library for common tasks
3. Custom chat mode for learning
4. Onboarding checklist prompt
5. FAQ documentation

**Structure:**
```markdown
.github/
  copilot-instructions.md (team standards)
  prompts/
    onboarding/
      setup-environment.prompt.md
      learn-architecture.prompt.md
      first-contribution.prompt.md
    development/
      create-feature.prompt.md
      fix-bug.prompt.md
      write-tests.prompt.md
    documentation/
      document-component.prompt.md
      update-readme.prompt.md
  chatmodes/
    Onboarding.chatmode.md
    Learning.chatmode.md
```

#### **Recipe 3: The "Code Quality" Enforcer**
*Goal: Maintain high standards automatically*

**Create custom mode: Code Quality Checker**
```markdown
---
description: 'Enforce code quality standards'
tools: ['codebase', 'search']
---

# Code Quality Checker

For every code submission, verify:

## ✅ Required Checks
- [ ] TypeScript strict mode compliance
- [ ] All functions have type annotations
- [ ] Error handling present
- [ ] Tests included
- [ ] Documentation updated
- [ ] Accessibility attributes
- [ ] Performance considerations
- [ ] Security best practices

## 🎯 Quality Metrics
- Cyclomatic complexity < 10
- Function length < 50 lines
- File length < 500 lines
- No duplicate code
- No commented-out code
- No console.logs in production

## 📋 Output Format
Provide checklist with specific issues and fixes.
```

#### **Recipe 4: The "Documentation Generator"**
*Goal: Never have outdated docs*

**Create automated doc workflow:**

**Prompt 1: generate-api-docs.prompt.md**
```markdown
---
description: 'Generate API documentation from code'
mode: 'agent'
---

Analyze ${file} and generate comprehensive API docs:

## Function Signatures
Extract all exported functions with:
- Parameters and types
- Return types
- Exceptions
- Examples

## Component Props
For React components:
- All props with types
- Required vs optional
- Default values
- Usage examples

## Output
Generate docs/api/${fileBasename}.md
```

**Prompt 2: sync-readme.prompt.md**
```markdown
---
description: 'Sync README with codebase changes'
mode: 'agent'
---

Review changes in the last commit.

Update README.md to reflect:
- New features added
- Changed APIs
- New dependencies
- Updated examples

Keep:
- Getting started section
- Existing examples still valid
```

### 🔬 Advanced Experimentation

#### **Experiment 1: Model Performance Benchmarking**

Create a testing framework:

```markdown
## Test Suite for Model Comparison

### Test 1: Code Generation Quality
Task: Generate React component with specific requirements
Measure:
- Correctness (does it work?)
- Completeness (all requirements met?)
- Code quality (maintainable?)
- Style consistency (matches project?)

### Test 2: Explanation Quality
Task: Explain complex algorithm
Measure:
- Clarity (easy to understand?)
- Accuracy (technically correct?)
- Depth (covers edge cases?)
- Examples (provides good examples?)

### Test 3: Refactoring Quality
Task: Improve existing code
Measure:
- Correctness (maintains behavior?)
- Improvement (actually better?)
- Safety (preserves tests?)
- Explanation (documents changes?)

### Results Tracking
| Model | Test 1 | Test 2 | Test 3 | Avg | Cost |
|-------|--------|--------|--------|-----|------|
| A     | 9/10   | 8/10   | 9/10   | 8.7 | $0.10|
| B     | 8/10   | 9/10   | 8/10   | 8.3 | $0.15|
```

#### **Experiment 2: Prompt Engineering A/B Testing**

Test variations of prompts:

```markdown
## A/B Test: Component Generation Prompt

### Version A (Baseline)
"Create a React component for displaying a photo"

### Version B (Structured)
"Create a React component with these requirements:
- Purpose: Display photo with metadata
- Props: photo object
- Styling: Tailwind CSS
- Features: Click to enlarge"

### Version C (Example-Driven)
"Create a React component like PhotoCard but for albums.
Reference: @src/components/gallery/PhotoCard.tsx
Follow same patterns and styling."

### Metrics
- Time to generate
- Number of iterations needed
- Code quality score
- Developer satisfaction

### Winner: Version C (25% better results)
```

### 🎓 Expert Tips & Tricks

#### **Tip 1: Context is King**
```markdown
Weak: "Create a button component"

Strong: "Create a button component following our design system
(@src/components/ui/Button.tsx) for the photo upload flow.
Include loading state and error handling."

Result: 3x better first-attempt quality
```

#### **Tip 2: Progressive Refinement**
```markdown
Don't try to get perfect results in one prompt.

Round 1: Basic implementation
Round 2: Add error handling
Round 3: Improve performance
Round 4: Add tests
Round 5: Polish and document

Each round builds on previous, maintaining quality.
```

#### **Tip 3: Build a Prompt Library**
```markdown
Start a team repository of proven prompts:

effective-prompts/
  components/
    react-component-with-tests.md
    typescript-hook.md
    context-provider.md
  refactoring/
    extract-component.md
    optimize-performance.md
    improve-types.md
  testing/
    unit-test-suite.md
    integration-test.md
    e2e-scenario.md

Share and refine as team learns.
```

#### **Tip 4: Measure Everything**
```markdown
Track your customization effectiveness:

Weekly Dashboard:
- Time saved: X hours
- Premium requests used: Y / 300
- Code quality score: Z
- Test coverage: W%
- Documentation completeness: V%

Adjust customizations based on data.
```

### 🔧 Troubleshooting Guide

#### **Issue: Inconsistent Results**
```markdown
Symptoms:
- Same prompt gives different results
- Quality varies significantly
- Can't reproduce good results

Solutions:
1. Add more specific constraints
2. Include concrete examples
3. Reference exact files to follow
4. Specify output format clearly
5. Use temperature=0 for consistency
6. Lock to specific model in prompt file
```

#### **Issue: Slow Response Times**
```markdown
Symptoms:
- Long wait for responses
- Timeouts
- IDE freezes

Solutions:
1. Reduce context size
2. Use faster models for simple tasks
3. Break large prompts into steps
4. Close unnecessary files
5. Clear Copilot cache
6. Check network connection
```

#### **Issue: Context Not Applied**
```markdown
Symptoms:
- Ignores custom instructions
- Doesn't follow project patterns
- Suggests outdated approaches

Solutions:
1. Verify .github/copilot-instructions.md exists
2. Check file is in correct format
3. Make instructions more explicit
4. Use @file references
5. Add concrete examples
6. Reload VS Code window
```

#### **Issue: MCP Server Not Working**
```markdown
Symptoms:
- Tools not appearing
- Connection errors
- Authentication failures

Solutions:
1. Check .vscode/mcp.json syntax
2. Verify environment variables set
3. Test server independently
4. Check logs in Output panel
5. Validate token permissions
6. Restart VS Code
7. Re-authenticate
```

### 📖 Additional Resources

#### **Official Documentation**
- [Custom Instructions Guide](https://docs.github.com/copilot/customizing-copilot/custom-instructions)
- [Prompt Files Documentation](https://docs.github.com/copilot/using-github-copilot/prompt-engineering)
- [Chat Modes Reference](https://docs.github.com/copilot/using-github-copilot/chat-modes)
- [MCP Server Specification](https://modelcontextprotocol.io/)

#### **Community Resources**
- GitHub Copilot Community Forums
- VS Code Copilot Extension Issues
- MCP Server Registry
- Copilot Best Practices Repository

#### **Learning Paths**
1. **Week 1**: Master basic customization
2. **Week 2**: Create prompt file library
3. **Week 3**: Build custom chat modes
4. **Week 4**: Implement MCP servers
5. **Ongoing**: Measure and optimize

### 🎯 Next Steps

Now that you've mastered customization:

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

**Ready for the next challenge? Move on to Lab 7 to learn about GitHub Copilot's Coding Agent!**
