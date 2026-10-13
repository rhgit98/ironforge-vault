---
title: Architectural Decision Records (ADR Log)
aliases: [ADR, Decisions]
tags: [adr, decisions, architecture]
created: 2026-10-12
updated: 2026-10-12
---

# 📜 Architectural Decision Records (ADR Log)

| Date | ID | Title | Status | Summary |
| :--- | :--- | :--- | :--- | :--- |
| 2026-10-12 | [[ADR-001]] | Sandbox Scoping to `AI_Projects` | Accepted | Restrict all subagents exclusively to `C:\Users\rob\Desktop\AI_Projects`. |
| 2026-10-12 | [[ADR-002]] | Unity New Input System Standard | Accepted | Adopt `UnityEngine.InputSystem` natively across all gameplay scripts. |
| 2026-10-12 | [[ADR-003]] | Humanoid Mecanim Retargeting | Accepted | Switch from custom keyframes to Unity Humanoid T-Pose retargeting with free Asset Store mocap packs. |
| 2026-10-12 | [[ADR-004]] | Obsidian Vault as Project Memory | Accepted | Establish `ironforge_vault` managed by `ArchiverAgent` as the single source of truth for design & code specs. |

---

## ADR-001: Sandbox Scoping to `AI_Projects`
* **Context**: Prevent accidental writes or file pollution across the user's desktop and other workspaces.
* **Decision**: All agent actions, models, unity scripts, and documentation must reside under `C:\Users\rob\Desktop\AI_Projects`.

## ADR-002: Unity New Input System Standard
* **Context**: Unity 6 / URP templates default to the New Input System package; calling legacy `Input.GetAxis` throws runtime `InvalidOperationException`.
* **Decision**: Target `Keyboard.current` and `Gamepad.current` directly in all locomotion scripts.

## ADR-003: Humanoid Mecanim Retargeting
* **Context**: Hand-crafted procedural keyframes produced unnatural posture ("hunched" model).
* **Decision**: Generate models in standard T-Pose with canonical bone hierarchies and leverage verified mocap libraries (RPG Animations Pack Free).

## ADR-004: Obsidian Vault as Project Memory
* **Context**: Maintain long-term architectural continuity and design vision accessible directly in Obsidian.
* **Decision**: Provision `ironforge_vault` with dedicated `ArchiverAgent` librarian.
