# thewhyman/agent-marketplace

**Standalone Claude Code marketplace for all thewhyman-authored units.**

This repo holds the canonical `.claude-plugin/marketplace.json` for `@thewhyman`. Install once, get any plugin in the family.

## Install

```
/plugin marketplace add thewhyman/agent-marketplace
/plugin install <plugin>@thewhyman
```

## What's available

| Plugin | Version | What it does |
|---|---|---|
| `co-dialectic` | 3.4.0 | LLM prompt sharpening + cross-family judge-panel cascade + hallucination detection |
| `career-os` | 0.24.0 | AI-powered career management — persistent memory, pipeline tracking, outreach drafting |

xOS family plugins (`xteamos`, `xhumanos`, `xfamilyos`, `xcommunityos`) ship into this marketplace as each lands.

## Examples

```
/plugin install co-dialectic@thewhyman
/plugin install career-os@thewhyman
```

## How updates work

Plugins live in their own repos; this marketplace pins each one to a specific commit SHA. When a plugin updates:

1. Plugin repo pushes the change
2. This repo bumps the plugin's `version` + `sha` in `.claude-plugin/marketplace.json`
3. Users run `/plugin marketplace update thewhyman` to pull the new pins

## Architecture

- **Repo name** `agent-marketplace` — branded to the agent thesis (Cyborg = human + agents)
- **Marketplace name** `thewhyman` — author-scoped; same publisher pattern as `@anthropic-ai/sdk`, `@vercel/next`. Accommodates xOS plugins AND non-xOS plugins under one install scope.
- **Source pattern** — every plugin pinned via `url + sha` (one source repo per plugin, except co-dialectic which lives at `prompt-engineering-in-action/plugins/co-dialectic` and uses `path` to specify the subdirectory)

## Migration history

- **2026-04-27:** Repo created. Migrated from per-plugin marketplaces (`thewhyman/prompt-engineering-in-action` + `thewhyman/career-os-plugin`). Old install paths still work as legacy mirrors but this is the canonical marketplace going forward.

See [WIP/agent-marketplace-product/PRD.md](https://github.com/thewhyman/anand-career-os/blob/main/WIP/agent-marketplace-product/PRD.md) (private) for full design rationale.

## Contributing

This marketplace is curated to thewhyman-authored plugins only. Third-party plugins should ship via their own marketplaces. Issues + PRs welcome for marketplace metadata fixes.

## License

Marketplace metadata: MIT. Each listed plugin retains its own license — see plugin repo for terms.
