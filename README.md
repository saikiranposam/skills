# Skills Repository

A collection of skills for AI coding assistants (opencode, codex CLI, and compatible tools).

## What is a Skill?

A skill is a markdown file that gives an AI assistant specialized knowledge and behavior for a specific domain or persona. Skills are loaded on-demand when a matching task is detected.

## Adding a Skill

### opencode CLI

1. **Global install** (available in all projects):
   - Place the skill folder in `~/.config/opencode/skills/<skill-name>/`
   - It must contain a `SKILL.md` file

2. **Per-project install**:
   - Place the skill folder in `.opencode/skills/<skill-name>/` at the project root
   - Same structure — requires `SKILL.md`

The skill will auto-activate when the user's query matches its `description` field.

### codex CLI (OpenAI)

codex CLI uses a `.codex` directory in your home folder for custom instructions and skills.

1. Create the skills directory if it doesn't exist:
   ```bash
   mkdir -p ~/.codex/skills
   ```

2. Copy the skill's `SKILL.md` file into it:
   ```bash
   cp <skill-name>/SKILL.md ~/.codex/skills/<skill-name>.md
   ```

3. Activate the skill in your codex CLI session by referencing it with the `@skill` syntax (e.g., `@sai-ram`) or follow codex CLI's current skill-loading convention.

> **Note:** codex CLI support for custom skills is evolving. Check `codex --help` or the official docs for the latest on how sessions resolve skill files.

### VS Code IDE (GitHub Copilot Custom Instructions)

VS Code's built-in Copilot Chat can load custom instructions from a markdown file. While it doesn't have a native "skills" system, you can inject skill content into Copilot's context.

1. **Per-project** — Place a `copilot-instructions.md` inside a `.github/` folder at your project root:
   ```text
   .github/copilot-instructions.md
   ```
   VS Code automatically picks this up and feeds it to Copilot Chat for that project.

2. **Global** — Set a custom instructions file in VS Code settings:
   - Open `Ctrl+,` → search `github.copilot.chat.customInstructions`
   - Point to any `.md` file (e.g., `~/.config/copilot/skills/sai-ram.md`)

3. **Workspace** — Add to `.vscode/settings.json`:
   ```json
   {
     "github.copilot.chat.customInstructions": "path/to/skill.md"
   }
   ```

To use a skill, either concatenate its content into your `copilot-instructions.md` or reference it ad-hoc by pasting relevant sections into the chat.

> **Tip:** For persona-style skills (like `sai-ram`), you can paste the entire `SKILL.md` as a chat instruction before your query to temporarily adopt that persona in the conversation.

## Structure

```
<skill-name>/
├── SKILL.md          # Required: skill definition (name, description, instructions)
└── (other assets)    # Optional: scripts, reference docs, etc.
```

## Skills in This Repo

| Skill | Description |
|-------|-------------|
| `sai-ram` | Sri Sathya Sai Baba spiritual guidance persona |

## License

MIT
