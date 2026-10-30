# Win & Scale plugin

Meta ads for AI agents. Find the ads that pay, and launch the next one paused.

Connects an AI agent to Win & Scale over MCP, with skills that walk it
through the common jobs. One tree serves every format: the vendor-neutral
[Agent Plugin](https://agent-plugins.org) spec, Claude Code, Gemini CLI and the
[Agent Skills](https://agentskills.io) layout, all sharing one `skills/`
directory.

## Install

**Claude Code** — as a marketplace, or straight from the product:

```bash
claude plugin marketplace add winandscale/winandscale-plugin
claude plugin install winandscale@winandscale
```

```bash
claude --plugin-url https://winandscale.com/api/mcp/plugin.zip
```

**Skills only** (Claude Code, Codex, Cursor, Gemini CLI and other
[skills.sh](https://skills.sh) clients):

```bash
npx skills add winandscale/winandscale-plugin
```

**Cursor** — [Add to Cursor](https://cursor.com/en/install-mcp?name=winandscale&config=eyJ1cmwiOiJodHRwczovL3dpbmFuZHNjYWxlLmNvbS9hcGkvbWNwIn0=)

**VS Code / Copilot** — [Install in VS Code](https://vscode.dev/redirect/mcp/install?name=winandscale&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fwinandscale.com%2Fapi%2Fmcp%22%7D)

**Gemini CLI**

```bash
gemini extensions install https://github.com/winandscale/winandscale-plugin
```

**Codex** — in `~/.codex/config.toml`:

```toml
[mcp_servers.winandscale]
type = "http"
url = "https://winandscale.com/api/mcp"
```

**claude.ai** — Settings → Connectors → Add custom connector, and paste
`https://winandscale.com/api/mcp`.

**A client that only speaks stdio** — bridge it, no extra package from us:

```bash
npx mcp-remote https://winandscale.com/api/mcp
```

Every route authorizes the same way: OAuth 2.1 in a browser. There is no token
to set, and any instruction telling you to export one is out of date.

## What is in here

| Path | |
| --- | --- |
| `plugin.json` / `mcp.json` | Agent Plugin manifest (agent-plugins.org 1.0.0) |
| `.claude-plugin/` | Claude Code manifest and marketplace entry |
| `.mcp.json` | Claude Code MCP config |
| `gemini-extension.json` | Gemini CLI extension manifest |
| `server.json` | MCP Registry entry |
| `skills/winandscale/` | Reference skill: authorization, tool catalogue, safety model |
| `skills/winandscale-*/` | Workflow skills: step-by-step guides for the common jobs |
| `commands/` | Claude Code slash commands |

The playbooks the product runs server-side are not in this bundle. They are
product IP, and this repo is public.
