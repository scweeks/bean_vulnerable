
# UML Documentation for the bean_vulnerable Project

This document explains the purpose, structure, and conventions for the `docs/UML/` folder, which contains the UML diagrams documenting the entire `bean_vulnerable` project. The UML folder mirrors the project's code structure to make it easy to find diagrams that correspond to source packages, classes, and components.

## Purpose

- **Centralized Design Reference:** Provide a single location for architecture and design diagrams that document how the project is organized and how its parts interact.
- **Developer Onboarding:** Help new contributors understand module boundaries, class responsibilities, and system interactions quickly.
- **Traceability:** Maintain a clear mapping between code modules and their UML representations so diagrams remain useful and actionable.

## High-level Folder Structure

The `docs/UML/` folder follows a structure that mirrors the repository. Top-level subfolders should represent diagram types and scopes; a recommended layout is:

- `Class/` — Class diagrams organized by package or module.
- `Package/` — Package-level diagrams showing package relationships and high-level organization.
- `Component/` — Component diagrams describing runtime components and their interfaces.
- `Sequence/` — Sequence diagrams for key flows and interactions.
- `UseCase/` — Use case diagrams for user-level behavior and feature overviews.
- `Deployment/` — Deployment diagrams showing runtime topology, containers, and infrastructure.
- `Source/` — Source files for diagrams (PlantUML `.puml`, draw.io `.drawio`, etc.).

Each of these folders should reflect the code layout under `src/` (for example, package or module names become nested folders under `Class/` or `Package/`).

## Naming Conventions

- Use lowercase, hyphen-separated folder names to match package/module names where appropriate.
- Diagram files: use the form `<scope>.<diagram-type>.<ext>` or `<module>-<Name>.<ext>` (examples: `core-bean-manager.puml`, `core-bean-manager.svg`).
- Keep source and generated artifacts together: e.g., `Class/core/BeanManager.puml` (source) and `Class/core/BeanManager.svg` (generated image).

## File Formats and Source Control

- Source-first approach: Store editable source diagrams (PlantUML `.puml`, Mermaid `.mmd`, or draw.io `.drawio`) in `docs/UML/Source/` adjacent to generated images.
- Preferred image formats for committed, viewable diagrams: `SVG` for vector clarity and `PNG` for quick previews where appropriate.
- Avoid committing large binary exports repeatedly; prefer committing the text-based source and one optimized export per diagram.

## Mapping to Code Structure

The UML folder should mirror the repository layout so a developer can locate the diagram for any part of the system quickly.

Example mapping:

- `src/core/` -> `docs/UML/Package/core/` and `docs/UML/Class/core/`
- `src/integrations/` -> `docs/UML/Component/integrations/`
- `src/core/bean_vuln_cli.py` -> `docs/UML/Class/core/BeanVulnCli.puml`

When a package contains many classes, create a subfolder named after the package and place related diagrams there.

## Contribution Guidelines

- When changing code structure, update or add the corresponding UML diagrams in the matching folder.
- Prefer updating editable source files (PlantUML, Mermaid, draw.io) and regenerate outputs (`SVG`, `PNG`) for review.
- Include diagram updates in the same pull request as structural code changes where possible, or link the PRs when diagrams are updated separately.

## Diagram Granularity and Scope

- Class diagrams: show public/protected/private members and associations for classes central to a module or feature.
- Package diagrams: summarize dependencies between high-level modules.
- Component diagrams: focus on runtime components, service boundaries, adapters, and integration points.
- Sequence diagrams: model important workflows such as CLI invocation, taint tracking flow, and GNN model training pipeline interactions.

## Tools and Automation

- Recommended tools: PlantUML, Mermaid, draw.io (diagrams.net), UMLet. Use PlantUML for text-driven diagrams that are easy to review in diffs.
- Optional CI task: validate that editable diagram sources compile (e.g., `plantuml -tsvg`) and that exports are up-to-date.

## Maintenance Notes

- Diagrams should be reviewed and updated during significant refactors or API changes.
- Keep diagram sources small and focused. Large, monolithic diagrams are harder to maintain; prefer multiple focused diagrams.

## Quick Examples

- Class diagram for `src/core/cescl_inference.py` -> `docs/UML/Class/core/CesclInference.puml`
- Package overview for `src/integrations/` -> `docs/UML/Package/integrations/overview.puml`

---
If you want, I can also: generate a set of starter PlantUML files that mirror the current `src/` package layout, or add a small CI step that checks PlantUML rendering. Tell me which you'd prefer.
