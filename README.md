# Exmergo Agent Plugins

**Every open plugin Exmergo ships, from one Claude Code marketplace.**

## Install

Add the marketplace once (run these inside Claude Code, one at a time):

```
/plugin marketplace add exmergo/exmergo-agent-plugins
```

Then install any plugin from it:

```
/plugin install dex@exmergo
```

```
/plugin install no-em-dashes@exmergo
```

Pull the latest catalog and plugin versions later:

```
/plugin marketplace update exmergo
```

Not on Claude Code? See [Beyond Claude Code](#beyond-claude-code).

## What's in the catalog

| Plugin | What it does | Install | Repo |
|---|---|---|---|
| **dex** | Analytics engineering for your coding agent: explore a warehouse, transform it with reviewable dbt and semantic-layer edits, and maintain it as schemas and data drift. Read-only against your data, cost quoted before any spend. | `/plugin install dex@exmergo` | [exmergo/dex](https://github.com/exmergo/dex) |
| **no-em-dashes** | Produces em-dash-free prose and avoids the sentence shapes that invite an em dash, so writing reads as a person's rather than machine-generated. | `/plugin install no-em-dashes@exmergo` | [exmergo/skill-no-em-dashes](https://github.com/exmergo/skill-no-em-dashes) |

### dex

dex gives a coding agent the habits of an analytics engineer, with the guardrails
built into its engine rather than its prompt. It installs three skills:

- **`/dex:explore`** maps a warehouse you have never seen: ranked inventory, profiles built from aggregates, PII flags, and verified joins.
- **`/dex:transform`** authors and refactors dbt models and the semantic layer as reviewable plans, built only on a dev target.
- **`/dex:maintain`** finds schema, volume, grain, and metric-definition drift and proposes the fix.

The skills trigger on matching intent, so you rarely need to call them by name.

> [!IMPORTANT]
> **dex needs [`uv`](https://docs.astral.sh/uv/) on your `PATH`.** Run
> `brew install uv` or `pipx install uv` before your first dex command.

Quickstart, connectors, and benchmarks are in the [dex README](https://github.com/exmergo/dex#readme),
and the full documentation is at [docs.exmergo.com/dex](https://docs.exmergo.com/dex).

### no-em-dashes

Triggers automatically whenever Claude writes or edits prose. Examples and details are
in the [skill-no-em-dashes README](https://github.com/exmergo/skill-no-em-dashes).

## How the catalog works

This repository holds no plugin code. It is a catalog:
[`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) points at each
plugin's own repository, which carries its own README, examples, and issues.

Single-skill repositories are named with a `skill-` prefix so they group together in
our GitHub organization. dex is a full toolkit with its own engine, so it lives at
`exmergo/dex`.

## Beyond Claude Code

The `/plugin` commands are specific to Claude Code. The plugins themselves are not.

- **dex** installs into any agent that loads Agent Skills:

  ```bash
  npx skills add exmergo/dex                  # any agent
  npx skills add exmergo/dex --agent codex    # Codex
  ```

  Any other agent can drive dex through its [`AGENTS.md`](https://github.com/exmergo/dex/blob/main/AGENTS.md).

- **no-em-dashes** ships an `AGENTS.md` (read by Cursor, GitHub Copilot, Codex,
  Windsurf, and others) plus native rule files for the major agents. Follow
  [Use with other coding agents](https://github.com/exmergo/skill-no-em-dashes#use-with-other-coding-agents).

## About Exmergo

[Exmergo](https://www.exmergo.com) is the team building AI agents for data analytics.
This catalog is part of the work we share at
[exmergo.com/open-research](https://www.exmergo.com/open-research).

## Maintaining the catalog

See [MAINTAINING.md](MAINTAINING.md) for how to add a plugin, pin versions, and ship
updates.

## License

[MIT](LICENSE). Each plugin is licensed in its own repository (dex is Apache-2.0).
