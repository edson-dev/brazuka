# Antigravity Kit Architecture

> Skill-first agent runtime for Trae IDE

---

## 📋 Overview

Antigravity Kit is a skill-driven system where:

- **Skills** define behavior and expertise
- **Rules** enforce global standards
- **ARCHITECTURE.md** documents how to route and apply skills

This document reflects the actual layout in this repo, and this repo is inported on projects to assert skill and proeficiencies of agents.

---

## 🏗️ Repository Layout

```plaintext
.trae/
├── ARCHITECTURE.md      # This file
├── rules/
│   └── GEMINI.md         # Global behavior rules
└── skills/               # Skill library (one folder per skill)
```

---

## ⚙️ Skill-First Runtime

### Core Flow

```plaintext
User Request
→ Intelligent Routing (domain detection)
→ Skill Invocation (Skill tool)
→ Read SKILL.md
→ Apply skill instructions
→ Verify with skill scripts when available
```

### Priority Order

1. Workspace rules (`.trae/rules/GEMINI.md`)
2. Skill instructions (`.trae/skills/<skill>/SKILL.md`)
3. Repository conventions

---

## 🧩 Skill Structure

```plaintext
skills/
└── skill-name/
    ├── SKILL.md       # Required: instructions and triggers
    ├── scripts/       # Optional: validation/automation
    ├── references/    # Optional: templates/docs
    └── assets/        # Optional: images/resources
```

---

## ✅ Verification Scripts

Some skills include scripts under `scripts/`. When a skill specifies verification, run:

```plaintext
python .trae/skills/<skill>/scripts/<script>.py .
```

Use the exact script paths defined by the skill.

---

## 📚 Skills Inventory (235)

This list mirrors the `.trae/skills` folders.

```plaintext
3d-web-experience
ab-test-setup
active-directory-attacks
address-github-comments
agent-evaluation
agent-manager-skill
agent-memory-mcp
agent-memory-systems
agent-tool-builder
ai-agents-architect
ai-product
ai-wrapper-product
algolia-search
algorithmic-art
analytics-tracking
api_specifications
api-documentation-generator
api-fuzzing-bug-bounty
api-patterns
api-security-best-practices
app-builder
app-store-optimization
architecture
autonomous-agent-patterns
autonomous-agents
avalonia-layout-zafiro
avalonia-viewmodels-zafiro
avalonia-zafiro-development
aws-penetration-testing
aws-serverless
azure-functions
backend-dev-guidelines
bash-linux
behavioral-modes
blockrun
brainstorming
brand-guidelines-anthropic
brand-guidelines-community
broken-authentication
browser-automation
browser-extension-builder
bullmq-specialist
bun-development
burp-suite-testing
canvas-design
cc-skill-backend-patterns
cc-skill-clickhouse-io
cc-skill-coding-standards
cc-skill-continuous-learning
cc-skill-frontend-patterns
cc-skill-project-guidelines-example
cc-skill-security-review
cc-skill-strategic-compact
claude-code-guide
claude-d3js-skill
clean-code
clerk-auth
cloud-penetration-testing
code-review-checklist
competitor-alternatives
computer-use-agents
concise-planning
content-creator
context-window-management
conversation-memory
copy-editing
copywriting
core-components
crewai
database-design
deployment-procedures
discord-bot-architect
dispatching-parallel-agents
doc-coauthoring
docker-expert
documentation-templates
docx-official
email-sequence
email-systems
environment-setup-guide
ethical-hacking-methodology
executing-plans
file-organizer
file-path-traversal
file-uploads
finishing-a-development-branch
firebase
form-cro
free-tool-strategy
frontend-design
frontend-dev-guidelines
game-development
gcp-cloud-run
geo-fundamentals
git-pushing
github-workflow-automation
golang-backend
graphql
html-injection-testing
hubspot-integration
i18n-localization
idor-testing
inngest
intelligent-routing
interactive-portfolio
internal-comms-anthropic
internal-comms-community
javascript-mastery
kaizen
langfuse
langgraph
launch-strategy
lint-and-validate
linux-privilege-escalation
linux-shell-scripting
llm-app-patterns
loki-mode
marketing-ideas
marketing-psychology
mcp-builder
metasploit-framework
micro-saas-launcher
mobile-design
moodle-external-api-development
neon-postgres
nestjs-expert
network-101
nextjs-best-practices
nextjs-supabase-auth
nodejs-best-practices
notebooklm
notion-template-business
onboarding-cro
page-cro
paid-ads
parallel-agents
paywall-upgrade-cro
pdf-official
pentest-checklist
pentest-commands
performance-profiling
personal-tool-builder
plaid-fintech
plan-writing
planning-with-files
playwright-skill
popup-cro
postgres-best-practices
powershell-windows
pptx-official
pricing-strategy
prisma-expert
privilege-escalation-methods
product-manager-toolkit
production-code-audit
programmatic-seo
prompt-caching
prompt-engineer
prompt-engineering
prompt-library
python-patterns
rag-engineer
rag-implementation
react-best-practices
react-patterns
react-ui-patterns
receiving-code-review
red-team-tactics
red-team-tools
referral-program
remotion-best-practices
requesting-code-review
research-engineer
salesforce-development
scanning-tools
schema-markup
scroll-experience
segment-cdp
senior-architect
senior-fullstack
seo-audit
seo-fundamentals
server-management
shodan-reconnaissance
shopify-apps
shopify-development
signup-flow-cro
skill-creator
skill-developer
slack-bot-builder
slack-gif-creator
smtp-penetration-testing
social-content
software-architecture
sql-injection-testing
sqlmap-database-pentesting
ssh-penetration-testing
stripe-integration
subagent-driven-development
systematic-debugging
tailwind-patterns
tdd-workflow
telegram-bot-builder
telegram-mini-app
test-driven-development
test-fixing
testing-patterns
theme-factory
top-web-vulnerabilities
trigger-dev
twilio-communications
typescript-expert
ui-ux-pro-max
upstash-qstash
using-git-worktrees
using-superpowers
vercel-deployment
verification-before-completion
viral-generator-builder
voice-agents
voice-ai-development
vulnerability-scanner
web-artifacts-builder
web-design-guidelines
web-performance-optimization
webapp-testing
windows-privilege-escalation
wireshark-analysis
wordpress-penetration-testing
workflow-automation
writing-plans
writing-skills
xlsx-official
xss-html-injection
zapier-make-patterns
```

---

## 🔗 Usage Notes

- Prefer skill invocation over generic answers
- Load `intelligent-routing` to auto-select the best skill
- Use `using-superpowers` at session start to discover skills fast
