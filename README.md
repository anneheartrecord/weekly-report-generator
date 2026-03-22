# 周报生成器 / Weekly Report Generator

![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux-blue)
![Shell](https://img.shields.io/badge/shell-zsh-yellow)
![AI](https://img.shields.io/badge/AI%20Powered-LLM-purple)

中文 | [English](README_EN.md)

AI Skill：根据 Git 提交记录和手动输入，自动生成按模块归类的周报。

适用于任何支持 Skill/Tool 调用的 AI Agent，包括但不限于：
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [OpenClaw](https://github.com/anthropics/openclaw)
- 其他支持 Markdown Skill 格式的 Agent

## 功能

- 自动提取 git commit 记录，支持配置**多个项目目录**聚合
- 支持**手动输入文本**作为补充数据源（会议纪要、待办事项等），非程序员也能用
- **时间范围可配置**：本周 / 近两周 / 本月 / 自定义日期区间
- **三种输出模板**：开发周报、管理者周报、项目周报
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

2. 编辑 `config.conf`：

```bash
# 项目目录（非程序员可留空，仅使用手动输入）
PROJECT_DIRS=(
    "/home/user/project-a"
    "/home/user/project-b"
)

# 可选：指定 git author（留空则自动读取）
AUTHOR=""

# 时间范围：week（本周）、biweek（近两周）、month（本月）、自定义如 2026-03-01,2026-03-21
DATE_RANGE="week"

# 输出模板：dev（开发周报）、manager（管理者周报）、project（项目周报）
OUTPUT_TEMPLATE="dev"
```

## 使用

在 AI 对话中输入：

```
/generate-weekly-report
```

### 手动输入补充

可以在调用时附带额外文本，会自动合并到周报中：

```
/generate-weekly-report
本周还参加了安全评审会议，推动了 SSO 对接方案落地，协助新人熟悉开发流程
```

即使不配置任何 git 项目，也能纯靠手动输入生成周报。

## 输出模板示例

### `dev` — 开发周报（默认）

```
1. 用户模块：登录流程增加二次验证
2. 权限管理：
    - 角色权限支持批量配置
    - 新增操作审计日志
3. 数据导出：导出任务改为异步执行
```

### `manager` — 管理者周报

```
本周完成：
1. 完成用户登录流程二次验证功能
2. 权限管理支持批量配置

下周计划：
1. 二次验证功能上线灰度验证
2. 完善权限管理的审计日志查询

风险与阻塞：
- 无
```

### `project` — 项目周报

```
用户中心：
1. 登录流程增加二次验证
2. 权限管理支持批量配置

数据平台：
1. 导出任务改为异步执行
```

## 环境要求

- macOS 或 Linux
- Git（如使用 git 数据源）
- Zsh（脚本使用 zsh 数组语法）

## License

[MIT](LICENSE)
