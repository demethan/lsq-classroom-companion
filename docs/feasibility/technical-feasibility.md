# Technical Feasibility

## Purpose

Determine whether LSQ Classroom Companion can run reliably using classroom Windows computers for capture/display and a Dell GB10 AI computer in the datacenter for inference.

## Feasibility conclusion

A useful MVP is technically feasible.

The feasible MVP is not “automatic perfect LSQ interpretation.” That would be unsafe to promise. The feasible MVP is:

1. capture the teacher's microphone audio in a browser;
2. stream audio securely to a backend server;
3. generate live French captions with local ASR;
4. assemble a transcript;
5. extract key classroom terms from the transcript;
6. match terms to a validated LSQ media/vocabulary library;
7. display LSQ support cards/videos for approved terms;
8. generate a teacher-reviewable summary after class.

This can be built with current web/audio/AI tooling. The hard parts are not basic software feasibility; the hard parts are classroom audio quality, latency tuning, LSQ content rights, and LSQ validation.

## What can be promised now

### Technically realistic

- Browser-based classroom app on Windows classroom computers.
- Teacher microphone capture using Web Audio API or WebRTC.
- Backend audio ingestion over WebSocket or WebRTC.
- Local or datacenter French ASR using faster-whisper, whisper.cpp, NVIDIA Riva, or similar.
- Live captions with an initial target latency of 2-5 seconds.
- Transcript assembly and teacher review.
- Keyword/term extraction using deterministic vocabulary matching plus an LLM-assisted layer.
- LSQ vocabulary/media lookup from an approved internal library.
- Lesson summary generation.
- Privacy-first mode with no raw-audio retention by default.

### Not safe to promise yet

- Fully automatic LSQ translation of arbitrary teacher speech.
- Grammatically correct generated LSQ from unrestricted French.
- Validated avatar signing for all classroom content.
- High accuracy with laptop microphones in noisy rooms.
- Reuse or AI training on third-party LSQ videos without written permission.

## Confidence by feature

| Feature | Confidence | Notes |
|---|---:|---|
| Browser microphone capture | High | Standard browser capability, subject to device permission and school browser policy. |
| Audio streaming to backend | High | WebSocket/WebRTC are mature. Firewall/proxy testing still required. |
| Live French captions | High | Modern Whisper-family systems can transcribe French locally; quality depends on microphone and noise. |
| 2-5 second caption latency | Medium/High | Achievable with chunking and model tuning; must benchmark on GB10. |
| Transcript assembly | High | Straightforward once ASR works. |
| Key-term extraction | High | Start with approved vocabulary matching; LLM can assist but should not be sole authority. |
| LSQ media lookup/display | High | Easy if validated/permissioned media exists. |
| Summary generation | High | Technically straightforward; teacher review should be included. |
| Validated LSQ correctness | Medium | Depends on CCJL/UQAM/LSQ experts and approved content. |
| Automatic generated LSQ/avatar | Low/Research | Do not make this the MVP. |
| Multi-classroom concurrency | Medium | Depends on GB10 benchmarks and model sizes. |

## Feasibility questions

1. Can classroom microphone audio be captured reliably in a browser?
2. Can the audio be streamed to the datacenter with acceptable latency?
3. Can the GB10 run French ASR fast enough for live captions?
4. Can local LLM processing summarize and extract key terms quickly enough?
5. Can key educational terms be matched to an LSQ media library in real time?
6. Can the system run for a full class period without instability?
7. Can multiple classrooms run concurrently?
8. Can privacy/security requirements be satisfied?

## Candidate architecture

Classroom browser:

- microphone selection
- audio capture using Web Audio API or WebRTC
- secure WebSocket/WebRTC streaming
- live caption display
- LSQ media panel
- session controls

Datacenter services:

- API gateway
- audio ingestion service
- ASR service
- transcript/session service
- key-term extraction service
- LSQ media lookup service
- summary service
- admin/content service

Storage:

- PostgreSQL for metadata, sessions, transcripts, vocabulary
- object storage or filesystem for approved LSQ media
- Redis for live session state/queues if needed

## GB10 benchmark plan

### Hardware/software inventory

Collect:

- exact Dell model
- CPU/GPU details
- RAM/unified memory
- OS and kernel
- NVIDIA driver
- CUDA version
- container runtime
- Docker availability
- Python version
- PyTorch CUDA support
- available disk
- network bandwidth to classrooms

Known public GB10-class claims indicate the Dell Pro Max with GB10 / NVIDIA Grace Blackwell class machines are intended for local AI inference, with 128GB unified memory and strong FP4 inference capability. That is more than enough to justify a prototype benchmark. Exact performance must still be measured because ASR support, drivers, ARM64 compatibility, and model runtimes matter.

### ASR candidates

Benchmark:

- faster-whisper / CTranslate2
- whisper.cpp
- NVIDIA Riva, if supported
- NVIDIA NeMo ASR, if practical

Metrics:

- word error rate on French classroom audio
- latency per audio chunk
- real-time factor
- GPU memory usage
- CPU usage
- stability over 60 minutes
- simultaneous stream capacity

### LLM candidates

Use local French-capable models for:

- transcript cleanup
- topic segmentation
- key-term extraction
- homework/deadline detection
- post-class summary

Potential runtimes:

- vLLM
- Ollama for prototype simplicity
- llama.cpp
- TensorRT-LLM later if performance requires

Metrics:

- tokens/second
- latency for incremental summaries
- summary quality in French
- ability to extract educational terms
- memory usage
- concurrent session capacity

## First benchmark prototype

Bench Prototype 0:

1. Browser captures microphone audio.
2. Browser streams audio to backend.
3. Backend writes temporary audio chunks.
4. ASR transcribes French in near real time.
5. Captions return to browser.
6. Transcript is assembled.
7. Summary is generated at end.

Acceptance criteria:

- runs for 20 minutes without crash
- captions appear within target latency
- transcript is usable enough for teacher review
- no raw audio stored after session unless explicitly enabled
- logs do not contain sensitive transcript text unless configured

## MVP build path

### Phase 0: proof spike

- Use browser microphone capture.
- Stream audio chunks to a local FastAPI/WebSocket backend.
- Run faster-whisper or whisper.cpp on French audio.
- Return captions to browser.
- Save transcript text only.

Success: live French captions appear consistently for a 10-20 minute test.

### Phase 1: classroom support MVP

- Add teacher session start/stop controls.
- Add vocabulary list for science/math terms.
- Detect terms in transcript.
- Display LSQ placeholder cards or approved CCJL/pilot content.
- Generate lesson summary.

Success: teacher can run one class session and review transcript/summary afterward.

### Phase 2: LSQ validated pilot

- Add licensed/permissioned LSQ media for a small term set.
- Add attribution and content source metadata.
- Add validation status controls.
- Run controlled classroom pilot.

Success: Deaf student and educators find the tool useful for vocabulary and review, without pretending it is full interpretation.

## Latency targets

Initial target:

- captions visible within 2-5 seconds
- key term cards visible within 3-10 seconds
- post-class summary generated within 2 minutes

Stretch target:

- captions visible within 1-2 seconds

## Classroom network requirements

Need to measure:

- upload bandwidth from classroom computer
- packet loss
- Wi-Fi vs wired stability
- firewall/proxy constraints
- WebSocket/WebRTC availability
- TLS certificate requirements

## Microphone requirements

Preferred:

- wireless lavalier or headset microphone
- USB receiver where possible
- stable device name in Windows
- minimal classroom noise pickup

Avoid if possible:

- unreliable Bluetooth microphones
- laptop built-in microphones
- far-field room microphones for first pilot

## LSQ media library technical model

Each LSQ item should include:

- canonical French term
- alternate French terms
- subject
- grade level
- LSQ gloss or description
- media file path
- source
- license status
- permission status
- validator name/organization
- validation date
- status: draft, validated, deprecated, restricted

## Technical risks

| Risk | Impact | Mitigation |
|---|---|---|
| ASR inaccurate in noisy classrooms | High | Use wearable mic, benchmark models, domain vocabulary hints |
| Latency too high | High | tune chunking, use faster model, reduce LLM in live path |
| GB10 runtime compatibility issues | Medium | test faster-whisper, whisper.cpp, Riva/NeMo; keep CPU fallback for spike |
| GB10 cannot handle concurrency | Medium/High | benchmark, queue non-live tasks, scale later |
| Browser microphone issues | Medium | provide setup check, possibly Windows helper later |
| LSQ media rights unavailable | High | use partner-created/validated pilot content |
| Generated LSQ is wrong | High | avoid generative signing in MVP; use validated media |

## Statement for stakeholders

We can technically build a working classroom-support prototype today using established browser audio capture, local speech-to-text, transcript processing, vocabulary matching, and media display.

The responsible MVP is a support tool: captions, key terms, summaries, and validated LSQ vocabulary cards/videos. It should not be represented as a full LSQ interpreter or automatic sign-language translator.

The main feasibility dependency is not whether software can be built. It can. The main dependencies are:

- good teacher microphone input;
- acceptable school network/firewall conditions;
- written permission or custom creation for LSQ media;
- LSQ expert validation;
- classroom privacy approval.

## Next actions

1. Build Bench Prototype 0.
2. Get GB10 hardware/runtime details.
3. Obtain or record representative French classroom audio.
4. Run ASR benchmarks.
5. Define first pilot vocabulary list.
6. Continue CCJL/AQEPA/RESO/UQAM outreach for LSQ content and validation.
