# Exponential-OS/agent-marketplace

**Standalone Claude Code marketplace for all Exponential-OS/xos-authored units.**

This repo holds the canonical `.claude-plugin/marketplace.json` for `@xos`. Install once, get any plugin in the family.

## Install

```
/plugin marketplace add Exponential-OS/agent-marketplace
/plugin install <plugin>@xos
```

## Currently pinned plugins (2026-04-27)

| Plugin | Version | What |
|---|---|---|
| co-dialectic | 4.1.0 | LLM prompt optimizer + 5 protocols (Auto-Verify · Auto-Handoff · Honesty · Agent-Swarm · Hygiene) + cross-family review |
| career-os | 0.27.0 | Career-OS + outreach-fact-check (T4 immunity) + interviewer-research (panel prep) |

See `.claude-plugin/marketplace.json` for canonical pinned commits.

xOS family plugins (`xteamos`, `xhumanos`, `xfamilyos`, `xcommunityos`) ship into this marketplace as each lands.

## Examples

```
/plugin install co-dialectic@xos
/plugin install career-os@xos
```

## How updates work

Plugins live in their own repos; this marketplace pins each one to a specific commit SHA. When a plugin updates:

1. Plugin repo pushes the change
2. This repo bumps the plugin's `version` + `sha` in `.claude-plugin/marketplace.json`
3. Users run `/plugin marketplace update xos` to pull the new pins

## Architecture

- **Repo name** `agent-marketplace` — branded to the agent thesis (Cyborg = human + agents)
- **Marketplace name** `xos` — author-scoped; same publisher pattern as `@anthropic-ai/sdk`, `@vercel/next`. Accommodates xOS plugins AND non-xOS plugins under one install scope.
- **Source pattern** — every plugin pinned via `url + sha` (one source repo per plugin, except co-dialectic which lives at `prompt-engineering-in-action/plugins/co-dialectic` and uses `path` to specify the subdirectory)

## Migration history

- **2026-04-27:** Repo created. Migrated from per-plugin marketplaces (`Exponential-OS/prompt-engineering-in-action` + `Exponential-OS/career-os-plugin`). Old install paths still work as legacy mirrors but this is the canonical marketplace going forward.

See [WIP/agent-marketplace-product/PRD.md](https://github.com/Exponential-OS/anand-career-os/blob/main/WIP/agent-marketplace-product/PRD.md) (private) for full design rationale.

## Contributing

This marketplace is curated to Exponential-OS/xos-authored plugins only. Third-party plugins should ship via their own marketplaces. Issues + PRs welcome for marketplace metadata fixes.

## License

Marketplace metadata: MIT. Each listed plugin retains its own license — see plugin repo for terms.
