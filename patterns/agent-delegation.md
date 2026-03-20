# Pattern: Agent Delegation

**Category:** Interaction
**Problem:** The design of the moment when a user hands off a task to an AI agent — what needs to be visible, what can be invisible.

---

## The Problem

Agent delegation — handing a task to an AI that will execute it autonomously — is the highest-trust interaction in AI products. It is also the most underdesigned.

Most products that support agent delegation treat it as a technical feature rather than a UX design challenge. The agent is given a task. It executes. The user sees the result. What happens in between is invisible.

This invisibility is the problem. Users who cannot see what the agent is doing cannot intervene when it goes wrong. They cannot verify that the agent understood the task correctly before it executes. They cannot calibrate their trust in the agent based on its behavior — because they cannot see its behavior.

## The Pattern

Agent delegation design makes the delegation contract explicit: what the user is asking the agent to do, what the agent understands the task to be, what the agent will and will not do autonomously, and how the user can intervene.

**The delegation contract has four elements:**

**1. Task confirmation** — before the agent begins, it surfaces its understanding of the task in plain language. Not a technical description of what it will do, but a user-readable statement of what it understands the goal to be and what it will do to achieve it.

**2. Scope declaration** — the agent declares what is within its autonomous action scope and what it will pause and check back on. "I'll draft the email and schedule it for 9am — but I'll check with you before sending if the recipient hasn't responded to your last three messages."

**3. Progress visibility** — for long-running tasks, the user should be able to see what the agent is doing at a level of granularity appropriate to the stakes. Not a technical log, but a user-readable summary of progress and any decisions made.

**4. Intervention affordance** — the user should be able to pause, modify, or cancel the agent's work at any point. The intervention affordance should be visible and accessible throughout the delegation, not just at the beginning and end.

**The trust ladder for delegation:**

See [The Delegation Ladder](https://github.com/aldojmb/delegation-ladder) for the full framework. The key principle: users should not be asked to delegate before they have had the opportunity to observe the agent's behavior at lower stakes. The delegation pattern assumes a prior history of trust-building interactions.

## Design Mandates

**Never delegate silently.** An agent that begins executing without confirming its understanding of the task is a trust liability. The confirmation step costs seconds; a misunderstood delegation can cost hours.

**Design the interrupt, not just the handoff.** Most agent design focuses on the moment of delegation. Design the moment of intervention — when the user realizes the agent is going wrong and needs to stop it. How easy is that? How much damage can the agent do before it can be stopped?

**Calibrate autonomy scope to demonstrated trust.** An agent that has completed 10 successful delegations for a user can be given wider autonomy scope than one in its first interaction. Design explicit trust accumulation that unlocks progressively wider agent autonomy.

## Example in Production

**Maya, Banorte:** For high-value transfers (above a threshold determined by user history and risk profile), Maya implements a full delegation contract: it states the transfer details in plain language, confirms the user's intent, declares what it will do (execute the transfer) and what it will not do (it will not modify the amount or recipient without explicit confirmation), and provides a clear cancellation affordance up until the moment of execution. This adds approximately 8 seconds to the average transfer flow — and reduced transfer disputes by 34%.
