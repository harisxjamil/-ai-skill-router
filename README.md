# AI Skill Router

A beginner-friendly, reusable decision skill for **Claude Code** and **Codex**. It helps an agent decide when it needs extra skills, evaluate candidates, use the right available tools, and verify the final result.

**Important:** This is a skill containing instructions. It does not by itself search GitHub, install software, run scripts, grant permissions, or change the underlying AI model. Those actions require tools and permissions available in the environment.

## What's in this repository?

- [`skills/skill-router/SKILL.md`](skills/skill-router/SKILL.md): the master workflow.
- [`skills/skill-router/references/evaluation.md`](skills/skill-router/references/evaluation.md): quality and safety checklist.

## Beginner setup on Windows

**1.** Install and sign into Claude Code (via Claude Desktop) and/or Codex. GitHub access alone is not the same as a local coding-agent installation.

**2.** Install the current Node.js LTS from https://nodejs.org/ . The Skills CLI requires Node.js 22.20 or later. Open Command Prompt and check:

```bat
node -v
npx -v
```

**3.** Install the routing skill into the agent you actually have. Run the appropriate command in **Command Prompt**, not ordinary Claude Chat or ChatGPT chat:

For Claude Code:

```bat
npx skills add https://github.com/harisxjamil/-ai-skill-router --skill skill-router -g -a claude-code
```

For Codex:

```bat
npx skills add https://github.com/harisxjamil/-ai-skill-router --skill skill-router -g -a codex
```

The first run may ask for permission to download the Skills CLI. Review the prompt before proceeding. The `-g` option is a **local, user-level** installation, not a universal cloud-account installation.

**4.** Install the complementary `find-skills` discovery skill, if you want the agent to search the skill ecosystem:

```bat
npx skills add vercel-labs/skills --skill find-skills -g -a claude-code
npx skills add vercel-labs/skills --skill find-skills -g -a codex
```

Only run the line for agents installed on your machine. Confirm the installed skills:

```bat
npx skills list -g
```

**5.** Restart your agent session. Ask it:

> Use the skill-router skill to plan a website for a student society. Check existing tools first. Search for potentially useful design and testing skills if necessary. Show me candidates and risks, but do not install anything else without permission.

## What happens next?

1. The agent understands your goal and checks its tools/skills.
2. It decides whether discovery is worthwhile.
3. It uses available discovery tools to shortlist relevant skills.
4. You approve any new third-party installation or execution.
5. The agent completes the task and checks output quality.

## Claude Chat and ChatGPT Work

You may **read and reuse** the instructions in these environments, if the product can access the repository or you supply the text. This does **not** imply identical support for native skills, terminal commands, automatic installation, or execution. Use each product's supported custom-skill/account tools if available.

## Updates

Changes to this GitHub repository are tracked by Git. An already installed copy of a skill may require an explicit update or reinstall; editing GitHub alone does not guarantee live synchronization across every agent.

## Security and efficiency

- Review third-party skills before installation or execution.
- Never put API keys, passwords, or private data in a public repository.
- Do not load every skill on every task. Use the smallest effective set.
- Compare output quality and total attempts against a baseline before claiming the router saves usage.

Resources: https://agentskills.io/specification and https://github.com/vercel-labs/skills .
