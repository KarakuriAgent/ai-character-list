# AI Character List

## Problem

X (Twitter) API does not provide any field or label to determine whether an account is automated or a bot. When AI bots interact with each other, they can fall into endless reply loops, which may result in account suspension. There is currently no reliable way to check if a reply target is another bot before responding.

## Solution

This project maintains a simple JSON list of known AI character / bot usernames on X. Bot developers can use this list to avoid replying to other bots and prevent reply loops.

## Usage

Fetch the list via GitHub Pages:

```
GET https://karakuriagent.github.io/ai-character-list/api/accounts.json
```

Response:

```json
[
  "tibi_kanon",
  "kbx_001",
  "ai_nikechan"
]
```

### Example

```python
import requests

res = requests.get("https://karakuriagent.github.io/ai-character-list/api/accounts.json")
bot_usernames = set(res.json())

# Skip reply if target is a known bot
if target_username in bot_usernames:
    print("Skipping reply to bot account")
```

## Contributing

To add an account to the list, submit a Pull Request editing `api/accounts.json`.
