# Initial Architecture

## Overview

LSQ Classroom Companion should begin as a browser-based classroom application with centralized AI processing on a datacenter Dell GB10 server.

The architecture is intentionally conservative: live captions and validated LSQ vocabulary support first; generative LSQ/avatar interpretation later.

## Components

### Classroom browser app

Responsibilities:

- teacher/session login or selection
- microphone selection
- audio capture
- stream audio to backend
- display live captions
- display LSQ vocabulary/sign cards
- show lesson status
- provide smartboard/student display mode

### Backend API

Responsibilities:

- session management
- authentication/authorization
- classroom configuration
- audio stream ingestion
- transcript storage
- LSQ media lookup
- teacher review endpoints
- admin/content endpoints

### ASR service

Responsibilities:

- receive audio chunks/stream
- run French speech-to-text
- return partial and final transcript segments
- preserve timestamps

### Lesson processing service

Responsibilities:

- clean transcript segments
- detect key terms
- detect questions/homework/deadlines
- segment lesson topics
- generate summaries

### LSQ media library

Responsibilities:

- store approved LSQ videos/cards/metadata
- enforce license/status flags
- match French terms to LSQ items
- provide display-safe media URLs

### Admin/content dashboard

Responsibilities:

- manage vocabulary
- upload/approve LSQ media
- track source/license/permission status
- record validator and validation date
- deprecate incorrect/restricted content

## Data model sketch

### Session

- id
- classroom_id
- teacher_id
- subject
- grade_level
- started_at
- ended_at
- privacy_mode
- raw_audio_retained: boolean

### TranscriptSegment

- id
- session_id
- start_time
- end_time
- raw_text
- cleaned_text
- confidence

### VocabularyTerm

- id
- canonical_french
- aliases
- subject
- grade_level
- description

### LSQMediaItem

- id
- vocabulary_term_id
- media_type
- storage_path
- source
- license_status
- permission_status
- validator
- validation_date
- status

### LessonSummary

- id
- session_id
- generated_text
- teacher_review_status
- reviewed_text
- created_at
- updated_at

## Security principles

- TLS for all classroom-to-server communication
- no raw audio retention by default
- role-based access control
- separate teacher/admin/student views
- audit access to transcripts and summaries
- encryption at rest for sensitive data
- deletion/export capability

## MVP sequence

### Milestone 0: Bench Prototype

- browser microphone capture
- server audio ingestion
- French ASR
- live captions
- transcript
- end-of-session summary

### Milestone 1: Vocabulary Prototype

- predefined science/math vocabulary list
- key-term detection
- LSQ media metadata model
- display LSQ sign cards/videos

### Milestone 2: Teacher Review

- transcript review
- summary review
- correction workflow
- export/share lesson notes

### Milestone 3: Pilot Hardening

- authentication
- privacy controls
- logging/audit
- classroom setup checks
- deployment scripts

## Deferred

- full continuous LSQ translation
- real-time generated avatar
- LSQ gloss generation
- offline Windows app
- multi-school scaling
