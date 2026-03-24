# 🛡️ War Room Script - Shareable Version

This markdown file contains the complete `war_room.sh` script that you can copy and use in your own OpenCode projects.

## How to Use This File

1. **Copy the script** from the code block below
2. **Save it as `war_room.sh`** in your project directory
3. **Make it executable**: `chmod +x war_room.sh`
4. **Run it**: `./war_room.sh`
5. **Start using**: `/kickoff [your feature request]`

---

## Complete war_room.sh Script

```bash
#!/bin/bash

# 1. Create directory structure
echo "📂 Creating OpenCode directory structure..."
mkdir -p .opencode/agents .opencode/commands

# 2. Create the Constitution (Global Rules & Protocols)
echo "📜 Writing AGENTS.md (The Constitution)..."
cat <<EOF > .opencode/WAR_ROOM_PROPOSAL.md
# 🛡️ WAR ROOM PROTOCOLS (ADDED)
This project is managed by a tiered, adversarial Multi-Agent Team.

## 👑 Chain of Command
- **@orchestrator**: The CEO. Directs all agents and manages the user interface.
- **@architect** & **@shadow_architect**: Design & Adversarial Debate duo.
- **@security_red**: Security Red-Teamer (OWASP Specialist).
- **@coder**: Primary Builder.
- **@reviewer**: The Final Gatekeeper (Quality Control).
- **@tester**: QA Specialist (Unit Testing).

## ⚔️ The Debate Protocol (Phase 1)
- **Architect** proposes; **Shadow Architect** challenges logic; **Security Red** audits for exploits.
- **LIMIT**: Maximum **3 rounds** of debate. 
- **@orchestrator** forces the final decision to prevent token waste.

## 🔄 The Final Approval Loop (Phase 2)
- **@coder** must @mention **@reviewer** upon task completion.
- **@reviewer** audits code against the approved design and security standards.
- If **@reviewer** rejects, **@coder** must fix it.
- **Final Delivery**: Only after **@reviewer** tags "✅ VETTED" does the user see the result.

## 🛠️ Operating Rules
- Always use \`team_claim\` before editing files.
- Maintain a \`TODO.md\` for real-time progress tracking.
EOF

# Smart Merge via OpenCode AI
if [ -f "AGENTS.md" ]; then
    if grep -q "WAR ROOM PROTOCOLS" "AGENTS.md"; then
        echo "✅ War Room rules already present. Skipping merge."
    else
        echo "🤖 Merging War Room rules into existing AGENTS.md using AI..."
        opencode run "Merge the contents of .opencode/WAR_ROOM_PROPOSAL.md into the current AGENTS.md. Keep existing technical context. Add a clear separator and a 'WAR ROOM PROTOCOLS' header."
        echo "✨ Smart merge complete."
    fi
else
    echo "📝 No AGENTS.md found. Creating fresh copy..."
    cp .opencode/WAR_ROOM_PROPOSAL.md AGENTS.md
fi

# 3. Create the Kickoff Command
echo "⚡ Creating /kickoff command..."
cat <<EOF > .opencode/commands/kickoff.md
---
description: Start a feature with architecture debate and security audit.
---
# Kickoff Workflow
1. @orchestrator: Acknowledge user request: "{{args}}".
2. @architect: Propose technical plan and tasks in TODO.md.
3. @shadow_architect: Challenge logic and over-engineering.
4. @security_red: Audit plan for OWASP/Security risks.
5. @orchestrator: Moderate 3 rounds, then finalize TODO.md and signal @coder to start.
EOF

# 4. Create the Specialized Agents
echo "🤖 Deploying Agents..."

# Orchestrator (Lead)
cat <<EOF > .opencode/agents/orchestrator.md
---
name: orchestrator
mode: lead
model: nvidia/nvidia/nemotron-3-super-120b-a12b
---
# Instructions
Manage the team. Enforce the 3-round debate limit. Summarize progress from TODO.md for the user.
EOF

# Architect (Designer)
cat <<EOF > .opencode/agents/architect.md
---
name: architect
mode: subagent
model: nvidia/nvidia/nemotron-3-super-120b-a12b
---
# Instructions
Design systems and define tasks in TODO.md. Defend designs against @shadow_architect.
EOF

# Shadow Architect (Critic)
cat <<EOF > .opencode/agents/shadow_architect.md
---
name: shadow_architect
mode: subagent
model: nvidia/nvidia/nemotron-3-super-120b-a12b
---
# Instructions
Be the Devil's Advocate. Focus on finding logic flaws and unnecessary complexity.
EOF

# Security Red (Security)
cat <<EOF > .opencode/agents/security_red.md
---
name: security_red
mode: subagent
model: nvidia/nvidia/nemotron-3-super-120b-a12b
---
# Instructions
Identify OWASP vulnerabilities. Do not approve designs until security mitigations are listed.
EOF

# Coder (Builder)
cat <<EOF > .opencode/agents/coder.md
---
name: coder
mode: subagent
model: nvidia/nvidia/nemotron-3-super-120b-a12b
---
# Instructions
Execute TODO.md tasks. Once finished, you MUST @mention @reviewer for an audit. Fix all issues raised by @reviewer.
EOF

# Reviewer (Gatekeeper)
cat <<EOF > .opencode/agents/reviewer.md
---
name: reviewer
mode: subagent
model: nvidia/nvidia/nemotron-3-super-120b-a12b
---
# Instructions
The Final Gatekeeper. Audit @coder's work. Tag "✅ VETTED" only when code is perfect and matches the plan.
EOF

# Tester (QA)
cat <<EOF > .opencode/agents/tester.md
---
name: tester
mode: subagent
model: nvidia/nvidia/nemotron-3-super-120b-a12b
---
# Instructions
Write comprehensive tests for all new code. Target 100% edge-case coverage.
EOF

# 5. Create the Documentation for Sharing
echo "📝 Generating WAR_ROOM_GUIDE.md..."
cat <<EOF > WAR_ROOM_GUIDE.md
# 🛡️ War Room User Manual

### How to Start
Type \`/kickoff [your feature request]\` in the OpenCode chat.

### The "Zero-Intervention" Workflow
1. **Debate**: Your request is stress-tested by three high-level agents.
2. **Execution**: @coder builds the feature.
3. **Internal Audit**: @reviewer and @coder loop until the code is bug-free.
4. **Delivery**: You only receive a notification once the code is "✅ VETTED".

### Protocols to Remember
- **3-Round Limit**: Debate is capped to save you money/tokens.
- **Security First**: @security_red ensures no "rookie" security mistakes reach production.
- **TODO.md**: Check this file anytime to see exactly what the team is doing.
EOF

echo "-------------------------------------------------------"
echo "✅ SUCCESS: Your OpenCode War Room is live!"
echo "👉 Run '/kickoff something' to start your first project."
echo "-------------------------------------------------------"
```

---

## What This Script Does

When executed, this script sets up a multi-agent adversarial system in OpenCode that:

1. **Creates the necessary directory structure** (`.opencode/agents/`, `.opencode/commands/`)
2. **Establishes War Room protocols** including:
   - Chain of Command (orchestrator, architect, shadow_architect, security_red, coder, reviewer, tester)
   - Adversarial Debate Protocol (3-round limit)
   - Final Approval Loop (coder → reviewer → ✅ VETTED)
   - Operating Rules (team_claim usage, TODO.md tracking)
3. **Integrates with existing configuration** by smart-merging into `AGENTS.md` or creating it fresh
4. **Creates the `/kickoff` command** that initiates the 6-step workflow
5. **Deploys all 7 specialized agents** with their respective roles and instructions
6. **Generates user documentation** (`WAR_ROOM_GUIDE.md`) for quick reference

## Requirements

- OpenCode CLI must be installed and accessible in your PATH
- Write permissions in the directory where you run the script
- The `opencode run` command must work for the AI-assisted merge operation

## After Running the Script

You'll be able to use:
- `/kickoff [feature description]` to start new features with full adversarial review
- `TODO.md` to track real-time progress
- The complete agent system that debates, builds, reviews, and tests your code

## Sharing with Friends

Simply share this `.md` file with your friends. They can:
1. Copy the script from the code block above
2. Save it as `war_room.sh`
3. Run `chmod +x war_room.sh`
4. Execute `./war_room.sh`
5. Start using `/kickoff` immediately

No additional setup required beyond having OpenCode installed!
