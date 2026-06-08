# Claude Code 学习路线

基于仓库的完整内容探索，从零基础到高级，分为六个阶段。

---

## 🟢 第一阶段：安装与第一个对话（Day 0-1）

**目标**：在终端中与 Claude Code 完成第一次交互。

| 步骤 | 内容 | 资源 |
|------|------|------|
| 1 | 按操作系统安装 Claude Code | `tutorial/day0/` — [linux.md](tutorial/day0/linux.md)、[mac.md](tutorial/day0/mac.md)、[windows.md](tutorial/day0/windows.md) |
| 2 | 登录认证（订阅 / API Key / 团队邀请） | `tutorial/day0/README.md` |
| 3 | Level 1 — Prompting（直接提问） | `tutorial/day1/README.md` 的前半部分 |
| 4 | Level 2 — 理解 Agent（专人专事） | `tutorial/day1/README.md` 中间部分 |
| 5 | Level 3 — 理解 Skill（专项训练） | `tutorial/day1/README.md` 后半部分 |

> **关键认知**：Prompting → Agent → Skill 是**控制力递增**的三个层级。Prompting 只控制"问什么"；Agent 控制"谁回答"；Skill 控制"怎么做"。

---

## 🟡 第二阶段：核心概念理解（5 大基石）

**目标**：理解 Claude Code 的五大核心原语，建立心智模型。

| 顺序 | 概念 | 为什么先学这个 | 资源 |
|------|------|---------------|------|
| 1 | **Memory（记忆）** | 所有行为的基础——Claude 如何"知道"你的项目 | [best-practice/claude-memory.md](best-practice/claude-memory.md)、`CLAUDE.md`（本仓库的实际例子） |
| 2 | **Subagents（子代理）** | Agent 是最小的工作单元 | [best-practice/claude-subagents.md](best-practice/claude-subagents.md)、[implementation/claude-subagents-implementation.md](implementation/claude-subagents-implementation.md) |
| 3 | **Skills（技能）** | 给 Agent 装上具体能力 | [best-practice/claude-skills.md](best-practice/claude-skills.md)、[implementation/claude-skills-implementation.md](implementation/claude-skills-implementation.md) |
| 4 | **Commands（命令）** | 一键触发工作流 | [best-practice/claude-commands.md](best-practice/claude-commands.md)、[implementation/claude-commands-implementation.md](implementation/claude-commands-implementation.md) |
| 5 | **Settings（配置层级）** | 理解 5 层配置的优先级 | [best-practice/claude-settings.md](best-practice/claude-settings.md) |

> **关键认知**：这五个概念的关系是——Memory 提供上下文，Settings 控制行为边界，Agent 执行任务，Skill 赋予 Agent 专业能力，Command 作为一键入口串联一切。

---

## 🟠 第三阶段：动手实践 — Weather 工作流

**目标**：通过完整的 "Command → Agent → Skill" 示例深入理解编排模式。

| 步骤 | 内容 | 资源 |
|------|------|------|
| 1 | 阅读编排流程图 | [orchestration-workflow/orchestration-workflow.md](orchestration-workflow/orchestration-workflow.md) |
| 2 | 运行 `/weather-orchestrator` 命令 | 在终端执行 `claude` 然后 `/weather-orchestrator` |
| 3 | 阅读命令定义 | `.claude/commands/weather-orchestrator.md` |
| 4 | 阅读 Agent 定义 | `.claude/agents/weather-agent.md` |
| 5 | 阅读 Skill 定义（fetcher + svg creator） | `.claude/skills/weather-fetcher/SKILL.md`、`.claude/skills/weather-svg-creator/SKILL.md` |

> **关键认知**：两种 Skill 模式 — `weather-fetcher` 是 **agent skill**（通过 `skills:` 字段预加载到 agent 的上下文中），`weather-svg-creator` 是 **普通 skill**（通过 `Skill` 工具调用）。理解这种区别是设计高效工作流的关键。

---

## 🔵 第四阶段：进阶专题（按需深入）

**目标**：掌握生产级开发必备的专项能力。

| 专题 | 为什么重要 | 资源 |
|------|-----------|------|
| **Hooks 钩子系统** | 在工具调用前后执行确定性代码，是 "prompt 无法替代" 的能力之一 | `.claude/hooks/`、[reports/why-harness-is-important.md](reports/why-harness-is-important.md) |
| **MCP 服务器** | 扩展 Claude Code 的工具能力 | [best-practice/claude-mcp.md](best-practice/claude-mcp.md)、`.mcp.json` |
| **Context 管理与会话** | 1M 上下文窗口的正确使用方式——何时 compact、rewind、新建 session | [tips/claude-thariq-tips-16-apr-26.md](tips/claude-thariq-tips-16-apr-26.md) |
| **Agent Teams** | 多个 agent 并行工作 | [implementation/claude-agent-teams-implementation.md](implementation/claude-agent-teams-implementation.md) |
| **Scheduled Tasks** | 定时任务和自主循环 | [implementation/claude-scheduled-tasks-implementation.md](implementation/claude-scheduled-tasks-implementation.md) |
| **Browser Automation** | 让 Claude 操作浏览器 | [reports/claude-in-chrome-v-chrome-devtools-mcp.md](reports/claude-in-chrome-v-chrome-devtools-mcp.md) |

> **关键认知**：阅读 `reports/why-harness-is-important.md` — 它解释了为什么 Hooks、allowed-tools、context isolation 这些"Harness 层"的能力不能用更好的 prompt 替代。这是从 "Vibe Coding" 升级到 "Agentic Engineering" 的分水岭。

---

## 🟣 第五阶段：工作流方法论（83 条实战技巧 + 11 种工作流）

**目标**：建立自己的开发工作流，从社区最佳实践中学习。

### 5a. 按主题阅读 83 条技巧

按 README 的 Tips 分类逐类阅读：Prompting → Planning → Context → Session → CLAUDE.md → Agents → Commands → Skills → Hooks → Workflows → Git/PR → Debugging → Utilities

所有技巧在 `README.md` 的 [💡 TIPS AND TRICKS](README.md#tips-prompting) 章节，每个都有来源链接。

### 5b. 研究社区工作流

所有工作流遵循相同架构：**Research → Plan → Execute → Review → Ship**

| 排名 | 工作流 | 特色 |
|------|--------|------|
| 1 | [Superpowers](https://github.com/obra/superpowers) (216k ★) | brainstorming → plan → subagent-driven-development → review |
| 2 | [Everything Claude Code](https://github.com/affaan-m/everything-claude-code) (204k ★) | 63 agents + 121 commands + 300+ skills |
| 3 | [Spec Kit](https://github.com/github/spec-kit) (108k ★) | GitHub 官方 —— constitution → specify → plan → implement |

### 5c. 阅读深度报告

| 报告 | 内容 |
|------|------|
| [Agent vs Command vs Skill](reports/claude-agent-command-skill.md) | 何时用哪个 |
| [Agent SDK vs CLI](reports/claude-agent-sdk-vs-cli-system-prompts.md) | SDK 和 CLI 的区别 |
| [Why Harness is Important](reports/why-harness-is-important.md) | Harness 的 10 个不可替代能力 |
| [Skills in Monorepos](reports/claude-skills-for-larger-mono-repos.md) | 大型仓库的 Skill 管理 |
| [LLM Day-to-Day Degradation](reports/llm-day-to-day-degradation.md) | 模型输出质量波动 |
| [Advanced Tool Use](reports/claude-advanced-tool-use.md) | 工具使用进阶 |

---

## 🔴 第六阶段：专家级 — 构建自己的体系

**目标**：从"使用别人的工作流"到"设计自己的工作流"。

| 活动 | 说明 |
|------|------|
| **阅读 Boris Cherny 的全部建议** | `tips/claude-boris-*.md` — Claude Code 创建者的直接建议 |
| **收听核心视频/播客** | [Boris on Pragmatic Engineer](https://youtu.be/julbw1JuAz0)、[Boris on Lenny's Podcast](https://youtu.be/We7BZVKbCVw)、[Boris on Y Combinator](https://youtu.be/PQU9o_5rHC4) |
| **阅读 Hot Features** | README 的 🔥 Hot 表格 — Ultrareview、Agent Teams、Ralph Wiggum Loop、Git Worktrees 等 |
| **研究跨模型工作流** | Claude Code + Codex/Gemini 协作 |
| **从 Skill Collections 获取灵感** | [anthropics/skills](https://github.com/anthropics/skills)、[awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) |
| **每天更新 Claude Code** | `claude --version` + 阅读 [Changelog](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md) |

---

## 📋 学习路线总图

```
第一阶段 (1-2天)          第二阶段 (1周)             第三阶段 (1天)
安装 + 第一个对话    →    五大核心概念         →    Weather 工作流实战
Prompting/Agent/Skill     Memory/Subagents/          阅读 → 运行 → 理解
                          Skills/Commands/Settings

第四阶段 (2周)            第五阶段 (持续)             第六阶段 (持续)
进阶专题深入           →  工作流方法论            →   构建自己的体系
Hooks/MCP/Context/        83条技巧 + 11种工作流       Boris 深度内容
Agent-Teams/Browser       + 深度报告                  + 跨模型协作
```

---

## 💡 学习要点总结

1. **不要跳阶段**：很多新手直接跳到第五阶段（找别人的工作流直接用），跳过了第二阶段的概念理解。结果是遇到问题时不知道为什么出错，因为不理解底层机制。
2. **这个仓库的设计哲学就是渐进式学习**：README 的 CONCEPTS 表 → Tutorial Day 0/1 → Weather 编排示例 → Tips → Reports → Advanced。顺着这个顺序读效率最高。
3. **"Why Harness is Important" 是最重要的一篇报告**：它解释了为什么 Claude Code 不仅仅是"ChatGPT 套壳"——Harness 层提供了 prompt 无法替代的 10 种能力（context isolation、hook 拦截、权限分类等）。
