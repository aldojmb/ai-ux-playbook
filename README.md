# AI UX Playbook

**A practitioner's guide to designing AI products that earn trust, not just attention.**

> *Most AI products are designed like software with a chatbot bolted on. This playbook is for the ones that aren't.*

---

## Who This Is For

Product managers, designers, and builders who are shipping AI products — not experimenting with them. If you are responsible for an AI experience that real users depend on, this playbook is for you.

It is not a collection of UI components or a style guide. It is a framework for making the design decisions that determine whether an AI product earns durable trust or erodes it.

---

## Vision — What Is AI-Native UX

AI-native UX is not about aesthetics. It is not about conversational interfaces, dark mode, or animated loading states. It is about building products from the correct assumptions about how AI systems actually work.

Traditional software is deterministic. The user clicks a button. The system executes a function. The output is predictable. Design optimizes for clarity and efficiency within that contract.

AI products break that contract. The output is probabilistic. The system infers intent rather than executing commands. Failure is not exceptional — it is regular, expected, and designable. The user's mental model of the system is as important as the system's capability.

AI-native UX starts from those assumptions. It does not adapt traditional patterns to fit. It builds from the reality of how AI systems operate — and designs experiences that are honest about that reality.

**The core shift:**

| | Traditional UX | AI-Native UX |
|---|---|---|
| Output | Deterministic | Probabilistic |
| Interface | State-driven | Context-driven |
| User input | Commands | Intentions |
| Error | Exceptional state | Designed state |
| Trust | Assumed from reliability | Earned through honesty |
| Mental model | User learns the system | System adapts to user |

---

## Core Principles

### Trust > Accuracy

The instinct in AI product development is to optimize for accuracy — make the model more correct, reduce hallucinations, improve performance benchmarks. Accuracy matters. But it is not what determines whether users trust and keep using an AI product.

Trust is built through consistency, honesty about limitations, and graceful handling of failure. A product that is 95% accurate but hides its uncertainty will lose user trust faster than one that is 85% accurate but signals clearly when it is unsure.

Design for trust first. Accuracy improvements compound on a foundation of trust. They erode without it.

### AI as Collaborator, Not Tool

A tool executes commands. A collaborator participates in a process. The distinction changes everything about how you design the interaction.

When AI is designed as a tool, the user is responsible for all judgment. The AI executes. Errors are the user's fault for giving bad input. The interface optimizes for command clarity.

When AI is designed as a collaborator, judgment is shared. The AI contributes perspective, flags uncertainty, asks clarifying questions, and acknowledges when it is outside its reliable territory. The interface optimizes for shared understanding.

Most AI products are designed as tools. The ones that earn long-term engagement are designed as collaborators.

### Progressive Autonomy

Users do not arrive at an AI product ready to delegate. They arrive skeptical, uncertain about what the system can do, and unwilling to trust outputs they cannot verify.

Trust is earned through repeated positive experiences at progressively higher stakes. Design the early experience to demonstrate reliability on low-stakes tasks. Build explicit paths from low-trust to high-trust interactions. Never ask users to delegate before they have earned confidence in the system.

See: [The Delegation Ladder](https://github.com/aldojmb/delegation-ladder) for the full framework on progressive trust design.

---

## Pattern Library

Patterns are organized into four categories. Each has a dedicated file in `/patterns/` with full detail, examples, and design mandates.

### Input Patterns
*How users communicate intent to the AI*

| Pattern | What it solves |
|---|---|
| [Prompt Scaffolding](patterns/prompt-scaffolding.md) | Users don't know how to talk to AI — scaffolding guides them toward effective input without feeling like a form |
| [Intent Capture](patterns/intent-capture.md) | The gap between what users say and what they mean — designing disambiguation as a feature, not a fallback |

### Output Patterns
*How the AI communicates results to users*

| Pattern | What it solves |
|---|---|
| [Editable Responses](patterns/editable-responses.md) | AI output as a starting point, not a final answer — designing for collaboration, not consumption |
| [Structured Answers](patterns/structured-answers.md) | When and how to structure AI output for scanability without sacrificing conversational naturalness |

### Trust Patterns
*How the product communicates reliability and uncertainty*

| Pattern | What it solves |
|---|---|
| [Confidence Indicators](patterns/confidence-indicators.md) | Making model uncertainty visible without creating anxiety — proportional, specific, located at the point of uncertainty |
| [Citations & Attribution](patterns/citations-attribution.md) | When AI output draws on specific sources, showing the provenance builds trust and enables verification |

### Interaction Patterns
*How users and AI develop shared understanding over time*

| Pattern | What it solves |
|---|---|
| [Multi-Turn Refinement](patterns/multi-turn-refinement.md) | Designing conversations that improve — where each turn builds context and narrows toward what the user actually needs |
| [Agent Delegation](patterns/agent-delegation.md) | The design of the moment when a user hands off a task to an AI agent — what needs to be visible, what can be invisible |

---

## Real Examples

### ChatGPT — What It Gets Right and Wrong

**What it gets right:**

*Editable responses* — every output is selectable, copyable, and implicitly editable. ChatGPT never presents its output as final. The interaction model assumes the user will work with the output, not just consume it. This is one of the strongest AI-native UX decisions in any consumer product.

*Multi-turn refinement* — the conversation model naturally supports progressive narrowing. Users who know how to use it can iterate toward excellent outputs. The product rewards engagement.

**What it gets wrong:**

*Confidence signals are absent* — ChatGPT presents every response with identical visual confidence, whether the model is operating in well-covered territory or hallucinating confidently. There is no signal to help users calibrate trust. This is its most significant UX failure — and the source of most real-world harm from the product.

*Prompt scaffolding is minimal* — new users face an empty text field with no guidance on how to communicate effectively. The learning curve is entirely on the user. This creates a bifurcated user base: power users who have learned prompt craft, and occasional users who get mediocre results and blame the AI.

---

### Copilot (Microsoft) — What It Gets Right and Wrong

**What it gets right:**

*Context integration* — Copilot's strongest design decision is embedding in the tools where work already happens. In Word, Excel, Teams, and Outlook, the AI has access to the user's actual context — the document being edited, the email thread being replied to, the meeting being summarized. This is intent capture at the infrastructure level: the system understands what the user is trying to do because it can see what they are doing.

*Structured answers in the right contexts* — in search and research contexts, Copilot structures output appropriately. Bullet points for lists, tables for comparisons, prose for narrative. The formatting is not uniform — it adapts to the content type.

**What it gets wrong:**

*Over-automation in sensitive contexts* — Copilot's email drafting and meeting summary features sometimes act before users have established trust in the output. Summarizing a meeting that a user has not reviewed, or suggesting a response to an email that requires nuanced judgment, can create errors that are more costly than the time saved. The product optimizes for speed over the user's need to maintain oversight.

*Confidence indicators are inconsistent* — in some contexts Copilot shows citations and sources. In others it presents outputs with no attribution. The inconsistency makes it impossible for users to build a reliable mental model of when to verify.

---

### Maya, Banorte — Designed for a Regulated Environment

Maya is Banorte's multichannel AI banking assistant, serving 20M+ users across mobile app, web, WhatsApp, and branch channels. It processes 28K+ secure transactions monthly in a regulatory environment where AI UX decisions carry compliance, trust, and financial consequence.

**What production at this scale teaches:**

*Intent capture is the highest-leverage design investment* — in banking, the gap between what users say and what they mean is not just a UX problem. Acting on the wrong intent in a financial transaction has real consequences. Maya's intent resolution layer went through more design iteration than any other component — and the 43% reduction in clarification sequences it eventually achieved had direct impact on NPS and task completion rates.

*Trust must be earned transaction by transaction* — users do not arrive at a banking AI trusting it with their finances. Maya was designed with explicit trust-building flows: low-stakes interactions first (balance checks, transaction history), then medium-stakes (transfers to saved recipients), then high-stakes (new payees, large amounts). The progressive autonomy principle is not theoretical in this context — it was a compliance and risk requirement.

*Failure design is not optional in regulated environments* — every failure mode in Maya has a designed response. Low confidence triggers linguistic hedging and a verification affordance. Scope violations trigger hard boundaries and specialist routing. Error acknowledgment follows a direct structure: acknowledgment, correction, explanation. This was not optional UX polish — it was built into the product specification from day one.

---

## Anti-Patterns

These are the design decisions that appear reasonable but consistently erode user trust, reduce engagement, or cause harm. They are common because they are easy to build and hard to notice until they have already done damage.

### 🔥 One-Shot AI

**What it looks like:** The product is designed around a single interaction — the user asks, the AI answers, the session ends. There is no conversation, no refinement, no memory of prior context.

**Why it happens:** One-shot is easier to build. No session management, no context window design, no multi-turn evaluation. It ships faster.

**Why it fails:** Real user needs are rarely resolved in a single exchange. Users who cannot refine outputs abandon the product or work around it — pasting outputs into other tools, asking the same question multiple ways, or giving up. One-shot AI optimizes for the demo, not the use case.

**The tell:** User sessions average 1.2 turns. Users report the AI "doesn't understand" them.

---

### 🔥 Black Box Outputs

**What it looks like:** The AI produces outputs with no indication of how it reached them, what sources it drew on, or how confident it is. The interface presents outputs as facts.

**Why it happens:** Confidence indicators and citations add complexity. They can make outputs feel less authoritative. They require the model to have calibrated uncertainty, which is hard to build and evaluate.

**Why it fails:** Users cannot calibrate trust in a black box. They either over-trust (and get hurt when the model is wrong) or under-trust (and verify everything, eliminating the value of the AI). Black box outputs are the primary driver of trust collapse after a high-profile error.

**The tell:** When the AI gets something wrong, users say "I had no idea it could be wrong." Trust collapses completely rather than recalibrating.

---

### 🔥 Over-Automation

**What it looks like:** The AI takes actions — sends emails, creates documents, makes changes — without explicit user confirmation. The product optimizes for speed and reduced friction.

**Why it happens:** Automation is the promise of AI. Reducing steps feels like improving the product. Confirmation dialogs feel like friction.

**Why it fails:** Users who lose control of outcomes disengage. Over-automation in high-stakes contexts (financial, communication, medical) creates errors that are more costly than the time saved. More importantly, it prevents users from climbing the trust ladder — they cannot build confidence in a system that acts before they have had a chance to verify.

**The tell:** Users turn off AI features they initially enabled. Support tickets spike around "the AI did something I didn't want."

---

### 🔥 Confidence Theater

**What it looks like:** The product displays confidence indicators, percentage scores, or certainty signals — but they are not calibrated to actual model confidence. They are designed to look trustworthy, not to communicate real uncertainty.

**Why it happens:** Calibrated uncertainty is hard to build and evaluate. Confidence theater is easy to ship and looks good in demos.

**Why it fails:** Users who learn that confidence signals are decorative stop using them — and stop trusting other signals from the product. Confidence theater is worse than no confidence signals because it actively miscalibrates user trust.

**The tell:** Confidence indicators do not correlate with error rates. High-confidence outputs fail at similar rates to low-confidence ones.

---

## Relationship to Related Frameworks

This playbook is part of a connected body of work on AI product design:

- [**AI-Native UX Patterns**](https://github.com/aldojmb/ai-native-ux-patterns) — three deep-dive patterns with case studies from production: intent-first design, stateful conversation design, failure-as-feature design
- [**Designing for Model Uncertainty**](https://github.com/aldojmb/designing-for-model-uncertainty) — five patterns specifically for communicating model uncertainty to users without creating anxiety
- [**The Delegation Ladder**](https://github.com/aldojmb/delegation-ladder) — framework for designing AI agents that earn trust progressively, from consultation to autonomous action

---

## Origin

This playbook was developed from direct experience designing and shipping AI products in production — including Maya, Banorte's multichannel AI banking assistant (20M+ users, 28K+ secure transactions monthly), and a multi-agent workforce intelligence platform serving 300K+ employees.

The patterns and anti-patterns documented here were not identified from research or observation of other products. They were discovered through production, validated through behavioral data, and refined through years of iteration in environments where design decisions carry real consequences.

---

## Author

**Aldo J. Macías** — Principal AI Product Leader

- LinkedIn: [linkedin.com/in/aldojmacias](https://linkedin.com/in/aldojmacias)
- Portfolio: [aldojm.com](https://aldojm.com)
- GitHub: [github.com/aldojmb](https://github.com/aldojmb)

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## Citation

```
Macías, Aldo J. (2025). AI UX Playbook: A practitioner's guide to designing
AI products that earn trust, not just attention.
https://github.com/aldojmb/ai-ux-playbook
```

---

## License

[MIT](LICENSE) — use freely, attribution appreciated.
