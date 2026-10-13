---
title: Archiver Agent SOP & Knowledge Protocol
aliases: [Archiver SOP, Vault Protocol]
tags: [sop, archiver, obsidian, memory]
created: 2026-10-12
updated: 2026-10-12
---

# 📚 Archiver Agent SOP (Standard Operating Procedure)

> **Agent Name**: `ArchiverAgent`  
> **Workspace**: `C:\Users\rob\Desktop\AI_Projects\ironforge_vault\`  
> **Status**: Active

---

## 1. Core Mandate

The Archiver Agent serves as the **memory engine and vault librarian** for Project Ironforge. Whenever new models are created, animations are imported, architecture decisions are made, or bugs are resolved, the Archiver records the event, updates the relevant documentation, and ensures Obsidian graph integrity.

---

## 2. Directory Hierarchy Standards

Every note inside `ironforge_vault` must live in its designated numerical folder:

| Folder | Purpose |
| :--- | :--- |
| `00_Hub/` | Master Index, Maps of Content (MOCs), Dashboards. |
| `01_Game_Design/` | GDDs, character lore, combat balance, level design notes. |
| `02_Agents_and_Instructions/` | Agent definitions, prompts, boundaries, and SOPs. |
| `03_Pipelines_and_Tech/` | Technical specs, Blender export settings, Mecanim setup, C# conventions. |
| `04_Assets/` | Inventories of 3D models, textures, animations, and sound assets. |
| `05_Devlogs_and_Decisions/` | ADRs (Architectural Decision Records) and session changelogs. |

---

## 3. Obsidian Formatting Rules

1. **YAML Frontmatter**:
   Every markdown file must open with:
   ```yaml
   ---
   title: Page Title
   aliases: [Alias1, Alias2]
   tags: [tag1, tag2]
   created: YYYY-MM-DD
   updated: YYYY-MM-DD
   ---
   ```
2. **Wikilinks**:
   Always link related concepts using standard `[[Folder/Note_Name|Display Text]]` or `[[Note_Name]]`.
3. **Mermaid Diagrams**:
   Use `mermaid` blocks for state machines, pipelines, and class hierarchies.
4. **No Orphan Pages**:
   Every new page must be referenced by at least one Map of Content (MOC) or the `Master_Index.md`.
