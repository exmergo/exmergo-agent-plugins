# Exmergo Skills

Open skills for AI coding agents from [Exmergo](https://www.exmergo.com), the team
building AI agents for data analytics. They install into
[Claude Code](https://code.claude.com/docs/en/plugins) through this marketplace, and
they also work in other coding agents (see [Beyond Claude Code](#beyond-claude-code)).

This repository is a Claude Code plugin marketplace. Add it once, then install any
skill in the catalog. It is part of the work we share at
[exmergo.com/open-research](https://www.exmergo.com/open-research).

## Install

Add the marketplace once:

```
/plugin marketplace add exmergo/exmergo-skills
```

Then install any skill from it:

```
/plugin install no-em-dashes@exmergo-skills
```

To pull the latest catalog and skill versions later:

```
/plugin marketplace update exmergo-skills
```

## Skills in this catalog

| Skill | What it does | Repo |
|-------|--------------|------|
| `no-em-dashes` | Produces em-dash-free prose and avoids the sentence shapes that invite an em dash, so writing reads as a person's rather than machine-generated. | [exmergo/skill-no-em-dashes](https://github.com/exmergo/skill-no-em-dashes) |

Each skill lives in its own repository, with its own README, examples, and issues. This
catalog only points at them, so one marketplace gives you everything Exmergo ships.
Skill repositories are named with a `skill-` prefix so they group together in our
GitHub organization, separate from our open-research experiments and other tools.

## Beyond Claude Code

The `/plugin` commands above are specific to Claude Code, which is what this
marketplace plugs into. The skills themselves are not Claude-only: each one ships an
`AGENTS.md` (the cross-tool standard read by Cursor, GitHub Copilot, Codex, Windsurf,
and others) along with native rule files for the major agents. To use a skill outside
Claude Code, open its repository and follow the "Use with other coding agents" section
there. For example, see
[exmergo/skill-no-em-dashes](https://github.com/exmergo/skill-no-em-dashes#use-with-other-coding-agents).

## Maintaining the catalog

See [MAINTAINING.md](MAINTAINING.md) for how to add a skill, pin versions, and ship
updates.

## License

[MIT](LICENSE). Each skill is licensed in its own repository.
