# Clawdbot Communication Skill

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 概述

这是一个用于 OpenCode 与 Clawdbot 通信的 skill，实现了向 Clawdbot 代理发送消息的功能。

**重要说明**：此 skill 预设使用 `main` 代理名称（身份为 Natuo）。如需使用其他代理，请修改 SKILL.md 中的代理名称配置。

## 功能

- 通过 clawdbot CLI 向指定代理发送消息
- 实现多代理之间的信息同步
- 支持状态记录和通知功能

## 系统要求

- **macOS**
- **OpenCode**
- **Clawdbot CLI** (已安装)
- **GitHub CLI** (用于安装)

## 安装

使用 GitHub CLI 安装此 skill：

```bash
gh repo clone twischen-dot/clawdbot-skill
cd clawdbot-skill
cp SKILL.md ~/.claude/skills/clawdbot/SKILL.md
```

### 配置你的代理名称

此 skill 预设使用 `main` 代理名称。如需修改为其他代理：

1. 编辑 `~/.claude/skills/clawdbot/SKILL.md`
2. 找到 `--agent main` 部分
3. 将 `main` 替换为你自己的 Clawdbot 代理名称（如 `ops`、`assistant` 等）

**如何查看你的代理名称**：
```bash
clawdbot agents list
```

## 使用方法

安装后，你可以在 OpenCode 对话中自然地请求通信（消息会发送到 main 代理）：

### 示例 1: 通知系统状态
```
通知：系统配置已完成
```

### 示例 2: 记录事件
```
同步信息：SSH 隧道正在测试
```

### 示例 3: 发送提醒
```
告诉代理：注意备份配置
```

### 示例 4: 状态同步
```
记录状态：任务已进入测试阶段
```

## 工作原理

1. OpenCode 识别用户的通信请求
2. 构建标准命令：`clawdbot agent --agent main --message "..."`
3. 执行命令发送消息
4. 返回通信结果

## Skill 结构

```
clawdbot/
└── SKILL.md    # Skill 定义文件
```

## 自定义配置

### 修改代理名称

默认情况下，skill 使用 `main` 作为代理名称。如需修改为其他代理：

1. 查看你的代理列表：`clawdbot agents list`
2. 编辑 `~/.claude/skills/clawdbot/SKILL.md`
3. 将 `--agent main` 中的 `main` 替换为你的实际代理名

### 示例配置

如果你需要使用其他代理（如 `assistant`），修改 `SKILL.md` 中的命令：

```bash
# 修改前（使用 main）
clawdbot agent --agent main --message "..."

# 修改后（使用 assistant）
clawdbot agent --agent assistant --message "..."
```

## 开发

如果你想修改或扩展此 skill：

1. 编辑 `SKILL.md` 文件
2. 根据你的 Clawdbot 配置调整代理名称
3. 测试命令格式和错误处理
4. 提交更改

## 故障排查

### 命令执行失败
检查：
- `/opt/homebrew/bin/clawdbot` 是否存在
- 是否使用正确的代理名称：`--agent main`（或你配置的其他代理名）
- 消息是否用双引号正确包裹

### 找不到代理
- 查看你的代理列表：`clawdbot agents list`
- 确认 SKILL.md 中配置的代理名称与你的实际配置一致

### 代理无响应
- 检查 Clawdbot 网关是否运行：`clawdbot health`
- 查看 Clawdbot 日志：`clawdbot logs`

## 常见问题

**Q: 如何知道我的代理名称？**
A: 运行 `clawdbot agents list` 查看所有可用代理。

**Q: 可以向多个代理发送消息吗？**
A: 可以，只需要修改 SKILL.md 或在命令中指定代理名称。

**Q: 文档中的 "main" 是什么？**
A: 这是本 skill 预设使用的代理名称（配置为 Natuo）。你可以修改为任何其他你已经配置的 Clawdbot 代理名称。

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License

## 作者

Created for OpenCode + Clawdbot integration

## 相关链接

- [OpenCode](https://github.com/OhMyOpenCode)
- [Clawdbot](https://docs.clawd.bot)
- [Clawd Documentation](https://docs.clawd.bot/cli)

---

**Version**: 1.0.0  
**Last Updated**: 2026-01-28