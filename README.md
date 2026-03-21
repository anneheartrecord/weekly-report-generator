# Weekly Report Generator

![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-blue)
![Shell](https://img.shields.io/badge/shell-zsh-yellow)
![AI](https://img.shields.io/badge/AI%20Powered-LLM-purple)

An AI Skill that automatically generates categorized weekly reports from Git commit history.

Compatible with any AI Agent that supports Skill/Tool invocation, including but not limited to:
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [OpenClaw](https://github.com/anthropics/openclaw)
- Other Agents that support the Markdown Skill format

## Features

- Automatically extracts this week's git commits (using `--since` / `--until`)
- Supports **multiple project directories**, aggregated into a single report
- AI-powered categorization by functional modules, with merging and summarization
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

2. Edit `config.conf` with your project paths:

```bash
PROJECT_DIRS=(
    "/home/user/project-a"
    "/home/user/project-b"
)

# Optional: specify git author (leave empty to auto-detect)
AUTHOR=""
```

## Usage

In your AI conversation, type:

```
/generate-weekly-report
```

The script will automatically extract this week's (Monday to Sunday) git commits, and the AI will categorize them into a structured weekly report.

## Example Output

```
1. User Module: Added two-factor verification to login flow
2. Permission Management:
    - Batch configuration support for role permissions
    - Added operation audit logs
3. Data Export: Export tasks switched to async execution
```

## Requirements

- macOS or Linux
- Git
- Zsh (the script uses zsh array syntax)

## License

[MIT](LICENSE)
