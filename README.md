
# Peiyuan Hu

**I build the load-bearing parts of AI agent systems: the execution runtime, the permission boundary, and the eval gate.**

Most agent demos stop at "the model answered." I care about what comes after — who is allowed to act, which side effects are irreversible, what a half-finished run leaves behind, and how you prove it actually worked.

---

## Currently building: MUC

**MUC** — an Agent-native, multi-tenant CRM built around a controlled execution runtime.

`TypeScript` · `Next.js 16` · `PostgreSQL / Supabase` · `Pi Agent Core` · `MCP` · `Vercel AI SDK`

> Private repository — company project, in active development. Architecture and code walkthrough available in interview.

A CRM task becomes an auditable execution run instead of a chat reply:

```text
CRM task / object
  -> context + memory + knowledge
  -> AgentRuntime        CRM-owned contract, provider-agnostic
  -> model + tools
  -> policy / permissions / approval / durable execution
  -> CRM state change + trace + evaluation
```

My scope is **runtime, harness, eval**:

- **Runtime seam.** Defined the `AgentRuntime` contract so CRM domain code never imports Pi or a provider SDK. Model binding, budget, usage, and audit stay CRM concerns, outside the agent loop.
- **Effect-typed tools.** Every tool call is classified `read` / `reversible_write` / `external` / `irreversible`. External and irreversible actions can require human approval before any CRM handler executes.
- **Durable execution.** API admission is separated from worker execution: queue, lease, cancellation, resume, retry, and explicit `partial` / `needs_review` / reconciliation states — instead of one HTTP request waiting on a model.
- **Evidence-aware eval.** Deterministic gates run first; an optional semantic judge can never override a failed gate. Judge failures route to `needs_review` rather than manufacturing a pass.

The implementation stays private. I'm glad to walk through the runtime seam, the effect taxonomy, and the lease lifecycle in an interview.

---

## How I think about agent systems

1. **Side effects need a type, not a prompt.** "Please don't send that email" is a suggestion. An `irreversible` effect class with an approval gate is a boundary.
2. **A long-running agent is a queue problem, not an HTTP problem.** Leases, resumption, and partial states are what make it survivable.
3. **"It answered" is not "it worked."** Verification means checking events, policy, approvals, and provenance — not whether the prose reads well.
4. **Unproven success should look unproven.** `partial` and `needs_review` are honest states, not defects to hide.

---

## Stack

![TypeScript](https://img.shields.io/badge/-TypeScript-0F172A?style=flat-square&logo=typescript&logoColor=3178C6)
![Node.js](https://img.shields.io/badge/-Node.js-0F172A?style=flat-square&logo=nodedotjs&logoColor=5FA04E)
![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-0F172A?style=flat-square&logo=postgresql&logoColor=4169E1)
![Redis](https://img.shields.io/badge/-Redis-0F172A?style=flat-square&logo=redis&logoColor=FF4438)
![Next.js](https://img.shields.io/badge/-Next.js-0F172A?style=flat-square&logo=nextdotjs&logoColor=FFFFFF)
![React](https://img.shields.io/badge/-React-0F172A?style=flat-square&logo=react&logoColor=61DAFB)

![Vercel AI SDK](https://img.shields.io/badge/-Vercel%20AI%20SDK-0F172A?style=flat-square&logo=vercel&logoColor=FFFFFF)
![MCP](https://img.shields.io/badge/-MCP-0F172A?style=flat-square)
![OpenAI](https://img.shields.io/badge/-OpenAI-0F172A?style=flat-square&logo=openai&logoColor=FFFFFF)
![Anthropic](https://img.shields.io/badge/-Anthropic-0F172A?style=flat-square&logo=anthropic&logoColor=FFFFFF)

![Docker](https://img.shields.io/badge/-Docker-0F172A?style=flat-square&logo=docker&logoColor=2496ED)
![Playwright](https://img.shields.io/badge/-Playwright-0F172A?style=flat-square&logo=playwright&logoColor=2EAD33)
![Vitest](https://img.shields.io/badge/-Vitest-0F172A?style=flat-square&logo=vitest&logoColor=6E9F18)
![Sentry](https://img.shields.io/badge/-Sentry-0F172A?style=flat-square&logo=sentry&logoColor=FFFFFF)

---

## Background

- **AI engineering intern** — Muchen AI, Chongqing · 2026.07 – present
- **AI acquisition agent intern** — Lingka Software, Changsha · 2026.04 – 2026.06
  Private-domain sales and lead-generation agents.
- **Before that** — RAG knowledge base: multi-route recall (vector + BM25), RRF fusion, rerank, SSE-streamed answers.

Graduating 2027.

---

## Reach me

- **Email** — your.email@example.com
- **Open to** — backend / AI application engineering roles, 2027

---

<sub>Deliberately short — the details are easier to explain than to read.</sub>
