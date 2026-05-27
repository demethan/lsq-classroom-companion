# Classroom Data Policy Draft

## Purpose

This draft defines initial privacy principles for LSQ Classroom Companion pilots.

It must be reviewed by school administration, privacy officers, and legal counsel before deployment.

## Data minimization

The system should collect only what is needed to support accessibility in the classroom.

Default:

- process teacher audio live
- do not retain raw audio
- retain transcript only when required for lesson review/support
- allow deletion according to school policy

## Data types

Potentially processed:

- teacher voice
- incidental student voices
- live transcript
- lesson summary
- vocabulary terms
- classroom metadata
- user/session logs

Potentially sensitive:

- student names
- disability/accommodation context
- classroom participation
- educational performance indicators
- personal comments captured in transcript

## Default retention proposal

- Raw audio: not stored
- Temporary audio chunks: deleted immediately after transcription
- Transcript: retained only for approved period
- Summary: retained only if teacher approves/saves
- Logs: no transcript text in routine technical logs

## Access model

Suggested roles:

- Teacher: access own class sessions and summaries
- Student/parent: access approved lesson supports, if authorized
- School admin: limited operational access
- Content admin: LSQ media library management, not classroom transcript access unless needed
- System admin: infrastructure access with audit controls

## Consent topics

Before pilot:

- teacher consent for microphone use
- parent/student consent if required
- classroom notice for incidental capture
- data retention explanation
- deletion/export process
- clear statement that the tool assists access and is not a certified interpreter replacement

## Security controls

- HTTPS/TLS only
- authenticated users
- role-based access control
- encryption at rest
- audit log for transcript access
- secure deletion process
- no third-party cloud AI processing unless explicitly approved

## Open questions

1. Are transcripts considered educational records under applicable school-board policy?
2. Can incidental student voices be captured?
3. Is parental consent required for all students in the classroom or only the Deaf student?
4. Must all processing remain in Canada?
5. What retention period is acceptable?
6. Who owns generated summaries?
7. Can summaries be shared with parents/students?
