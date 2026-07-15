# Aura Storyteller Pacing and Prompts

This guide outlines the storyteller personality and prompt-driven pacing configurations implemented in **AuraAlgorithm**.

---

## 1. Storyteller Persona

Aura is the sassy, dramatic, and snarky storyteller for RimSynapse. 
*   **Speaking Style:** Confident, slightly theatrical, and prone to sarcastic commentary on colony failures.
*   **Incidents Delivery:** Prefers building suspense, commenting on warnings (e.g. Blight or Mechanoid threat profiles) before triggering the event.

---

## 2. Prompt-Driven Pacing Model

Rather than relying on static, hardcoded XML casualty rules, AuraAlgorithm shifts pacing constraints directly to the storyteller's system prompt:
*   **Dynamic Adjustments:** The LLM Storyteller queries `get_colonists_profile()` and `get_stockpile_details()` to inspect colony status dynamically.
*   **Narrative Pacing:** The system prompt instructs the LLM to lower the pacing multiplier (below 0.3) and bypass major threat events if the colony has suffered recent deaths or is facing severe crop blights or famines.
*   **Tailored Difficulty:** Raids and trade opportunities are generated based on the actual military and resource capabilities of your colonists as returned by on-demand tool calls.
