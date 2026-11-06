# Skills

Agent skills for software development. Each skill is a folder with a `SKILL.md` file in the [Agent Skills](https://agentskills.io) format, so it works in Claude Code, Codex, Cursor and other agents that read that format.

## Skills

| Category | Skill | What it does |
| --- | --- | --- |
| writing | [natural-cadence-editor](plugins/writing/skills/natural-cadence-editor/SKILL.md) | Rewrites prose that stumbles when read aloud: stacked clauses, repeated word stems, accidental alliteration. |

## Install

### Claude Code

```
/plugin marketplace add devszilla/skills
/plugin install writing@devszilla
```

Each category is one plugin. Claude Code installs a whole category, not single skills. To get new skills after an update, run `/plugin marketplace update devszilla`.

### Other agents

The [skills CLI](https://github.com/vercel-labs/skills) installs into Codex, Cursor, OpenCode and other agents:

```bash
npx skills add devszilla/skills --skill natural-cadence-editor
```

Leave off `--skill` to choose from the full list.

### Manual

Copy a skill folder into your agent's skills directory. For Claude Code that is `~/.claude/skills/`:

```bash
git clone https://github.com/devszilla/skills
cp -r skills/plugins/writing/skills/natural-cadence-editor ~/.claude/skills/
```

## Layout

```
.claude-plugin/marketplace.json     one entry per category
plugins/<category>/
  .claude-plugin/plugin.json
  skills/<skill-name>/SKILL.md
skills.sh.json                      points the skills CLI at plugins/
```

## Add a skill

1. Create `plugins/<category>/skills/<skill-name>/SKILL.md`. The folder name must match the `name` field in the frontmatter.
2. For a new category, also add `plugins/<category>/.claude-plugin/plugin.json` and an entry in `.claude-plugin/marketplace.json`.
3. Add a row to the table above.
4. Run `claude plugin validate .` and `claude plugin validate plugins/<category>` before you push.

## License

[MIT](LICENSE)
