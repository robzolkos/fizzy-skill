# No longer maintained - the SKILL is moved into the Fizzy CLI project https://github.com/robzolkos/fizzy-cli

# Agent Skill for Fizzy

A skill that enables natural language management of [Fizzy](https://fizzy.do) boards, cards, and tasks directly from your terminal. Works with both [Claude Code](https://docs.anthropic.com/en/docs/claude-code/skills) and [OpenCode](https://opencode.ai/docs/skills.md).

## What is Fizzy?

[Fizzy](https://fizzy.do) is a task and project management application. This skill allows your AI coding assistant to interact with your Fizzy workspace using the `fizzy` CLI.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) or [OpenCode](https://opencode.ai) installed
- [Fizzy CLI](https://github.com/robzolkos/fizzy-cli) installed and authenticated

## Installation

The easiest way to install this skill is using the Fizzy CLI's built-in command:

```bash
fizzy skill
```

This will automatically install the skill to the correct location for both Claude Code (`~/.claude/skills/`) and OpenCode (`~/.config/opencode/skills/`).

### Manual Installation

Alternatively, copy the `fizzy` folder to your skills directory:

**For Claude Code:**
```bash
cp -r fizzy ~/.claude/skills/
```

**For OpenCode:**
```bash
cp -r fizzy ~/.config/opencode/skills/
```

## Authentication

Before using the skill, authenticate with your Fizzy account:

```bash
fizzy auth login YOUR_API_TOKEN
```

You can verify your authentication status:

```bash
fizzy auth status
```

## Example Commands

Once installed, you can use natural language to manage your Fizzy tasks:

### Viewing Your Work

```
Show me all my boards
```

```
List open cards on the Engineering board
```

```
What tasks are assigned to me?
```

### Creating Cards

```
Create a new card on the Product board titled "Update login page design"
```

```
Add a card to Engineering with title "Fix authentication bug" and description "Users are being logged out unexpectedly"
```

### Managing Cards

```
Close card #42
```

```
Move card #15 to the "In Progress" column
```

```
Add the tag "urgent" to card #23
```

```
Postpone card #8 for later
```

### Working with Steps (To-dos)

```
Add a checklist to card #12 with steps: "Write tests", "Update documentation", "Deploy to staging"
```

```
Mark the first step on card #12 as completed
```

### Comments and Collaboration

```
Add a comment to card #5 saying "Ready for review"
```

```
Assign card #30 to user ID 123
```

### Notifications

```
Show my notifications
```

```
Mark all notifications as read
```

## Documentation

- [Claude Code Skills Documentation](https://docs.anthropic.com/en/docs/claude-code/skills)
- [OpenCode Skills Documentation](https://opencode.ai/docs/skills.md)
- [Fizzy](https://fizzy.do)

## License

MIT
