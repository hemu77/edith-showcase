<div align="center">

# EDITH

### A Windows-native, local-first voice and Codex assistant

EDITH turns the Windows desktop into an interactive AI workspace: invoke it with a hotkey, speak or type naturally, and let it understand the document or web page currently in view.

![Windows](https://img.shields.io/badge/Windows-native-0078D4?logo=windows11&logoColor=white)
![Local first](https://img.shields.io/badge/AI-local--first-22c55e)
![Codex](https://img.shields.io/badge/Codex-integrated-111827)

</div>

## Why I built it

Most assistants are isolated chat boxes: users must upload a file, copy text, explain their context, and restart that process for every task. EDITH is designed around the opposite interaction. It lives in Windows, acquires foreground context only when requested, and selects the least expensive capable route for each command.

## What makes it different

- **Native activation:** `Win+Shift+E` opens EDITH without navigating to a web application.
- **Context without a separate RAG workflow:** EDITH can inspect the foreground PDF or active browser article at request time.
- **Local-first routing:** ordinary conversation and lightweight commands stay on a private local model.
- **Codex escalation:** engineering, deep research, and tool-assisted work route to Codex with the selected model and progress visible in the HUD.
- **Grounded output:** EDITH records the transcript, capture method, source completeness, route, task events, and answer.
- **Privacy and control:** sensitive mutations require approval, and temporary EDITH-owned Codex sessions are cleaned up when the session ends.

## Local document understanding

In this run, EDITH captured a 20-page foreground PDF locally and produced a detailed explanation based on the extracted document rather than a generic topic overview.

![EDITH explaining a local PDF](assets/edith-local-pdf.png)

## Live web context

Here EDITH used the active browser page as evidence, routed the research request to Codex Terra, and clearly disclosed that the captured article was truncated instead of claiming a complete reading.

![EDITH researching the active web page](assets/edith-web-context.png)

## System flow

`Voice / hotkey → Windows listener → EDITH gateway → local model or Codex → streamed native HUD response`

The system includes a supervised Windows listener, microphone diagnostics, conversational session state, foreground context capture, a private browser companion, deterministic routing, task lifecycle management, and a React-based native HUD.

## Verification

- 159 targeted Python tests passed; 1 platform-dependent test skipped.
- 9 frontend authentication tests passed.
- Production TypeScript and Vite build passed.
- Local-PDF and active-web journeys were exercised end to end on the target Windows machine.
- Explicit session shutdown was verified to leave no EDITH-owned Codex task behind.

## Repository access

This is a documentation-only portfolio showcase. The implementation repository is private to protect local-runtime details and active development work. Source access can be discussed for a technical review.

## Foundation

EDITH is an independent specialization built on the Apache-2.0-licensed [OpenJarvis](https://github.com/open-jarvis/OpenJarvis) foundation.
