# Weekly Report Generator

![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-blue)
![Shell](https://img.shields.io/badge/shell-zsh-yellow)
![AI](https://img.shields.io/badge/AI%20Powered-LLM-purple)

[English](README_EN.md) | [中文](README.md)

An AI Skill that automatically generates categorized weekly reports from Git commit history and manual input.

Compatible with any AI Agent that supports Skill/Tool invocation, including but not limited to:
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [OpenClaw](https://github.com/anthropics/openclaw)
- Other Agents that support the Markdown Skill format

## Features

- Automatically extracts git commits, supports **multiple project directories**
- Supports **manual text input** as supplementary data (meeting notes, TODOs, etc.) — works for non-developers too
- **Configurable date range**: this week / biweekly / monthly / custom date range
- **Three output templates**: dev report, manager report, project report
- Cross-platform: macOS and Linux

## Installation

Place this directory under the skills directory of your AI Agent. For example:

| Agent | Path |
|-------|------|
| Claude Code | `.claude/skills/` in your project root |
| OpenClaw | Search `generate-weekly-report` on Skill Hub, or install manually |

## Configuration

1. Copy the config template:

```bash
cp config.example.conf config.conf
```

2. Edit `config.conf`:

```bash
# Project directories (leave empty for non-developers, use manual input only)
PROJECT_DIRS=(
    "/home/user/project-a"
    "/home/user/project-b"
)

# Optional: specify git author (leave empty to auto-detect)
AUTHOR=""

# Date range: week, biweek, month, or custom like 2026-03-01,2026-03-21
DATE_RANGE="week"

# Output template: dev, manager, project
OUTPUT_TEMPLATE="dev"
```

## Usage

In your AI conversation, type:

```
/generate-weekly-report
```

### Manual Input

You can append extra text when invoking, which will be merged into the report:

```
/generate-weekly-report
Also attended security review meeting this week, pushed SSO integration forward, helped onboard new team members
```

Even without any git project configured, you can generate reports purely from manual input.

## Output Template Examples

### `dev` — Developer Report (default)

```
1. User Module: Added two-factor verification to login flow
2. Permission Management:
    - Batch configuration support for role permissions
    - Added operation audit logs
3. Data Export: Export tasks switched to async execution
```

### `manager` — Manager Report

```
Completed This Week:
1. Finished two-factor verification for user login
2. Permission management supports batch configuration

Next Week Plan:
1. Gradual rollout of two-factor verification
2. Improve audit log query for permission management

Risks & Blockers:
- None
```

### `project` — Project Report

```
User Center:
1. Added two-factor verification to login flow
2. Permission management supports batch configuration

Data Platform:
1. Export tasks switched to async execution
```

## Requirements

- macOS or Linux
- Git (if using git data source)
- Zsh (the script uses zsh array syntax)

## License

[MIT](LICENSE)
