# spec-generator — installation

The skill is a self-contained folder with two files: `SKILL.md` (the
instructions, with YAML frontmatter) and `spec-template.md` (the template).
The content is tool-agnostic; only the location changes.

## Claude Code

It is already installed in this project. To have it in all your projects:

```bash
cp -R .claude/skills/spec-generator ~/.claude/skills/
```

It triggers on its own when you ask for a spec, or manually with
`/spec-generator`.

## opencode

Same skill format, different path. It is already linked in this repo
(`.opencode/skill/spec-generator` is a symlink to the canonical folder).
In another project, or if your system does not handle symlinks (Windows
without permissions):

```bash
mkdir -p .opencode/skill && cp -R .claude/skills/spec-generator .opencode/skill/
```

Global instead of per project: `~/.config/opencode/skill/`.

## Maintenance

`SKILL.md` is the single source of truth: opencode reaches it through the
symlink and the Cursor command references it by path. Edit only that file. If
somewhere you have a copy instead of a link, remember to keep it in sync.
