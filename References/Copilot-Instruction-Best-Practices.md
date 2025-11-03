# Best Practices for Repository Custom Instructions

## Overview

GitHub Copilot supports custom instructions at the repository level to guide AI-assisted development and ensure code consistency across your project. Understanding how to effectively use both repository-wide and path-specific instructions is essential for maximizing Copilot's effectiveness.

This guide provides evidence-based best practices with practical, real-world examples focused specifically on **repository custom instructions** (not user-level personal instructions).

## Types of Repository Custom Instructions

GitHub Copilot supports two types of custom instructions within a repository:

### 1. **Repository-Wide Instructions** (`.github/copilot-instructions.md`)
- **Location**: Single file at `.github/copilot-instructions.md`
- **Scope**: Applies to **all files** in the repository
- **Purpose**: Define universal standards, tech stack, and patterns for the entire project
- **Best For**: Broad, consistent standards that affect the entire codebase

### 2. **Path-Specific Instructions** (`.github/instructions/*.instructions.md`)
- **Location**: Multiple files in `.github/instructions/` directory
- **Scope**: Applies only to files matching specified `applyTo` patterns
- **Purpose**: Provide targeted guidance for specific parts of the codebase
- **Best For**: Different conventions for frontend/backend, security-sensitive areas, or legacy code

## How They Work Together

**Research Finding**: Both instruction types work together through **context merging**. When editing a file:
1. Repository-wide instructions (`.github/copilot-instructions.md`) are always included
2. Any matching path-specific instructions are also included
3. Copilot merges all relevant instructions to inform its suggestions

**Important**: There's no strict priority hierarchy - Copilot uses all matching instructions as context. This means instructions should complement each other, not conflict.

## When to Use Each Type

| Scenario | Repository-Wide<br>(`copilot-instructions.md`) | Path-Specific<br>(`.instructions.md`) |
|----------|---------------------------------------------|----------------------------------|
| Technology stack and frameworks | ✅ | ❌ |
| Universal coding standards | ✅ | ❌ |
| Project architecture overview | ✅ | ❌ |
| Frontend-specific React patterns | ❌ | ✅ |
| Backend API conventions | ❌ | ✅ |
| Security-sensitive file handling | ❌ | ✅ |
| Test file requirements | ❌ | ✅ |
| Legacy code modernization hints | ❌ | ✅ |
| Monorepo with multiple sub-projects | ❌ | ✅ |

---

# Part 1: Repository-Wide Instructions (`.github/copilot-instructions.md`)

## Why Repository-Wide Instructions Matter

Repository-wide custom instructions are the **foundation** of effective AI-assisted development. Research shows that teams using well-crafted repository instructions report:

- **50%+ increase** in coding productivity
- **3-4x faster** feature delivery
- **60% reduction** in code review cycles
- **Improved onboarding** for new team members

These instructions serve critical purposes:
- **Team Consistency**: All contributors receive the same project-specific guidance
- **Code Quality**: Enforce architectural patterns and coding standards automatically
- **Living Documentation**: Version-controlled documentation of project decisions
- **Onboarding**: Help new developers understand conventions quickly
- **Standards Enforcement**: Prevent introducing outdated or incompatible patterns

## Best Practices for Repository-Wide Instructions

### 1. Start with a Clear Project Overview

Help Copilot understand what the project does and who it's for.

**Evidence-Based Recommendation**: Research shows that context and clarity are the most critical factors in instruction effectiveness.

**Real-World Example:**
```markdown
# Project Overview
This is a Photo Gallery & Portfolio application for professional photographers to showcase their work. Built with Next.js 15, TypeScript, and Tailwind CSS. The application prioritizes performance, accessibility, and mobile-first design.

## Target Users
- Professional photographers uploading high-resolution images
- Portfolio visitors browsing on various devices
- Gallery administrators managing content

## Core Functionality
- Photo upload with metadata
- Responsive grid-based gallery display
- Portfolio management dashboard
- Dark mode support
```

**Why This Works**: Copilot can make context-aware suggestions that fit your application's purpose and user needs.

### 2. Define the Technology Stack Explicitly

Specify exact versions and choices to avoid incompatible suggestions.

**Evidence-Based Recommendation**: Specific technology declarations prevent Copilot from suggesting outdated patterns or incompatible libraries found in the project's history.

**Real-World Example:**
```markdown
## Technology Stack
- **Framework**: Next.js 15 with App Router (NOT Pages Router)
- **Language**: TypeScript 5+ with strict mode enabled
- **Styling**: Tailwind CSS 3.x - no CSS modules or styled-components
- **State Management**: React hooks (useState, useEffect, useContext) - no Redux
- **Data Fetching**: React Server Components and Server Actions
- **Testing**: Jest + React Testing Library
- **Linting**: ESLint with recommended config
- **Package Manager**: npm (not yarn or pnpm)
```

**Why This Works**: Copilot won't suggest Redux when you've chosen Context API, or Pages Router patterns in an App Router project.

### 3. Document Architecture and Code Organization

Define where code lives and how components should be structured.

**Evidence-Based Recommendation**: Clear architectural guidance helps Copilot place new code in the right locations and follow established patterns.

**Real-World Example:**
```markdown
## Project Structure
\`\`\`
src/
├── app/              # Next.js 15 App Router pages
├── components/
│   ├── ui/           # Reusable UI components (buttons, inputs)
│   ├── layout/       # Layout components (Header, Footer, Container)
│   └── features/     # Feature-specific components
└── lib/              # Utility functions and shared logic
\`\`\`

## Architecture Patterns
- **Layout Components**: Place in `components/layout/`, accept `children` prop
- **Feature Components**: Place in `components/features/{feature-name}/`
- **UI Components**: Reusable across features, place in `components/ui/`
- **Services**: Business logic in `lib/services/`
- **Utilities**: Helper functions in `lib/utils/`
- **Server Actions**: Co-locate with components that use them

## Component Guidelines
- One component per file
- Use default exports for components
- Use named exports for utilities
- Co-locate tests: `Component.test.tsx`
- Follow Atomic Design principles for UI components
```

**Impact**: Copilot will suggest placing new components in correct directories and following your organizational patterns.

### 4. Specify Code Style and Conventions

Define the specific formatting, naming, and code organization standards for your project.

**Evidence-Based Recommendation**: Specific, actionable guidance works far better than vague directives like "write clean code."

**Real-World Example:**
```markdown
## Code Style Standards
- **Naming Conventions**:
  - camelCase for variables and functions
  - PascalCase for components and classes
  - UPPER_SNAKE_CASE for constants
  - Prefix boolean variables with `is`, `has`, `should`

- **File Organization**:
  - One component per file
  - Import order: external → internal → relative
  - Alphabetize imports within groups

- **TypeScript**:
  - Define interfaces for all component props
  - Use `type` for unions/intersections
  - Use `interface` for object shapes
  - Enable strict mode
  - No `any` type - use `unknown` if necessary

- **Functions**:
  - Max function length: 50 lines
  - Extract complex logic into helper functions
  - Use arrow functions for React components
  - Use named functions for utilities

- **Comments**:
  - JSDoc for all exported functions
  - Inline comments to explain "why", not "what"
  - Document complex algorithms
```

**Why This Works**: Consistent, specific standards reduce code review friction and ensure all team members (and Copilot) follow the same patterns.

### 5. Include Security Requirements

Define security standards that should be followed in all generated code.

**Evidence-Based Recommendation**: Security vulnerabilities are costly. Having Copilot follow security patterns by default significantly reduces risk.

**Real-World Example:**
```markdown
## Security Requirements
- **Input Sanitization**: Validate and sanitize all user input
- **Authentication**: Use NextAuth.js for authentication flows
- **Environment Variables**: Never commit secrets, use `.env.local`
- **API Routes**: Implement rate limiting on all API endpoints
- **SQL Queries**: Use parameterized queries only, never string concatenation
- **XSS Prevention**: Escape all dynamic content in JSX
- **File Uploads**: Validate file types and sizes before processing
- **Error Messages**: Never expose sensitive information in error messages

## Code Example
\`\`\`typescript
// Good: Parameterized query
const user = await db.user.findUnique({ where: { id: userId } });

// Bad: String concatenation (vulnerable to SQL injection)
// const query = "SELECT * FROM users WHERE id = '" + userId + "'";
\`\`\`
```

**Critical Impact**: Security patterns built into generated code from the start prevent vulnerabilities rather than requiring security audits later.

### 6. Document Deprecated Patterns

**Evidence-Based Practice**: Explicitly list patterns to avoid prevents Copilot from suggesting outdated code from project history.

**Real-World Example:**
```markdown
## Deprecated Patterns (Do Not Use)
- ❌ Class components - use functional components with hooks
- ❌ Pages Router - we use App Router only
- ❌ `any` type - use explicit types or `unknown`
- ❌ CSS-in-JS - use Tailwind classes
- ❌ `!important` in CSS - fix specificity instead
- ❌ Global state - use React Context or props

## Why These Are Deprecated
- Class components: Maintenance burden, hooks provide better patterns
- Pages Router: App Router provides better performance and features
- `any` type: Defeats purpose of TypeScript, causes runtime errors
```

**Impact**: Prevents Copilot from mimicking old patterns still present in the codebase.

### 7. Provide Code Examples

**Research Finding**: Concrete examples significantly improve Copilot's ability to generate consistent code.

**Real-World Example:**
```markdown
## Component Pattern Example

\`\`\`tsx
// Good: Follow this pattern for all feature components
import { useState } from 'react';
import { Button } from '@/components/ui/Button';

interface PhotoCardProps {
  photoUrl: string;
  title: string;
  onSelect: (id: string) => void;
}

export default function PhotoCard({ photoUrl, title, onSelect }: PhotoCardProps) {
  const [isHovered, setIsHovered] = useState(false);
  
  return (
    <div 
      className="rounded-lg overflow-hidden shadow-md"
      onMouseEnter={() => setIsHovered(true)}
      onMouseLeave={() => setIsHovered(false)}
    >
      <img src={photoUrl} alt={title} className="w-full h-48 object-cover" />
      {isHovered && (
        <Button onClick={() => onSelect(photoUrl)}>Select</Button>
      )}
    </div>
  );
}
\`\`\`
```

## Critical Limitations of Repository-Wide Instructions

**Evidence-Based Research**: Understanding these limitations is essential for setting realistic expectations.

### Token Limits and Context Windows

**Research Finding**: GitHub Copilot models have context windows between 8K-32K tokens, with part reserved for code context.

**Best Practice:**
- Keep repository instructions concise (preferably under 2KB)
- Focus on the most important patterns and standards
- Use clear, direct language
- Extremely large files may be truncated or partially ignored

### Non-Deterministic Behavior

**Research Finding**: Repository instructions "tilt" Copilot's suggestions but don't guarantee strict enforcement. Copilot may occasionally diverge due to the probabilistic nature of AI.

**Reality Check:**
- Instructions guide behavior, they don't control it absolutely
- Some suggestions may not follow instructions perfectly
- Code review is still necessary
- Update instructions when patterns don't work as expected

### Legacy Code Influence

**Research Finding**: Without clear instructions, Copilot dropped into a legacy codebase tends to replicate bad patterns seen in the repository.

**Solution:**
- Use deprecated patterns section to explicitly call out what not to do
- Consider path-specific instructions for legacy code areas
- Provide examples of correct patterns to override legacy influence

## Common Mistakes with Repository-Wide Instructions

**Evidence-Based Analysis**: These patterns have been identified in real-world case studies as ineffective.

### 1. Being Too Vague or Generic

**❌ Doesn't Work:**
```markdown
Write clean, maintainable code
Follow best practices
Use good coding standards
```

**✅ Works Better:**
```markdown
- Functions should be < 50 lines
- Extract complex logic into named helper functions
- Use TypeScript strict mode with explicit types
- Follow the existing patterns in `src/components/ui/`
```

**Research Insight**: Vague directives yield inconsistent results. Copilot needs specific, actionable guidance.

### 2. Overloading the Instructions File

**Research Finding**: Large, unfocused instruction files dilute Copilot's ability to synthesize productive suggestions.

**Best Practice:**
- Focus on the 20% of patterns that matter 80% of the time
- Remove outdated or rarely-used instructions
- Link to external documentation for deep details
- Keep the file under 2KB when possible

### 3. Not Updating Instructions

**Research Finding**: Instructions that reference obsolete dependencies or don't match current code cause Copilot to suggest broken solutions.

**Best Practice:**
- Review and update instructions with each major project change
- Remove deprecated patterns explicitly
- Test instructions by asking Copilot to generate code
- Version control allows tracking changes over time

### 4. Assuming Strict Enforcement

**Critical Mistake**: Expecting instructions to work like configuration files or linters.

**Reality:**
- Instructions are **guidance**, not rules
- Always review generated code
- Run linters and tests on Copilot-generated code
- Treat Copilot suggestions as drafts, not final code
- Use code review processes for all code

---

# Part 2: Path-Specific Instructions (`.github/instructions/*.instructions.md`)

## Why Path-Specific Instructions Matter

Path-specific instructions allow you to provide **granular, context-aware guidance** for different parts of your codebase. This is especially valuable for:

- **Monorepos** with different standards for different projects
- **Frontend vs Backend** with different technology stacks
- **Security-sensitive areas** requiring stricter patterns
- **Legacy code** that needs modernization guidance
- **Test files** with specific conventions
- **Different teams** working on different areas

## How Path-Specific Instructions Work

Path-specific instructions use the `applyTo` field to define which files they affect:

**File Structure:**
```
.github/
├── copilot-instructions.md              # Repository-wide instructions
└── instructions/
    ├── frontend.instructions.md         # Frontend-specific
    ├── backend-api.instructions.md      # Backend-specific
    ├── security.instructions.md         # Security areas
    └── tests.instructions.md            # Test files
```

**Example File** (`.github/instructions/frontend.instructions.md`):
```markdown
applyTo:
  - src/frontend/**
  - webapp/components/**
  - ui/**

---

# Frontend-Specific Instructions

## React Patterns
- Use React Server Components by default
- Add 'use client' only when necessary (interactivity, hooks, browser APIs)
- Prefer composition over prop drilling
- Use Context sparingly - props first

## Styling
- Use Tailwind utility classes
- Mobile-first responsive design
- Include dark mode variants with `dark:` prefix
- Accessibility: semantic HTML, ARIA labels, keyboard navigation

## Performance
- Lazy load components below the fold
- Use Next.js Image component for all images
- Implement virtualization for long lists
- Optimize re-renders with React.memo and useCallback
```

## Best Practices for Path-Specific Instructions

### 1. Use Precise Path Globs

**Research Finding**: Incorrect path globs are the #1 reason path-specific instructions don't work.

**Best Practices:**
```markdown
✅ Good - Specific and testable:
applyTo:
  - src/frontend/**
  - components/ui/**/*.tsx

❌ Bad - Too broad or wrong:
applyTo:
  - frontend  # Missing /**
  - /src/**   # Leading slash may not match
  - *.tsx     # Missing path, matches all levels
```

**Test Your Globs:**
- Verify patterns match actual file paths
- Test with `find` command: `find . -path "./src/frontend/**"`
- Remember globs are relative to repository root

### 2. Keep Instructions Focused and Relevant

**Evidence-Based Recommendation**: Path-specific instructions should only contain guidance relevant to that specific area.

**Real-World Example** (`.github/instructions/tests.instructions.md`):
```markdown
applyTo:
  - **/*.test.ts
  - **/*.test.tsx
  - **/*.spec.ts
  - tests/**

---

# Testing Standards

## Test Structure
- Use Arrange-Act-Assert pattern
- One test per behavior
- Descriptive test names: `it('should X when Y')`
- Group related tests in `describe` blocks

## Best Practices
- Test behavior, not implementation
- Mock external dependencies only
- Use `data-testid` for component queries
- Include accessibility tests for interactive components
- Aim for 80% coverage on utilities, 60% on components

## Example
\`\`\`typescript
describe('PhotoCard', () => {
  it('should display hover actions when mouse enters', () => {
    // Arrange
    const onSelect = jest.fn();
    render(<PhotoCard title="Test" onSelect={onSelect} />);
    
    // Act
    fireEvent.mouseEnter(screen.getByRole('img'));
    
    // Assert
    expect(screen.getByRole('button')).toBeInTheDocument();
  });
});
\`\`\`
```

### 3. Handle Conflicts with Repository-Wide Instructions

**Research Finding**: Path-specific and repository-wide instructions merge through context, not hierarchy.

**Best Practice:**
- Ensure path-specific instructions complement, not contradict, repository-wide instructions
- Use path-specific to add detail, not override basics
- Document intentional differences explicitly

**Example:**
```markdown
# backend-api.instructions.md
applyTo:
  - src/api/**
  - server/**

---

# Backend API Specific Instructions

Note: These instructions extend the repository-wide instructions with
backend-specific patterns. For general TypeScript and project standards,
see `.github/copilot-instructions.md`.

## API-Specific Patterns
- Use Express.js middleware pattern
- Implement request validation with Zod
- Return consistent error format: { error: string, code: number }
- Log all requests with structured logging
```

### 4. Use for Gradual Migration

**Real-World Use Case**: Use path-specific instructions to guide modernization of legacy code.

**Example** (`.github/instructions/legacy.instructions.md`):
```markdown
applyTo:
  - legacy/**
  - deprecated/**

---

# Legacy Code Modernization

When working with files in these directories:

## Current State
- These use class components and older patterns
- Do NOT replicate these patterns in new code

## When Modifying
- Suggest migration to functional components
- Flag usage of deprecated APIs
- Recommend modern alternatives
- Link to migration guide: /docs/modernization-guide.md

## Do Not
- Make breaking changes without team approval
- Remove code without understanding its purpose
- Introduce new dependencies to legacy code
```

## Common Mistakes with Path-Specific Instructions

### 1. Missing `applyTo` Section

**Critical Error**: Without `applyTo`, the instructions won't apply to any files.

**Fix:**
```markdown
❌ Wrong - No applyTo:
---
# Frontend Instructions
Use React hooks...

✅ Correct - Include applyTo:
applyTo:
  - src/frontend/**

---
# Frontend Instructions
Use React hooks...
```

### 2. Incorrect File Extension

**Research Finding**: Only files ending in `.instructions.md` are recognized.

**Fix:**
```
❌ Wrong:
.github/instructions/frontend.md
.github/instructions/frontend-instructions.md

✅ Correct:
.github/instructions/frontend.instructions.md
.github/instructions/backend-api.instructions.md
```

### 3. Glob Patterns Don't Match Files

**Most Common Issue**: Path globs that don't match actual file structure.

**Debug Steps:**
1. Test glob with `find`: `find . -path "./src/frontend/**"`
2. Check for leading slashes (often not needed)
3. Verify `**` for recursive matching
4. Ensure case sensitivity matches

### 4. Conflicting Instructions

**Problem**: Path-specific instructions that contradict repository-wide or each other.

**Example of Conflict:**
```markdown
# Repository-wide says:
Use TypeScript strict mode

# Path-specific says:
Use any type for quick prototyping

# Result: Confusing and unpredictable
```

**Fix**: Ensure instructions complement each other:
```markdown
# Path-specific should say:
Follow repository-wide TypeScript standards.
For prototyping in this area, use unknown instead of any.
```

### 5. Too Many Overlapping Instructions

**Research Finding**: Having many path-specific files with overlapping patterns dilutes effectiveness.

**Best Practice:**
- Limit to 3-5 path-specific instruction files
- Ensure each has a clear, distinct purpose
- Minimize overlap in `applyTo` patterns
- Test which instructions apply to key files

---

# Implementation Strategies

## For New Projects

**Evidence-Based Approach**: Starting with instructions from day one shows the highest return on investment.

### Phase 1: Repository-Wide Foundation (Week 1)
1. Create `.github/copilot-instructions.md`
2. Include:
   - Project overview and purpose
   - Technology stack with versions
   - Basic code style standards
   - Project structure

### Phase 2: Core Patterns (Week 2-3)
3. Add to repository-wide instructions:
   - Architecture patterns
   - Security requirements
   - Error handling standards
   - Testing expectations

### Phase 3: Path-Specific Refinement (Week 4+)
4. Create path-specific instructions for:
   - Test files (`tests.instructions.md`)
   - Frontend vs backend (if applicable)
   - Security-sensitive areas
5. Test and refine based on usage

## For Existing Projects

**Research Finding**: Gradual adoption with team input leads to better adoption and effectiveness.

### Step 1: Audit Current Patterns
- Review existing code to identify common patterns
- Document what's working well
- Identify inconsistencies to address

### Step 2: Start with Repository-Wide Basics
- Create `.github/copilot-instructions.md`
- Focus on:
  - Tech stack (prevent suggesting wrong frameworks)
  - Deprecated patterns (prevent replicating old code)
  - Project structure overview
- Test with team: ask Copilot to generate code

### Step 3: Add Path-Specific as Needed
- Identify areas with unique requirements
- Create targeted instruction files
- Start with 1-2 files, expand based on need

### Step 4: Iterate Based on Feedback
- Collect team feedback on what's working
- Refine instructions based on Copilot's output
- Remove ineffective instructions
- Update as project evolves

## Measuring Effectiveness

**Research-Backed Metrics**: Track these indicators to quantify impact.

### Qualitative Metrics:
- **Code Review Time**: Faster reviews due to consistent patterns?
- **Code Consistency**: New code following established patterns?
- **Onboarding Speed**: New developers productive faster?
- **Team Satisfaction**: Developers finding Copilot more helpful?

### Quantitative Metrics:
- **Review Cycle Time**: Days from PR creation to merge
- **Pattern Adherence**: % of code reviews with style comments
- **Copilot Acceptance Rate**: % of suggestions accepted
- **Bug Rate**: Issues per 1000 lines of code

### Example Tracking:
```markdown
## Repository Instructions Effectiveness Log

### November 2025
- Average PR review time: 4 hours (was 8 hours in October)
- Style-related review comments: 12% (was 35%)
- Copilot suggestion acceptance: 42% (was 28%)
- Team feedback: "Much more relevant suggestions"

### Actions Taken
- Added deprecated patterns section → reduced legacy pattern replication
- Created tests.instructions.md → better test generation
- Need to add more examples for API route patterns
```

## Maintaining Instructions

**Critical Success Factor**: Instructions are living documents requiring active maintenance.

### Regular Review Cadence

**Best Practice Schedule:**
- **Monthly**: Quick review of effectiveness metrics
- **Quarterly**: Deep review with team feedback session
- **After Major Changes**: Update immediately when architecture changes
- **During Onboarding**: Get feedback from new team members

### Update Triggers

Update instructions when:
- ✅ New major technology is adopted
- ✅ Architectural patterns change
- ✅ Security requirements evolve
- ✅ Team consistently asks the same questions
- ✅ Code review patterns emerge
- ✅ Copilot generates unexpected code
- ✅ Project structure changes significantly

### Feedback Process

**Template for Collecting Feedback:**
```markdown
## Instructions Feedback Form

**Date**: 2025-11-03
**Contributor**: [Name]
**Area**: [ ] Repository-wide  [ ] Path-specific: ___________

**What's Not Working?**
[Describe the issue or unclear guidance]

**Suggested Improvement:**
[What should be changed or added?]

**Impact Level:**
[ ] Daily - affects me constantly
[ ] Weekly - I encounter this regularly  
[ ] Monthly - occasional issue
[ ] Rare - but important

**Example:**
[Link to PR or code where this came up]
```

### Version Tracking

**Best Practice:**
```markdown
---
# .github/copilot-instructions.md
version: 2.1.0
last-updated: 2025-11-03
maintainer: Development Team
---

## Changelog
- v2.1.0 (2025-11-03): Added path-specific instructions for tests
- v2.0.0 (2025-10-15): Migrated from Pages Router to App Router
- v1.5.0 (2025-09-20): Added security requirements section
- v1.0.0 (2025-08-01): Initial repository instructions
```

---

# Summary & Key Takeaways

## Repository-Wide vs Path-Specific Instructions

| Aspect | Repository-Wide<br>(`.github/copilot-instructions.md`) | Path-Specific<br>(`.github/instructions/*.instructions.md`) |
|--------|---------------------------------------------------|--------------------------------------------------|
| **Scope** | All files in repository | Only files matching `applyTo` globs |
| **Purpose** | Universal standards & tech stack | Context-specific guidance |
| **Number of Files** | One file | Multiple files (3-5 recommended) |
| **Size Recommendation** | < 2KB | < 1KB each |
| **Update Frequency** | Quarterly or on major changes | As specific areas evolve |
| **Best For** | Project foundations | Specialized requirements |
| **Complexity** | Simple - no `applyTo` needed | More complex - requires glob patterns |

## Evidence-Based Impact

**Research shows well-implemented repository instructions deliver:**
- 50%+ increase in coding productivity
- 3-4x faster feature delivery
- 60% reduction in code review cycles
- Improved onboarding experience
- Higher code consistency
- Reduced technical debt

**Critical Success Factors:**
1. Specificity over vagueness
2. Regular maintenance and updates
3. Team collaboration and buy-in
4. Realistic expectations about AI limitations
5. Always review generated code

## Top 10 Dos and Don'ts

### ✅ DO:
1. **Be specific** - "Use Next.js App Router" not "use modern patterns"
2. **Provide examples** - Show actual code patterns you want
3. **Document deprecated patterns** - Explicitly say what NOT to do
4. **Keep it concise** - Under 2KB for repo-wide, under 1KB for path-specific
5. **Use `applyTo` correctly** - Test your glob patterns
6. **Update regularly** - Review quarterly and after major changes
7. **Test instructions** - Ask Copilot to generate code, verify results
8. **Version track** - Use changelog to document evolution
9. **Collect feedback** - Get input from team members
10. **Complement, don't conflict** - Ensure instructions work together

### ❌ DON'T:
1. **Be vague** - "Write good code" provides no guidance
2. **Overload files** - Don't create encyclopedia-length instructions
3. **Forget `applyTo`** - Path-specific instructions need glob patterns
4. **Let them stagnate** - Outdated instructions cause bad suggestions
5. **Expect strict enforcement** - Instructions guide, not control
6. **Create too many files** - Limit to 3-5 path-specific files
7. **Use wrong extensions** - Must end in `.instructions.md`
8. **Skip testing** - Always verify instructions work as expected
9. **Create conflicts** - Ensure instructions complement each other
10. **Trust blindly** - Always review Copilot's generated code

## Quick Start Checklist

### Creating Your First Repository Instructions

- [ ] Create `.github/copilot-instructions.md`
- [ ] Add project overview (what, who, why)
- [ ] Define technology stack with versions
- [ ] Document project structure
- [ ] List coding style standards
- [ ] Add security requirements
- [ ] Document deprecated patterns
- [ ] Provide code examples
- [ ] Keep under 2KB total
- [ ] Test by asking Copilot to generate code
- [ ] Get team feedback
- [ ] Iterate and refine

### Adding Path-Specific Instructions (Optional)

- [ ] Identify areas needing specific guidance
- [ ] Create `.github/instructions/` directory
- [ ] Create first file: `{area}.instructions.md`
- [ ] Add `applyTo:` with glob patterns
- [ ] Test glob patterns match intended files
- [ ] Keep instructions focused and relevant
- [ ] Ensure no conflicts with repo-wide instructions
- [ ] Test with actual files in that path
- [ ] Limit to 3-5 files total
- [ ] Document why each file exists

## Conclusion

Repository custom instructions are a powerful tool for guiding Copilot, but they work best when:

1. **Focused on the repository** - Not user preferences
2. **Clearly structured** - Repository-wide for foundations, path-specific for nuance
3. **Specific and actionable** - Not vague or generic
4. **Regularly maintained** - Updated as the project evolves
5. **Realistic about limitations** - Guidance, not enforcement

**Remember**: Instructions guide Copilot's behavior—they don't control it absolutely. Always review generated code, run tests, and use your judgment. Copilot is a powerful assistant that works best with clear guidance, but it's not a replacement for human expertise and code review.

The combination of well-crafted repository-wide instructions and targeted path-specific instructions creates an environment where Copilot can provide relevant, context-aware suggestions that truly accelerate development while maintaining code quality and consistency.

---

## Additional Resources

### Official Documentation
- [Adding Repository Custom Instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
- [Path-Scoped Custom Instruction Files](https://github.blog/changelog/2025-09-03-copilot-code-review-path-scoped-custom-instruction-file-support/)
- [GitHub Copilot Tutorials](https://docs.github.com/copilot/tutorials)

### Best Practices & Research
- [5 Tips for Writing Better Custom Instructions (GitHub Blog)](https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/)
- [The Complete Guide to GitHub Copilot Instructions](https://www.copilotcraft.dev/blog/getting-started-github-copilot-instructions)
- [Everything About Copilot Instructions (DEV Community)](https://dev.to/anchildress1/everything-i-know-about-github-copilot-instructions-from-zero-to-onboarded-for-real-4nb0)
- [All I've Learned About Copilot Instructions (DEV Community)](https://dev.to/anchildress1/all-ive-learned-about-github-copilot-instructions-so-far-5bm7)

### Common Problems & Solutions
- [Common Problems with GitHub Copilot](https://hackernoon.com/common-problems-with-github-copilot-and-how-to-solve-them)
- [GitHub Copilot Best Practices](https://www.coderabbit.ai/blog/github-copilot-best-practices-10-tips-and-tricks-that-actually-help)
