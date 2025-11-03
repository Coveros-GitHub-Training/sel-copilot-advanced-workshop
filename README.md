# GitHub Copilot Hands-On Labs - Photo Gallery & Portfolio

Welcome to the **GitHub Copilot Hands-On Labs**! This comprehensive workshop teaches you how to use GitHub Copilot as an AI-powered assistant throughout the software development lifecycle. Through practical exercises using a real-world photo gallery application, you'll learn to leverage Copilot for code generation, understanding, refactoring, and autonomous development.

## 🎯 Workshop Overview

This hands-on lab is designed to give developers practical experience using **GitHub Copilot** across all phases of the SDLC. Built around **PixelPerfect Gallery**—a professional photo gallery and portfolio application—you'll explore how GitHub Copilot can improve developer productivity, code quality, and collaboration.

### What You'll Learn

Through guided, real-world exercises, you will:
- Understand GitHub Copilot's role across all phases of the SDLC
- Use AI-powered code completions directly within the IDE
- Leverage GitHub Copilot Chat in Ask, Edit, and Agent modes
- Explore GitHub Copilot Spaces for collaborative development
- Delegate tasks to the GitHub Copilot Coding Agent
- Optimize GitHub Copilot with Custom Instructions and Prompt Files
- Apply engineering best practices for AI-assisted development

## 📚 Lab Exercises

All lab exercises are located in the [`Labs/`](Labs/) directory:

| Lab | Title | Duration | Description |
|-----|-------|----------|-------------|
| [Lab 1](Labs/Lab-1-Getting-Started.md) | Getting Started | 15 min | Set up your development environment and get introduced to PixelPerfect Gallery |
| [Lab 2](Labs/Lab-2-Lab-2-Exploring-the-Codebase.md) | Exploring the Codebase | 20 min | Use Copilot Chat to understand project structure, technologies, and architecture |
| [Lab 3](Labs/Lab-3-Code-Editing.md) | Code Editing & Generation | 30 min | Master Edit mode and Agent mode for code generation and multi-file modifications |
| [Lab 4](Labs/Lab-4-Engineering-Practices-and-Copilot-Instructions.md) | Engineering Practices & Copilot Instructions | 45 min | Debug Copilot's decisions, configure personal and repository instructions, switch models |
| [Lab 5](Labs/Lab-5-Prompt-Files-Custom-Modes-and-MCP.md) | Prompt Files, Custom Modes, and MCP | 45 min | Create prompt files and custom chat modes, set up GitHub MCP for advanced integrations |
| [Lab 6](Labs/Lab-6-Copilot-Spaces.md) | Copilot Spaces | 40 min | Create dedicated AI workspaces for focused, collaborative development and IDE integration |
| [Lab 7](Labs/Lab-7-Coding-Agent.md) | Coding Agent | 45 min | Assign issues to Copilot for autonomous implementation and PR creation |

**Total Duration**: Approximately 4 hours

## 🚀 Quick Start

### Option 1: GitHub Codespaces (Recommended)

The fastest way to get started:

1. Click the **"Code"** button on the repository page
2. Select the **"Codespaces"** tab
3. Click **"Create codespace on main"**
4. Wait for the environment to build

The codespace will automatically:
- Install all dependencies
- Configure GitHub Copilot and VS Code extensions
- Provide a ready-to-use development environment

### Option 2: Local Development

**Prerequisites:**
- Node.js v18 or newer
- npm, yarn, pnpm, or bun
- Git
- Visual Studio Code (recommended)

**Setup:**
```bash
# Clone the repository
git clone https://github.com/Coveros-GitHub-Training/sel-copilot-advanced-workshop.git
cd sel-copilot-advanced-workshop/pixelperfect-gallery

# Install dependencies
npm install

# Start the development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

## 📖 Getting Started

1. **Start with Lab 1**: Begin with [Lab 1 - Getting Started](Labs/Lab-1-Getting-Started.md)
2. **Follow the sequence**: Complete labs in order for the best learning experience
3. **Practice hands-on**: Each lab includes practical exercises and examples
4. **Explore freely**: Feel free to experiment beyond the guided exercises

## 📸 About PixelPerfect Gallery

The workshop uses **PixelPerfect Gallery**, a professional photo gallery and portfolio application built with modern web technologies. This real-world application provides authentic scenarios for learning GitHub Copilot features.

### Technologies Used

- **Next.js 15**: React framework with App Router
- **TypeScript**: Type-safe JavaScript
- **Tailwind CSS**: Utility-first CSS framework
- **Framer Motion**: Animation library
- **Radix UI**: Accessible component primitives
- **React Dropzone**: File upload with drag-and-drop

### Application Features

- **Photo Gallery**: Browse and filter professional photo collections
- **Upload System**: Drag-and-drop photo upload with preview
- **Admin Dashboard**: Manage photos and view statistics
- **Responsive Design**: Mobile-first, works on all devices
- **Dark Mode**: Full dark mode support throughout
- **Component Library**: Reusable UI components with consistent patterns

## 🏗️ Repository Structure

```
.
├── Labs/                  # Hands-on lab exercises (START HERE!)
├── References/            # Reference documentation
├── pixelperfect-gallery/  # Photo Gallery & Portfolio Application
│   ├── src/
│   │   ├── app/          # Next.js 15 App Router pages
│   │   ├── components/   # Reusable React components
│   │   │   ├── ui/      # UI components (buttons, cards, etc.)
│   │   │   ├── gallery/ # Gallery-specific components
│   │   │   └── upload/  # Upload-specific components
│   │   └── lib/         # Utility functions and mock data
│   ├── public/          # Static assets
│   └── ...              # Configuration files (package.json, tsconfig.json, etc.)
├── .github/
│   ├── prompts/         # Custom prompt files for Copilot
│   ├── chatmodes/       # Custom chat modes
│   └── copilot-instructions.md  # Repository-level Copilot instructions
└── media/               # Workshop media assets
```

## 📝 Additional Resources

### Component Documentation
- [Component Usage Guide](pixelperfect-gallery/COMPONENT_USAGE_GUIDE.md) - Detailed guide for using UI components

### Custom Copilot Features
- **Prompt Files** (`.github/prompts/`) - Reusable prompts for common tasks
- **Chat Modes** (`.github/chatmodes/`) - Specialized AI modes for specific workflows  
- **Instructions** (`.github/copilot-instructions.md`) - Project-specific AI guidance

### Reference Materials
- [References/](References/) - Additional reference documentation and guides

## 🤝 Contributing

Contributions to improve the labs or add new exercises are welcome! Please:
1. Follow the existing lab structure and format
2. Maintain consistency with the PixelPerfect Gallery scenario
3. Test all exercises thoroughly
4. Update documentation as needed

## 📄 License

This project is licensed under the terms specified in the [LICENSE](LICENSE) file.

## 🆘 Support

If you encounter issues or have questions:
- Review the lab instructions carefully
- Check the [Component Usage Guide](pixelperfect-gallery/COMPONENT_USAGE_GUIDE.md)
- Ask GitHub Copilot for help (it's great at explaining this codebase!)
- Create an issue in the repository for technical problems

---

**Ready to start?** Head to [Lab 1 - Getting Started](Labs/Lab-1-Getting-Started.md) and begin your GitHub Copilot journey! 🚀
