# Inspirations: Game MCP Architecture for AuraAlgorithm

This document outlines the refactoring guidelines for **AuraAlgorithm** using the Model Context Protocol (MCP) tool integration.

---

## 1. What Stays the Same
- **Storyteller Def XML Structure**: The storyteller def structure, definition mappings (`portraitLarge`, `listOrder`, `StorytellerVoiceExtension` voices, etc.) remain in XML.
- **Storyteller Persona Mappings**: Speeches, character name (`Aura`), and speaking style (`sassy, dramatic, and snarky`) remain defined in the mod configs.

---

## 2. What Changes (The MCP Shift)
- **Remove C# Aspect Checking Rules**: We can scrap the complex XML lists of `IncidentModifierRule` containing static threshold and aspect checks (e.g. `<threshold>2</threshold>`, `<comparison>GreaterThan</comparison>`).
- **Prompt-Driven Tool Direction**: Instead of writing XML code blocks for casualty rules, document these constraints directly in the storyteller's system prompt.
  - *Example prompt constraint*: *"If you query `get_colonists_profile()` and see that the colony has suffered recent casualties, you MUST reduce the pacing multiplier below 0.3 and avoid ThreatBig events."*

---

## 3. New Prompt-Driven MCP Guidelines
- Use the storyteller prompts to direct the LLM on which tools to invoke first.
- Instruct the storyteller to query `get_stockpile_details()` to determine if a crop blight, trade opportunity, or famine scenario fits the narrative best.
- Instruct the storyteller to query `get_colonists_profile()` before launching a raid to tailor the threat severity to their current military capabilities.
