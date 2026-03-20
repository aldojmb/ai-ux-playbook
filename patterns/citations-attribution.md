# Pattern: Citations & Attribution

**Category:** Trust
**Problem:** When AI output draws on specific sources, showing the provenance builds trust and enables verification.

---

## The Problem

AI outputs that synthesize information from multiple sources present a trust design challenge: the user cannot tell what is retrieved fact, what is inferred, and what is the model's general knowledge. All three are presented identically. The user has no mechanism for verification.

In low-stakes contexts, this is a minor UX issue. In high-stakes contexts — medical, legal, financial, regulatory — it is a product failure. Users who make consequential decisions based on unattributed AI output have no way to verify those decisions, and no recourse when the output is wrong.

## The Pattern

Citations and attribution serve three functions: they enable verification, they communicate provenance, and they signal the type of knowledge the output draws on.

**When to show attribution:**
- When the output draws on specific, checkable sources (documents, databases, dated information)
- When the output makes claims that are time-sensitive (regulations, rates, policies)
- When the user is in a high-stakes domain (financial, medical, legal)
- When the output synthesizes multiple sources and the synthesis could obscure important distinctions

**When attribution adds noise rather than value:**
- Conversational responses that draw on general knowledge
- Creative tasks where source attribution is irrelevant
- Simple factual queries with stable, unambiguous answers

**Attribution formats:**
- **Inline:** "According to your account statement from March 2024..." — best for specific claims
- **Footer:** Source list at the end of a longer response — best for research synthesis
- **Affordance:** A "sources" button that reveals attribution on demand — best for users who want the option without default clutter

## Design Mandates

**Match attribution granularity to the stakes.** A research synthesis needs source-level attribution. A conversational response about general concepts does not. Over-attribution creates noise; under-attribution creates risk.

**Make attribution actionable.** A citation is only valuable if the user can follow it. Link to sources when possible. Provide enough context (document name, date, section) for users to find the source when direct linking is not possible.

**Distinguish retrieved from inferred.** The most important attribution distinction is not which source something came from — it is whether it was retrieved from a specific source or inferred from the model's general knowledge. These carry different levels of reliability and should be visually distinguished.

## Example in Production

**Perplexity:** Perplexity's inline citation model — numbered references that link directly to sources within the response text — is the strongest implementation of this pattern in consumer AI. Users can verify specific claims without leaving the interface, and the citation density signals the depth of research behind a response.
