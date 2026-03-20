# Pattern: Prompt Scaffolding

**Category:** Input
**Problem:** Users don't know how to talk to AI — scaffolding guides them toward effective input without feeling like a form.

---

## The Problem

An empty text field is the default interface for most AI products. It is also the worst onboarding experience for new users.

Users who have never used a specific AI product — regardless of their general AI familiarity — do not know what inputs produce good outputs. They default to either over-simplified queries ("summarize this") or over-specified ones that include unnecessary constraints. Both produce mediocre results. The user blames the AI.

The cost is not just a bad first session. Users form durable mental models of AI products in their first 2-3 interactions. A user who gets poor results early develops a low ceiling for what they expect the product to deliver — and rarely revises that ceiling upward.

## The Pattern

Prompt scaffolding provides structure that guides users toward effective input — without requiring them to learn prompt engineering, and without making the experience feel like filling out a form.

**Three levels of scaffolding:**

**Level 1 — Contextual placeholders**
Replace the generic "Ask me anything" placeholder with specific, task-relevant guidance that changes based on where the user is in the product.

Instead of: *"Ask me anything..."*
Use: *"Describe what you're trying to accomplish — I'll help you figure out the best approach."*

Or for a specific context: *"Which account or transaction do you want to know about?"*

**Level 2 — Example prompts**
Surface 3-4 example prompts that represent the highest-value use cases for the specific user context. Examples should be specific enough to be useful, not generic enough to be meaningless.

Not: *"Try: 'Help me with my finances'"*
But: *"Try: 'Show me everything I spent on food last month' or 'What's my credit limit on my Platinum card?'"*

**Level 3 — Progressive disclosure of complexity**
As users develop fluency, gradually expose more sophisticated input patterns — multi-step requests, contextual references, refinement commands — without overwhelming new users.

## Design Mandates

**Match scaffolding to context, not to the product.** A user asking about transactions needs different scaffolding than a user starting a new document. Scaffolding that does not adapt to context becomes noise.

**Show, don't instruct.** Examples are more effective than instructions. "You can ask about your spending by category" is less useful than "Try: 'How much did I spend on subscriptions this year?'"

**Remove scaffolding as users demonstrate fluency.** Scaffolding shown to experienced users creates friction. Track engagement with scaffolding elements and fade them for users who are generating effective inputs on their own.

## Example in Production

**Maya, Banorte:** Maya's initial interaction surface varies by entry point. Users entering from the transfers section see transfer-specific scaffolding. Users entering from the investments section see investment-specific examples. Generic entry points show the top 3 use cases by session volume for that user's profile. This context-matching reduced the rate of "I don't know what to ask" session abandonment by 31% versus a generic placeholder.
