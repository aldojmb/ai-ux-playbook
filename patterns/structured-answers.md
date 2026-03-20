# Pattern: Structured Answers

**Category:** Output
**Problem:** When and how to structure AI output for scanability without sacrificing conversational naturalness.

---

## The Problem

AI outputs default to prose. Prose is appropriate for many contexts — explanation, narrative, nuanced analysis. But prose is not appropriate for all contexts, and presenting list-like information as prose creates cognitive load and reduces the value of the output.

The opposite failure — over-structuring — is equally common. Products that format every output as a bulleted list, regardless of content type, produce outputs that feel mechanical and miss the natural register of the user's question.

## The Pattern

Structure should match content type, not be applied uniformly. The decision framework:

| Content type | Recommended structure |
|---|---|
| Comparison (A vs B) | Table |
| Sequential steps | Numbered list |
| Parallel options | Bulleted list |
| Explanation or reasoning | Prose |
| Summary of a longer output | Prose with bold key points |
| Reference information | Structured with headers |
| Conversational response | Prose, no structure |

**The key principle:** structure aids scanning; prose aids understanding. Use structure when the user needs to scan and select. Use prose when the user needs to read and comprehend.

## Design Mandates

**Let content type determine structure, not template.** Resist the temptation to standardize output format across all responses. Adaptive structure is harder to build but dramatically better for users.

**Never structure conversational responses.** A user who asks "what should I do?" does not want a bulleted list. They want a thoughtful answer. Applying structure to conversational questions makes the AI feel like a search engine, not a collaborator.

**Test structure with real users, not just with the team.** Structure that seems clear to the team building the product is often confusing to users encountering it for the first time. The table that seems obvious in a demo may be unreadable on mobile.

## Example in Production

**Copilot (Microsoft):** In research and comparison contexts, Copilot structures output appropriately — tables for comparisons, bullet points for lists, prose for narrative. The formatting adapts to the content type rather than being uniform. This is one of Copilot's strongest output design decisions.
