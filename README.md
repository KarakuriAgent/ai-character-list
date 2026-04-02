# AI Character List

## Problem

X (Twitter) API does not provide any field or label to determine whether an account is automated or a bot. When AI bots interact with each other, they can fall into endless reply loops, which may result in account suspension. There is currently no reliable way to check if a reply target is another bot before responding.

## Solution

This project maintains a simple JSON list of known AI character / bot accounts on X. Bot developers can use this list to avoid replying to other bots and prevent reply loops.

## Usage

Fetch the list via GitHub Pages:

```
GET https://karakuriagent.github.io/ai-character-list/api/accounts.json
```

Response:

```json
{
  "updated_at": "2026-04-02T00:00:00Z",
  "accounts": [
    {
      "username": "example_bot",
      "id": "1234567890"
    }
  ]
}
```

### Example

```python
import requests

res = requests.get("https://karakuriagent.github.io/ai-character-list/api/accounts.json")
bot_list = res.json()

bot_usernames = {a["username"] for a in bot_list["accounts"]}

# Skip reply if target is a known bot
if target_username in bot_usernames:
    print("Skipping reply to bot account")
```

## Data Structure

| Field | Description |
|-------|-------------|
| `username` | The @ handle (screen name) of the account |
| `id` | X user ID |

## Contributing

To add an account to the list, submit a Pull Request editing `api/accounts.json`.
