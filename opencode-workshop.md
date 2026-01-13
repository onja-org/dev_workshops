# OpenCode 1-Hour Workshop: AI-Powered Terminal Development

**Target Audience:** Intermediate Developers  
**Focus:** Project-Agnostic Development with OpenCode  
**Setup:** Provided Laptops with Linux Environment  
**AI Provider:** OpenCode Free Model (Big Pickle)

---

## Prerequisites & Pre-Session Setup

**Complete this section BEFORE the workshop begins.** This ensures we can maximize hands-on time during the session.

### System Requirements
- Linux laptop with internet access
- Modern terminal emulator (WezTerm, Alacritty, or GNOME Terminal recommended)
- Git installed

### Step 1: Install System Dependencies (5 minutes)

```bash
# Update package manager
sudo apt update && sudo apt upgrade -y

# Install essential development tools
sudo apt install -y curl git nodejs npm build-essential

# Install clipboard support (CRITICAL for copy/paste in terminal)
# For X11 systems (most Linux desktops)
sudo apt install -y xclip

# For Wayland systems (newer desktop environments)
sudo apt install -y wl-clipboard

# Verify clipboard support
echo "test clipboard" | xclip -selection clipboard
# or for Wayland:
echo "test clipboard" | wl-copy
```

**Why these matter:**
- `xclip`/`wl-clipboard`: Essential for OpenCode's copy/paste functionality
- `nodejs`/`npm`: Alternative installation method for OpenCode
- `build-essential`: Required for potential native module compilation

### Step 2: Install OpenCode (3 minutes)

**Method 1: Official Install Script (Recommended)**
```bash
curl -fsSL https://opencode.ai/install | bash
```

**Method 2: NPM (Alternative)**
```bash
npm install -g opencode-ai
```

**Verify Installation:**
```bash
opencode --version
# Should output version information
```

### Step 3: (not required) Configure OpenCode Free Model (5 minutes)

```bash
# Create workspace directory
mkdir -p ~/workspace/webapp-workshop
cd ~/workspace/webapp-workshop

# Start OpenCode
opencode
```

**In OpenCode TUI:**
1. Type `/connect` and press Enter
2. Select "opencode" from the provider list
3. Choose the **free model option** (Big Pickle - no account required)
4. Test with a simple question like "Hello, can you help me create a todo app?"

**Exit OpenCode** with `Ctrl+D` or type `/exit`

---

## Session Overview

- **0:00-0:20 (20 min):** AI Agents & Terminal-Based Development Fundamentals
- **0:20-0:30 (10 min):** OpenCode Core Features & Context Management
- **0:30-1:00 (30 min):** Open Project Workshop with OpenCode

---

## Part 1: AI Agents & Terminal Development (20 minutes)

### Welcome & Workshop Goals
- Quick introductions
- What we'll accomplish today
- Why terminal-based AI development matters in 2025

### The Spectrum of AI Coding Assistance - Degrees of Freedom

**Understanding AI coding assistance as a spectrum of autonomy:**

#### Level 1: Tightly Controlled (Autocomplete)
- **Examples:** GitHub Copilot, Tabnine, IDE IntelliSense
- **Freedom:** Character/word level suggestions
- **Control:** Maximum human control, AI suggests only
- **Use case:** Speeding up routine typing, maintaining flow
- **Limitation:** Can't architect, only completes patterns

#### Level 2: Line/Block Assistance (Conversational Coding)
- **Examples:** ChatGPT, Claude in chat interfaces
- **Freedom:** Line or function block suggestions
- **Control:** Human prompts, AI responds with code snippets
- **Use case:** Explaining concepts, writing specific functions
- **Limitation:** No project context, stateless conversations

#### Level 3: Tool-Specific Workflows (Specialized AI)
- **Examples:** AI testing tools, debugging assistants, code reviewers
- **Freedom:** Domain-specific problem solving
- **Control:** Human defines problem scope, AI solves within domain
- **Use case:** Automated testing, performance optimization
- **Limitation:** Siloed functionality, limited cross-tool integration

#### Level 4: Agent-Based Development (OpenCode's Approach)
- **Examples:** OpenCode, Cursor, Aider
- **Freedom:** Project-aware, multi-tool, stateful assistance
- **Control:** Human directs strategy, AI handles implementation details
- **Use case:** Feature development, refactoring, architectural decisions
- **Advantage:** Context awareness, tool orchestration, conversation memory

#### Level 5: Full Autonomy ("Ralph Wiggum Style")
- **Named after:** Ralph Wiggum's "I'm a helper" approach - enthusiastic but needs guidance
- **Freedom:** Agent makes most implementation decisions
- **Control:** Human provides high-level goals, minimal specific guidance
- **Use case:** Rapid prototyping, boilerplate generation, learning exploration
- **Risk:** Can produce unexpected results without proper constraints

**Where OpenCode Excels:**
- **Levels 3-4:** Agent-based with tool orchestration
- **Configurable autonomy:** Switch between Plan mode (Level 2) and Build mode (Level 4)
- **Context persistence:** Remembers project structure across conversations
- **Multi-tool integration:** File operations, search, git, LSP understanding

### Terminal vs IDE Development in 2025

**Why Terminal-Based Development is Resurgent:**
- **Performance:** Faster startup, lower resource usage
- **Remote work:** Native SSH workflow, no GUI forwarding needed
- **Keyboard-first:** Faster for experienced developers
- **AI integration:** Terminal is natural interface for AI agents
- **Collaboration:** Easy to share sessions and screen recordings

**When to Choose Each Approach:**
- **Terminal:** Quick tasks, scripting, remote development, AI-assisted coding
- **IDE:** Complex debugging, visual design tools, large codebase navigation

**OpenCode's Terminal-First Philosophy:**
- Designed for terminal interaction patterns
- Keyboard-driven workflow
- Integrates with existing terminal tools
- Shareable session links for collaboration

---

## Part 2: OpenCode Core Features & Context Management (10 minutes)

### Essential Commands & Navigation

**Core Commands You'll Use Daily:**
```bash
opencode                    # Start OpenCode in current directory
/connect                    # Configure AI provider
/init                       # Analyze project and create AGENTS.md
@filename                   # Reference specific files
<TAB>                       # Switch between Plan and Build modes
/undo                       # Undo last changes
/redo                       # Redo undone changes
/share                      # Create shareable session link
```

**Navigation & Context:**
- `@` symbol for file references (fuzzy search)
- Plan mode (bottom-right indicator) - planning only
- Build mode - actual implementation
- Context awareness across entire project

### 0:25-0:30: Context Management with AGENTS.md

**What is AGENTS.md?**
- Project-specific instruction file for OpenCode
- Guides AI behavior and coding patterns
- Automatically created by `/init` command
- Should be committed to Git for team consistency

**AGENTS.md Structure (Basic to Intermediate):**

```markdown
# Project Instructions

## Project Overview
This is a [project type] project using [technologies].

## Coding Standards
- Use [language] version [version]
- Follow [style guide] conventions
- Prefer [patterns] over [alternatives]

## File Organization
- [directory] contains [purpose]
- [directory] contains [purpose]

## Development Workflow
- Run [command] to start development
- Run [command] for testing
- Run [command] for building

## Important Notes
- [specific project considerations]
- [integration requirements]
```

**Web Development Example (Applicable to Most Projects):**
```markdown
# Web Development Project

## Project Overview
Modern web application using HTML5, CSS3, and JavaScript/TypeScript.

## Coding Standards
- Use semantic HTML5 elements
- Follow responsive design principles
- Implement proper accessibility (ARIA labels, keyboard navigation)
- Use modern JavaScript features (ES6+)
- Write clean, commented code

## File Organization
- `/src` contains source code
- `/assets` contains static resources
- `/tests` contains test files
- `index.html` is the main entry point

## Development Workflow
- Open `index.html` in browser for testing
- Use browser developer tools for debugging
- Test on multiple screen sizes

## Important Notes
- Ensure cross-browser compatibility
- Optimize for performance and accessibility
- Use semantic markup for SEO
```

**Context Levels:**
1. **Global AGENTS.md** - Your general coding preferences
2. **Project AGENTS.md** - Repository-specific rules and patterns
3. **Session Instructions** - Temporary guidance for current work

---

## Part 3: Open Project Workshop (30 minutes)

### 0:30-0:35: Project Selection & Setup

**Choose Your Project:**
- Bring any project you want to work on
- Web app, CLI tool, API, data processing, etc.
- Existing project or start something new
- Focus on applying OpenCode to real work

**Setup Steps:**
```bash
# Navigate to your project directory
cd /path/to/your/project

# Start OpenCode
opencode

# Initialize project context (if not already done)
/init

# Review/update AGENTS.md if needed
```

### 0:35-1:00: Guided Project Work

**Suggested Activities:**
- **Feature Development:** Add new functionality using Plan → Build workflow
- **Bug Fixing:** Debug issues with context-aware assistance
- **Code Refactoring:** Improve organization and maintainability
- **Documentation:** Generate or update project docs
- **Testing:** Add tests with AI guidance
- **Learning:** Explore unfamiliar codebases with AI explanations

**Best Practices During Workshop:**
- Use Plan mode for complex changes
- Reference specific files with `@` symbol
- Leverage `/undo` when experiments don't work
- Share interesting discoveries with the group
- Focus on learning OpenCode patterns, not just getting results

### 1:00: Workshop Wrap-up

**Key Takeaways:**
- OpenCode adapts to any project type
- Context management (AGENTS.md) guides AI behavior
- Plan vs Build modes provide control vs autonomy balance
- Terminal-based workflow is fast and shareable

**Next Steps:**
- Apply OpenCode to your daily development
- Experiment with different autonomy levels
- Join Discord community for continued learning
- Share your sessions and learn from others

---

## Learning Outcomes Assessment

**By the end of this session, you should be able to:**

✅ **Explain** the spectrum of AI coding assistance and where OpenCode fits.

✅ **Compare** terminal vs IDE development workflows and their trade-offs.

✅ **Install** and **configure** OpenCode on Linux with proper dependencies.

✅ **Use** essential OpenCode commands (`/init`, `@`, `/undo`, `/share`).

✅ **Switch** between Plan mode (controlled) and Build mode (autonomous).

✅ **Navigate** codebases using file references (@ symbol) and context awareness.

✅ **Create** and **modify** AGENTS.md files for project guidance.

✅ **Apply** OpenCode to any project type (web, CLI, API, etc.).

✅ **Debug** and **iterate** on code using `/undo` and conversational refinement.

✅ **Share** sessions for collaboration and code review.

---

## Post-Workshop Practice Exercises

**To reinforce your learning, try these exercises on your own projects:**

1. **Context Setup:** Run `/init` on an existing project and review the generated AGENTS.md
2. **Plan Mode Practice:** Use Plan mode to design a new feature before implementing
3. **File Navigation:** Practice using `@` symbol to reference specific files in your codebase
4. **Iterative Development:** Make changes, use `/undo` to experiment, then refine your approach
5. **Cross-Project Application:** Try OpenCode on different types of projects (web, backend, scripts)
