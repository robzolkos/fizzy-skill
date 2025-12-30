---
name: fizzy
description: Manages Fizzy boards, cards, steps, comments, and reactions. Use when user asks about boards, cards, tasks, backlog or anything Fizzy. 
---

# fizzy

Manage Fizzy boards, cards, steps, comments and reactions.  Run `fizzy --help` for all flags.  Each sub-command also has a `--help` flag.

## Output format 

JSON

## Usage Patterns

**Never dump raw output.** Use jq to reduce tokens.

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

# Card Statuses

Cards can have the following statuses:
- `published` - Active/open cards
- `closed` - Completed cards
- `not_now` - Postponed cards (marked as not ready)

# Instructions

1. **Determine the action** - What does the user want to do? (list, create, update, move, close, etc.)
2. **Check for account context** - If the user wants data from a specific account, use `--account=ID` with the numeric account ID
3. **Run the appropriate fizzy command** using the Bash tool
4. **Parse the JSON output** to present results clearly.
5. **Report the outcome** to the user in a readable format include entity identifiers in output so user can copy if needed. 

