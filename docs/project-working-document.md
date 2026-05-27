# LSQ Classroom Companion — Project Working Document

## Current status

Global requirements have been defined at concept level. This document captures the working understanding so the project does not become scattered across chat history.

## Core use case

A non-LSQ teacher teaches in a classroom. A Deaf student who relies on LSQ needs better access to the instructional content.

The classroom already has:

- A Windows classroom computer
- A smartboard or TV display
- Potential wearable teacher microphone connected to the classroom computer
- Possible access to a Dell GB10 AI computer in the datacenter for centralized inference

## Product goal

Build an LSQ classroom accessibility assistant that helps a Deaf LSQ student follow classroom instruction through:

- live French captions
- LSQ vocabulary/sign support
- lesson transcript
- post-class summary
- eventually LSQ avatar or generated signing, once validated

The initial product should assist access to instruction. It should not be positioned as a replacement for a professional LSQ interpreter.

## Recommended MVP

Name: LSQ Classroom Companion

Initial scope:

- French-speaking teacher
- science or math classroom
- one classroom pilot
- wearable microphone
- browser-based classroom app
- server-side processing on datacenter GB10
- live captions on smartboard/TV
- automatic key educational term detection
- display validated LSQ sign clips or sign cards for key terms
- transcript saved according to privacy policy
- post-class summary generated for teacher review

Not in MVP:

- universal real-time LSQ interpretation
- full generative LSQ avatar
- all subjects
- offline-first Windows installer
- unlicensed scraping/training on LSQ videos

## Recommended architecture

Classroom:

- Windows computer
- Chrome or Edge browser
- USB/wireless wearable microphone
- smartboard/TV display

Datacenter:

- Dell GB10 AI computer
- web application backend
- local ASR service
- local LLM service
- LSQ media library
- transcript/session database
- admin/content dashboard

Data flow:

1. Teacher opens classroom web app.
2. Browser captures wearable microphone audio.
3. Audio streams securely to datacenter server.
4. GB10 runs French speech-to-text locally.
5. Backend returns live captions.
6. Backend extracts key classroom terms and events.
7. LSQ library displays matching validated LSQ videos/cards.
8. Transcript and summary are created under defined privacy rules.
9. Teacher reviews summary after class.

## Preferred deployment model

Start with a server web app using the GB10 for inference.

Reasons:

- simple classroom setup
- centralized updates
- lower recurring cloud cost
- better privacy than public cloud APIs
- no heavy AI install on each classroom computer
- easier pilot expansion

Add a Windows helper app later only if needed for:

- better microphone control
- offline fallback
- automatic launch
- school IT deployment

## AI components

Initial:

- French ASR: faster-whisper, whisper.cpp, NVIDIA Riva, or NeMo benchmarked on GB10
- Local LLM: French-capable model for transcript cleanup, key term extraction, homework/deadline detection, and summaries
- Embeddings/search: multilingual semantic matching to LSQ vocabulary metadata

Later:

- LSQ gloss generation
- pose generation
- avatar rendering
- pre-rendered lesson signing

## LSQ content strategy

Use open-source and partner resources for scaffolding and validation, but do not assume public videos are legally trainable.

Priority LSQ resources/contacts:

- UQAM LSQ research group
- RESO / DICO LSQ
- Lexique LSQ
- Mon dictionnaire LSQ-français
- CDRIN LSQ API project
- CIUSSS LSQ video resources
- OPHQ / Télé-Québec En classe LSQ resources
- LSQ interpreters/native signers for validation

Priority technical open-source resources:

- sign-language-processing/spoken-to-signed-translation
- sign-language-processing pose tools
- sign.mt
- aws-samples/genai-asl-avatar-generator
- ZhengdiYu/SignAvatars
- carolNeves/HamNoSys2SiGML
- Signothèque
- Sign-Kit avatar toolkit

## Legal and privacy constraints

Before using any LSQ videos or dictionaries for training/product content, confirm:

- copyright holder
- license
- permission for internal research
- permission for product use
- permission for AI training/fine-tuning
- permission for classroom deployment
- attribution requirements
- data retention restrictions

Classroom data policy should define:

- whether raw audio is stored
- whether transcripts are stored
- retention period
- who can access transcripts/summaries
- student/parent consent requirements
- school-board privacy requirements

Default recommendation:

- do not store raw audio unless explicitly needed and approved
- store transcript/summary only when required
- allow deletion/export
- encrypt in transit and at rest

## First technical milestone

Bench Prototype 0:

- browser captures teacher microphone
- streams audio to GB10 server
- server transcribes French live
- captions appear in browser/smartboard display
- transcript is saved
- summary is generated after session

No LSQ yet. First make the pipe reliable.

## Second technical milestone

Vocabulary Support Prototype:

- add subject vocabulary list
- detect key terms in live transcript
- display LSQ media card/video for matched terms
- allow teacher/admin to review terms
- store metadata: term, subject, grade, source, license, validator, status

## Open questions

1. Exact Dell GB10 hardware/OS/runtime details?
2. Number of simultaneous classrooms expected in pilot?
3. First subject and grade level?
4. School-board privacy/data requirements?
5. Who can authorize contact with LSQ content owners?
6. Is there already a school IT environment or domain policy to respect?
7. Can we get sample classroom audio for ASR benchmarking?
8. Should the student view be on shared smartboard/TV, a separate student device, or both?

## Immediate next steps

1. Confirm first pilot scope: subject, grade, number of classrooms.
2. Benchmark French ASR on the GB10.
3. Inspect selected open-source repos and licenses.
4. Prepare contact emails for LSQ resource owners.
5. Create MVP specification and implementation plan.
