---
description: 'Detailed documentation of the development environment for VSCode Copilot to reference when assisting with code generation, debugging, and other tasks.'
---

# Machine Environment: M2 Max MacBook Pro (2023)

**Generated**: 2025-11-04
**Purpose**: Provide VSCode Copilot with comprehensive understanding of this development environment

---

## 🖥️ System Specifications

- **Model**: MacBook Pro (Mac14,5)
- **Processor**: Apple M2 Max
- **Architecture**: ARM64 (Apple Silicon)
  - ⚠️ **IMPORTANT**: VSCode Copilot may run under Rosetta 2 (x86_64 emulation) in some contexts
  - Use `arch` command to verify architecture when it matters for builds/compilation
- **Memory**: 32GB RAM
- **OS**: macOS 26.0.1 (Build 25A362)
- **Shell**: zsh (Oh My Zsh framework)
- **CPU Cores**: 12 cores (performance + efficiency)

---

## 🐚 Shell Configuration

### Oh My Zsh Setup
- **Framework**: Oh My Zsh (installed at ~/.oh-my-zsh)
- **Theme**: robbyrussell
- **Plugins**: (loaded from ~/.zshrc)
- **Custom Config**: ~/.oh-my-zsh/custom/

### Shell Aliases Reference
⚠️ **CRITICAL**: Shell aliases defined in .zshrc or Oh My Zsh custom files are **NOT available** in VSCode Copilot' bash execution environment. Always use the actual commands listed below.

| Alias | Actual Command | Purpose |
|-------|----------------|---------|
| `rm` | `rm -i` | Interactive delete (asks confirmation) |
| `mv` | `mv -i` | Interactive move (asks confirmation) |
| `cp` | `cp -i` | Interactive copy (asks confirmation) |
| `lr` | `ls -hartl` | List files with full details, sorted by time |

**When working with VSCode Copilot**: Use the "Actual Command" column values directly, as aliases won't resolve.

---

## 📦 Package Managers

### Homebrew
- **Version**: 4.6.20
- **Location**: `/opt/homebrew/bin/brew` (ARM64-optimized location)
- **Note**: Installed at `/opt/homebrew` (not `/usr/local` which is Intel location)

### Node.js Package Managers
- **npm**: 11.6.2 (bundled with Node.js)
- **yarn**: 1.22.22
- **pnpm**: Available (defers to yarn per package.json configuration)

### Python Package Managers
- **uv**: 0.8.15 - Ultra-fast Python package installer and resolver
  - Modern replacement for pip, pip-tools, and virtualenv
  - Significantly faster than traditional pip
  - **PREFERRED** for all Python package management
- **pipx**: 1.8.0 - Install Python CLI tools in isolated environments
  - Use for global CLI tools (black, pytest, ruff, etc.)
  - Each tool gets its own isolated environment
- **pip**: 25.3 - Traditional Python package installer
  - ⚠️ **CRITICAL**: Homebrew Python blocks global pip installs (PEP 668)
  - Only use inside virtual environments or with uv

### Version Managers
- **nvm**: Installed at `~/.nvm` - Node Version Manager
  - Current Node version: v24.10.0
  - Activation: `source ~/.nvm/nvm.sh` (if needed in scripts)
- **rbenv**: 1.3.2 - Ruby Version Manager
  - Current Ruby version: 3.4.7 (set globally)
  - Installed versions: 3.4.2, 3.4.4, 3.4.5, 3.4.6, 3.4.7, system
  - Activation: Typically auto-initialized via ~/.zshrc
- **pyenv**: Not installed

---

## 🛠️ Installed Development Tools

### Core Development
| Tool | Version | Notes |
|------|---------|-------|
| **git** | 2.50.1 (Apple Git-155) | Apple's bundled version |
| **node** | v24.10.0 | Managed via nvm |
| **python3** | 3.14.0 | **Homebrew-installed** (see critical notes below) |
| **pip** | 25.3 | Bundled with Homebrew Python (**NOT for global installs**) |
| **pipx** | 1.8.0 | For installing Python CLI tools globally |
| **uv** | 0.8.15 | Fast Python package manager (preferred) |
| **ruby** | 3.4.7 | Managed via rbenv, ARM64 native |
| **make** | GNU Make 3.81 | Build automation |
| **docker** | 28.2.2 (build e6534b4) | Containerization |
| **kubectl** | v1.32.2 | Kubernetes CLI (Kustomize v5.5.0) |

### Modern CLI Replacements (Preferred Tools)
| Tool | Version | Use Instead Of | Notes |
|------|---------|----------------|-------|
| **ripgrep (rg)** | 15.1.0 | `grep` | Much faster code search |
| **jq** | 1.7.1-apple | - | JSON parsing/manipulation |

### Missing Tools (not currently installed)
The following common tools are **not installed**:
- `exa` (modern ls replacement)
- `bat` (better cat)
- `fd` (faster find)
- `fzf` (fuzzy finder)
- `go` (Golang)
- `cargo` (Rust)
- `aws` (AWS CLI)
- `terraform`

---

## 🔧 Tool Preferences & Best Practices

### Search & File Operations
- **Code Search**: Use `rg` (ripgrep) over `grep` for searching code
  - Example: `rg "pattern" --type js` instead of `grep -r "pattern" *.js`
- **File Finding**: Use `find` (standard tool available)
- **JSON Processing**: Use `jq` for JSON manipulation

### Architecture-Specific Considerations

#### Apple Silicon (M2 Max) Best Practices
1. **Homebrew Location**:
   - ARM64 packages: `/opt/homebrew/`
   - Intel packages (if any): `/usr/local/homebrew/`

2. **Building from Source**:
   - Most packages have ARM64 support
   - If Rosetta 2 needed: `/usr/sbin/softwareupdate --install-rosetta`
   - Check architecture: `arch` or `uname -m`

3. **Docker Considerations**:
   - Prefer ARM64/aarch64 images when available
   - Multi-platform builds: `docker buildx build --platform linux/amd64,linux/arm64`
   - Some x86_64 images run via emulation (slower)

4. **Compilation Flags**:
   - Native ARM64 builds: Generally automatic
   - Force ARM64: `arch -arm64 <command>`
   - Force x86_64: `arch -x86_64 <command>` (uses Rosetta 2)

5. **Performance Optimization**:
   - M2 Max has performance and efficiency cores
   - Parallel builds: `make -j$(sysctl -n hw.ncpu)` (uses all cores)
   - Current core count: Use `sysctl -n hw.ncpu` to check

---

## 🌍 Environment Variables

### Key System Paths
```bash
SHELL=/bin/zsh
HOMEBREW_PREFIX=/opt/homebrew
HOME=/Users/stevenims
```

### Version Manager Paths
```bash
NVM_DIR=$HOME/.nvm        # Node Version Manager
RBENV_ROOT=$HOME/.rbenv   # Ruby Version Manager
```

---

## 🚀 Common Development Workflows

### Node.js Projects
```bash
# Start development server
npm run dev
# or
yarn dev

# Install dependencies
npm install
# or
yarn install

# Run tests
npm test
# or
yarn test

# Build project
npm run build
# or
yarn build
```

### Docker Operations
```bash
# Run docker commands directly
docker ps
docker compose up
docker compose down

# Note: Docker Desktop must be running
```

### Git Workflows
```bash
# Use actual git commands (not aliases)
git status
git pull
git commit -m "message"
git push
```

### Ruby Projects
```bash
# Check current Ruby version
rbenv version

# Switch Ruby version for project
rbenv local 3.4.7

# Install gems
bundle install

# Run Ruby scripts
ruby script.rb

# Rails commands (if applicable)
rails server
rails console
```

### Python Projects

⚠️ **CRITICAL: Homebrew Python Restrictions**
- Python 3.14 is installed via Homebrew
- **NEVER run `pip install package` globally** - it will fail with "externally-managed-environment" error
- **ALWAYS use virtual environments** for project dependencies
- **Use pipx** for global CLI tools

```bash
# ========================================
# VIRTUAL ENVIRONMENTS (Required for project work)
# ========================================

# Create virtual environment with uv (PREFERRED - much faster)
uv venv
uv venv .venv  # specify directory

# OR create with standard venv (slower)
python3 -m venv .venv

# Activate virtual environment (REQUIRED before installing packages)
source .venv/bin/activate

# Install packages INSIDE virtual environment
uv pip install package-name              # Fast
uv pip install -r requirements.txt       # From requirements
uv sync                                  # From pyproject.toml

# OR use traditional pip (inside venv only)
pip install package-name
pip install -r requirements.txt

# Deactivate when done
deactivate

# ========================================
# GLOBAL CLI TOOLS (Use pipx)
# ========================================

# Install CLI tools globally with pipx
pipx install black              # Code formatter
pipx install pytest            # Testing framework
pipx install ruff              # Linter
pipx install httpie            # HTTP client

# List installed pipx tools
pipx list

# Upgrade a tool
pipx upgrade black

# Uninstall a tool
pipx uninstall black

# ========================================
# RUNNING PYTHON SCRIPTS
# ========================================

# Inside virtual environment
python script.py
python3 script.py

# Using uv to run with automatic dependency management
uv run script.py
```

---

## 📝 Important Notes for VSCode Copilot

### Architecture Awareness
- **Current session architecture**: Check with `arch` command
- **VSCode Copilot may run as**: x86_64 (Rosetta 2) or arm64 (native)
- **When it matters**: Compilation, builds, architecture-specific binaries
- **When to check**: Run `arch` before architecture-sensitive operations

### Shell Behavior
- **Interactive shell**: Uses ~/.zshrc with Oh My Zsh, aliases work
- **VSCode Copilot bash**: Non-interactive, aliases DON'T work, use actual commands
- **Script execution**: Bash scripts run in bash (not zsh), no Oh My Zsh features

### Python Environment (CRITICAL)
⚠️ **Homebrew Python Restrictions - READ THIS BEFORE ANY Python work**:
- Python 3.14 installed via Homebrew enforces PEP 668 (externally-managed-environment)
- **NEVER suggest `pip install package` without a virtual environment** - it WILL FAIL
- **ALWAYS create/activate virtual environment first**: `uv venv && source .venv/bin/activate`
- **For global CLI tools ONLY**: Use `pipx install tool-name`
- **Project dependencies**: Always in virtual environment (uv venv or python -m venv)
- **Quick test scripts**: Use `uv run script.py` for automatic dependency management

**Decision Tree for Python Package Installation**:
1. Is it a CLI tool (black, pytest, ruff)? → Use `pipx install`
2. Is it a project dependency? → Create venv first, then `uv pip install`
3. Is it a quick script? → Use `uv run` or create temporary venv

### File System Conventions
- **Case Sensitivity**: macOS is case-insensitive by default (but case-preserving)
- **Hidden Files**: Files starting with `.` are hidden (e.g., `.env`, `.zshrc`)
- **Home Directory**: `/Users/stevenims` or `~`
- **Homebrew Bins**: `/opt/homebrew/bin` (should be in PATH)

---

## 🔄 Maintenance

**Last Updated**: 2025-11-04 (Updated all tool versions, added kubectl, confirmed system specs)
**Update Frequency**: Recommended to refresh when major tools/versions change

To update this file with latest environment state, run:
```bash
# Check versions
node --version
python3 --version
brew --version
docker --version

# Check Oh My Zsh updates
omz update

# Check for new aliases
grep "^alias" ~/.zshrc ~/.oh-my-zsh/custom/*.zsh
```

---

*This file provides context for VSCode Copilot to understand your development environment. It should be updated when your setup changes significantly.*
