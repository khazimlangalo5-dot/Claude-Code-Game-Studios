# Unreal Engine — Version Reference

| Field | Value |
|-------|-------|
| **Engine Version** | Unreal Engine 5.8.4 |
| **Installed at pin time** | NOT DETERMINED — `/setup-engine` §3 probes the installed editor and records the result here. |
| **Release Date** | June 2026 (5.8.0); latest hotfix 5.8.4, October 20, 2026 |
| **Project Pinned** | 2026-11-24 |
| **Last Docs Verified** | 2026-11-24 (5.8.4 hotfix and UE 5.8 Android rendering/support documentation) |
| **LLM Knowledge Cutoff** | May 2025 |

## Knowledge Gap Warning

May 2025 is a floor for every model the studio runs on: a newer model may know more, but check this folder first.

The LLM's training data likely covers Unreal Engine up to ~5.3. Versions 5.4
through 5.8 introduced significant changes that the model does NOT know about
(5.4 and 5.5 predate the cutoff but are not reliably covered). Always
cross-reference this directory before suggesting Unreal API calls.

## Installed-Version Gap Warning

The warning above is one-directional — it covers the **model** knowing less than
this pin. The reverse gap is real and `/setup-engine` §3 creates it deliberately
("pin the newer one and upgrade later"): this reference can sit **ahead of the
installed editor**, and an agent citing it correctly then emits APIs that do not
compile locally. **Check `Installed at pin time` above before trusting a
version-qualified claim** — `NOT DETERMINED` means the gap is unknown, not absent.

## Post-Cutoff Version Timeline

| Version | Release | Risk Level | Key Theme |
|---------|---------|------------|-----------|
| 5.6 | Jun 2025 | MEDIUM | Large open worlds at 60 Hz (Hardware Ray Tracing Lumen performance, Fast Geometry Streaming plugin, Experimental), MetaHuman Creator in the engine, in-editor animation and rigging tools |
| 5.7 | Nov 2025 | HIGH | PCG production-ready, Substrate production-ready (on by default for new projects), MegaLights Beta, in-editor AI Assistant (Experimental) |
| 5.8 | Jun 2026 | HIGH | MegaLights production-ready, Iris replication production-ready, Mesh Terrain (Experimental), Lumen Lite (Beta), Enhanced Input and Common UI unified, MCP Server plugin (Experimental), C++20 minimum, WASAPI default audio backend on Windows, multi-pass deferred default on mobile |

| 5.8.4 | Oct 20, 2026 | HIGH | Hotfix: editor and Blueprint stability, UAT, Landscape, Modeling, Media, MetaHuman, Movie Render Pipeline and rendering fixes |

## Unreal Engine 5 Releases Before the Cutoff

These two predate the May 2025 cutoff, so they are not post-cutoff. The Knowledge
Gap Warning above still applies to them: treat their APIs as unconfirmed until
checked against this directory.

| Version | Release | Risk Level | Key Theme |
|---------|---------|------------|-----------|
| 5.4 | Apr 2024 | HIGH | Motion Matching production-ready, Choosers, animation authoring (Modular Control Rig, Sequencer rework), Nanite Tessellation (Experimental), Motion Design mode |
| 5.5 | Nov 2024 | HIGH | MegaLights introduced, Substrate moves to Beta, Sequencer animation authoring, mobile game development, many features reach production-ready |

Release dates verified 2026-10-17 against Epic's release announcement threads:
5.4 (Apr 23, 2024) https://forums.unrealengine.com/t/unreal-engine-5-4-released/1817064,
5.5 (Nov 12, 2024) https://forums.unrealengine.com/t/unreal-engine-5-5-released/2117936,
5.6 (Jun 3, 2025) https://forums.unrealengine.com/t/unreal-engine-5-6-released/2538952,
5.7 (Nov 12, 2025) https://forums.unrealengine.com/t/unreal-engine-5-7-released/2673913,
5.8 (Jun 17, 2026) https://forums.unrealengine.com/t/unreal-engine-5-8-released/2729274.
Hotfixes 5.8.1 (Jul 28, 2026), 5.8.2 (Aug 25, 2026) and 5.8.3 (Sep 22, 2026):
https://forums.unrealengine.com/t/5-8-3-hotfix-released/2833315. Key themes come
from the same threads and from the 5.7 and 5.8 release notes (Verified Sources below).

## Major Changes from UE 5.3 to UE 5.8

### Breaking Changes
- **Substrate Material System**: New material framework (replaces legacy materials); new projects created in 5.7+ have it enabled automatically
- **PCG (Procedural Content Generation)**: Production-ready, major API changes
- **MegaLights**: New lighting system for many shadow-casting dynamic lights; production-ready in 5.8
- **Animation Authoring**: New rigging and animation tools
- **C++20 minimum (5.8)**: `CppStandardVersion.Cpp14` and `Cpp17` are obsolete and no longer compile
- **5.8 API removals**: deprecated animation, Control Rig and Live Link symbols from 5.0-5.6 removed; PhysicsMover removed from Mover in favour of ChaosMover — see `breaking-changes.md`

### New Features (Post-Cutoff)
- **MegaLights**: Dynamic lighting at massive scale (production-ready in 5.8)
- **Substrate Materials**: Production-ready modular material system (5.7)
- **PCG Framework**: Procedural world generation (production-ready in 5.7)
- **Iris**: Replication system, production-ready in 5.8
- **Lumen Lite (5.8, Beta)**: Medium-quality GI setting, the default on current-generation handheld consoles
- **Mesh Terrain (5.8, Experimental)**: Mesh-based terrain beyond heightfield landscapes
- **Enhanced Virtual Production**: MetaHuman integration, deeper VP workflows
- **Animation Improvements**: Better rigging, blending, procedural animation
- **AI Assistant (5.7)**: In-editor AI help (Experimental)
- **MCP Server (5.8)**: Editor plugin that lets agentic AI systems connect to the Unreal Editor (Experimental)

### Deprecated Systems
- **Legacy Material System**: Migrate to Substrate for new projects
- **Old PCG API**: Use new production-ready PCG API (5.7+)
- **Raw Input plugin (5.8)**: Deprecated in favour of the Game Input for Windows plugin
- **`UE_LOG` (5.8)**: Still supported; Epic says it "will eventually be deprecated" and asks for `UE_LOGF`

## Verified Sources

- Official docs: https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-8-documentation?application_version=5.8
- UE 5.8 release notes: https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-8-release-notes?application_version=5.8
- UE 5.8 release thread: https://forums.unrealengine.com/t/unreal-engine-5-8-released/2729274
- UE 5.8.3 hotfix: https://forums.unrealengine.com/t/5-8-3-hotfix-released/2833315
- UE 5.7 release notes: https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-7-release-notes
- What's new in 5.7: https://dev.epicgames.com/documentation/en-us/unreal-engine/whats-new
- UE 5.7 announcement: https://www.unrealengine.com/en-US/news/unreal-engine-5-7-is-now-available
- UE 5.5 blog: https://www.unrealengine.com/en-US/blog/unreal-engine-5-5-is-now-available
- Migration guides: https://dev.epicgames.com/documentation/en-us/unreal-engine/upgrading-projects-to-newer-versions-of-unreal-engine
- Engine source, read from a UE 5.8.1 install on 2026-10-17: `Engine/Source/Programs/UnrealBuildTool/System/CppCompileEnvironment.cs` (C++ standard), `Engine/Source/Runtime/RenderCore/Private/RenderUtils.cpp` (Substrate defaults)


## Android Rendering Strategy (UE 5.8)

- Initial baseline: Mobile Forward. Epic documents it as the default mobile shading mode and the fastest baseline with compatibility across the widest variety of hardware. This is a cautious starting point for a project that must scale across Android devices; it is not a final rendering decision.
- Profile Mobile Deferred as a possible higher-tier path. Epic says deferred shading can improve performance and memory use for complex dynamic lighting on tile-based mobile GPUs, while requiring relatively higher-end hardware and carrying Mali/Vulkan attachment limitations. Test representative devices before choosing it.
- Do not enable the Android desktop renderer for the baseline. Epic classifies the Android Vulkan desktop renderer as Experimental and notes its high resource cost. Lumen on Android requires this renderer and Vulkan SM5 on supported high-end device profiles; Epic does not recommend shipping that experimental combination.
- Maintain device profiles and quality tiers; profile GPU, CPU, memory, thermal behaviour, frame pacing and battery use on real hardware. The Blackview Tab 60 WiFi is a test device only, not the project's declared minimum or maximum specification.

## UE 5.8.4 Hotfix (2026-10-20)

Epic's official hotfix notes list editor and Blueprint stability fixes, AutomationTool output fixes, Landscape/Modeling/Media/MetaHuman/Movie Render Pipeline fixes, and rendering fixes including a Lumen SceneCapture2D regression. The notes reviewed list iOS/tvOS/iPadOS platform changes; do not infer an Android-specific fix from them.

## Verified Sources (2026-11-24)

- UE 5.8.4 hotfix release notes: https://forums.unrealengine.com/t/5-8-4-hotfix-released/2842775
- UE 5.8 Mobile Rendering and Shading Modes: https://dev.epicgames.com/documentation/en-us/unreal-engine/mobile-rendering-and-shading-modes-for-unreal-engine
- UE 5.8 Mobile Deferred Shading: https://dev.epicgames.com/documentation/unreal-engine/using-the-mobile-deferred-shading-mode-in-unreal-engine
- UE 5.8 Android desktop renderer: https://dev.epicgames.com/documentation/unreal-engine/using-the-desktop-renderer-on-mobile-in-unreal-engine?lang=en-US
- UE 5.8 Lumen on Mobile: https://dev.epicgames.com/documentation/en-us/unreal-engine/using-lumen-global-illumination-on-mobile-in-unreal-engine
- UE 5.8 Android Support: https://dev.epicgames.com/documentation/unreal-engine/android-support-for-unreal-engine?lang=en-US
