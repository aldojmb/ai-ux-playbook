# Pattern: Editable Responses

**Category:** Output
**Problem:** AI output as a starting point, not a final answer — designing for collaboration, not consumption.

---

## The Problem

When AI output is presented as a final answer, users face a binary choice: accept it or reject it. There is no middle ground — no way to keep what is useful and modify what is not, no way to signal partial agreement, no way to build on the output collaboratively.

This binary framing produces two failure modes. Users who accept outputs uncritically over-delegate judgment to the system. Users who reject imperfect outputs abandon the product rather than refining it. Both behaviors reduce the value the product delivers.

## The Pattern

Editable responses design AI output as the first draft of a collaborative process, not the final product of a transactional one.

**Design elements:**

**Inline editability** — outputs should be directly editable in place, without copy-pasting to another tool. The act of editing signals collaboration; it also creates a feedback signal about what parts of outputs users find useful versus what they change.

**Section-level acceptance** — for long outputs, allow users to accept or modify sections independently. A user who loves the structure of a document but wants to rewrite one paragraph should not have to regenerate the entire thing.

**Regeneration with constraints** — "regenerate this section" should accept constraints from the user: "make this more formal," "shorter," "add a specific example." The constraint is a form of collaboration — the user is directing, the AI is executing.

**Change tracking** — in contexts where output quality matters (documents, communications, analysis), showing what the AI suggested versus what the user kept creates a useful audit trail and reinforces the collaborative framing.

## Design Mandates

**Default to editability.** If your product presents AI outputs that users cannot directly modify, ask why. The default should be editable; non-editable outputs should be the exception with a specific justification.

**Make the editing interface feel like editing, not prompting.** Users who have to re-enter the chat interface to modify a specific sentence are being asked to re-engage with the AI rather than with their work. Inline editing keeps the focus on the output.

**Track edit patterns as product signals.** Which sections do users consistently edit? Which do they keep? Edit patterns are the most direct signal of where AI output is and is not meeting user needs.

## Example in Production

**ChatGPT:** Every output is selectable, copyable, and implicitly editable. The product never presents outputs as final. This is one of the strongest AI-native UX decisions in any consumer product — it keeps the user in a collaborative rather than evaluative posture, which increases engagement and reduces the trust cost of imperfect outputs.
