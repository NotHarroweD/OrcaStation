# Model examples

**Last verified: October 13, 2026**, against each vendor's official model page (linked below).

Model lineups change quickly. Treat this page as a snapshot and check the vendors' own pages before relying on it.
It keeps two things apart:

1. **What the vendors say** about their models.
2. **OrcaStation's suggestions** for which role each might fill. These are our judgment, not vendor guidance and not
   benchmark results. Your own results (Chapter 11) should override them.

What you can use depends on your plan and tool, and relative performance can differ by product and task, so confirm what you
actually have.

For the reasoning behind tiers, see [Chapter 7](../guide/07-choosing-tiers.md).

## What the vendors say

### Claude (Anthropic)

| Model | How Anthropic positions it |
|---|---|
| Claude Fable 5.1 | For demanding reasoning and long-horizon agentic work, and a suggested step up when evals on Opus 5.5 at higher effort still fall short |
| Claude Opus 5.5 | For long-running agentic coding and knowledge work, and Anthropic's suggested starting point for most workloads |
| Claude Sonnet 5.5 | The best combination of speed and intelligence |
| Claude Haiku 5.5 | For high-volume, latency-sensitive tasks such as classification, extraction, and routing |

Official overview: <https://platform.claude.com/docs/en/models/overview>

### ChatGPT / OpenAI

| Model | How OpenAI positions it |
|---|---|
| GPT-6 Astra | The flagship for complex reasoning and coding, and OpenAI's suggested starting point |
| GPT-6.1 Sol | Near-Astra performance for complex work at a lower cost; balances intelligence and cost |
| GPT-6 Luna | The most efficient model, for focused, high-volume, cost-sensitive work |

**Effort settings:** Astra and GPT-6.1 Sol offer low, medium, high, xhigh, and max. Luna adds a "none" option.

Official catalog: <https://developers.openai.com/api/docs/models>
Model selection guide: <https://developers.openai.com/api/docs/guides/model-selection>

## OrcaStation's suggested starting points

| Role | Claude | ChatGPT / OpenAI |
|---|---|---|
| **Orchestrator** | Opus 5.5, higher effort (Fable 5.1 if your results at higher effort fall short) | GPT-6 Astra, or GPT-6.1 Sol at high effort |
| **Implementer: standard** (start here) | Sonnet 5.5 | GPT-6.1 Sol, medium effort |
| **Implementer: mechanical** | Haiku 5.5 | GPT-6 Luna |
| **Implementer: hard** | Opus 5.5 | GPT-6 Astra |
| **Reviewer** | Sonnet 5.5 or Opus 5.5, higher effort, fresh session | GPT-6.1 Sol at high effort, fresh session |

**A note on the light tier:** both vendors position their lightest models for high-volume work like classification and extraction.
Using them for mechanical implementation is our suggestion to test, not vendor guidance. If tasks keep failing on well-written specs,
move that kind of task up a tier.

**Cost:** the top models cost noticeably more per token. For orchestration, the second tier at a high effort setting is often
enough, so reserve the top model for your hardest planning. Check each vendor's pricing page, and measure before assuming.

**Mixing vendors:** a reviewer from a different vendor than the implementer can catch different problems.
It's optional and adds setup work, so try it once your basic loop is stable.

## Keeping this page honest

When you update it, change the date at the top, re-check the official pages, and remove anything you can't verify.
