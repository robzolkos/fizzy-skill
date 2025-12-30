---
name: fizzy
description: ALWAYS invoke before running fizzy CLI commands to get correct syntax. Manages boards, cards, steps, comments, and reactions.
---

# When to Use This Skill

**Proactively use this skill when:**
- User asks to create, view, or manage cards/tasks
- User mentions Fizzy boards or columns
- User wants to list, close, or update work items
- User asks about their current tasks or backlog

# CLI Reference

## Boards

```bash
fizzy board list                    # List all boards
fizzy board show ID                 # Show a specific board
fizzy board create --name=NAME      # Create a new board
fizzy board update ID               # Update a board
fizzy board delete ID               # Delete a board
```

### Board List Options
- `--page=N` - Page number
- `--all` - Fetch all pages (default: false)

### Board Create Options
- `--name=NAME` - Board name (required)
- `--all-access` - Allow all users to access (default: true)
- `--auto-postpone-period=N` - Auto-postpone period in days

### Board Update Options
- `--name=NAME` - Board name
- `--all-access` / `--no-all-access` - Allow all users to access
- `--user-ids=USER_IDS` - Comma-separated user IDs for access
- `--auto-postpone-period=N` - Auto-postpone period in days

## Cards

```bash
fizzy card list                                  # List cards
fizzy card show NUMBER                           # Show a specific card by number
fizzy card create --board=BOARD --title=TITLE    # Create a new card
fizzy card update NUMBER                         # Update a card
fizzy card delete NUMBER                         # Delete a card
fizzy card close NUMBER                          # Close a card
fizzy card reopen NUMBER                         # Reopen a closed card
fizzy card column NUMBER --column=COLUMN         # Move card to a column (by column ID)
fizzy card assign NUMBER --user=USER             # Toggle user assignment (by user ID)
fizzy card tag NUMBER --tag=TAG                  # Toggle a tag on a card (by tag title, creates if needed)
fizzy card watch NUMBER                          # Watch a card for notifications
fizzy card unwatch NUMBER                        # Stop watching a card
fizzy card postpone NUMBER                       # Mark card as not now
fizzy card untriage NUMBER                       # Send card back to triage
```

### Card List Options
- `--board=BOARD` - Filter by board ID
- `--tag=TAG` - Filter by tag ID
- `--assignee=ASSIGNEE` - Filter by assignee user ID
- `--status=STATUS` - Filter by status (published, closed, not_now)
- `--page=N` - Page number
- `--all` - Fetch all pages (default: false)

### Card Create Options
- `--board=BOARD` - Board ID (required)
- `--title=TITLE` - Card title (required)
- `--description=DESCRIPTION` - Card description (rich text/HTML)
- `--description-file=DESCRIPTION_FILE` - Read description from file
- `--status=STATUS` - Card status
- `--tag-ids=TAG_IDS` - Comma-separated tag IDs
- `--image=IMAGE` - Path to header image file
- `--created-at=CREATED_AT` - Custom creation timestamp (ISO 8601)

### Card Update Options
- `--title=TITLE` - Card title
- `--description=DESCRIPTION` - Card description (rich text/HTML)
- `--description-file=DESCRIPTION_FILE` - Read description from file
- `--status=STATUS` - Card status
- `--tag-ids=TAG_IDS` - Comma-separated tag IDs
- `--image=IMAGE` - Path to header image file
- `--created-at=CREATED_AT` - Custom creation timestamp (ISO 8601)

### Card Column Options
- `--column=COLUMN` - Column ID to move into (required)

### Card Assign Options
- `--user=USER` - User ID to toggle assignment (required)

### Card Tag Options
- `--tag=TAG` - Tag title to toggle (required, creates tag if needed)

## Columns

```bash
fizzy column list --board=BOARD                  # List columns for a board
fizzy column show ID --board=BOARD               # Show a specific column
fizzy column create --board=BOARD --name=NAME    # Create a column
fizzy column update ID --board=BOARD             # Update a column
fizzy column delete ID --board=BOARD             # Delete a column
```

### Column List Options
- `--board=BOARD` - Board ID (required)
- `--page=N` - Page number
- `--all` - Fetch all pages (default: false)

### Column Create Options
- `--board=BOARD` - Board ID (required)
- `--name=NAME` - Column name (required)
- `--color=COLOR` - CSS color variable name

### Column Update Options
- `--board=BOARD` - Board ID (required)
- `--name=NAME` - Column name
- `--color=COLOR` - CSS color variable name

## Comments

```bash
fizzy comment list --card=CARD       # List comments on a card
fizzy comment show ID --card=CARD    # Show a specific comment
fizzy comment create --card=CARD     # Create a new comment
fizzy comment update ID --card=CARD  # Update a comment
fizzy comment delete ID --card=CARD  # Delete a comment
```

### Comment List Options
- `--card=CARD` - Card number (required)
- `--page=N` - Page number
- `--all` - Fetch all pages (default: false)

### Comment Create Options
- `--card=CARD` - Card number (required)
- `--body=BODY` - Comment body (supports rich text)
- `--body-file=BODY_FILE` - Read body from file
- `--created-at=CREATED_AT` - Custom creation timestamp (ISO 8601)

### Comment Update Options
- `--card=CARD` - Card number (required)
- `--body=BODY` - Comment body (supports rich text)
- `--body-file=BODY_FILE` - Read body from file
- `--created-at=CREATED_AT` - Custom creation timestamp (ISO 8601)

## Steps (To-do Items)

```bash
fizzy step show ID --card=CARD                     # Show a specific step
fizzy step create --card=CARD --content=CONTENT    # Create a step
fizzy step update ID --card=CARD                   # Update a step
fizzy step delete ID --card=CARD                   # Delete a step
```

### Step Create Options
- `--card=CARD` - Card number (required)
- `--content=CONTENT` - Step content (required)
- `--completed` - Mark as completed (default: false)

### Step Update Options
- `--card=CARD` - Card number (required)
- `--content=CONTENT` - Step content
- `--completed` - Mark as completed
- `--not-completed` - Mark as not completed

## Tags

```bash
fizzy tag list                      # List all tags
```

### Tag List Options
- `--page=N` - Page number
- `--all` - Fetch all pages (default: false)

## Authentication

```bash
fizzy auth login TOKEN              # Save API token to config file
fizzy auth logout                   # Remove stored credentials
fizzy auth status                   # Show current authentication state
```

## Notifications

```bash
fizzy notification list             # List notifications
fizzy notification read ID          # Mark a notification as read
fizzy notification read-all         # Mark all notifications as read
fizzy notification unread ID        # Mark a notification as unread
```

### Notification List Options
- `--page=N` - Page number
- `--all` - Fetch all pages (default: false)

## Users

```bash
fizzy user list                     # List all users
fizzy user show ID                  # Show a specific user
fizzy user update ID                # Update a user
fizzy user deactivate ID            # Deactivate a user
```

### User List Options
- `--page=N` - Page number
- `--all` - Fetch all pages (default: false)

### User Update Options
- `--name=NAME` - User name
- `--avatar=AVATAR` - Path to avatar image file

## Reactions

```bash
fizzy reaction list --card=CARD --comment=COMMENT                      # List reactions
fizzy reaction create --card=CARD --comment=COMMENT --content=CONTENT  # Add a reaction
fizzy reaction delete ID --card=CARD --comment=COMMENT                 # Remove a reaction
```

### Reaction Create Options
- `--card=CARD` - Card number (required)
- `--comment=COMMENT` - Comment ID (required)
- `--content=CONTENT` - Emoji (max 16 chars, required)

## Uploads

```bash
fizzy upload file PATH              # Upload a file for use in rich text fields
```

The upload command returns a `signed_id` that can be used in rich text fields (card descriptions, comment bodies) by embedding it in an action-text-attachment tag:

```html
<action-text-attachment sgid="SIGNED_ID"></action-text-attachment>
```

**Example workflow:**
1. Upload the file:
   ```bash
   fizzy upload file /path/to/image.png
   # Returns: {"signed_id": "eyJfcmFpbHMi..."}
   ```
2. Use the signed_id in a card description:
   ```bash
   fizzy card create --board BOARD_ID --title "My Card" \
     --description '<p>See image:</p><action-text-attachment sgid="eyJfcmFpbHMi..."></action-text-attachment>'
   ```

## Identity

```bash
fizzy identity show                 # Show your identity and accessible accounts
```

# Global Options

These options can be used with any command:

- `--token=TOKEN` - API access token (or set FIZZY_TOKEN env var)
- `--account=ACCOUNT` - Account slug (or set FIZZY_ACCOUNT env var). **Important:** Use just the number (e.g., `6086023`), not a path with a slash.
- `--api-url=API_URL` - API base URL (default: https://app.fizzy.do)
- `--format=FORMAT` - Output format: json (default) or text
- `--quiet` - Suppress non-essential output (default: false)
- `--verbose` - Show request/response details (default: false)

# Working with Multiple Accounts

Users may have access to multiple Fizzy accounts. To list boards or cards from a specific account:

```bash
# List boards in a specific account (use account ID number, no slash)
fizzy board list --account=6086023

# List cards in a specific account
fizzy card list --account=6074589
```

To see all accessible accounts, use:
```bash
fizzy identity show
```

This returns account info including the numeric ID (shown in the `slug` field, e.g., `/6086023` - use just the number part).

# Card Statuses

Cards can have the following statuses:
- `published` - Active/open cards
- `closed` - Completed cards
- `not_now` - Postponed cards (marked as not ready)

# Instructions

1. **Determine the action** - What does the user want to do? (list, create, update, move, close, etc.)
2. **Check for account context** - If the user wants data from a specific account, use `--account=ID` with the numeric account ID
3. **Run the appropriate fizzy command** using the Bash tool
4. **Parse the JSON output** (default format) to present results clearly
5. **Report the outcome** to the user in a readable format

# Common Workflows

## Creating a card with a description
```bash
fizzy card create --board=BOARD_ID --title="My Task" --description="<p>Task details here</p>"
```

## Moving a card to a column
First get the column ID:
```bash
fizzy column list --board=BOARD_ID
```
Then move the card:
```bash
fizzy card column CARD_NUMBER --column=COLUMN_ID
```

## Filtering cards by board
```bash
fizzy card list --board=BOARD_ID
```

## Filtering cards by status
```bash
fizzy card list --status=published    # Open cards
fizzy card list --status=closed       # Closed cards
fizzy card list --status=not_now      # Postponed cards
```

## Adding steps (to-do items) to a card
```bash
fizzy step create --card=CARD_NUMBER --content="Step 1: Do this"
fizzy step create --card=CARD_NUMBER --content="Step 2: Do that"
```

## Marking a step as completed
```bash
fizzy step update STEP_ID --card=CARD_NUMBER --completed
```
