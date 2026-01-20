# Ant Marketplace

Ant Studio skills for Claude Code.

## Installation

1. Run `/marketplace add` in Claude Code
2. Press **Tab** to switch to **"Marketplaces"** tab
3. Select **"+ Add Marketplace"**
4. Enter: `LeMatosDeFuk/lematodefuk-marketplace`
5. Press Enter to add marketplace
6. Install the plugin:

```bash
/plugin install ant@ant-marketplace
```

## Available Skills

After installing the `ant` plugin, these skills are available:

| Skill | Command | Description |
|-------|---------|-------------|
| **google-docs** | `/ant:google-docs` | Read and extract content from Google Docs |
| **asana-task-analyzer** | `/ant:asana-task-analyzer` | Analyze Asana tasks for implementers |
| **handle-mr-feedback** | `/ant:handle-mr-feedback` | Handle GitLab MR review feedback |

## Update

```bash
/plugin update ant
```

## Contributing

1. Create a folder in `skills/your-skill-name/` with a `SKILL.md` file
2. Open a PR
