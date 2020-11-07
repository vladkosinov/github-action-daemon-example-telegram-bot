# Example github-action-daemon with telegram-bot

Runs telegram bot using Github Actions.

Write to the bot by yourself: [t.me/github_action_daemon_bot](https://t.me/github_action_daemon_bot)

And check logs here: https://github.com/vladkosinov/github-action-daemon-example-telegram-bot/actions

![Check last running workflow](./screenshot.jpg)


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
