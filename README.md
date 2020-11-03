# Example github-action-daemon with telegram-bot

Runs telegram bot https://t.me/github_action_daemon_bot

### Running bot

```yml
name: Running bot
on:
  push:
    branches:
      - main
  schedule:
    # # # # # # # # # #
    # restart each hour
    - cron: "0 */1 * * *"
    # # # # # # # # # # 

jobs:
  start:
    runs-on: ubuntu-latest
    name: Start

    steps:
      - uses: actions/checkout@v2

      - name: npm i
        run: npm i

      - uses: vladkosinov/github-action-daemon@v1.0.0
        env:
          BOT_TOKEN: ${{ secrets.BOT_TOKEN }}
        with:
          command: node ./index.js
```