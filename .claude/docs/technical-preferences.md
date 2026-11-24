# Technical Preferences

<!-- project.yaml at the repo root is the machine-readable source of truth for
     engine, specialists, naming, performance, platform, and testing.framework.
     This file is the human-readable LEGACY FALLBACK: agents and skills resolve
     each key from project.yaml first and fall back here only when the
     project.yaml key is absent. /setup-engine dual-writes both.
     Forbidden patterns and allowed libraries are NOT migrated — they live only
     in this file. Populated by /setup-engine; updated as decisions are made. -->

## Engine & Language

- **Engine**: Unreal Engine 5.8.4
- **Language**: C++ (primary); Blueprints for gameplay prototyping and tuning
- **Rendering**: Mobile Forward (initial broad-compatibility baseline; validate against device matrix before finalizing)
- **Physics**: Chaos

## Input & Platform

<!-- Written by /setup-engine. Read by /ux-design, /ux-review, /test-setup, /team-ui, and /dev-story -->
<!-- to scope interaction specs, test helpers, and implementation to the correct input methods. -->

- **Target Platforms**: Android
- **Input Methods**: Touch
- **Primary Input**: Touch
- **Gamepad Support**: None (initial release target)
- **Touch Support**: Full
- **Platform Notes**: The Blackview Tab 60 WiFi is a test device, not the minimum or maximum supported device. Build scalable quality tiers for a range of Android phones and tablets. Validate GPU feature support, memory, thermals, frame pacing, battery use, screen aspect ratios, and touch layouts on physical devices.

## Naming Conventions

- **Classes**: Prefixed PascalCase (AActor, UObject, FStruct conventions)
- **Variables**: PascalCase
- **Signals/Events**: PascalCase On<Event> delegates/events
- **Files**: PascalCase matching class without type prefix
- **Scenes/Prefabs**: PascalCase Levels/Maps
- **Constants**: UPPER_SNAKE_CASE (UNVERIFIED — confirm against pinned Unreal coding standard)

## Performance Budgets

- **Target Framerate**: [TO BE CONFIGURED — define low/mid/high Android tiers after profiling]
- **Frame Budget**: [TO BE CONFIGURED — depends on selected frame-rate tier]
- **Draw Calls**: [TO BE CONFIGURED — measure on representative Android devices]
- **Memory Ceiling**: [TO BE CONFIGURED — set per Android device tier]

## Testing

- **Framework**: [TO BE CONFIGURED — Unreal Automation Spec suggested; confirm before adding test infrastructure]
- **Minimum Coverage**: [TO BE CONFIGURED]
- **Required Tests**: Balance formulas, gameplay systems, networking (if applicable)

## Forbidden Patterns

<!-- Add patterns that should never appear in this project's codebase -->
- [None configured yet — add as architectural decisions are made]

## Allowed Libraries / Addons

<!-- Add approved third-party dependencies here -->
- [None configured yet — add as dependencies are approved]

## Architecture Decisions Log

<!-- Quick reference linking to full ADRs in docs/architecture/ -->
- [No ADRs yet — use /architecture-decision to create one]

## Engine Specialists

<!-- Written by /setup-engine when engine is configured. -->
<!-- Read by /code-review, /architecture-decision, /architecture-review, and team skills -->
<!-- to know which specialist to spawn for engine-specific validation. -->

- **Primary**: unreal-specialist
- **Language/Code Specialist**: unreal-specialist (C++); ue-blueprint-specialist (Blueprint graphs)
- **Shader Specialist**: unreal-specialist (materials and shaders)
- **UI Specialist**: ue-umg-specialist (UMG, CommonUI, touch input routing)
- **Additional Specialists**: ue-gas-specialist (abilities/attributes), ue-replication-specialist (networking if multiplayer is introduced)
- **Routing Notes**: Primary handles C++ architecture; Blueprint specialist handles graph design; GAS handles abilities and attributes; replication specialist only if multiplayer is added; UMG specialist handles touch-first UI.

### File Extension Routing

<!-- Skills use this table to select the right specialist per file type. -->
<!-- If a row says [TO BE CONFIGURED], fall back to Primary for that file type. -->

| File Extension / Type | Specialist to Spawn |
|-----------------------|---------------------|
| Game code (.cpp, .h files) | unreal-specialist |
| Shader / material files (.usf, .ush, Material assets) | unreal-specialist |
| UI / screen files (.umg, UMG Widget Blueprints) | ue-umg-specialist |
| Scene / level files (.umap, .uasset) | unreal-specialist |
| Native extension / plugin files (.uplugin, modules) | unreal-specialist |
| Blueprint graphs (.uasset BP classes) | ue-blueprint-specialist |
| General architecture review | Primary |
