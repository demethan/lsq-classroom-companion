# Technical Feasibility

## Purpose

Determine whether LSQ Classroom Companion can run reliably using classroom Windows computers for capture/display and a Dell GB10 AI computer in the datacenter for inference.

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
| GB10 cannot handle concurrency | Medium/High | benchmark, queue non-live tasks, scale later |
| Browser microphone issues | Medium | provide setup check, possibly Windows helper later |
| LSQ media rights unavailable | High | use partner-created/validated pilot content |
| Generated LSQ is wrong | High | avoid generative signing in MVP; use validated media |

## Next actions

1. Get GB10 hardware/runtime details.
2. Obtain or record representative French classroom audio.
3. Run ASR benchmarks.
4. Build minimal browser-to-server audio streaming spike.
5. Define first pilot vocabulary list.
