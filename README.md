# Claude Code cheat sheet

70 commands and aliases, one short line each. I tested every one of them over more than 2 weeks. Skim it, find what you need, and start using it.

*Last checked: October 2026. Claude Code changes fast, so some names may move.*

## Contents

- [How it works](#how-it-works)
- [Tools and access](#tools-and-access)
- [Set up a project](#set-up-a-project)
- [Keep context healthy](#keep-context-healthy)
- [Plan, review, verify](#plan-review-verify)
- [Work in parallel](#work-in-parallel)
- [Always on](#always-on)
- [Sessions and sharing](#sessions-and-sharing)
- [Troubleshooting](#troubleshooting)
- [Look and feel](#look-and-feel)
- [Artifacts and design](#artifacts-and-design)
- [Work setup](#work-setup)

## How it works

- **Agentic loop:** gather context, reason, act, check: done? If not, loop again. That's what makes agents different from chatbots.
- **Context window:** your session, system prompt, tools and MCP. Everything counts. When it's full, Claude summarises the older conversation. Use `/compact <instruction>` to point it.

## Tools and access

| Command | What it does |
|---|---|
| `/cd` | Move the session to another directory. |
| `/add-dir` | Add more directories to the session, so Claude can work with them directly. |
| `/permissions` | Allow, ask or deny tools. Set bash rules early, for example make `git push` ask first. |

## Set up a project

| Command | What it does |
|---|---|
| `/init` | The first command for every new project. Writes a CLAUDE.md for it. |
| `/memory` | See CLAUDE.md, rules and auto memory. CLAUDE.md files also load from parent folders: in `foo/bar`, both `foo/bar/CLAUDE.md` and `foo/CLAUDE.md` load. |
| `/mcp` | Add and remove MCP servers. Scopes: user, project, local. MCP prompts also work as commands, kept on the server and shareable. |
| `/hooks` | View hooks: actions that run on tool calls, agent calls and other events. |
| `/plugin` | Manage plugins. |
| `/skills` | Show active skills. |
| `/config` | Claude Code settings. |
| `/update-config` | Change settings by describing what you want. |
| `/fewer-permission-prompts` | Scans your transcripts and allowlists common read-only commands. |
| `/import` | Pull config over from Codex, Gemini CLI or Cursor. |
| `/output-style` | Set the reply style: proactive, concise, explanatory, learning. |
| `/statusline` | Customise the line under the input box. Mine shows model, effort, cost and context. |
| `/keybindings` | Customise keyboard shortcuts. Worth it if you live in the terminal. |

## Keep context healthy

| Command | What it does |
|---|---|
| `/context` | See what is filling your context window. I ignored it at the start; now it's my go-to in every session. |
| `/compact` | Summarise the conversation to free space. `/compact <instruction>` tells it what to keep. I always add an instruction. |
| `/autocompact` | Set when automatic compaction kicks in, for example `/autocompact 500k`. |
| `/clear`, `/new`, `/reset` | Start a clean session. |
| `/resume` | Go back to an earlier session. |
| `/rewind` | Roll back to an earlier checkpoint. |
| `/recap` | One-line summary of the session. Handy to hand to another agent. |
| `/status` | Quick overview: session, model, path, MCP, settings sources. |
| `/model`, `/effort` | Switch model and effort. Put them on your statusline so you always see them. |

## Plan, review, verify

| Command | What it does |
|---|---|
| `/plan` | Plan mode: no edits. Claude reads, gathers context and proposes a plan for you to approve. |
| `/diff` | Show the changes made in the current directory. |
| `/code-review` | Review your changes for bugs. |
| `/security-review` | Review your changes for vulnerabilities. |
| `/simplify` | Review changed code for quality, reuse and efficiency. |
| `/verify` | Confirm a change works by running the app, not just the tests. |
| `/run` | Launch and drive your app to see a change working. |
| `/run-skill-generator` | Teach Claude how to run your app, per project. |

## Work in parallel

| Command | What it does |
|---|---|
| `/batch` | Hand over a big task. It plans, splits the work across agents in parallel and handles git so changes don't clash. |
| `/fork` | Copy the conversation into a new background session. The original keeps going, and the copy's file edits go to its own worktree by default. |
| `/branch` | Branch the session to try another direction; go back with `/resume`. Caution: it might change things your main session doesn't know about. A worktree is safer. |
| `/btw` | Side question that sees your full context. No tools, and the answer isn't added to history. |
| `/subtask` | A side task inside your session. The final response goes back to the main agent. |
| `/tasks` | See background agents and switch to one to check progress. |
| `/background`, `/bg` | Send the session to the background and free your terminal. Find it again in `claude agents`. |
| `claude agents` | One view of all your agents and sessions. |
| `claude --worktree <name>` | Start in a git worktree: a separate folder and branch, so edits stay apart. |

## Always on

| Command | What it does |
|---|---|
| `/goal` | Give Claude a condition, not a task. It keeps working until the condition is met. Clear it with `/goal clear`. |
| `/loop [interval] [task]` | Repeat a task on a schedule, for example `/loop 1h check my chat and email and tell me what needs attention`. Runs only while Claude Code is open, and expires after 7 days. Cancel by asking Claude. |
| `/schedule` | Cloud routines that run even with your laptop closed, at most once an hour. |
| `/teleport` | Pull a cloud session into this terminal and continue. |
| `/desktop`, `/app` | Continue the session in the Claude desktop app. |
| `/remote-control` | Control a session running on your machine from your phone. |

## Sessions and sharing

| Command | What it does |
|---|---|
| `/rename` | Name the session so you can find it later. |
| `/export` | Export the session to a file. Good for sharing or notes. |
| `/copy` | Copy the last message. |
| `/exit`, `/quit` | Close Claude Code. |

## Troubleshooting

| Command | What it does |
|---|---|
| `/doctor` | Find and fix problems with your setup. |
| `/debug` | Debug a specific MCP server or setup item. |
| `/skill-doctor` | See how often each skill was used. |

## Look and feel

| Command | What it does |
|---|---|
| `/theme`, `/color` | Colours. |
| `/scroll-speed` | Scrolling speed. |
| `/terminal-setup` | Terminal integration. |
| `/voice` | Dictation. |

## Artifacts and design

| Command | What it does |
|---|---|
| `/artifacts` | List, attach or open artifacts you own or that are shared with you. |
| `/design`, `/design-login`, `/design-sync` | UI mockup canvas. |
| `/slides` | Presentation artifact. |
| `/dataviz` | Chart and dashboard design guidance. |

## Work setup

Folders worth setting up in every project:

- `.claude/rules/` — rules Claude follows; a rule can apply only to certain paths.
- `.claude/skills/` — reusable instructions for tasks you repeat.
- `.claude/agents/` — your own subagents.
- Hooks — commands that run automatically on events, set in your settings (see `/hooks`).

---

Spotted a renamed or missing command? Open an issue or a pull request.
