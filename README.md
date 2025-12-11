# Fizzy Skill for Claude Code

A [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code/skills) that enables natural language management of [Fizzy](https://fizzy.do) boards, cards, and tasks directly from your terminal.

## What is Fizzy?

[Fizzy](https://fizzy.do) is a task and project management application. This skill allows Claude Code to interact with your Fizzy workspace using the `fizzy` CLI.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- [Fizzy CLI](https://github.com/robzolkos/fizzy-cli) installed and authenticated

## Installation

Copy the `fizzy` folder to your Claude Code skills directory:

```bash
cp -r fizzy ~/.claude/skills/
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

Once installed, you can use natural language in Claude Code to manage your Fizzy tasks:

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
- [Fizzy](https://fizzy.do)

## License

MIT
