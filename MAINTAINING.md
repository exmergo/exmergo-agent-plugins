# Maintaining the catalog

This repo is a Claude Code marketplace named `exmergo-skills`. It holds no skill code
of its own. It is a catalog: `.claude-plugin/marketplace.json` lists each skill and
points at the skill's own repository via a `github` source. The marketplace is "live"
whenever this file is reachable in a git repo your users can access. There is no
separate publish step with Anthropic.

## How users consume it

```
/plugin marketplace add exmergo/exmergo-skills      # add the catalog once
/plugin install <skill>@exmergo-skills              # install any listed skill
/plugin marketplace update exmergo-skills           # pull catalog + skill updates
```

## Naming convention

Skill repositories are named with a `skill-` prefix (for example
`exmergo/skill-no-em-dashes`). The prefix groups skills together in the GitHub org,
separate from open-research experiments and other tools. The prefix is only the repo
name; the plugin's own `name` (set in its `plugin.json`) is the clean identifier users
type, so `exmergo/skill-no-em-dashes` installs as `no-em-dashes@exmergo-skills`.

## Adding a skill to the catalog

1. Build and publish the skill as a standalone plugin repo (`exmergo/skill-<name>`),
   with its `.claude-plugin/plugin.json` and `skills/<name>/SKILL.md`.
2. Add an entry to the `plugins` array in `.claude-plugin/marketplace.json`:

   ```json
   {
     "name": "<plugin-name>",
     "source": { "source": "github", "repo": "exmergo/skill-<name>" },
     "description": "One line describing what the skill does."
   }
   ```

3. Add a row to the "Skills in this catalog" table in `README.md`.
4. Validate, commit, and push (see below).

## Pinning versions

By default a `github` source tracks the skill repo's default branch, so users get the
latest on `/plugin marketplace update`. For tighter control, pin the entry:

```json
{ "source": "github", "repo": "exmergo/skill-<name>", "ref": "v1.2.0" }
```

Use `ref` for a tag or branch, or `sha` for an exact commit. Pinning is the safer
choice once a skill is widely used: the catalog decides which version ships, and a
push to the skill repo does not reach users until you bump the `ref` here.

## Pre-publish checks

```bash
claude plugin validate .
python -c "import json; json.load(open('.claude-plugin/marketplace.json')); print('valid JSON')"
```

Note: `claude plugin validate` resolves each `github` source, so it only fully passes
once the referenced skill repos are pushed and reachable (public, or private with your
git auth).

## Private first, public later

The catalog works privately for the team, then opens up with no repackaging.

- **While private:** each teammate needs read access to this repo and to every
  referenced skill repo, plus working git auth (SSH keys or `gh auth login`).
- **Going public:** flip the visibility of this repo and each skill repo in GitHub
  settings. Nothing in the manifests changes and existing installs keep working.
- **Before going public:** scrub git history for secrets, since public exposes every
  past commit.

## Cutting a release

- **A skill changed:** bump the `version` in that skill's own `plugin.json`, push the
  skill repo, and if you pin versions here, update its `ref` in `marketplace.json`.
- **The catalog changed** (added or removed a skill): commit and push this repo.

Either way, users run `/plugin marketplace update exmergo-skills` to pick it up.
