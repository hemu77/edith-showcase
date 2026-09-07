<div align="center">

<img src="https://img.shields.io/badge/EDITH-WINDOWS%20AI%20ASSISTANT-07111f?style=for-the-badge&labelColor=07111f&color=d8a84e" alt="EDITH Windows AI Assistant">

# E D I T H

### A local-first Windows assistant for documents, desktop context, research, and engineering

<p>
  <a href="https://github.com/hemu77/edith-windows-assistant"><strong>View the private implementation repository</strong></a>
  &nbsp;&middot;&nbsp;
  <a href="mailto:skilaru@arizona.edu?subject=EDITH%20technical%20review"><strong>Request code access</strong></a>
</p>

<img src="https://img.shields.io/badge/Windows-native-0078D4?style=flat-square&logo=windows11&logoColor=white" alt="Windows native">
<img src="https://img.shields.io/badge/Local--first-private-16a085?style=flat-square" alt="Local first and private">
<img src="https://img.shields.io/badge/Codex-integrated-111827?style=flat-square" alt="Codex integrated">
<img src="https://img.shields.io/badge/Status-working%20prototype-d8a84e?style=flat-square" alt="Working prototype">

</div>

## What EDITH is

EDITH is a Windows-native personal AI assistant designed to make interacting with a computer more natural, contextual, and private. Instead of behaving only like a chatbot, EDITH is being built to understand the work already in front of the user, including a local document, foreground window, browser article, or software project. A request can be spoken through the Windows runtime or typed directly into EDITH's transparent golden 3D HUD. Simple questions stay on the device whenever possible, while complex research and engineering work can be routed through a protected local gateway to Codex. The end goal is a dependable desktop companion that can explain what it sees, preserve useful conversational context, disclose which source and model it used, ask before consequential actions, and verify outcomes instead of merely claiming success.

## Current capabilities

- Native `Win+Shift+E` activation with a supervised Windows host, tray lifecycle, and single-instance HUD.
- Golden, transparent 3D desktop reactor rendered with real OpenGL geometry and a NumPy software fallback.
- Typed interaction inside the native HUD: Shift-click the reactor, type a request, press Enter to send, or Escape to leave typing mode.
- Local Windows answers for time, date, battery, configured region/time zone, clipboard text, recent items, open-file handles, and indexed filename searches.
- Natural-language variants for common local commands, with safeguards against quoted, negated, or compound phrases accidentally triggering a reader.
- Bounded foreground-window capture through Windows UI Automation with an OCR fallback.
- Local text, DOCX, and PDF extraction with explicit source, extraction method, limits, and coverage reporting.
- Browser-page context for explicit requests such as "summarize this page," with unavailable or incomplete sources reported honestly.
- Local-model conversation and lightweight explanation through a `llama.cpp`-compatible Qwen GGUF runtime.
- Codex routing for bounded repository inspection, research, debugging, and implementation tasks.
- Codex task status, continuation, retry, cancellation, approval, and EDITH-owned lifecycle tracking.
- Allowlisted Windows controls for volume, media, scrolling, navigation, and approved minimize, restore, or maximize operations.
- Personal and Research session foundations, including temporary research-context cleanup.
- Evidence-aware streamed responses that withhold some unsupported action claims and surface model failures instead of silently completing.

## See it in action

### Local PDF understanding

EDITH captured a 20-page foreground PDF and produced a document-specific explanation while reporting its extraction limits.

![EDITH explaining a local PDF](assets/edith-local-pdf.png)

### Active web context

EDITH used captured browser text as evidence, routed deeper analysis to Codex Terra, and disclosed that the captured article was incomplete.

![EDITH researching an active web page](assets/edith-web-context.png)

## How it works

```text
Voice / typed request / Win+Shift+E
                 |
                 v
Supervised Windows host and session runtime
                 |
                 v
Capture + transcription + deterministic routing
       |                 |                 |
       v                 v                 v
Windows-native       Local Qwen       Codex Luna/Terra
facts and controls   conversation      research/engineering
       |                 |                 |
       +-----------------+-----------------+
                         |
                         v
Golden native HUD: state, context, progress, result, and errors
```

## Technology stack

### AI and voice

- Python, Pydantic, FastAPI-style HTTP/WebSocket routes, and SQLite persistence
- Qwen3-4B GGUF served locally through `llama.cpp`
- Faster Whisper for offline speech-to-text
- Silero VAD for speech segmentation
- ONNX wake-word and owner-verification foundations
- Local text-to-speech with interruption and stop-control foundations
- Codex App Server integration through an EDITH-owned gateway

### Native Windows and perception

- Win32 APIs through Python `ctypes`
- Windows UI Automation with cached, bounded traversal
- Local OCR fallback with a hard subprocess timeout
- Windows Search, clipboard, power, process, and foreground-window APIs
- Typed perception records containing hashes, source identity, capture attempts, coverage, and limits
- Local IPC between the Windows host, listener, and HUD

### Interface

- ModernGL/OpenGL meshes, perspective camera, depth testing, per-fragment lighting, and offscreen rendering
- NumPy software painter used when the GPU context is unavailable or lost
- `UpdateLayeredWindow` per-pixel alpha for a floating transparent desktop surface
- React, TypeScript, Vite, Tailwind CSS, Zustand, Motion, Recharts, and Vitest for the separate diagnostics/control surface

### Reliability and governance

- Single-instance host/HUD protections and bounded runtime recovery
- Typed action allowlist and approval boundaries for consequential operations
- Context treated as untrusted data rather than executable instructions
- Evidence-bearing task, model, route, capture, and cleanup records
- Local-first storage under `D:\EDITH`

## Recent reliability improvements

- Prevented tray commands from opening repeated browser tabs; Show EDITH and Open control center now restore the existing native HUD.
- Prevented Show EDITH from unintentionally toggling microphone capture.
- Added native typed requests for testing when voice input is unavailable.
- Added maximize support to the approved window-action registry.
- Made the HUD expire stale backend state and reject malformed state payloads.
- Added automatic software-renderer fallback after a GPU context/render failure.
- Added bounded document reads, UI Automation capture, and OCR execution.
- Corrected battery handling so Windows unknown values never become invented percentages.
- Removed frontend defaults that presented unknown capture coverage as complete.
- Improved local phrasing and filename parsing while avoiding accidental readers for commands such as "do not read my clipboard."
- Changed microphone configuration to follow the current Windows default input rather than pinning EDITH to a disconnected headset.

## Verification status

Focused automated checks currently cover the native HUD and 3D renderer, host lifecycle, bounded perception, local Windows answers, command phrasing, streaming safeguards, and microphone-device selection. The latest focused runs completed successfully, including native-runtime renderer checks and local-command regressions.

Automated tests are not presented as proof of physical voice reliability. The current laptop microphone produces audio frames, but a recent live diagnostic did not produce recognizable speech through either Silero VAD or direct Faster Whisper. Live transcription, wake behavior, interruption, memory cleanup, browser correlation, Codex task cleanup, and fully disconnected operation remain human acceptance gates.

## Honest project status

EDITH is a working engineering prototype, not a production-ready autonomous desktop agent. The native HUD, local command routing, context capture, local-model path, and Codex integration exist, but capabilities have different confidence levels. Arbitrary desktop clicking and typing, unrestricted file opening, reliable multi-task Codex targeting, mobile control, macOS support, zero hallucinations, and zero false wakes are not claimed as completed features. EDITH intentionally does not receive blanket administrator access.

## Code access

The full implementation repository is private because it contains active local-runtime integration and development work. GitHub does not provide a public read-only URL for a private repository: reviewers must be invited to the repository or request access.

<div align="center">

## Interested in reviewing the engineering?

### Contact **skilaru@arizona.edu** for private source-code access

<a href="mailto:skilaru@arizona.edu?subject=EDITH%20source%20access"><img src="https://img.shields.io/badge/REQUEST%20PRIVATE%20CODE%20ACCESS-C62828?style=for-the-badge&logo=gmail&logoColor=white" alt="Request private source-code access"></a>

</div>

## Relationship to OpenJarvis

EDITH began as a fork of and reference to the Apache-2.0 OpenJarvis project. OpenJarvis remains the attributed upstream foundation, but EDITH is not presented as the official OpenJarvis product. EDITH's Windows-native host, golden 3D HUD, local/Codex routing, perception records, bounded Windows capture, approval model, task lifecycle, and product direction have been developed for a different goal: a private, context-aware desktop assistant that lives within the owner's operating environment. Applicable upstream license and attribution notices are preserved.

---

<p align="center"><strong><span style="color:#c62828">WORK IN PROGRESS — EDITH IS AN ACTIVELY EVOLVING ENGINEERING PROTOTYPE.</span></strong></p>
