# Pattern: Multi-Turn Refinement

**Category:** Interaction
**Problem:** Designing conversations that improve — where each turn builds context and narrows toward what the user actually needs.

---

## The Problem

Most AI conversations are designed as a series of independent exchanges, not as a progressive narrowing toward a goal. Each turn starts from a similar baseline. Context from prior turns is retained technically (it is in the context window) but not leveraged designedly — the system does not actively build on what it has learned about the user's goal.

The result is conversations that feel like repeated attempts rather than progressive refinement. Users who do not get what they need in the first turn try again with a different prompt — rather than building on what the first turn revealed about the gap between their need and the output.

## The Pattern

Multi-turn refinement design treats each turn as new information about the user's actual goal, not as a fresh request. The system explicitly builds on prior turns — surfacing what it has learned, updating its model of the user's need, and narrowing toward the target.

**Design elements:**

**Explicit context acknowledgment** — when a follow-up request builds on a prior turn, the system should signal that it is using that context: "Based on what you shared about your project timeline..." This signals to the user that the system is paying attention, not just processing a new prompt.

**Gap identification** — when a user's follow-up reveals a gap between the prior output and their actual need ("that's not quite what I meant"), the system should identify the gap explicitly before generating a new response: "I think I missed that you needed X — let me try again with that in mind."

**Progressive commitment** — as the conversation narrows toward a goal, the system should be able to commit to elements that are working while continuing to refine elements that are not. "The structure looks right — do you want me to adjust the tone of the second section?"

**Session summaries for long conversations** — in conversations that extend beyond a few turns, a periodic summary of what has been established helps users verify that the system's model of their goal is accurate before continuing.

## Design Mandates

**Design the refinement path, not just the first response.** Most AI product design focuses on the quality of a single response. Design the quality of the conversation over multiple turns — how does the system get better at serving the user's need as the conversation progresses?

**Make it easy to correct without restarting.** Users who have to regenerate from scratch after a partial failure lose all the context established in prior turns. Partial correction — "keep everything except the tone" — should be a first-class interaction, not a workaround.

**Track conversation depth as a product metric.** Average turns per session is a proxy for how well the product is serving complex needs. Short average sessions may indicate that users are getting what they need quickly — or that they are giving up quickly. Distinguish between the two.

## Example in Production

**ChatGPT:** ChatGPT's conversation model naturally supports progressive refinement — users can reference prior outputs ("make that shorter," "add an example to the third paragraph") and the system maintains context effectively across a session. This is one of the product's core design strengths and a primary driver of its engagement among users who have learned to use it as a collaborative writing and thinking tool.
