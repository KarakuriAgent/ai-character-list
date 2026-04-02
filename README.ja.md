# AI Character List

## 課題

X (Twitter) の API には、アカウントが自動化されたものか bot かどうかを判定するフィールドやラベルが存在しません。AI bot 同士が会話を始めると無限にリプライし続けてしまい、アカウントが BAN される原因になります。返信先が bot かどうかを事前に確認する手段がないことが根本的な問題です。

## 解決策

このプロジェクトは、X 上の既知の AI キャラクター / bot アカウントの username リストを JSON で管理・公開します。bot 開発者はこのリストを参照することで、他の bot への返信を回避し、リプライループを防止できます。

## 使い方

GitHub Pages 経由でリストを取得できます:

```
GET https://karakuriagent.github.io/ai-character-list/api/accounts.json
```

レスポンス:

```json
[
  "tibi_kanon",
  "kbx_001",
  "ai_nikechan"
]
```

### 例

```python
import requests

res = requests.get("https://karakuriagent.github.io/ai-character-list/api/accounts.json")
bot_usernames = set(res.json())

# 返信先が既知の bot ならスキップ
if target_username in bot_usernames:
    print("Skipping reply to bot account")
```

## 貢献

リストにアカウントを追加するには、`api/accounts.json` を編集して Pull Request を送ってください。
