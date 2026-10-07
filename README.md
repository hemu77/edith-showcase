<div align="center">

<img src="https://img.shields.io/badge/EDITH-WINDOWS%20AI%20ASSISTANT-07111f?style=for-the-badge&labelColor=07111f&color=d8a84e" alt="EDITH Windows AI Assistant">

# E D I T H

### A local-first Windows assistant that understands the work in front of you

<p>
  <a href="https://github.com/hemu77/edith-windows-assistant"><strong>Private implementation repository</strong></a>
  &nbsp;&middot;&nbsp;
  <a href="mailto:skilaru@arizona.edu?subject=EDITH%20private%20repository%20access"><strong>Request access</strong></a>
</p>

<img src="https://img.shields.io/badge/Windows-native-0078D4?style=flat-square&logo=windows11&logoColor=white" alt="Windows native">
<img src="https://img.shields.io/badge/Local--first-private-16a085?style=flat-square" alt="Local first and private">
<img src="https://img.shields.io/badge/Voice-and%20typed-111827?style=flat-square" alt="Voice and typed">

</div>

## The vision

EDITH is a personal AI assistant that lives on the Windows desktop and understands what its owner is working on. Instead of copying text into a chatbot, the owner simply asks: "what is this page about?", "which year has the highest value in this file?", "what is the difference between these two?". EDITH looks at the window, document, or data in front of the owner, answers from that source, and says which source it used.

The goal is a desktop companion that is private by default, honest about what it saw, and careful about what it does. Everyday questions and document reading stay on the device. Larger research and engineering work can be handed to a more capable model through a protected gateway. Nothing on the computer changes without the owner's clear confirmation.

## The HUD

![EDITH golden 3D HUD with layered message panes](assets/edith-hud.png)

EDITH appears as a transparent golden reactor floating on the desktop. Answers arrive as layered holographic panes connected to the ring by light filaments: the newest answer in focus above the ring, earlier ones resting on a curved wall to either side. Panes can be pinned, folded, dismissed, or brought into focus with a click, and the owner can speak or type at any time.

## What EDITH is designed to do

### Understand what is on screen

- Read the spreadsheet, document, PDF, or web page in front of the owner and answer questions about it.
- Compare two windows side by side: ask about each one, then ask what separates them.
- Keep the thread of a conversation, so "give an example of that" or "and this one?" means what the owner expects.
- Name the source behind every answer, and say plainly when something is not in the source instead of filling the gap.

### Act carefully

- Control windows, sound, media, and navigation through a fixed list of allowed actions.
- Ask for a spoken confirmation that names the exact target before acting, and stop the moment the owner says no.
- Notice when the owner has switched to a different application and ask which one they mean, rather than silently reading it.

### Stay private and in the owner's control

- Activate with `Win+Shift+E`, with separate Personal and Research modes.
- Stop instantly on "EDITH, stop", and forget temporary research context when a session ends.
- Recognise its owner's voice, keep processing local wherever possible, and treat everything it reads as data, never as instructions.

## How it fits together

```text
Voice / typed request / Win+Shift+E
                 |
                 v
Windows host and session runtime
                 |
                 v
Understand the request and the source in front of the owner
       |                 |                 |
       v                 v                 v
Windows actions     Local model        Larger model for
and facts           on the device      research and engineering
       |                 |                 |
       +-----------------+-----------------+
                         |
                         v
Golden HUD: answers with their source, progress, and confirmations
```

## Built with

- Python and native Windows APIs
- A local language model and offline speech recognition
- OpenGL for the 3D HUD
- React and TypeScript for diagnostics tooling

## Current progress and source code

This page describes where EDITH is headed. Current progress, demonstrations, and the full implementation live in a private repository.

<div align="center">

### To see EDITH's current progress, request access to the private repository

<a href="mailto:skilaru@arizona.edu?subject=EDITH%20private%20repository%20access"><img src="https://img.shields.io/badge/REQUEST%20PRIVATE%20REPOSITORY%20ACCESS-C62828?style=for-the-badge&logo=gmail&logoColor=white" alt="Request private repository access"></a>

Contact **skilaru@arizona.edu** for repository access or a live demonstration.

</div>

## Relationship to OpenJarvis

EDITH began as a fork of and reference to the Apache-2.0 OpenJarvis project. OpenJarvis remains the attributed upstream foundation, but EDITH is not presented as the official OpenJarvis product. EDITH has been developed toward a different goal: a private, context-aware desktop assistant that lives within its owner's operating environment. Applicable upstream license and attribution notices are preserved.
