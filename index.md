---
layout: default
title: LocalPibox
---

# LocalPibox

**A personal AI devstack built on Pi.dev** — a containerized Pi coding agent
paired with a **local** Lemonade/Qwen LLM, MCP servers, and a curated set of
forked extensions. Local, private, reproducible, forkable.

## The stack

| Repo | What it is | Tracked upstream |
|---|---|---|
| [`devstack`](https://github.com/localpibox/devstack) | container image + `lpb` launcher, CI, bootstrap | own |
| [`pi`](https://github.com/localpibox/pi) | Pi monorepo fork: Qwen reasoning, overflow fixes | [`earendil-works/pi`](https://github.com/earendil-works/pi) |
| [`config`](https://github.com/localpibox/config) | preset: settings, MCP servers, skills, agents | own |
| [`lemonade-pi-plugin`](https://github.com/localpibox/lemonade-pi-plugin) | Lemonade provider: Qwen thinking + vision | [`lemonade-sdk`](https://github.com/lemonade-sdk/lemonade-pi-plugin) |
| [`pi-subagents`](https://github.com/localpibox/pi-subagents) | centralized subagent model registry | [`tintinweb/pi-subagents`](https://github.com/tintinweb/pi-subagents) |
| [`lpb-memory`](https://github.com/localpibox/lpb-memory) | persistent memory extension | independent |

## Quick start

```bash
curl -fsSL https://raw.githubusercontent.com/localpibox/devstack/main/scripts/install.sh | bash
lpb /path/to/project
```

`lpb` boots the container, starts the local Lemonade/Qwen backend, and opens a
Pi CLI session in your project.

## Architecture

```
Your shell → lpb → container
                    ├─ Pi CLI (custom fork: Qwen reasoning)
                    ├─ Lemonade provider (local Qwen LLM)
                    ├─ MCP servers (agent-browser, …)
                    └─ extensions: memory, subagents, footer
```

## Fork it

Devstack is built to be forked and repointed. Edit `lpb.stack.env` in a devstack
fork to point at your own `PI_FORK`, `CONFIG_FORK`, images, and container name.
See [Forking & Repointing](https://github.com/localpibox/devstack#forking--repointing).
