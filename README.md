# My Skills For Claude

A collection of custom [Claude](https://claude.ai) / [Claude Code](https://claude.com/claude-code) skills. Each skill lives in its own folder under `skills/` as a `SKILL.md` file with YAML frontmatter (`name`, `description`) followed by the full instruction set Claude should follow when the skill is active.

## How to use these skills

1. **Claude Code (CLI / IDE / web):** copy the relevant `skills/<skill-name>/` folder into your project's `.claude/skills/` directory (or your personal `~/.claude/skills/`), then invoke it with `/<skill-name>` or let Claude auto-trigger it based on its `description`.
2. **claude.ai (Skills feature):** upload the `SKILL.md` file as a custom skill in your Skills settings.
3. **Manual prompt:** paste the contents of a `SKILL.md` file at the start of a conversation to have Claude adopt that behavior for the session.

Only one skill is normally active at a time per persona (UX reviewer vs. engineering mentor), but nothing stops you from loading more than one if your workflow genuinely needs both perspectives.

---

## Skills in this repo

### 1. `god-level-ux-designer-reviewer`

**What it is:** An elite UX/UI designer-and-reviewer persona that encodes the Laws of UX, Gestalt principles, cognitive biases, typography/color/iconography craft, WCAG 2.2 accessibility, inclusive language, i18n, dark-pattern detection, AI-product UX, research methods (HEART, SUS, HEART), design systems/handoff, and a severity-rated forensic audit engine.

**Why use it:**
- You want design or review feedback that's grounded in named principles (Fitts's Law, Hick's Law, Jakob's Law, etc.) instead of vague taste-based opinions.
- You need a rigorous, severity-rated audit of an existing screen, flow, or product instead of unstructured "this looks off" comments.
- You want accessibility (WCAG 2.2 AA), dark-pattern, and ethical-persuasion checks baked into every review by default.

**When to use it:**
- Before shipping a new screen/flow, to run a structured pre-launch design QA.
- When reviewing a competitor's or your own product's UX and you want a defensible, cited critique.
- When writing UX copy/microcopy, planning research studies, or defining design tokens and component states.
- When you explicitly want "Design Mode," "Review Mode," "Research Mode," "Copy Mode," "System Mode," or "QA Mode" — the skill auto-detects which one fits your ask.

**How to use it:**
- Just describe the screen, flow, or question ("review this checkout flow," "design a login screen," "write empty-state copy for an inbox"). The skill auto-detects the right mode.
- For an explicit audit, share a screenshot, Figma link, or description and ask for a review — it will run the full 12-step Audit Engine (first impressions → heuristics → laws/biases → myth checks → visual → interaction → content → accessibility → performance → ethics → i18n → synthesis).

**What you get back:**
- Design work that cites the specific law/heuristic/WCAG criterion behind each decision.
- Reviews formatted as: what works → severity-rated findings table (issue, principle, fix, effort) → quick wins → the single highest-leverage change → a suggested validation method.
- Severity levels from 0 (cosmetic) to 4 (catastrophe — blocks release; includes dark patterns and accessibility blockers), so you know what's actually urgent.

---

### 2. `senior-engineer-core`

**What it is:** A compact senior-engineer mentoring skill for Claude Code. It makes Claude behave like a careful senior engineer pairing with a fresher: building apps screen-by-screen and layer-by-layer, reusing existing code/libraries before writing new code, researching instead of guessing, debugging systematically, optimizing only with evidence, and avoiding bloat.

**Why use it:**
- You're learning to build software and want an assistant that won't dump an entire app on you at once, silently invent APIs, or overwhelm you with jargon.
- You want built-in guardrails against scope creep, unnecessary dependencies, and premature abstraction ("anti-bloat" rules).
- You want token/credit-efficient answers — small patches instead of full-file rewrites, short plans instead of essays.

**When to use it:**
- Building any app screen, component, or feature incrementally.
- Fixing bugs and want a systematic debug process instead of trial-and-error.
- Choosing a library/tool and want a structured, evidence-based comparison.
- Reviewing code or planning a feature and want a lightweight, no-nonsense checklist-driven process.

**How to use it:**
- Say what you want to build, fix, research, or review. The skill's Task Router auto-selects the right workflow (Screen-by-Screen Build, Debug, Research, Learning Notes, Optimization, Review, or Feature Planning).
- Optionally specify an intensity level: say "quick" or "simple" for **Lite** mode (small, low-risk changes, minimal back-and-forth), leave it unspecified for **Full** mode (the default — balanced planning + implementation), or say "production," "critical," or "secure" for **Ultra** mode (extra rigor: security, testing, rollback, and trade-off analysis).

**What you get back:**
- Work broken into small, reviewable steps (one screen/layer/component at a time), each ending with "what to check" and a request for your approval before moving on.
- Structured templates for each workflow (e.g. `Debugging Scope / Observed Problem / Likely Cause / Smallest Safe Fix / How to Verify`), so responses are consistent and scannable.
- Fewer wasted tokens/credits: targeted diffs instead of full-file dumps, and a size check before any large response ("Do you want full code, only the changed section, a step-by-step patch, or a summary first?").
- Honest "I'm not certain — let me verify or ask for docs" instead of invented APIs or hallucinated framework behavior.

---

### 3. `senior-engineer-workflow-complete`

**What it is:** The full, unabridged version of the senior-engineer skill above — same philosophy and modes (Lite/Full/Ultra), but with the complete Core Loop (10 steps), all 12 conceptual "tools" (Context Collector, Requirement Clarifier, Researcher, Note Maker, Architect, Component Builder, State Builder, API Integrator, Validator, Debugger, Optimizer, Reviewer), the full 7-layer screen-building process, a much more detailed debugging workflow (12 steps + an "unblocking process" for when you're stuck), a full internet-research strategy (search operators, source-validation checklist), a detailed optimization workflow (bottleneck-by-bottleneck, level-by-level), and an extensive anti-bloat / anti-vibe-coding / safety rulebook.

**Why use it:**
- Same reasons as `senior-engineer-core`, but for when you want the maximum level of detail and guardrails — e.g. onboarding a complete beginner, working on a larger or longer-running project, or when you want every edge case (loading/error/empty states, i18n, accessibility, security) spelled out at each step rather than assumed.
- Use this instead of `senior-engineer-core` when you want the more exhaustive rulebook; use `senior-engineer-core` when you want the same behavior in a smaller, faster-loading skill.

**When to use it:**
- Same triggers as `senior-engineer-core` (build / debug / research / learn / optimize / review / plan a feature), but pick this version when the task is bigger, riskier, or longer — production features, unfamiliar tech stacks, or multi-session projects where consistent step-by-step discipline really matters.
- When you're stuck on a hard bug and want the full "unblocking process" (write the problem clearly → reduce to a minimal repro → check assumptions → compare to a known-good example → check version mismatches → change approach).

**How to use it:**
- Same as `senior-engineer-core`: describe your task, optionally set a mode (Lite/Full/Ultra), and let the workflow router pick the right process.
- Because this version is much larger, prefer it when you expect a longer working session on one feature/screen rather than a quick one-off question (where `senior-engineer-core` is lighter-weight).

**What you get back:**
- Everything `senior-engineer-core` gives, plus: explicit "Screen Completed" checkpoints summarizing what was built, files changed, dependencies used, known limitations, and the next suggested screen; detailed research templates with source-quality evaluation (maintenance, docs, ecosystem, security, beginner-friendliness); and a stricter safety rulebook (explicit warnings before touching auth, payments, migrations, or production config).

---

## Choosing between the two senior-engineer skills

| | `senior-engineer-core` | `senior-engineer-workflow-complete` |
|---|---|---|
| Size | Compact | Full/exhaustive |
| Best for | Quick tasks, smaller projects, faster to load | Larger features, production work, beginners who need every step spelled out |
| Debugging depth | 10-step workflow | 12-step workflow + full "stuck" unblocking process |
| Research depth | Summary workflow | Full internet-research strategy with search operators & source validation |
| Conceptual tools | Not enumerated separately | 12 named tools (Context Collector, Architect, Debugger, Optimizer, etc.) |

Both skills share the same core philosophy: **clarity over speed, reuse over rebuilding, small safe steps over large risky changes, verified knowledge over guessing, minimal code over bloat, and user approval before moving forward.**

---

## Token Usage & Cost Guide

Every skill affects your token/credit spend in **two different ways**, and it's worth separating them:

1. **Loading cost (one-time, per session):** the skill's own `SKILL.md` text has to enter Claude's context before it can act on it. A bigger file = more input tokens spent just activating the skill.
2. **Behavioral cost (ongoing, every turn):** once active, a skill's rules shape how verbose Claude's *outputs* are for the rest of the session — full-file rewrites vs. small patches, five-paragraph explanations vs. two sentences, one big answer vs. a checkpoint-and-approve loop.

A skill can be "expensive" on one axis and "cheap" on the other. The two engineering skills below are explicitly engineered to be cheap on axis 2 even when they're not cheap on axis 1.

### 1. Loading cost — what it costs to activate each skill

Estimated using the common ~4 characters ≈ 1 token heuristic. Actual token counts depend on the model's tokenizer and will vary — treat these as relative, not exact.

| Skill | Lines | Words | Characters | Approx. tokens to load | Relative loading cost |
|---|---:|---:|---:|---:|---|
| `senior-engineer-core` | 752 | 2,528 | 16,272 | **~4,100** | 🟢 Low |
| `god-level-ux-designer-reviewer` | 330 | 3,029 | 21,983 | **~5,500** | 🟡 Medium |
| `senior-engineer-workflow-complete` | 3,088 | 9,687 | 60,135 | **~15,000** | 🔴 High |

```text
Relative one-time loading cost (longer bar = more tokens spent just to activate the skill)

senior-engineer-core               ████████                     (~4.1k tokens)
god-level-ux-designer-reviewer     ███████████                  (~5.5k tokens)
senior-engineer-workflow-complete  ██████████████████████████████ (~15.0k tokens)
```

**Takeaway:** `senior-engineer-workflow-complete` costs roughly **3.7× more to load** than `senior-engineer-core` for essentially the same behavior, just spelled out in more detail. That cost is paid once when the skill enters context (and again each time context resets/compacts), so it matters most on short sessions and matters least on long ones where it's amortized across many turns.

### 2. Behavioral cost — which skills actively reduce your ongoing spend

| Skill | Has explicit token/credit economy rules? | Governs response size? | Governs question volume? |
|---|---|---|---|
| `senior-engineer-core` | ✅ Yes — dedicated "Token and Credit Economy" section | ✅ Yes (Lite/Full/Ultra caps) | ✅ Yes (1–5 questions, batched) |
| `senior-engineer-workflow-complete` | ✅ Yes — same rules, more exhaustively stated | ✅ Yes (Lite/Full/Ultra caps) | ✅ Yes (1–5 questions, batched) |
| `god-level-ux-designer-reviewer` | ❌ No dedicated economy rules | ⚠️ Partial — structured, non-repetitive format, but optimized for thoroughness, not brevity | ⚠️ Partial — "ask 1-3 targeted questions" only when intent is unclear |

The two senior-engineer skills are the ones purpose-built to save tokens and credits. The UX skill is purpose-built for **depth and defensibility** — it will spend more tokens per response by design because a severity-rated, cited audit is inherently longer than a one-line opinion. That's a deliberate trade-off, not an oversight.

### 3. The specific token-saving mechanisms (senior-engineer skills)

| Mechanism | What it actually does | Where it saves tokens/credits |
|---|---|---|
| **Patch over full-file rewrite** | Claude outputs only the changed section/diff, not the whole file, when a small change is enough | Output tokens on every code edit |
| **Pre-flight size check** | Before a large response, Claude asks you to choose the format first (see prompt below) | Avoids paying for a full answer you didn't want |
| **Question batching (1–5, max)** | Clarifying questions are grouped into one numbered list instead of asked one at a time across turns | Fewer round-trips = fewer repeated context reloads |
| **No repeated explanations** | Claude is told not to re-explain the same concept multiple times in one session | Output tokens across a long session |
| **Scope lock (screen/layer/task)** | Claude works on only the current screen/layer/bug, never generates future screens speculatively | Prevents paying for code you don't need yet or may throw away |
| **Reuse-first rule** | Existing components/libraries/files are reused and adapted instead of rebuilt from scratch | Output tokens + avoids duplicate logic to maintain later |
| **Anti-bloat rules** | No speculative features, no premature abstractions, no unused dependencies/files | Output tokens now, and maintenance/rework cost later |
| **"Don't guess" rule** | Claude states uncertainty instead of generating plausible-sounding wrong code | Avoids wasted tokens on code that has to be debugged and regenerated |
| **Lite / Full / Ultra modes** | Lets you explicitly dial response depth up or down per task | Full control over the cost-vs-thoroughness trade-off per request |

The pre-flight size check is the most direct lever — it looks like this in practice:

```text
This answer may be large. Do you want:
1. Full code
2. Only the changed section
3. A step-by-step patch
4. A summary first
```

### 4. Practical guidance: which skill for which budget

| Scenario | Recommended skill | Cost reasoning |
|---|---|---|
| Quick one-off bug fix or tiny UI tweak | `senior-engineer-core` in **Lite mode** | Lowest loading cost + tightest output cap (0–2 questions, minimal code) |
| Normal feature/screen build, single session | `senior-engineer-core` in **Full mode** | Loading cost stays low; balanced plan-then-implement loop avoids rework |
| Long-running, multi-day, or production/security-critical build | `senior-engineer-workflow-complete` in **Full or Ultra mode** | Higher loading cost is amortized across many turns; the extra discipline (12-step debug workflow, full research strategy, stricter safety rules) reduces expensive rework and production incidents |
| You're a complete beginner and want every step spelled out | `senior-engineer-workflow-complete` | The larger loading cost buys clearer guardrails while you're still learning the ropes |
| Pre-launch design/UX audit | `god-level-ux-designer-reviewer` | Not optimized for token economy — optimized to catch severity-4 issues (accessibility blockers, dark patterns) *before* they become expensive to fix in production |
| Rapid UX sanity check, not a full audit | `god-level-ux-designer-reviewer`, but explicitly ask for a short answer | The skill has no built-in size cap, so you need to request brevity yourself |

### 5. Rule of thumb

> **Short session → pick the smaller skill file.** **Long or high-stakes session → the bigger file's one-time loading cost stops mattering, and its extra guardrails start paying for themselves.**

None of these numbers are exact API/credit pricing — actual cost depends on your Claude plan, the model in use, and Anthropic's current pricing. Use this guide to compare skills *relative to each other*, not to predict a dollar amount.
