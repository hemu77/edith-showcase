<div align="center">

<img src="https://img.shields.io/badge/EDITH-WINDOWS%20AI%20ASSISTANT-07111f?style=for-the-badge&labelColor=07111f&color=d8a84e" alt="EDITH Windows AI Assistant">

# E D I T H

### A private, offline AI that sees your whole desktop and works by voice

<p>
  <a href="https://github.com/hemu77/edith-windows-assistant"><strong>Private implementation repository</strong></a>
  &nbsp;&middot;&nbsp;
  <a href="mailto:skilaru@arizona.edu?subject=EDITH%20private%20repository%20access"><strong>Request access</strong></a>
</p>

<img src="https://img.shields.io/badge/Windows-native-0078D4?style=flat-square&logo=windows11&logoColor=white" alt="Windows native">
<img src="https://img.shields.io/badge/Local--first-private-16a085?style=flat-square" alt="Local first and private">
<img src="https://img.shields.io/badge/Offline-no%20internet-111827?style=flat-square" alt="Offline">
<img src="https://img.shields.io/badge/Hands--free-accessible-8e44ad?style=flat-square" alt="Hands-free and accessible">

</div>

## The vision

A computer should understand what you are working on, help you think about it, and do it all without your data ever leaving the machine.

EDITH is being built toward that: a personal AI that lives on the Windows desktop, sees every window and tab its owner has open, reads documents of any length, reasons about them across sources, and acts on the computer by voice with the owner always in control. It runs entirely on the owner's own hardware, with no internet connection required, and is designed so that people who cannot easily use a keyboard, mouse, or their legs can operate a whole computer by speaking to it.

## The HUD

![EDITH golden 3D HUD with layered message panes](assets/edith-hud.png)

EDITH appears as a transparent golden reactor floating on the desktop. Answers arrive as layered holographic panes connected to the ring by light filaments: the newest in focus above the ring, earlier ones on a curved wall to either side, each one pinnable, foldable, and dismissible by click or by voice.

## What EDITH is aiming for

### Read anything, at any length

Whole books, 400-page reports, dense research papers, scanned contracts, and spreadsheets with thousands of rows, read end to end rather than skimmed. EDITH is designed to keep track of exactly how much of a document it has covered, cite the page or row behind every claim, pull numbers out of tables exactly instead of guessing at them, and answer questions that span several documents at once.

### Understand the whole desktop, not one window

What is on screen, across every open application and every browser tab. Ask "what is this?", then "and that one?", then "what is the difference between these two?", or "which of my open tabs actually answers my question?". EDITH follows the owner's attention from window to window, keeps the sources straight, and always says which one an answer came from.

### Fully offline

No cloud, no API keys, no connection required. Speech recognition, reasoning, document analysis, and speech synthesis all run on the local machine, so EDITH works on a plane, in a lab, or on a network that is not allowed to send data out.

### A model of its own

Rather than borrowing a general chatbot, EDITH is being distilled into its own compact model: trained from the behaviour of much larger models on exactly the work EDITH does, such as grounding answers in a source, reading long documents in passes, refusing to invent, and choosing the right tool. The goal is large-model judgement at a size that runs in real time on a laptop GPU.

### Hands-free computing for everyone

For people with limited use of their hands or legs, a computer should not require a mouse. EDITH is designed to let its owner navigate, read, write, compare, and operate applications entirely by voice, with clear spoken confirmation before anything changes and an instant "EDITH, stop" that always works.

### Secure reasoning by design

An assistant that reads web pages and documents will eventually read something written to manipulate it. EDITH's direction follows the CaMeL line of research: a privileged planner that decides what to do, a quarantined reader that handles untrusted content and cannot act, and data flow tracking so that nothing read from a page can trigger an action on its own. Every action leaves a receipt, and EDITH is not allowed to claim it did something that never ran.

### Private by default

The owner's voice, documents, and screen stay on the owner's machine. Temporary research context is forgotten when a session ends, personal memory is kept only with consent, and EDITH answers to its owner's voice.

## How it fits together

```text
Voice / typed request / Win+Shift+E
                 |
                 v
Windows host and session runtime
                 |
                 v
Understand the request and every source the owner is looking at
       |                 |                 |
       v                 v                 v
Planner             Quarantined        Governed actions
(trusted intent)    reader             with confirmation
                    (untrusted text)   and receipts
       |                 |                 |
       +-----------------+-----------------+
                         |
                         v
On-device model, offline, answering with its sources in the golden HUD
```

## Built with

- Python and native Windows APIs
- On-device language and speech models
- OpenGL for the 3D HUD

## Current progress and source code

This page describes where EDITH is headed. Current progress, demonstrations, and the full implementation live in a private repository.

<div align="center">

### To see EDITH's current progress, request access to the private repository

<a href="mailto:skilaru@arizona.edu?subject=EDITH%20private%20repository%20access"><img src="https://img.shields.io/badge/REQUEST%20PRIVATE%20REPOSITORY%20ACCESS-C62828?style=for-the-badge&logo=gmail&logoColor=white" alt="Request private repository access"></a>

Contact **skilaru@arizona.edu** for repository access or a live demonstration.

</div>

## Relationship to OpenJarvis

EDITH began as a fork of and reference to the Apache-2.0 OpenJarvis project. OpenJarvis remains the attributed upstream foundation, but EDITH is not presented as the official OpenJarvis product. EDITH has been developed toward a different goal: a private, context-aware desktop assistant that lives within its owner's operating environment. Applicable upstream license and attribution notices are preserved.
