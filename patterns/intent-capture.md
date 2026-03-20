# Pattern: Intent Capture

**Category:** Input
**Problem:** The gap between what users say and what they mean — designing disambiguation as a feature, not a fallback.

---

## The Problem

Language is inherently ambiguous. "Send money to my brother" is not a command — it is an intent expressed in natural language. The system must infer which brother, how much, from which account, and through which channel. Every one of those dimensions is an opportunity for the system to act on incorrect assumptions.

Most AI products handle this ambiguity in one of two ways: they ask a clarifying question (which creates friction and feels like an interrogation) or they make an assumption and act on it (which creates errors that erode trust). Neither is good intent capture design.

## The Pattern

Good intent capture is designed around three questions the system asks before formulating a response:

1. What did the user literally say?
2. What are the most likely actual goals behind this utterance, given context?
3. What is the minimum additional information needed to serve the most likely goal?

The answer to question 3 determines the interaction design. If the system has enough context to serve the most likely goal with high confidence, it should do so — and make it easy for the user to correct if the inference was wrong. If the system genuinely needs more information, it should ask for the single most important piece — not multiple questions in sequence.

**The disambiguation hierarchy:**

1. **Resolve from context** — use session history, user profile, and behavioral signals to resolve ambiguity without asking
2. **Resolve by inferring the most probable intent** — act on the most likely interpretation, signal the inference, make correction easy
3. **Ask the single most important clarifying question** — only when ambiguity cannot be resolved without it
4. **Present options** — only when the possible interpretations are genuinely equivalent in probability

## Design Mandates

**Make inferences visible.** When the system acts on an inferred intent, show the inference: "I'm showing you your checking balance — is that what you were looking for?" This builds trust and catches mismatches before they cause problems.

**One clarifying question maximum.** Multiple clarifying questions in sequence feel like an interrogation. If you need more than one piece of information, ask for the most important one and infer or default the rest.

**Measure intent match separately from task completion.** Task completion tells you the system executed correctly. Intent match tells you it served what the user actually needed. Track both.

## Example in Production

**Maya, Banorte:** "¿cuánto tengo?" ("how much do I have?") was originally answered with the checking account balance — the literal interpretation. Behavioral data showed 60%+ of users who asked this then immediately asked follow-up questions about other accounts. The intent was not "checking balance" but "financial overview." Redesigning the response around the most probable intent — a consolidated summary with checking balance prominent — reduced multi-turn clarification sequences by 43%.
