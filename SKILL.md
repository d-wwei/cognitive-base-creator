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
- [ ] cognitive-protocol.md contains zero theory names — only operational instructions
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
- NO theory names, NO jargon, NO academic references
- Every instruction must be directly executable: "Do X" or "Before Y, check Z"
- Instructions change the REASONING PROCESS, not the output format
- Banned phrases: "understand," "consider," "be aware of," "keep in mind" — these are not actions
- Good verbs: "identify," "list," "check," "reverse," "ask," "compare," "state," "name"

**Quality test:** If you remove the title, can you tell which theory it's based on? If yes, it's too theoretical. Strip further.

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

### 5. install/ directory (4 files)

Platform-specific installation guides. Follow the exact structure from tacit-knowledge's install files:

- **claude-code.md**: mkdir + cp commands, CLAUDE.md injection, two-layer table, verify, uninstall
- **codex.md**: AGENTS.md method, system prompt method, custom instructions method, what to include
- **gemini.md**: system_instruction API, AI Studio, CLI/framework, what to include
- **generic.md**: universal principle, agent/framework table, step-by-step, file selection guide, troubleshooting

Replace all references to "tacit-knowledge" with the new framework's name and directory.

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

2. **No theory in cognitive-protocol.md**
   - The core rules file must read as pure operational instructions
   - Theory names, academic jargon, and framework labels go in SKILL.md and README.md only
   - The agent should apply the rules without knowing which theory they come from

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
└── install/
    ├── claude-code.md
    ├── codex.md
    ├── gemini.md
    └── generic.md
```

Write files to the current working directory: `./[framework-name]/`

After generating, offer to install for the user's platform. Installation maps:

| Platform | Core rules destination | Skill files destination |
|---|---|---|
| Claude Code | `~/.claude/[name].md` (ref in `CLAUDE.md`) | `~/.claude/skills/[name]/` |
| Codex | Prepend to `AGENTS.md` | Project directory |
| Gemini | `system_instruction` field | Project directory |
| Cursor | Prepend to `.cursorrules` | Project directory |
| Any other | Prepend to system prompt / instructions file | Project directory |

If the user's platform is unknown, ask before installing. If the user wants multi-platform install, run all applicable steps.

---

## Intensity calibration for the Creator itself

**Full generation** (default): All 6 files, complete content, ready to install.

**Quick draft**: cognitive-protocol.md + SKILL.md only. Enough to test the framework. User can request the rest later.

**Review mode**: User provides an existing cognitive base. Creator reviews against the quality criteria and suggests improvements.
