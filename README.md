# LeMatosDeFuk Marketplace

Claude Code skills marketplace with auto-update support.

## Installation

```bash
/marketplace add github:LeMatosDeFuk/lematodefuk-marketplace
```

## Available Skills

| Skill | Description |
|-------|-------------|
| **google-docs** | Read and extract content from Google Docs including text and images |
| **asana-task-analyzer** | Analyze Asana tasks for implementers - extracts requirements, flags unclear items |
| **handle-mr-feedback** | Analyze GitLab MR review comments, validate against code, create implementation plan |

## Install a Skill

After adding the marketplace:

```bash
/install google-docs
/install asana-task-analyzer
/install handle-mr-feedback
```

## View Installed Skills

To see your installed marketplaces and skills:

```bash
/marketplace list
```

### Using the UI

When you run `/marketplace add`, you'll see a UI with multiple tabs:

| Tab | Description |
|-----|-------------|
| **Plugins** | Individual plugins from all sources |
| **Discover** | Browse plugins from *other* marketplaces (your own marketplace won't appear here) |
| **Installed** | Your currently installed plugins |
| **Marketplaces** | Your added marketplaces including this one |

**Note:** After adding this marketplace, your skills won't appear in "Discover" - that's for discovering *new* marketplaces. Switch to **"Marketplaces"** or **"Installed"** tab to see your skills.

Navigate between tabs using **Tab** key or **arrow keys**.

## Update Skills

Skills auto-update when Claude Code starts, or manually:

```bash
/marketplace update
```

## Contributing

Want to add your skill?

1. Create a folder in `skills/your-skill-name/` with a `SKILL.md` file
2. Add your plugin to `.claude-plugin/marketplace.json`
3. Open a PR
