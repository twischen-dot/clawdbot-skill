# Clawdbot Communication Skill

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 概述

这是一个用于 OpenCode 与 Clawdbot 通信的 skill，实现了与 Natuo 代理的消息同步功能。

## 功能

- 通过 clawdbot CLI 向 Natuo 代理发送消息
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

## 使用方法

安装后，你可以在 OpenCode 对话中自然地请求与 Natuo 通信：

### 示例 1: 通知系统状态
```
通知 Natuo：系统配置已完成
```

### 示例 2: 记录事件
```
同步信息到 Natuo：SSH 隧道正在测试
```

### 示例 3: 发送提醒
```
告诉 main 代理：注意备份配置
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

## 开发

如果你想修改或扩展此 skill：

1. 编辑 `SKILL.md` 文件
2. 测试命令格式和错误处理
3. 提交更改

## 故障排查

### 命令执行失败
检查：
- `/opt/homebrew/bin/clawdbot` 是否存在
- 是否使用正确的参数：`--agent main`
- 消息是否用双引号正确包裹

### 代理无响应
- 检查 Clawdbot 网关是否运行
- 查看 Clawdbot 日志：`clawdbot logs`

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
