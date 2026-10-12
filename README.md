# ReportBot Blueprint

**A case study: turning an organization's existing documentation into a governed, queryable AI knowledge bot.**

> Result: **doubled analyst delivery capacity with no added headcount.**

This repository is a showcase of the method behind ReportBot. It describes the problem, the approach, the architecture, the guardrails and the results. It does not include source code, prompts, templates or any employer material. All examples are generic.

## The problem

Analyst teams that produce executive and customer reports spend most of their time hunting for answers, not writing them. The knowledge exists, but it is spread across help articles, PDFs, internal research, past write-ups and the heads of a few senior people. Every new analyst repeats the same search, every report takes longer than it should, and quality depends on who happens to be on shift.

Hiring more analysts was not an option. The question was whether the documentation the organization already had could do more of the work.

## The approach

ReportBot is a knowledge bot built on a notebook-style LLM workspace (for example NotebookLM or Gemini). It answers only from a curated set of sources, cites where each answer came from, and is tuned for the questions analysts actually ask while building reports.

The method has five parts:

1. **Curate the sources, don't dump them.** Sources are organized into a clear taxonomy so the model can ground answers in the right material:
   - Knowledge links: official help and reference pages
   - PDFs: guides, product sheets and policy documents
   - Research: industry reports and benchmarks used to frame findings
   - Generated notes: summaries the team writes to fill gaps the docs leave open
   - Use-case write-ups: worked examples of real report requests and how they were answered
   - Welcome notes: orientation for new users on what the bot can and cannot do
   - Custom settings: the bot's role, tone, scope and answer format
2. **Give the bot a clear job.** A role definition sets who it serves, what it answers, how it cites, and when it must say "I don't know" instead of guessing.
3. **Pin the answers that matter most.** The questions analysts ask every week are answered once, reviewed by a senior person, and pinned so the bot returns the approved answer every time.
4. **Govern it like a system, not a toy.** Owners, review cycles, source rules and data handling are defined before launch, not after.
5. **Measure the outcome.** Track reports delivered per analyst, time to first draft and the share of answers needing correction.

## Architecture

```
  Existing documentation                  Notebook LLM workspace               Analysts
 ┌────────────────────────┐            ┌──────────────────────────┐        ┌─────────────┐
 │ Knowledge links        │            │ Role and scope settings  │        │ Ask a       │
 │ PDFs                   │  curated   │ Grounded retrieval       │ cited  │ question    │
 │ Research               │ ─────────► │ Pinned FAQ answers       │ ─────► │ Draft the   │
 │ Generated notes        │            │ "I don't know" fallback  │        │ report      │
 │ Use-case write-ups     │            └────────────┬─────────────┘        └──────┬──────┘
 └────────────────────────┘                         │                             │
            ▲                                       │ gaps, corrections           │
            └──────── owner review cycle ◄──────────┴─────────────────────────────┘
```

Gaps and corrections flow back to a named owner, who updates the sources or pins a new approved answer. The bot improves because the documentation improves.

## Guardrails

- **Grounded answers only.** The bot answers from curated sources and cites them. No source, no answer.
- **Human in the loop.** Analysts own every report. The bot drafts and finds; people review and decide.
- **No sensitive data in the workspace.** Customer data and credentials never go into sources.
- **Named ownership.** Every source category has an owner and a review date. Stale sources are removed.
- **Approved answers stay approved.** Pinned answers change only after review.
- **Clear limits.** New users learn what the bot is for, and what it should not be used for, before their first question.

## Results

- **Doubled analyst delivery capacity with no added headcount**
- Faster onboarding: new analysts got answers from day one instead of waiting on senior staff
- More consistent reports, because the same approved answers were used across the team
- Documentation gaps became visible and got fixed, instead of living in people's heads

## My role

I identified the problem, designed the source taxonomy and governance model, built and tuned the bot, wrote the pinned answers with subject matter experts, rolled it out to the analyst team, and measured the results.

## About me

Security, GRC & Customer Success leader and AI automation builder. CISSP. 2 U.S. patents (1 pending).
I build what leadership wants to see, from the data they already have.

[LinkedIn](https://www.linkedin.com/in/jasminerodriguez-security)

---

All rights reserved © 2026 Jasmine Rodriguez. Code available for review on request during interviews.
