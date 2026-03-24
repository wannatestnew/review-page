# KDCO OpenCode Workspace - Complete User Guide

## 🎯 What This Workspace Does

The KDCO OpenCode workspace helps you **automatically break down complex coding tasks into smaller, manageable subtasks** using specialized AI agents that work together intelligently.

Instead of wrestling with one big problem, you get:
- 🔍 **Research Agent**: Finds information and best practices
- 🗺️ **Explorer Agent**: Examines your existing codebase
- 💻 **Coder Agent**: Writes and modifies code
- 📝 **Scribe Agent**: Creates documentation
- 👀 **Reviewer Agent**: Checks code quality and security
- 🎯 **Plan/Build Orchestrators**: Manage the workflow and decomposition

Think of it like having a team of specialists who automatically organize themselves to tackle your complex programming challenges.

---

## 📋 Prerequisites

Before installing the workspace, make sure you have:

1. **OpenCode** installed (the AI coding agent)
   ```bash
   # Install via Homebrew (recommended)
   brew install anomalyco/tap/opencode
   
   # Or via npm
   npm i -g opencode-ai@latest
   ```

2. **OCX** (OpenCode Extension Manager) - This manages the workspace bundle
   *We'll install this in the setup steps below*

---

## 🚀 Installation Guide

The installation is a **one-time setup process**. Once completed, you can use the workspace from any project.

### Step 1: Install OCX (OpenCode Extension Manager)

OCX is required to manage the KDCO workspace bundle:
```bash
# Recommended: Using the official install script
curl -fsSL https://kcoc.tech/install | bash

# Alternative: Manual installation
# git clone https://github.com/kdcokenny/ocx.git
# cd ocx
# make install  # or follow their specific instructions
```

**What this does**: Installs the OCX CLI tool globally on your system, which manages OpenCode extensions and bundles.

### Step 2: Initialize OCX Globally

This prepares OCX to manage extensions for all your projects:
```bash
ocx init --global
```

**What this does**: 
- Creates OCX configuration in your home directory (`~/.ocx`)
- Sets up the global extension registry
- Prepares OCX to work across all your projects
- **You only need to run this once**

### Step 3: Install the KDCO Workspace Profile

Now install the actual workspace bundle:
```bash
ocx profile add ws --source tweak/p-1vp4xoqv --from https://tweakoc.com/r --global
```

**Breaking down this command**:
- `ocx profile add`: Tells OCX we're adding a new profile
- `ws`: The name we're giving this profile ("ws" for workspace)
- `--source tweak/p-1vp4xoqv`: Specific version/configuration from TweakOC
- `--from https://tweakoc.com/r`: Download source (the TweakOC registry)
- `--global`: Makes this available to all projects (not just one folder)

**What this does**: Downloads and installs the complete KDCO workspace bundle including all agents, plugins, skills, and configurations.

### Step 4: Verify Installation (Optional but Recommended)

Confirm everything is installed correctly:
```bash
ocx profile list
# You should see "ws" listed among your profiles
```

---

## 💻 Using the Workspace

Once installed, using the workspace is simple:

### From Any Project Directory:
```bash
# Navigate to your project
cd /path/to/your/project

# Launch OpenCode with the KDCO workspace
ocx oc -p ws
```

**What happens**:
- `ocx oc`: Launches OpenCode through the OCX extension manager
- `-p ws`: Uses the "ws" profile we installed (the KDCO workspace)
- OpenCode starts with all workspace components loaded and ready

You'll see the OpenCode interface where you can describe your complex task.

### Example Usage:
In the OpenCode interface, simply type:
> "Create a REST API for managing blog posts with CRUD operations including user authentication, validation, and database integration"

The workspace will automatically:
1. Analyze your request using the plan orchestrator
2. Break it down into logical subtasks (research, exploration, coding, review, etc.)
3. Delegate each subtask to the appropriate specialist agent
4. Execute the agents in the right order (handling dependencies)
5. Integrate results and verify completion

### Detailed Example Interaction:
Here's what you might see when you run a complex task:

**You type:** "Create a REST API for managing blog posts with CRUD operations including user authentication, validation, and database integration"

**Plan Orchestrator (thinking):** Analyzing request... Breaking down into subtasks: researching REST API best practices, exploring existing codebase patterns, implementing endpoints, documenting API, reviewing security, and building integration tests.

**[Agent Status: Researcher Active]**
Researcher: Searching for REST API design patterns using Context7 and Exa tools...
Researcher: Found 5 relevant resources on REST API design, JWT authentication, and input validation best practices.
Researcher: Summary: Use resource-based endpoints, stateless authentication, proper HTTP status codes, and comprehensive input validation.

**[Agent Status: Explorer Active]**
Explorer: Examining project structure for existing API patterns...
Explorer: Found Express.js server in /src/server.js with basic middleware setup.
Explorer: No existing REST API endpoints found - will need to create from scratch.

**[Agent Status: Coder Active]**
Coder: Creating REST API based on research findings...
Coder: Created /src/routes/posts.js with GET/POST/PUT/DELETE endpoints for /posts
Coder: Implemented JWT authentication middleware in /src/middleware/auth.js
Coder: Added input validation using Joi library in /src/validation/posts.js
Coder: Connected to MongoDB using Mongoose in /src/config/database.js

**[Agent Status: Scribe Active]**
Scribe: Creating API documentation...
Scribe: Generated POSTMAN collection and Swagger docs in /docs/api/
Scribe: Added usage examples for all endpoints with authentication headers

**[Agent Status: Reviewer Active]**
Reviewer: Conducting security audit...
Reviewer: Found potential SQL injection risk in query parameters - recommending parameterized queries
Reviewer: Noted missing rate limiting on auth endpoints
Reviewer: Suggested adding helmet.js middleware for additional security

**[Agent Status: Coder Active (again)]**
Coder: Addressing reviewer feedback...
Coder: Fixed SQL injection by using parameterized queries in database operations
Coder: Added rate limiting middleware to auth endpoints
Coder: Integrated helmet.js for enhanced security headers

**[Agent Status: Build Orchestrator Active]**
Build: Running integration tests...
Build: All endpoints returning correct status codes and data formats
Build: Authentication flow verified with valid/invalid tokens
Build: Validation working correctly for malformed inputs
Build: Task completed successfully!

---

### Monitoring Agent Status and Progress

While the workspace is working on your task, you can monitor what's happening in several ways:

#### 1. Agent Status Indicators
The OpenCode interface shows which specialist agent is currently active:
- Look for labels like **[Agent Status: Researcher Active]** in the output
- The interface typically highlights the currently working agent
- You'll see transitions between agents as they complete their subtasks

#### 2. Activity Logs
Each agent logs what it's doing:
- **Researcher**: Shows what it's searching for and what it found
- **Explorer**: Displays what files/code it's examining
- **Coder**: Lists files being created/modified and commands being run
- **Scribe**: Shows documentation being generated
- **Reviewer**: Displays issues found and recommendations
- **Build**: Shows test execution and verification results

#### 3. File Changes
Watch for:
- New files appearing in your project directory
- Existing files being modified (usually indicated in the coder agent's output)
- Documentation files appearing in docs/ or similar directories

#### 4. Command Execution
Only the **Coder agent** has bash access, so you'll see:
- Terminal commands being executed (like npm install, file creation, etc.)
- Build and test commands running
- Development server starts/stops (if applicable)

#### 5. Progress Indicators
Look for phrases like:
- "Searching for..." / "Found..." (Researcher)
- "Examining..." / "Found..." (Explorer)
- "Creating..." / "Implemented..." / "Fixed..." (Coder)
- "Generating..." / "Created..." (Scribe)
- "Checking..." / "Found..." / "Recommending..." (Reviewer)
- "Running..." / "Verifying..." / "Completed" (Build)

#### 6. Handling Dependencies
You'll observe the workflow respecting dependencies:
- Researcher finishes before Coder starts (need info to code)
- Explorer may run concurrently with Researcher
- Reviewer runs after Coder has done initial implementation
- Coder may return after Reviewer feedback to fix issues
- Build runs last to verify everything works together

#### 7. If Agents Appear Stuck
If you notice no progress for an extended period:
- Check if they're waiting for a dependency (e.g., Coder waiting for Research)
- Consider if the task needs clarification or human input
- You can provide additional guidance in your next message
- Consider breaking the task into smaller phases if it's extremely large

### Example Status Transition Flow:
```
[Agent Status: Researcher Active] → [Agent Status: Explorer Active] 
→ [Agent Status: Coder Active] → [Agent Status: Scribe Active] 
→ [Agent Status: Reviewer Active] → [Agent Status: Coder Active (again)] 
→ [Agent Status: Build Orchestrator Active] → Task Complete
```

This visibility helps you understand what's happening behind the scenes and confirms that the workspace is systematically working through your complex task rather than appearing to be stuck or unresponsive.

---

## 🔧 How Task Decomposition Works (Behind the Scenes)

When you give the workspace a complex task, here's what happens internally:

```
You: "Build a user authentication system"
        ↓
[Plan Orchestrator] 
  → Analyzes task using proven guidelines
  → Decomposes into: Research, Explore, Code, Document, Review, Build
        ↓
Delegates to Specialists:
  → [Researcher]: Finds auth best practices, security standards
  → [Explorer]: Examines existing auth patterns in your code
  → [Coder]: Implements login/register, token handling, etc.
  → [Scribe]: Creates API docs and usage guides
  → [Reviewer]: Checks for security issues and code quality
  → [Build]: Integrates everything and runs verification tests
        ↓
Results: Working authentication system with documentation
```

The system automatically handles:
- **Dependencies**: Waits for research to finish before coding
- **Parallelization**: Runs independent tasks simultaneously when possible
- **Expertise Matching**: Assigns tasks to agents with the right skills

---

## ⚙️ Agent Permissions & Security

Each agent type operates with specific boundaries for safety:

| Agent | File Access | Bash Access | Network | Purpose |
|-------|-------------|-------------|---------|---------|
| **plan** | Read-only | None | Denied | Task analysis & decomposition only |
| **build** | Read-only | None | Denied | Integration & verification only |
| **explore** | Read-only | None | Denied | Codebase inspection |
| **researcher** | Read-only | None | Denied* | MCP tools only (Context7, Exa) |
| **scribe** | Write-only | None | Denied | Documentation creation |
| **reviewer** | Read-only | None | Denied* | Git inspection + read-only |
| **coder** | Full | Full | Denied | Implementation & command execution |

\* Researcher and reviewer have limited network access only through approved MCP tools (Context7 for docs, Exa for search, etc.)

This security model ensures agents can only do what they're supposed to do—no agent can unexpectedly modify your system or access unauthorized resources.

---

## 🎯 Advanced Usage Tips

### Guiding Task Decomposition
You can influence how tasks are broken down by using specific language:
- **"Research and analyze..."** → Emphasizes the researcher agent
- **"Build/create/implement..."** → Emphasizes the coder agent  
- **"Refactor/clean/optimize..."** → Involves multiple agents for improvement
- **"Test/verify/check..."** → Emphasizes the reviewer agent

### Monitoring Progress
While agents work, you can observe:
- Which specialist is currently active (shown in the interface)
- Status of delegated subtasks
- Files being modified or created
- Command execution (visible only for the coder agent)

### Customizing the Workspace
Since this is pulled from a repository, you can personalize it:
1. Fork the workspace repository
2. Modify agents, skills, or plugins to suit your needs
3. Update your OCX profile to point to your fork
4. Maintain your own customized version

### Customizing Agent Models (Project-Specific)

You can specify which models different agents use by creating a project-specific override. This is the **recommended approach** as it only affects your current project and doesn't modify global or workspace settings.

#### Configuration Hierarchy
OpenCode configurations are applied in this order (later overrides earlier):
1. Built-in defaults
2. Global config (`~/.config/opencode/opencode.json`)
3. Profile config (from KDCO workspace via OCX)
4. **Project config** (`./.opencode/opencode.jsonc` - highest priority)

#### How to Override Models (Project-Only)
Create or edit `.opencode/opencode.jsonc` in your **project directory** (not global):

```jsonc
{
  "agent": {
    "coder": {
      "model": "opencode/gpt-5",
      "temperature": 0.3
    },
    "plan": {
      "model": "opencode/gpt-5-chat",
      "temperature": 0.1
    }
  }
}
```

#### Important Notes About Project Overrides

- ✅ **Only change the project-scoped file** (`./.opencode/opencode.jsonc`) - no need to modify global or workspace configs
- ❌ Do NOT edit `~/.config/opencode/opencode.json` for project-specific changes
- ❌ Do NOT modify the workspace profile files in the OCX installation
- Only specify agents you want to customize; others use workspace profile defaults
- You can also adjust `temperature`, `reasoningEffort`, and `textVerbosity` per agent
- Changes take effect in new OpenCode sessions (you must restart after editing)
- The coder agent often benefits from more capable models since it handles file modifications and command execution

#### Available Models

While specific models may vary by OpenCode installation, common options include:
- `opencode/big-pickle` (default for complex reasoning tasks)
- `opencode/gpt-5` (balanced performance)
- `opencode/gpt-5-nano` (faster, lower cost)
- `opencode/gpt-5-chat` (optimized for conversational tasks)

---

## 🐛 Troubleshooting

### Common Issues & Solutions

**Problem**: Task not decomposing as expected
**Solution**: 
- Be more specific about what you want accomplished
- Mention any known constraints or requirements
- Break extremely large requests into phases

**Problem**: Agents appear stuck
**Solution**:
- Check if they're waiting for dependencies
- Consider if the task needs human input or clarification
- Break the task down further manually if needed

**Problem**: Permission errors
**Solution**:
- Remember agents operate within strict security boundaries
- The coder agent has the most privileges for implementation work
- If you need broader access, you may need to adjust permissions (advanced)

---

## ✅ Best Practices

1. **Start Clear**: Begin with a well-defined end goal
2. **Be Specific**: Include constraints, technologies, and desired outcomes
3. **Iterate**: Use output from one session to inform the next
4. **Trust Specialists**: Each agent type knows its domain—let them work
5. **Review Output**: Always check the work of specialist agents
6. **Chain Tasks**: Use completed work as input for subsequent complex tasks

---

## 📚 Example Session Flow

Here's what a complete session looks like:

```
User: "Create a REST API for managing blog posts with CRUD operations"

[Plan Orchestrator] → Decomposes into: Research, Explore, Code, Document, Review, Build

[Researcher] → Studies REST API design, auth methods, error standards
[Explorer] → Examines current project structure and API patterns
[Coder] → Implements endpoints: GET/POST/PUT/DELETE /posts with validation
[Scribe] → Creates API docs with examples and error codes
[Reviewer] → Checks for SQL injection, auth bypass, input validation
[Coder] → Addresses reviewer feedback
[Build] → Runs integration tests, verifies all endpoints work
→ Task Complete!
```

---

## ⚠️ Limitations

- Task decomposition quality depends on the clarity of your initial request
- Extremely vague or ambiguous tasks may not decompose effectively
- Some creative or design-oriented tasks may require more human guidance
- The system is optimized for technical implementation tasks

---

## ❓ Getting Help

If you encounter issues:
1. Check the agent logs to see what each specialist is doing
2. Try rephrasing your task with more specific technical details
3. Consider breaking your request into smaller chunks manually
4. You can always guide the process with follow-up requests

---

## 🔗 Resources

- OpenCode Documentation: https://opencode.ai/docs
- OCX Repository: https://github.com/kdcokenny/ocx
- KDCO Workspace Source: https://github.com/kdcokenny/opencode-workspace
- TweakOC Registry: https://tweakoc.com

---

*This workspace is designed specifically to help you tackle complex tasks by leveraging AI agents that specialize in different aspects of software development, all working together under intelligent orchestration.*