# Cognitive Base Creator

A meta-skill for AI agents: give it any thinking framework, and it generates a complete **cognitive base skill** — ready to install on Claude Code, Codex, Gemini, Cursor, or any LLM-based agent.

**[中文说明见下方](#中文说明)**

---

## What problem does this solve?

The AI agent skill ecosystem is booming — design skills, coding skills, writing skills. But they all solve one problem: **what** to do. Nobody is solving the other problem: **how** to think.

A cognitive base skill is a different category of skill. It doesn't teach the agent to do a specific task — it changes the agent's reasoning process, improving the quality of **all** tasks.

| | Domain Skill | Cognitive Base Skill |
|---|---|---|
| Analogy | A recipe | Knife technique |
| Layer | Operational (what to do) | Meta-cognitive (how to think) |
| Scope | One task type | All tasks |
| Effect | Directly determines output | Changes reasoning, indirectly improves output |

This Creator automates the generation of cognitive base skills from any thinking framework.

## How it works

Give the Creator a framework name:

> "Generate a cognitive base from first principles thinking"

It produces a complete, installable package:

```
first-principles/
├── README.md                  ← Project documentation
├── cognitive-protocol.md      ← Core rules (~30 lines, always-on)
├── SKILL.md                   ← Full framework (~120 lines, reference)
├── anti-patterns.md           ← Framework-specific failure modes
├── examples.md                ← 3 before/after comparisons
└── install/
    ├── claude-code.md         ← Claude Code installation
    ├── codex.md               ← Codex installation
    ├── gemini.md              ← Gemini installation
    └── generic.md             ← Any other agent
```

### Generation pipeline

1. **Framework Analysis** — Extract core principles, map cognitive shifts, identify characteristic failure modes
2. **File Generation** — Produce all 6 files following strict quality specs
3. **Self-Review** — Verify: no theory names in core rules, all instructions are actionable, anti-patterns are unique

### What makes a good cognitive base

The Creator enforces these design principles:

- **Meta-cognitive, not operational** — "Before answering, list three constraints" (meta) vs "Use 8px grid" (operational)
- **No theory in core rules** — `cognitive-protocol.md` reads as pure instructions. If you can identify the theory from the rules alone, it's too theoretical.
- **Framework-specific anti-patterns** — Each framework has unique failure modes, not generic quality issues
- **Stackable** — Every cognitive base defines its relationship to [Tacit Knowledge](https://github.com/d-wwei/tacit-knowledge) (the foundational base layer) and to domain skills

## Installation

This skill works on **any** AI agent platform.

### Claude Code

```bash
mkdir -p ~/.claude/skills/cognitive-base-creator
cp SKILL.md ~/.claude/skills/cognitive-base-creator/
```

### Codex

Add the contents of `SKILL.md` to your `AGENTS.md` or system prompt.

### Gemini

Add the contents of `SKILL.md` to your system instructions (API `system_instruction` field or AI Studio).

### Cursor / Cline / Continue / Any other agent

Paste the contents of `SKILL.md` into whatever file your agent reads as instructions on startup.

## Example output

Using [Tacit Knowledge](https://github.com/d-wwei/tacit-knowledge) as a reference — the first cognitive base skill built with this approach:

**Core rules** (`cognitive-protocol.md`, 30 lines):
```
## Lead with judgment
- First sentence must be a directional judgment, not a preamble.
- When uncertain: "My judgment leans toward X because…" — not a pros/cons list.

## Information hierarchy
- One core judgment first (focal point), then 2-3 supporting signals.
- Proactively surface what experienced practitioners know but rarely say.
```

**Before** (default agent):
> "Microservices and monoliths each have pros and cons. The choice depends on your team size and business complexity."

**After** (with cognitive base):
> "Stay on the monolith. With 8 people, the coordination cost of microservices will eat all the gains. Fix your module boundaries first — that's the actual problem."

## Relationship to Tacit Knowledge

[Tacit Knowledge](https://github.com/d-wwei/tacit-knowledge) is the first and foundational cognitive base skill. It provides general reasoning quality improvements (commitment, hierarchy, indwelling, holism).

This Creator generates **additional** cognitive bases that stack on top of Tacit Knowledge. Each generated base:
- Defines whether it's complementary, reinforcing, or specialized
- Specifies stacking order and conflict resolution
- Has anti-patterns that don't overlap with Tacit Knowledge's 8 patterns

Think of it this way:
- **Tacit Knowledge** = the base operating system
- **Generated cognitive bases** = kernel modules that extend it
- **Domain skills** = applications that run on top

## Deep dive

📖 **[What is a Cognitive Base? (中文)](docs/article-zh.md)** — A detailed article explaining the concept, with 3 real before/after scenarios and design principles.

## File structure

```
cognitive-base-creator/
├── README.md       ← You are here
├── SKILL.md        ← The Creator skill (the only file you need)
└── docs/
    ├── article-zh.md   ← 认知基座详解文章（中文）
    └── images/         ← Article illustrations
```

## License

MIT

---

<a name="中文说明"></a>

# 认知底座 Creator

一个 AI Agent 的元技能：给它任意一个思维框架，它会自动生成一套完整的**认知底座 Skill** —— 可直接安装在 Claude Code、Codex、Gemini、Cursor 或任何基于 LLM 的 Agent 上。

## 解决什么问题？

AI Agent 的 Skill 生态正在快速膨胀 —— 设计 Skill、编程 Skill、写作 Skill。但它们全部在解决同一个问题：**做什么**。没有人在解决另一个问题：**怎么想**。

认知底座 Skill 是一个不同类别的 Skill。它不教 Agent 做某个任务 —— 它改变 Agent 的推理过程，提升**所有**任务的质量。

| | 领域 Skill | 认知底座 Skill |
|---|---|---|
| 类比 | 一道菜的菜谱 | 拿刀的方式 |
| 作用层面 | 操作层（做什么） | 元认知层（怎么想） |
| 绑定范围 | 特定任务类型 | 所有任务 |
| 影响路径 | 直接决定输出 | 改变推理过程，间接提升输出 |

这个 Creator 能从任何思维框架自动生成认知底座 Skill。

## 工作原理

给 Creator 一个框架名称：

> "用第一性原理帮我创建一个认知底座 Skill"

它会生成完整的、可安装的文件包：

```
first-principles/
├── README.md                  ← 项目说明
├── cognitive-protocol.md      ← 核心规则（~30 行，始终加载）
├── SKILL.md                   ← 完整框架（~120 行，按需参考）
├── anti-patterns.md           ← 该框架特有的思维反模式
├── examples.md                ← 3 个 Before/After 对比
└── install/
    ├── claude-code.md         ← Claude Code 安装指南
    ├── codex.md               ← Codex 安装指南
    ├── gemini.md              ← Gemini 安装指南
    └── generic.md             ← 其他 Agent 通用安装
```

### 生成流程

1. **框架分析** —— 提取核心原则，映射认知转换，识别特征性失败模式
2. **文件生成** —— 按严格质量规格生成全部 6 个文件
3. **自检** —— 验证：核心规则不含理论名字、所有指令可执行、反模式不重复

### 好的认知底座什么样

Creator 强制执行以下设计原则：

- **元认知而非操作层** —— "回答前先列出三个约束条件"（元认知） vs "使用 8px 网格"（操作层）
- **核心规则不提理论** —— `cognitive-protocol.md` 是纯操作指令。如果能从规则猜出理论来源，说明太理论化了
- **框架特有的反模式** —— 每个框架有独特的失败模式，不是通用质量问题
- **可叠加** —— 每个认知底座都定义与 [Tacit Knowledge](https://github.com/d-wwei/tacit-knowledge)（基础底座）及领域 Skill 的关系

## 安装

这个 Skill 适用于**任何** AI Agent 平台。

### Claude Code

```bash
mkdir -p ~/.claude/skills/cognitive-base-creator
cp SKILL.md ~/.claude/skills/cognitive-base-creator/
```

### Codex

将 `SKILL.md` 的内容添加到 `AGENTS.md` 或 system prompt 中。

### Gemini

将 `SKILL.md` 的内容添加到 system instructions（API 的 `system_instruction` 字段或 AI Studio）。

### Cursor / Cline / Continue / 其他 Agent

将 `SKILL.md` 的内容粘贴到你的 Agent 启动时读取的指令文件中。

## 深度阅读

📖 **[所有 Agent 都缺了 Skill 无法解决的一层：认知基座](docs/article-zh.md)** — 详细解释认知基座概念，包含 3 个真实 Before/After 场景对比和设计原则。

## 与 Tacit Knowledge 的关系

[Tacit Knowledge](https://github.com/d-wwei/tacit-knowledge) 是第一个也是基础的认知底座 Skill，提供通用推理质量提升（承诺、层级、内居、整体）。

这个 Creator 生成**额外的**认知底座，叠加在 Tacit Knowledge 之上。每个生成的底座：
- 定义与 Tacit Knowledge 的关系（互补、增强、特化）
- 指定叠加顺序和冲突处理
- 反模式不与 Tacit Knowledge 的 8 个反模式重复

架构关系：
- **Tacit Knowledge** = 基础操作系统
- **生成的认知底座** = 扩展内核模块
- **领域 Skill** = 运行在上层的应用

## 许可证

MIT
