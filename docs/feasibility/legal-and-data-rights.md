# Legal and Data-Rights Feasibility

## Purpose

Determine whether LSQ content, classroom audio, transcripts, and open-source components can be legally used to build and pilot LSQ Classroom Companion.

This is not legal advice. It is a structured diligence checklist so counsel, school administrators, resource owners, and project stakeholders can answer the correct questions early.

## Key legal risk

Publicly accessible LSQ videos or dictionaries are not automatically reusable for:

- product content
- classroom display
- AI training
- fine-tuning
- dataset creation
- redistribution
- commercial deployment

The project must not scrape or train on LSQ materials without clear permission.

## Content categories

### 1. LSQ videos and sign dictionaries

Potential sources:

- Lexique LSQ: https://lexiquelsq.ca/
- Mon dictionnaire LSQ-français: https://lsq-fr.ca/
- DICO LSQ / RESO: https://www.resosurdite.com/dico-lsq---application-mobile.html
- CIUSSS Centre-Sud LSQ videos: https://ciusss-centresudmtl.gouv.qc.ca/langue-des-signes-quebecoise-lsq-videos
- OPHQ LSQ materials
- Télé-Québec En classe LSQ materials
- UQAM LSQ / Marqspat materials
- CDRIN open-source LSQ API project

Questions for each source:

1. Who owns the content?
2. What license applies?
3. Is classroom display allowed?
4. Is copying/downloading allowed?
5. Is redistribution inside our app allowed?
6. Is derivative work allowed?
7. Is AI training or fine-tuning allowed?
8. Is internal research use allowed?
9. Is commercial use allowed?
10. Are there attribution requirements?
11. Are there signer consent limitations?
12. Are there territorial limitations?
13. Are there accessibility/public-sector exceptions?
14. Can permission be granted in writing?

## 2. Classroom audio and transcripts

Data involved:

- teacher voice
- student voices if captured
- classroom discussions
- names and personal information
- educational records
- transcripts
- summaries
- possibly disability-related accommodations

Questions:

1. Does the school board allow classroom audio capture?
2. Is teacher consent required?
3. Is student/parent consent required?
4. Can student voices be incidentally recorded?
5. Can raw audio be stored?
6. Can transcripts be stored?
7. What retention period is allowed?
8. Who may access transcripts and summaries?
9. Are transcripts educational records?
10. Are disability/accommodation details considered sensitive data?
11. Must the system run entirely within Canada or within the school board's infrastructure?
12. What breach notification obligations apply?

Initial recommendation:

- Do not store raw audio by default.
- Process audio in the datacenter when possible.
- Store only reviewed transcripts/summaries if needed.
- Provide deletion/export controls.
- Encrypt in transit and at rest.
- Keep strict access logs.

## 3. Open-source software

Potential repositories:

- sign-language-processing/spoken-to-signed-translation
- sign-language-processing pose tools
- aws-samples/genai-asl-avatar-generator
- ZhengdiYu/SignAvatars
- carolNeves/HamNoSys2SiGML
- Signothèque repositories
- Sign-Kit avatar toolkit

Questions:

1. What license applies?
2. Are there model/data licenses separate from code licenses?
3. Does the license allow commercial use?
4. Does the license require disclosure of source code?
5. Does the license require attribution?
6. Are datasets separately licensed or restricted?
7. Are pretrained model weights included, and under what license?
8. Are there patent or non-commercial clauses?

## 4. AI model licenses

Candidate model categories:

- ASR models: Whisper, faster-whisper, whisper.cpp, NVIDIA Riva, NeMo
- LLMs: Mistral, Llama, Qwen, other French-capable local models
- embedding models
- sign-language pose/avatar models

Questions:

1. Does the model license allow educational use?
2. Does it allow commercial use?
3. Does it allow serving to third parties?
4. Are there use-policy restrictions?
5. Are model outputs owned/restricted?
6. Are there data-processing obligations?

## Permission status tracker

| Resource | Owner | Type | License found? | Training allowed? | Product use allowed? | Contact needed? | Status |
|---|---|---|---:|---:|---:|---:|---|
| Lexique LSQ | TBD | LSQ vocabulary/videos | Unknown | Unknown | Unknown | Yes | To investigate |
| Mon dictionnaire LSQ-français | TBD | LSQ dictionary | Unknown | Unknown | Unknown | Yes | To investigate |
| DICO LSQ / RESO | RESO | App/videos/dictionary | Commercial/unknown | Unknown | Unknown | Yes | To investigate |
| UQAM Marqspat | UQAM | Research/lexicon/corpus | Unknown | Unknown | Unknown | Yes | To investigate |
| CDRIN LSQ API | CDRIN | API/software/research | Unknown | Unknown | Unknown | Yes | To investigate |
| CIUSSS LSQ videos | CIUSSS | Public videos | Unknown | Unknown | Unknown | Yes | To investigate |
| OPHQ/Télé-Québec LSQ | Govt/Télé-Québec | Public education videos | Unknown | Unknown | Unknown | Yes | To investigate |

## Required written permissions

Before using third-party LSQ content in a prototype beyond private evaluation, obtain written answers for:

- permission to store media
- permission to display in classroom pilot
- permission to annotate metadata
- permission to use for model evaluation
- permission or prohibition for AI training
- required attribution
- signer/personality rights
- termination/removal process

## Legal feasibility outcome categories

Each resource should be classified:

- Green: usable with clear license/permission
- Yellow: usable only after written permission or restricted to research
- Red: not usable for product/training
- Reference-only: may be viewed by humans but not copied/trained/deployed

## Next actions

1. Inspect visible licenses/terms for each LSQ resource.
2. Prepare outreach emails in French and English.
3. Ask for written permission language, not informal approval.
4. Identify school-board privacy requirements.
5. Draft a pilot consent/data policy.
