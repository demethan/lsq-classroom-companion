# LSQ Classroom Companion

LSQ Classroom Companion is a proposed classroom accessibility system for Deaf students who rely on Langue des signes québécoise (LSQ). The initial goal is to help a student follow a non-LSQ teacher's live instruction through French captions, validated LSQ vocabulary support, lesson transcripts, and teacher-reviewed summaries.

This repository begins as a discovery, feasibility, and design project. Implementation should not proceed until legal/data-rights and educational validation questions are answered.

## Core use case

A hearing/non-LSQ teacher teaches in French in a classroom. The classroom has:

- a Windows classroom computer
- a smartboard or TV display
- a wearable teacher microphone connected to the computer
- possible access to a Dell GB10 AI computer in the datacenter

The Deaf student receives support through:

- live French captions
- key vocabulary displayed in LSQ using validated video clips or sign cards
- lesson transcript
- post-class summary
- later, validated avatar or generated LSQ signing when feasible

## Important positioning

The MVP is not a replacement for a professional LSQ interpreter.

The early product should be positioned as an assistive classroom support tool for situations where interpreter availability, vocabulary preparation, summaries, or reinforcement are needed.

## Recommended MVP

The first prototype should be narrow:

- French instruction only
- one classroom pilot
- science or math first
- 30-100 validated LSQ educational terms
- browser-based classroom app
- server-side inference on datacenter hardware
- no raw audio retention by default

## Recommended architecture

Classroom computer:

- Chrome or Edge browser
- microphone capture
- smartboard/TV display

Datacenter:

- Dell GB10 AI computer
- ASR service for French transcription
- local LLM service for cleanup, key-term extraction, and summaries
- LSQ media library
- transcript/session database
- admin/content review dashboard

## First technical milestone

Bench Prototype 0:

1. Capture microphone audio in browser.
2. Stream audio securely to the datacenter server.
3. Run French speech-to-text locally on the GB10.
4. Display live captions in browser.
5. Save a transcript according to privacy policy.
6. Generate a post-session summary.

No LSQ generation in this milestone. First make the pipe reliable.

## Démonstration Web

Une démonstration statique sécuritaire pour les parties prenantes est publiée avec GitHub Pages :

- https://demethan.github.io/lsq-classroom-companion/
- Chemin direct : https://demethan.github.io/lsq-classroom-companion/spikes/001-avatar-demo-options/demo.html

La démonstration montre seulement la mécanique de l’interface : texte en entrée, détection de vocabulaire et affichage d’un soutien visuel associé aux signes. Elle ne constitue pas une traduction LSQ validée.

## Documentation

- `docs/project-working-document.md` — current project understanding
- `docs/feasibility/legal-and-data-rights.md` — legality and data-rights research plan
- `docs/feasibility/technical-feasibility.md` — technical feasibility plan
- `docs/feasibility/resource-inventory.md` — reusable projects, datasets, vendors, and contacts
- `docs/architecture/initial-architecture.md` — initial system architecture
- `docs/privacy/classroom-data-policy-draft.md` — draft privacy/data policy
- `docs/contacts/outreach-templates.md` — contact templates for resource owners and researchers

## Current phase

Discovery and feasibility.

The next decisions are:

1. Confirm pilot subject and grade level.
2. Verify GB10 hardware/software stack.
3. Benchmark French ASR on classroom-style audio.
4. Confirm licensing/permission for LSQ educational resources.
5. Identify LSQ experts/interpreters for validation.
