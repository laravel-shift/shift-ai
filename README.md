# Shift AI
A set of AI skills and commands for managing the entire [Shift](https://laravelshift.com) process. Determine what Shift needs to be run, open a PR, and review it for additional automation all from your AI of choice.

## Installation
To use these commands, you may add the marketplace and install globally with Claude Code:

```
/plugin marketplace add laravel-shift/shift-ai
/plugin install shift@laravel-shift --scope user
```

The `--scope user` flag installs the commands once for your entire system — no per-project setup needed.

## Commands
- `/shift:analyze` — analyze your project and determine the next Shift to run
- `/shift:run` — trigger a Shift to run against your current repository
- `/shift:review` — review and process the Shift PR for additional automation
- `/shift:refactor` — run a [Shift Workbench](https://laravelshift.com/workbench) task to refactor your code

**Note:** These commands are being beta tested. As such, the `/shift:run` command is currently limited to subscribers of a [Shifty Plan](https://laravelshift.com/shifty-plans). Once tested, these commands will be made available to all Shift users.

## Requirements
- [`gh`](https://cli.github.com) — required by the `/shift:review` command to interact with GitHub pull requests
