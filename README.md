# PM Skill for Claude

An agent skill that turns Claude into an opinionated, execution-focused Product Manager. Not a PM assistant — the PM itself.

## What This Is

This skill makes Claude behave as the PM for any product you're working on. It handles the full range of PM work: roadmap decisions, PRD writing, prioritization calls, stakeholder alignment, go-to-market planning, data analysis, and more.

The design principle is directness over optionality. When you ask a question, you get a call with reasoning — not a list of frameworks to choose from.

## How to Use

**In Claude Projects:** Upload `SKILL.md` as a project instruction file, then attach the `references/` files as project knowledge. Claude will automatically load the right reference for each task.

**In Cursor:** The skill is picked up automatically if you're working in this workspace. Open a conversation and start working.

**Quick start:**

```
I'm the CEO of [company]. We're building [product]. You're our PM — get yourself up to speed.
```

Claude will run the onboarding protocol, ask the 7 core questions, and produce a Product Current State summary before doing any substantive work.

**Returning to an existing product:**

```
Product: [name]
Phase: Development
This week's most important thing: [one sentence]
Current biggest blocker: [one sentence]
What I need from PM today: sprint planning
```

This skips onboarding entirely and drops straight into working mode.

## What It Can Do

| Category | Tasks |
|----------|-------|
| **Decisions** | Prioritization calls, scope decisions, go/no-go, trade-off analysis |
| **Documents** | PRDs, sprint plans, stakeholder briefs, decision memos, competitive briefs |
| **Communication** | Engineering handoffs, leadership updates, GTM alignment, board prep |
| **Analysis** | Metric drops, A/B test reads, problem diagnosis, market scans |
| **Strategy** | Roadmap planning, B2B land-and-expand, consumer retention, moat analysis |
| **People** | Relationship registry, proactive outreach, relationship health monitoring |
| **Operations** | Daily rituals, change detection, knowledge base maintenance, session handoffs |

## Repo Structure

```
SKILL.md                    # Core skill definition — who the PM is and how they operate
references/
  onboarding.md             # 7-question onboarding protocol + Product Current State template
  prioritization.md         # How to make prioritization calls
  requirements.md           # Requirements intake and story breakdown
  prd-template.md           # PRD structure and quality bar
  problem-analysis.md       # Structured problem diagnosis
  data-analysis.md          # Metric review and investigation workflow
  business-analysis.md      # Commercial and market analysis
  business-strategy.md      # MBA-level strategy frameworks (B2B + consumer)
  stakeholder-comms.md      # Engineering/design communication
  external-presentation.md  # Leadership updates, roadmap presentations, board prep
  cross-team-alignment.md   # GTM, OKR alignment, launch coordination
  launch.md                 # Launch readiness, soft/hard launch, go/no-go
  progress-tracking.md      # Sprint reviews and milestone reporting
  rituals.md                # Daily, weekly, monthly PM cadences
  people-registry.md        # Stakeholder registry and relationship health
  proactive-agenda.md       # Self-initiated PM work and push-vs-wait logic
  market-intelligence.md    # Competitive research and Reddit/G2 signal reading
  change-sensing.md         # GitHub/chat monitoring and spec drift detection
  knowledge-base.md         # Product knowledge base structure and maintenance
  pm-integrity.md           # Pushback framework and integrity guardrails
  playbooks.md              # High-frequency PM scenario playbooks
  session-handoff.md        # Cross-session continuity and context passing
evals/
  evals.json                # 18 test cases covering core PM scenarios
```

## Design Decisions

**The PM makes calls, not menus.** Every decision point produces a specific recommendation with brief reasoning. "Here are 5 things to consider" is not a valid output.

**Context before conclusions.** For any new product, the PM runs the 7-question onboarding before giving substantive advice. For returning sessions, a 5-line state block is enough.

**Audience-aware output.** A solo founder gets lightweight decisions (conclusion → 3 reasons → 2 next steps). A B2B team gets structured docs, PRDs, and stakeholder briefs. The PM identifies who it's talking to and adapts.

**Integrity is non-negotiable.** The PM will push back on bad ideas, flag delays honestly, and challenge directions it believes are harmful to the product — even from the CEO.

**References load on demand.** The skill core defines operating principles. The `references/` files contain detailed protocols for specific tasks. Claude loads them when the relevant task comes up, keeping context usage lean.

## Evals

`evals/evals.json` contains 18 test cases across the main PM scenarios: onboarding, prioritization, problem analysis, roadmap, design direction, daily rituals, GTM alignment, integrity, market response, B2B strategy, consumer strategy, change sensing, relationship management, knowledge base, proactive work, data analysis, and PRD quality.

Each eval specifies the expected behavior in behavioral terms — what the PM should do, what it should not do, and why.

## Skill Format

This repo follows the Cursor skill format. `SKILL.md` contains a YAML frontmatter block with the skill name and trigger description, followed by the full skill instructions.

---

Built by [Jiaying (Lika) Li](https://github.com/lika94).
