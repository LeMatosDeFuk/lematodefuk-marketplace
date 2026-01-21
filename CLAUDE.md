# Ant Marketplace - Development Instructions

## Project Structure

```
.claude-plugin/
  marketplace.json    # Marketplace config with skills list
  plugin.json         # Plugin metadata with version
commands/             # Command files (aliases for skills)
skills/               # Skill folders with SKILL.md files
```

## Adding a New Skill

1. **Create skill folder and SKILL.md:**
   ```
   skills/my-skill/SKILL.md
   ```

2. **SKILL.md format:**
   ```markdown
   ---
   user-invocable: true
   name: my-skill
   description: Short description for skill discovery
   ---

   # Skill Title

   Instructions for Claude to follow...
   ```

3. **Register in marketplace.json:**
   ```json
   "skills": [
     "./skills/google-docs",
     "./skills/my-skill"  // Add here
   ]
   ```

4. **Update README.md** - add to Available Skills table

5. **Release new version** (see below)

## Adding a New Command

Commands are optional aliases that reference skills. The skill itself is what matters.

1. **Create command file:**
   ```
   commands/my-command.md
   ```

2. **Command format:**
   ```markdown
   ---
   description: "Short description"
   ---

   Invoke the ant:my-skill skill and follow it exactly as presented to you
   ```

## Releasing a New Version

**Both files must have matching versions:**
- `.claude-plugin/plugin.json` → `"version": "X.Y.Z"`
- `.claude-plugin/marketplace.json` → `"version": "X.Y.Z"`

**Version bumping:**
- **Major (X.0.0)** - Breaking changes
- **Minor (X.Y.0)** - New features (new skills)
- **Patch (X.Y.Z)** - Bug fixes, improvements

**Release process:**
```bash
# 1. Update both version files
# 2. Commit changes
git add -A && git commit -m "feat/fix: description"

# 3. Push
git push origin master

# 4. Create GitHub release
gh release create vX.Y.Z --title "vX.Y.Z" --notes "## Changes
- Description of changes"
```

**Users update with:**
```
/plugin update ant
```

## Testing Locally

After making changes, users need to run `/plugin update ant` to get the latest version from the GitHub release.

## Skill Best Practices

- Use `AskUserQuestion` tool for user choices with predefined options
- For simple text input, just ask directly (no options needed)
- Reference other skills with `ant:skill-name` or `superpowers:skill-name`
- Add `**Announce at start:**` for clarity on what skill is being used
