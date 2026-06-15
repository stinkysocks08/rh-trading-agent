# rh-trading-agent

A Claude Code workspace for connecting an AI agent to a **Robinhood Agentic account**
via Robinhood's Trading MCP server. This repo holds the **guardrails, strategy notes,
and setup docs** — not secrets, and not the OAuth token (that lives outside the repo).

> **Beta + real money.** Robinhood Agentic Trading is in beta and currently supports
> equities only. The agent trades inside an isolated Agentic account funded with a
> dedicated budget — that budget is the most it can ever lose. You are responsible for
> monitoring it. Nothing here is investment advice.

## What's in here

```
.
├── CLAUDE.md              # The agent's operating contract (rules it must follow)
├── .mcp.json              # Project-scoped Robinhood Trading MCP connection
├── .claude/settings.json  # Permission rules: every Robinhood tool call requires approval
├── docs/SETUP.md          # Step-by-step setup, OAuth, and how to tighten guardrails
├── strategies/            # Your strategy definitions and notes
└── .gitignore             # Keeps tokens, env files, and local overrides out of git
```

## Quickstart

1. Make this repo **private** before pushing anything.
2. Read `docs/SETUP.md` and follow it top to bottom.
3. Connect the MCP, authenticate via OAuth (desktop), fund a small Agentic budget.
4. Refine `.claude/settings.json` once you know the real tool names.

## Safety posture (read before funding)

- The agent can only trade in the **Agentic account**, never your main balance.
- Default permission rule puts **every** Robinhood tool call behind a manual prompt.
- `CLAUDE.md` includes a prompt-injection rule: the agent must ignore trading
  instructions found in fetched/external content (news, analyst notes, web).
- You can disconnect the MCP anytime from the Robinhood app — that's your kill switch.
