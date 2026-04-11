---
name: 认知底座生成器
description: "认知底座生成器——从任何思维框架生成可安装的认知底座包。"
---

# Cognitive Base Creator

Generate complete cognitive base skill packages from any thinking framework or methodology.

Input: a thinking framework name (e.g., "first principles," "Bayesian reasoning," "systems thinking," "inversion," "design thinking").
Output: a full set of files that constitute a cognitive base skill, ready to install on any AI agent.

---

## What is a cognitive base skill

A cognitive base skill changes HOW the agent thinks, not WHAT it does. It operates at the meta-cognitive layer — always on, domain-agnostic, stackable with any domain skill.

Key properties:
- Instructions are meta-cognitive, not operational ("lead with judgment" vs "use 8px grid")
- No trigger conditions — active whenever the agent thinks
- Stacks with domain skills without conflict (OS vs app)
- Dual-layer architecture: ~30-line core rules (always-on) + ~120-line full framework (reference)

Reference implementation: the Tacit Knowledge project (based on Polanyi's theory). Repository: https://github.com/d-wwei/tacit-knowledge

---

## Generation workflow

### Phase 1: Framework analysis

Before generating anything, deeply understand the input framework:

1. **Core principles** — What are the 3-5 fundamental ideas? Not surface-level descriptions — the operational essence.
2. **Cognitive shift** — What does the framework change about default thinking? Map each principle to a shift: "Default mode → Target mode."
3. **Characteristic failure modes** — What mistakes do people (and agents) make when they think they're applying this framework but aren't? These become anti-patterns.
4. **Relationship to Tacit Knowledge** — Is it complementary, overlapping, or addressing a different axis? Define the stacking behavior.

### Phase 2: Generate files

Generate all 6 files in order. Each file has specific quality criteria below.

### Phase 3: Self-review

After generation, verify:
- [ ] cognitive-protocol.md body is pure operational instructions — no definitions, history, or academic citations (theory names allowed in title and section labels as anchors)
- [ ] Every instruction in cognitive-protocol.md is actionable by an LLM (not "understand deeply" but "before answering, list three constraints")
- [ ] Anti-patterns are unique to THIS framework, not duplicating Tacit Knowledge's 8 patterns
- [ ] Before/After examples show clear, measurable quality difference
- [ ] SKILL.md's cognitive shifts are genuinely meta-cognitive, not operational
- [ ] Install guides are accurate for each platform

---

## File specifications

### 1. cognitive-protocol.md (~30 lines)

The core rules file. Injected into always-on configuration. This is the most important file — it carries ~80% of the value.

**Format requirements:**
- Title: `# [Framework Name] — Cognitive Protocol`
- Opening line: `These rules apply to ALL tasks. No trigger needed. Always active.`
- 4-6 sections, each with a clear heading (verb phrase, not noun)
- Each section: 2-4 bullet points of operational instructions
- Final section: `## Output self-check (internal, not visible)` — 4-5 quick scan questions
- Total: ~30 lines of actual rules

**Content requirements:**
- Theory names allowed in title and section headings as anchors; body must be pure operational instructions
- NO definitions, NO history, NO academic citations in the body
- Every instruction must be directly executable: "Do X" or "Before Y, check Z"
- Instructions change the REASONING PROCESS, not the output format
- Banned phrases: "understand," "consider," "be aware of," "keep in mind" — these are not actions
- Good verbs: "identify," "list," "check," "reverse," "ask," "compare," "state," "name"

**Quality test:** Read only the bullet points under each heading. If they contain definitions, history, or "what X means" explanations, it's too theoretical. Every bullet should be an executable instruction.

### 2. SKILL.md (~120 lines)

The full reference framework. Loaded as a skill file for detailed guidance.

**Structure (follow exactly):**

```
# [Framework Name]

[One-line description of what this cognitive base does.]

[2-3 lines: not tied to any domain, stacks with domain skills, core rules in cognitive-protocol.md]

---

## 1. Cognitive Shifts (3-5 shifts)

### Shift N: [Default Mode] → [Target Mode]

Default: [what the agent does without this framework]
Target: [what the agent should do instead]

- [2-3 operational guidelines]

## 2. Information Filter

### [CATEGORY 1] — [Description]
[What to do with this type of information]

### [CATEGORY 2] — [Description]
[What to do with this type of information]

### [CATEGORY 3] — [Description]
[What to do with this type of information]

## 3. Anti-Pattern Checklist

[5-8 patterns, each with name, one-line description, and rewrite instruction]

## 4. Composing with Domain Skills

### Composition principles
[3 rules for how this cognitive base interacts with domain skills]

### Stacking examples
[3-4 examples: with design skill, coding skill, writing skill, standalone]

### Relationship to Tacit Knowledge
[Complementary/overlapping? Which loads first? Combined effect?]

## 5. Intensity Calibration

### Full intensity — [task type]
### Medium intensity — [task type]  
### Low intensity — [task type]
```

**Content requirements:**
- Cognitive shifts must be genuine DEFAULT → TARGET transformations, not "do good things"
- Information filter categories must be specific to this framework's way of processing information
- Anti-patterns must be UNIQUE to this framework — check against Tacit Knowledge's 8 patterns (empty balance, principle stacking, pseudo-depth, decorative opener, uncommitted recommendation, ungrounded framework, abstract ending, consultant voice) and avoid overlap
- Composition section must concretely describe how this framework interacts with Tacit Knowledge

### 3. anti-patterns.md (~100 lines)

Detailed anti-pattern reference with detection and fixes.

**Structure per pattern:**

```
## N. [Pattern Name]

**Pattern**: [One sentence describing the failure mode]

**Detection**:
- [Specific phrase or structure that signals this pattern]
- [Another signal]
- [Another signal]

**Fix**: [How to rewrite]

\`\`\`
❌ [Before example — realistic, 2-4 lines]
✅ [After example — same scenario, rewritten correctly]
\`\`\`
```

**Requirements:**
- 5-8 patterns, all SPECIFIC to this framework
- Detection signals must be concrete — specific phrases, structures, or reasoning patterns
- Before/After examples must be realistic scenarios, not toy examples
- End with a Quick Self-Check Sequence (ordered scan of where each pattern typically appears)

### 4. examples.md (~100 lines)

Three before/after scenarios demonstrating the framework in action.

**Structure per example:**

```
## Example N: [Domain/Scenario]

**User**: "[Realistic user question]"

### ❌ Before (default mode)

> [3-8 lines of typical default agent output]

**Problems**: [List which anti-patterns or missing shifts are visible]

### ✅ After (cognitive protocol active)

> [3-8 lines of improved output]

**Active shifts**: [List which cognitive shifts are active and how]
```

**Requirements:**
- Three DIFFERENT domains (e.g., technical, business, personal — vary them)
- Before examples must be realistic — the kind of output GPT-4/Claude actually produces
- After examples must be clearly better, not just differently formatted
- Problem and shift annotations help the reader understand WHY it's better

### 5. install.sh + install/ directory

Generate TWO things for installation:

**A. install.sh** (at repo root, executable)

A unified shell script that auto-detects installed AI agents and installs the cognitive base to all of them. The install.sh is IDENTICAL across all cognitive base repos — BASE_NAME is auto-derived from the directory name, SKILL_FILES are discovered dynamically.

Copy the canonical install.sh from any existing cognitive base repo (e.g., https://github.com/d-wwei/first-principles/install.sh) and include it unchanged.

The install.sh supports 6 agents with dual-mode injection:

| Agent | Config File | Default Mode | Protocol Location |
|---|---|---|---|
| Claude Code | `~/.claude/CLAUDE.md` | @ ref | `~/.claude/{base}.md` |
| Gemini CLI | `~/.gemini/GEMINI.md` | @ ref | `~/.gemini/{base}.md` |
| Codex CLI | `~/.codex/AGENTS.md` | inline | in AGENTS.md |
| Cursor | `.cursor/rules/*.mdc` | .mdc file | `.cursor/rules/cognitive-base-{base}.mdc` |
| OpenCode | `~/.config/opencode/AGENTS.md` | inline | in AGENTS.md |
| OpenClaw | `~/.openclaw/workspace/AGENTS.md` | inline | in AGENTS.md |

Features: auto-detection, idempotency (marker comments), `--uninstall`, `--status`, `--inline` fallback, mode switching.

**B. install/ directory** (4 markdown files, documentation/manual reference)

Keep the 4 platform-specific markdown files as human-readable guides. Each should begin with:

> **Recommended**: Run `./install.sh` from the repo root for automated installation.

Then follow the existing format for manual steps. Update generic.md to cover all 6 agents.

- **claude-code.md**: Documents both @ ref mode (default) and inline mode, skill file installation, verify, uninstall
- **codex.md**: AGENTS.md inline injection, what to include
- **gemini.md**: Both @ ref mode and inline mode, API and AI Studio methods
- **generic.md**: Universal principle, 6-agent platform mapping table, step-by-step, file selection guide, troubleshooting

**CRITICAL**: The install.sh defaults to `@` reference mode for Claude Code and Gemini CLI (cleaner, easier to update), and inline mode with marker comments for agents that don't support `@` references. The `--inline` flag forces inline mode for all agents. Both modes are idempotent and cleanly uninstallable.

### 6. README.md

Project documentation. Follow tacit-knowledge's README structure:

```
# [Framework Name]

[One paragraph: what it does, works with any agent]

## What it does

[The problem it solves + how]

### Before (default agent)
> [Short example]

### After (with [Framework Name])
> [Short example]

## How it works

[Cognitive shifts table + information filter + anti-pattern gate]

## Installation

[Quick install for Claude Code, Codex, Gemini, generic]

## File structure

[Tree diagram]

## Composability

[Stacking with domain skills + relationship to Tacit Knowledge]

## Theoretical foundation

[1 paragraph: which theory, what insight, link to further reading if applicable]

## License

MIT
```

---

## Design principles (enforce during generation)

1. **Meta-cognitive, not operational**
   - Every instruction must change HOW the agent reasons, not WHAT it outputs
   - Test: "Does this instruction apply regardless of whether the agent is writing code, designing UI, or giving career advice?" If no, it's operational — rewrite or remove.

2. **Body is operational, not academic**
   - Title and section headings may use theory names as anchors (e.g., `# First Principles — Cognitive Protocol`)
   - The body under each heading must be pure operational instructions — no definitions, history, or academic citations
   - Detailed theory explanations, academic context, and further reading go in SKILL.md and README.md

3. **Framework-specific anti-patterns**
   - Each framework has characteristic failure modes that are DIFFERENT from generic output quality issues
   - Tacit Knowledge already covers: empty balance, principle stacking, pseudo-depth, decorative opener, uncommitted recommendation, ungrounded framework, abstract ending, consultant voice
   - New anti-patterns must target failures specific to the framework being generated
   - Example: "First Principles" might have "analogy substitution" (using analogies instead of decomposing), "authority anchoring" (citing experts instead of reasoning from scratch)

4. **Explicit Tacit Knowledge relationship**
   - Every cognitive base must define its relationship to Tacit Knowledge (the foundational base layer)
   - Options: complementary (different axis), reinforcing (same axis, different depth), specialized (subset with more detail)
   - Must specify stacking order and conflict resolution

5. **Realistic examples**
   - Before examples should be indistinguishable from actual LLM output
   - After examples should be clearly, measurably better — not just "more words" or "different structure"
   - The quality gap should be obvious to someone who has never heard of the framework

---

## Output structure

When generating, create all files under a directory named after the framework (kebab-case):

```
[framework-name]/
├── README.md
├── cognitive-protocol.md
├── SKILL.md
├── anti-patterns.md
├── examples.md
├── install.sh                 ← unified installer (executable, identical across repos)
└── install/
    ├── claude-code.md         ← manual reference
    ├── codex.md               ← manual reference
    ├── gemini.md              ← manual reference
    └── generic.md             ← manual reference (covers all 6 agents)
```

Write files to the current working directory: `./[framework-name]/`

After generating, offer to install for the user's platform:

| Method | Command |
|---|---|
| Automated (recommended) | `cd [framework-name] && chmod +x install.sh && ./install.sh` |
| Specific agent only | `./install.sh --agent=claude-code` |
| Inline mode (no @ refs) | `./install.sh --inline` |
| Manual | See `install/` directory guides |

If the user's platform is unknown, ask before installing. The install.sh auto-detects installed agents.

---

## Intensity calibration for the Creator itself

**Full generation** (default): All 6 files, complete content, ready to install.

**Quick draft**: cognitive-protocol.md + SKILL.md only. Enough to test the framework. User can request the rest later.

**Review mode**: User provides an existing cognitive base. Creator reviews against the quality criteria and suggests improvements.