# Model examples

**Last verified: October 11, 2026.**

Model lineups change quickly. Treat this page as a snapshot, check the vendors' own model lists before relying on it,
and see [Chapter 7](../guide/07-choosing-tiers.md) for the reasoning behind the tiers.
The suggestions below are **starting points based on how each vendor positions its models**, not benchmark results
for your project. Your own tests (Chapter 11) should override them.

What you can use also depends on your plan and tool. Availability and relative performance can differ by product, plan, and task, so
confirm what you actually have, and let your own results decide.

## Claude

| Tier | Model | Notes |
|---|---|---|
| Top | Claude Fable 5.1 | Anthropic's top-capability tier. Has extra safeguards in some areas, and availability may vary. |
| Top | Claude Opus 5.5 | Flagship for demanding reasoning, coding, and long-running agent work. |
| Middle | Claude Sonnet 5.5 | A faster, lower-cost option for well-scoped everyday work. |
| Light | Claude Haiku 5.5 | The newest small model, published October 7, 2026 in the listings I checked. Verify availability on your plan. |
| Light (previous) | Claude Haiku 4.5 | The previous small model, still listed as active in some sources. |

Official model overview: <https://platform.claude.com/docs/en/docs/about-claude/models/overview>

## ChatGPT / OpenAI

| Tier | Model | Notes |
|---|---|---|
| Top | GPT-6 Astra | OpenAI's most capable model, and the most expensive. |
| Middle | GPT-6.1 Sol | Positioned by OpenAI as near-Astra performance at a lower cost. |
| Light | GPT-6 Luna | The fast, low-cost option. |

**Effort settings:** the GPT-6 family supports reasoning effort levels from low up through high and beyond, and defaults to medium.
Astra and GPT-6.1 Sol don't support turning reasoning off completely, while Luna does. Some settings only apply in certain APIs.
An optional "pro" mode also exists.

Check current models: <https://developers.openai.com/api/docs/models/all>

## Suggested starting assignments

| Role | Claude | ChatGPT / OpenAI |
|---|---|---|
| **Orchestrator** | Opus 5.5 (Fable 5.1 for the hardest planning), higher effort | GPT-6 Astra, or GPT-6.1 Sol at high effort |
| **Implementer: standard** (start here) | Sonnet 5.5 | GPT-6.1 Sol, medium effort |
| **Implementer: mechanical** | Haiku 5.5 | GPT-6 Luna |
| **Implementer: hard** | Opus 5.5 | GPT-6 Astra |
| **Reviewer** | Sonnet 5.5 or Opus 5.5, higher effort, fresh session | GPT-6.1 Sol at high effort, fresh session |

**Cost note:** the very top models cost noticeably more per token. For orchestration, the second tier at a high effort setting is
often enough, so reserve the top model for your hardest planning. Measure before assuming.

**Mixing vendors:** a reviewer from a different vendor than the implementer can catch different problems.
It's optional and adds setup work, so try it once your basic loop is stable.

## Keeping this page honest

When you update it, change the date at the top, and remove anything you can't verify.
