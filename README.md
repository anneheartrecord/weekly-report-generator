# 周报生成器 / Weekly Report Generator

![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-blue)
![Shell](https://img.shields.io/badge/shell-zsh-yellow)
![AI](https://img.shields.io/badge/AI%20Powered-LLM-purple)

AI Skill：根据 Git 提交记录自动生成按模块归类的中文周报。

适用于任何支持 Skill/Tool 调用的 AI Agent，包括但不限于：
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [OpenClaw](https://github.com/anthropics/openclaw)
- 其他支持 Markdown Skill 格式的 Agent

## 功能

- 自动提取本周 git commit 记录（基于 `--since` / `--until`）
- 支持配置**多个项目目录**，聚合生成一份周报
- AI 自动按功能模块归类、合并、简化输出
- 兼容 macOS 和 Linux

## 安装

将本目录放置到对应 Agent 的 skills 目录下即可。例如：

| Agent | 放置路径 |
|-------|---------|
| Claude Code | 项目根目录下的 `.claude/skills/` |
| OpenClaw | Skill Hub 搜索 `generate-weekly-report` 或手动放置 |

## 配置

1. 复制配置模板：

```bash
cp config.example.conf config.conf
```

2. 编辑 `config.conf`，填入你的项目路径：

```bash
PROJECT_DIRS=(
    "/home/user/project-a"
    "/home/user/project-b"
)

# 可选：指定 git author（留空则自动读取）
AUTHOR=""
```

## 使用

在 AI 对话中输入：

```
/generate-weekly-report
```

脚本会自动提取本周（周一到周日）的 git 提交记录，AI 将其归类为结构化周报。

## 输出示例

```
1. 用户模块：登录流程增加二次验证
2. 权限管理：
    - 角色权限支持批量配置
    - 新增操作审计日志
3. 数据导出：导出任务改为异步执行
```

## 环境要求

- macOS 或 Linux
- Git
- Zsh（脚本使用 zsh 数组语法）

## License

[MIT](LICENSE)
