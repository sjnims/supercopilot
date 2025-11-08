# SuperCopilot 🚀

> Supercharge GitHub Copilot in VSCode with powerful MCP servers and an intelligent instruction framework

SuperCopilot is a comprehensive framework that extends GitHub Copilot's capabilities in Visual Studio Code through Model Context Protocol (MCP) servers and structured instruction files. It provides enhanced AI assistance for software development, code navigation, web automation, research, and more.

## 🌟 Features

### Intelligent AI Assistant Framework

- **Structured Instructions**: Modular instruction files that guide Copilot's behavior
- **Core Principles**: Software engineering best practices built into the AI workflow
- **Context-Aware**: Understands your codebase, dependencies, and development environment

### Custom Slash Commands

- **11 Specialized Commands**: Pre-built workflows for common development tasks
- **MCP-Integrated**: Commands intelligently leverage available MCP tools
- **Context-Aware**: Adapt behavior based on selected files or code
- **Interactive**: Ask clarifying questions and offer follow-up actions
- **Categories**: Planning, Research, and Review workflows

### Powerful MCP Server Integration

- **[Context7](https://context7.com/)**: Access official library documentation and resolve library IDs
- **[Filesystem-with-morph](https://morph.so/)**: Advanced file system operations with intelligent code modifications
- **[Playwright](https://playwright.dev/)**: Browser automation, testing, and web interaction
- **[Sequential Thinking](https://github.com/modelcontextprotocol/servers)**: Structured problem-solving and complex reasoning workflows
- **[Serena](https://github.com/oraios/serena)**: Semantic code navigation and intelligent symbol-based editing
- **[Tavily](https://tavily.com/)**: Web search, content extraction, and site mapping

## 📋 Prerequisites

- **Visual Studio Code** (latest version recommended)
- **GitHub Copilot** subscription and extension installed
- **Node.js** (v18 or later) - for npm-based MCP servers
- **Python/uvx** (for Serena MCP server)
- **Git** (for version control)

### API Keys Required

You'll need API keys for some MCP servers:

- **Context7 API Key** - [Get it here](https://context7.com/)
- **MorphLLM API Key** - [Get it here](https://morph.so/)
- **Tavily API Key** - [Get it here](https://tavily.com/)

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/sjnims/supercopilot.git
cd supercopilot
```

### 2. Install Dependencies

The MCP servers are installed automatically via `npx` and `uvx` when first used. No manual installation is required.

### 3. Configure MCP Servers

The MCP server configuration is already set up in `.vscode/mcp.json`. When you first open the project in VSCode, you'll be prompted to enter your API keys:

- Context7 API Key
- MorphLLM API Key
- Tavily API Key

These keys are stored securely by VSCode and are not committed to the repository.

### 4. Start Using SuperCopilot

Open any file in VSCode and start using GitHub Copilot. The enhanced capabilities are automatically available through the MCP servers and instruction files.

## 📖 Documentation

### Instruction Files

The `.github/instructions/` directory contains modular instruction files that guide Copilot's behavior:

- **`SUPER_COPILOT.instructions.md`** - Main entry point for the SuperCopilot framework
- **`PRINCIPLES.instructions.md`** - Core software engineering principles
- **`ENVIRONMENT.instructions.md`** - Development environment documentation
- **`Git.instructions.md`** - Guidelines for generating git commit messages following Conventional Commits
- **`MCP_*.instructions.md`** - Comprehensive guides for each MCP server

### Key Concepts

#### Entry Point and Reference System

The instruction system uses a single entry point with cascading references:

- **`SUPER_COPILOT.instructions.md`** - The sole entry point file with an `applyTo: '**'` directive
  - This file is automatically included in GitHub Copilot's context for all files in the workspace
  - All other instruction files are brought into context via `@` references from this entry point

- **Referenced Files** - All other `.instructions.md` files are included via `@filename.md` syntax
  - These files only have a `description` in their frontmatter (no `applyTo` directive)
  - They are always included in context whenever the entry point is referenced
  - This creates a modular, maintainable structure where components can be easily managed

**Example Structure**:

```markdown
# In SUPER_COPILOT.instructions.md (the entry point)
---
applyTo: '**'
description: 'Main instructions file for the SuperCopilot framework.'
---

# Core Framework
@PRINCIPLES.md

# MCP Servers
@MCP_Context7.md
@MCP_Serena.md
```

```markdown
# In any referenced file (e.g., PRINCIPLES.instructions.md)
---
description: 'Core software engineering principles for VSCode Copilot to follow.'
---

# Content here...
```

**Key Benefits**:

- **Single Source of Truth**: Only one file controls what's included
- **Always Available**: All referenced components are always in Copilot's context
- **Modular**: Easy to organize related instructions into separate files
- **Flexible**: Can exclude optional components by not referencing them in the entry point

> **Note**: If you want certain instructions to only apply to specific files, create a separate entry point file with a more restrictive `applyTo` pattern and don't include those instructions in the main `SUPER_COPILOT.instructions.md`.

### Custom Slash Commands

The `.github/prompts/` directory contains 11 specialized slash commands that provide repeatable workflows for common development tasks. These commands are designed to intelligently leverage the MCP tools available in the framework.

#### What are Slash Commands?

Slash commands are custom prompts that you can invoke in GitHub Copilot Chat using the `/` prefix. Each command provides a structured, interactive workflow that:

- **Asks clarifying questions** before execution to understand your needs
- **Shows progress updates** during analysis and research
- **Leverages MCP tools intelligently** based on the task context
- **Adapts to your selection** (file, code block, or project-level)
- **Provides actionable output** with checklists and next steps
- **Offers follow-up actions** to continue the workflow

#### Command Naming Convention

All SuperCopilot commands use the `/scp-` prefix to namespace them from built-in Copilot commands:
- `/scp-feature-plan` - Plan a new feature
- `/scp-code-review` - Review code quality
- etc.

#### Available Commands

##### 📋 Planning Commands

**`/scp-feature-plan`**
- Plan a new feature from concept to implementation
- Researches best practices and analyzes current architecture
- Creates comprehensive breakdown with tasks, estimates, and integration requirements
- Uses: Tavily (research), Context7 (docs), Serena (codebase analysis), Sequential Thinking (evaluation)

**`/scp-task-breakdown`**
- Break complex tasks into actionable, prioritized steps
- Maps dependencies and identifies parallel work opportunities
- Provides estimates and critical path analysis
- Uses: Serena (code analysis), Sequential Thinking (complexity evaluation), Context7 (patterns)

**`/scp-spike`**
- Plan and execute technical spikes or proof-of-concepts
- Evaluates multiple approaches with pros/cons
- Provides POC implementation plan and remaining unknowns
- Uses: Sequential Thinking (comparison), Tavily (research), Context7 (API docs), Serena (integration analysis)

##### 🔍 Research Commands

**`/scp-library-research`**
- Research and evaluate libraries/frameworks for a use case
- Compares multiple options with detailed decision matrix
- Provides implementation checklist and integration notes
- Uses: Tavily (discovery), Context7 (official docs), Serena (integration analysis), Sequential Thinking (comparison)

**`/scp-best-practices`**
- Discover best practices and patterns for technologies or approaches
- Categorizes practices by priority (critical, important, helpful)
- Analyzes current project against best practices
- Uses: Tavily (current practices), Context7 (official guides), Serena (codebase analysis)

**`/scp-concept-explain`**
- Comprehensive explanations of programming concepts or patterns
- Provides layered explanation from simple to advanced
- Includes practical examples, anti-patterns, and learning path
- Uses: Tavily (explanations), Context7 (official specs), Serena (codebase examples), Sequential Thinking (structure)

**`/scp-find-examples`**
- Find real-world code examples and implementations
- Curates 3-5 best examples with quality assessment
- Provides adaptation guide for your project
- Uses: Tavily (search), Context7 (official examples), Serena (existing patterns), Sequential Thinking (evaluation)

##### ✅ Review Commands

**`/scp-code-review`**
- Comprehensive code quality review with severity levels
- Checks readability, maintainability, performance, and best practices
- Provides actionable checklist organized by priority
- Uses: Serena (structure analysis), Sequential Thinking (systematic review), Context7 (framework patterns)

**`/scp-architecture-review`**
- Review software architecture and design patterns
- Assesses scalability, maintainability, and structural quality
- Provides phased improvement roadmap
- Uses: Serena (architecture mapping), Sequential Thinking (pattern evaluation), Tavily (modern approaches), Context7 (framework architectures)

**`/scp-security-audit`**
- Comprehensive security analysis against OWASP Top 10
- Identifies vulnerabilities with severity scores and attack scenarios
- Provides remediation roadmap with estimates
- Uses: Serena (attack surface mapping), Sequential Thinking (OWASP checklist), Tavily (current threats), Context7 (security advisories)

**`/scp-refactor`**
- Guided code refactoring with preservation of behavior
- Creates step-by-step refactoring plan with validation points
- Identifies code smells and suggests appropriate patterns
- Uses: Serena (dependencies and usages), Sequential Thinking (strategy evaluation), Context7 (patterns), Filesystem-with-morph (can execute changes)

#### How to Use Slash Commands

1. **Copy the prompts to your project**: Copy the `.github/prompts/` directory to your project
2. **Open Copilot Chat** in VSCode
3. **Type the command**: e.g., `/scp-code-review`
4. **Answer clarifying questions** that the command asks
5. **Review the output** with actionable recommendations
6. **Take follow-up actions** offered by the command

#### Context-Aware Behavior

Slash commands adapt based on what you have selected:

- **File selected**: Command focuses on that specific file
- **Code selected**: Command analyzes that code block in detail
- **Project root**: Command provides project-wide analysis
- **No selection**: Command asks for the area of focus

#### Example Usage

```
# Review a specific file
1. Select a file in VSCode
2. Open Copilot Chat
3. Type: /scp-code-review
4. Answer: "Focus on performance and readability"
5. Get detailed code review with specific improvements

# Plan a new feature
1. Position cursor in relevant file (optional)
2. Type: /scp-feature-plan
3. Answer questions about the feature requirements
4. Get comprehensive plan with tasks, estimates, and integration requirements

# Research a library
1. Type: /scp-library-research
2. Specify: "state management for React"
3. Get comparison of Zustand, Jotai, Redux Toolkit with recommendations
```

## 🔧 Configuration

### MCP Server Configuration

The `.vscode/mcp.json` file defines all MCP servers and their configurations:

```json
{
  "servers": {
    "context7": { ... },
    "filesystem-with-morph": { ... },
    "playwright": { ... },
    "sequential-thinking": { ... },
    "serena": { ... },
    "tavily": { ... }
  }
}
```

### Customizing Instructions

You can customize the SuperCopilot framework by modifying instruction files or adding new ones:

#### Adding New Instruction Files

1. **Create** a new `<filename>.instructions.md` file in `.github/instructions/`
2. **Add YAML frontmatter** with a `description` (no `applyTo` needed unless creating a new entry point):

   ```yaml
   ---
   description: 'Brief description of what this instruction provides'
   ---
   ```

3. **Write your instructions** in Markdown format
4. **Reference it** in `SUPER_COPILOT.instructions.md` using `@<filename>.md` to include it in context

#### Modifying Existing Instructions

- Edit any `*.instructions.md` file directly
- Changes are automatically picked up when Copilot loads the context
- The modular structure makes it easy to update specific components

#### Creating Conditional Instructions

If you need instructions that only apply to specific files:

1. **Create a new entry point** file with a restrictive `applyTo` pattern:

   ```yaml
   ---
   applyTo: 'src/tests/**'
   description: 'Testing-specific instructions'
   ---
   ```

2. **Don't reference** these instructions in the main `SUPER_COPILOT.instructions.md`
3. GitHub Copilot will only load these instructions when working in matching files

## 🎯 Use Cases

### Code Navigation and Understanding

- **Serena**: Navigate large codebases semantically
- **Context7**: Access official library documentation
- **Sequential Thinking**: Break down complex problems

### Web Development

- **Playwright**: Automate browser testing and interactions
- **Tavily**: Extract web content and research information
- **Filesystem-with-morph**: Intelligent code modifications

### Research and Documentation

- **Tavily**: Web search and content extraction
- **Context7**: Library documentation lookup
- **Sequential Thinking**: Structured problem-solving

### Refactoring and Code Quality

- **Serena**: Symbol-based refactoring
- **Filesystem-with-morph**: Advanced file operations
- **Principles**: Built-in code quality guidelines

## 🛠️ MCP Server Details

### Context7

Access up-to-date documentation for libraries and frameworks:

- `resolve-library-id`: Find correct library identifiers
- `get-library-docs`: Retrieve documentation with examples

### Filesystem-with-morph

Advanced file system operations with intelligent code editing:

- Create, read, update, delete files and directories
- Smart code modifications that understand context
- Efficient edit operations with minimal token usage

### Playwright

Browser automation and testing:

- Navigate websites and take screenshots
- Fill forms and interact with elements
- Automate testing workflows
- Handle dialogs and file uploads

### Sequential Thinking

Structured problem-solving:

- Break down complex problems into steps
- Revise and refine thinking processes
- Generate and verify hypotheses
- Iterate until solution is found

### Serena

Semantic code navigation and editing:

- Find symbols by name patterns
- Navigate code relationships
- Symbol-based refactoring
- Intelligent code insertions and modifications

### Tavily

Web research and content extraction:

- Search the web with AI-powered results
- Extract content from multiple URLs
- Map website structures
- Crawl sites with custom instructions

## 📁 Project Structure

```text
supercopilot/
├── .github/
│   ├── instructions/          # Instruction files for Copilot
│   │   ├── SUPER_COPILOT.instructions.md
│   │   ├── PRINCIPLES.instructions.md
│   │   ├── ENVIRONMENT.instructions.md
│   │   ├── Git.instructions.md
│   │   ├── MCP_Context7.instructions.md
│   │   ├── MCP_Filesystem-with-morph.instructions.md
│   │   ├── MCP_Playwright.instructions.md
│   │   ├── MCP_Sequential.instructions.md
│   │   ├── MCP_Serena.instructions.md
│   │   └── MCP_Tavily.instructions.md
│   └── prompts/               # Custom slash commands for Copilot
│       ├── planning/          # Feature planning and task workflows
│       │   ├── scp-feature-plan.prompt.md
│       │   ├── scp-task-breakdown.prompt.md
│       │   └── scp-spike.prompt.md
│       ├── research/          # Research and learning workflows
│       │   ├── scp-library-research.prompt.md
│       │   ├── scp-best-practices.prompt.md
│       │   ├── scp-concept-explain.prompt.md
│       │   └── scp-find-examples.prompt.md
│       └── review/            # Code review and quality workflows
│           ├── scp-code-review.prompt.md
│           ├── scp-architecture-review.prompt.md
│           ├── scp-security-audit.prompt.md
│           └── scp-refactor.prompt.md
├── .vscode/
│   └── mcp.json              # MCP server configuration
├── LICENSE                    # MIT License
└── README.md                 # This file
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Make your changes**: Add new instruction files, improve documentation, etc.
4. **Commit your changes**: `git commit -m 'Add amazing feature'`
5. **Push to the branch**: `git push origin feature/amazing-feature`
6. **Open a Pull Request**

### Guidelines

- **Follow the instruction file format**:
  - Entry point files need `applyTo` and `description` in frontmatter
  - Referenced files only need `description` in frontmatter
  - Use `@filename.md` to reference other instruction files
- **Keep instructions clear and concise** - write for both AI and human readers
- **Test changes with GitHub Copilot** before submitting
- **Update documentation** (README.md) as needed
- **Maintain modularity** - each file should cover a distinct topic
- **Consider the entry point** - think about whether new instructions should always be in context

## 📝 Best Practices

### Working with Instructions

- **Keep instruction files focused** on a single topic or component
- **Use clear descriptions** in YAML frontmatter to document purpose
- **Reference thoughtfully** - only include in the entry point what should always be available
- **Organize logically** - group related instructions together
- **Document the "why"** - explain the reasoning behind instructions, not just what they do
- **Test your changes** - verify that Copilot behaves as expected after modifications
- **Keep it maintainable** - the modular structure makes updates easier

**Entry Point Management**:

- Only `SUPER_COPILOT.instructions.md` should have `applyTo: '**'`
- All other files referenced from the entry point are always in context
- Create separate entry points with restrictive `applyTo` patterns for conditional instructions

### Using MCP Servers

- Understand each server's capabilities before using
- Use the right tool for the job
- Combine servers for complex tasks
- Check API rate limits and quotas

### Code Quality

- Follow SOLID principles pragmatically
- Keep it simple (KISS)
- Don't repeat yourself (DRY)
- You aren't gonna need it (YAGNI)
- Write tests that give confidence

## 🔒 Security

### API Keys

- Never commit API keys to the repository
- Use VSCode's secure storage for keys
- Rotate keys regularly
- Monitor usage and set up alerts

### Code Safety

- Review AI-generated code before committing
- Run tests after AI modifications
- Use version control for easy rollback
- Follow security principles from `PRINCIPLES.instructions.md`

## 🐛 Troubleshooting

### MCP Server Not Working

1. Check that the server is properly configured in `.vscode/mcp.json`
2. Verify API keys are correct
3. Ensure required dependencies are installed (Node.js, Python, etc.)
4. Check VSCode Output panel for error messages

### Instruction Files Not Being Applied

1. **Verify YAML frontmatter** is correctly formatted in `SUPER_COPILOT.instructions.md`
2. **Check the entry point** has `applyTo: '**'` directive
3. **Ensure referenced files** use `@filename.md` syntax (without the `.instructions` part)
4. **Confirm file exists** in `.github/instructions/` directory
5. **Reload VSCode window** to refresh Copilot's context (Cmd+Shift+P → "Reload Window")
6. **Check file naming** - referenced files should match exactly (case-sensitive)

> **Tip**: Only `SUPER_COPILOT.instructions.md` needs the `applyTo` directive. All files it references via `@` are automatically included.

### API Rate Limits

1. Monitor API usage through provider dashboards
2. Implement caching where appropriate
3. Use rate limiting features
4. Consider upgrading API plans if needed

## 📚 Resources

### Official Documentation

- [GitHub Copilot](https://docs.github.com/en/copilot)
- [Model Context Protocol](https://modelcontextprotocol.io/)
- [VSCode Extension API](https://code.visualstudio.com/api)

### MCP Servers

- [Context7 Documentation](https://context7.com/docs)
- [Morph Documentation](https://morph.so/docs)
- [Playwright Documentation](https://playwright.dev/)
- [Serena on GitHub](https://github.com/oraios/serena)
- [Tavily Documentation](https://tavily.com/docs)

### Related Projects

- [Awesome MCP Servers](https://github.com/modelcontextprotocol/servers)
- [VSCode Copilot Documentation](https://code.visualstudio.com/docs/copilot/overview)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **GitHub Copilot Team** - For creating an amazing AI pair programmer
- **Model Context Protocol** - For enabling extensible AI capabilities
- **MCP Server Authors** - Context7, Morph, Playwright, Serena, Tavily teams
- **Open Source Community** - For inspiration and best practices

## 📮 Contact & Support

- **Issues**: [GitHub Issues](https://github.com/sjnims/supercopilot/issues)
- **Discussions**: [GitHub Discussions](https://github.com/sjnims/supercopilot/discussions)
- **Email**: <sjnims@gmail.com>

---

**Made with ❤️ for developers who want to supercharge their AI-assisted coding experience**

*"The best code is the code you don't have to write, but when you do, make it count."*
