# Pattern: Confidence Indicators

**Category:** Trust
**Problem:** Making model uncertainty visible without creating anxiety — proportional, specific, located at the point of uncertainty.

---

## The Problem

AI models are uncertain about some outputs and confident about others. Most products present both with identical visual treatment. Users have no signal for when to trust and when to verify. They either over-trust (and get hurt when the model is wrong) or under-trust (and verify everything, eliminating the value of the AI).

The naive solution — adding a disclaimer to every output — is worse than nothing. Universal disclaimers train users to ignore them and destroy the signal value of uncertainty communication.

## The Pattern

Confidence indicators must be three things: proportional, specific, and located at the point of uncertainty.

**Proportional** — the visual weight of a confidence indicator should match the importance of the uncertainty. A slight hedge in linguistic register is appropriate for medium-confidence outputs. A visible indicator and verification affordance is appropriate for high-stakes, low-confidence outputs. A hard stop with routing is appropriate for outputs the system should not attempt.

**Specific** — "I might be wrong" is not a confidence indicator. "This reflects account terms as of [date] — verify current rates at banorte.com" is. Specificity tells the user what to verify and where to go, not just that verification might be needed.

**Located at the point of uncertainty** — a disclaimer at the end of a response is not confidence design. It is confidence avoidance. The indicator should appear adjacent to the specific claim that is uncertain, not appended to the response as a footer.

**The confidence tier model:**

| Tier | Trigger | Design response |
|---|---|---|
| High confidence | Well-covered territory, retrieved data | No indicator needed |
| Medium confidence | Inferred information, general knowledge | Linguistic hedging ("Based on what I can see...") |
| Low confidence | Outside reliable territory, temporal uncertainty | Indicator + verification affordance |
| Very low / out of scope | Cannot reliably answer | Hard boundary + routing to authoritative source |

## Design Mandates

**Define your confidence tiers before designing the interface.** Without explicit tier definitions, confidence indicators are inconsistent and users cannot build a reliable mental model of when to trust.

**Calibrate your model's expressed confidence to its actual accuracy.** Confidence theater — displaying confidence indicators that do not correlate with actual model reliability — is worse than no indicators. It actively miscalibrates user trust.

**Never apply the same indicator to all outputs.** If everything has a disclaimer, nothing has a disclaimer. Reserve visible confidence indicators for outputs where they genuinely change what the user should do.

## Example in Production

**Maya, Banorte:** Maya operates with explicit confidence tiers. Regulatory information and fee structures — which change and have a temporal dimension — are always accompanied by a specific verification pointer, not a generic disclaimer. Balance and transaction data — retrieved directly from the core banking system — carry no uncertainty indicator. The distinction is consistent and users learn it quickly.
