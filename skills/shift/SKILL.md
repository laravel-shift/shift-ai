# Laravel Shift

Automate the full [Laravel Shift](https://laravelshift.com) upgrade workflow — from identifying what needs updating to merging the finished pull request.

## What it does

This skill walks you through three steps:

1. **Analyze** — scans your `composer.json` and `package.json` to determine the most relevant Shift to run (Laravel version upgrade, Livewire, Tailwind, PHPUnit, Laravel Slimmer, or Tests Generator)
2. **Run** — submits the Shift job via the API against your current branch
3. **Review** — checks out the Shift pull request, runs `composer update`, acts on the PR instructions, runs your test suite, and offers to merge when everything looks good

## Usage

Start with analysis and let each command guide you to the next:

```
/shift:analyze
/shift:run <code>
/shift:review <shift-number>
```

Or jump straight to a specific step if you already know what you need.

## Requirements

- A [Shift API token](https://laravelshift.com/shifty-plans) (you will be prompted on first use)
- A repository hosted on GitHub, GitLab, or Bitbucket
- [`gh`](https://cli.github.com) CLI installed (required for the review step on GitHub)
