# Exmergo Skills

Open [Claude Code](https://code.claude.com/docs/en/plugins) skills from
[Exmergo](https://www.exmergo.com), the team building AI agents for data analytics.

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

## Maintaining the catalog

See [MAINTAINING.md](MAINTAINING.md) for how to add a skill, pin versions, and ship
updates.

## License

[MIT](LICENSE). Each skill is licensed in its own repository.
