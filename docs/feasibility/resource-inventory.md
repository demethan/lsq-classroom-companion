# Resource Inventory

## Purpose

Track candidate software, datasets, dictionaries, videos, research groups, vendors, and contacts relevant to LSQ Classroom Companion.

## Status legend

- Green: likely reusable for code or reference under clear permissive terms.
- Yellow: potentially useful, but permission/license/technical maturity must be verified before product use.
- Red: not suitable for reuse without a new agreement or major change.
- Reference-only: useful to read or evaluate, but do not copy, train on, or redistribute.

## Priority resources

| Name | URL | Type | Language | Reuse potential | Current status | Evidence / notes | Next action |
|---|---|---|---|---|---|---|---|
| sign-language-processing/spoken-to-signed-translation | https://github.com/sign-language-processing/spoken-to-signed-translation | Code/research | de/fr/it to Swiss sign languages | High architecture reuse | Green for code; Yellow for data/models | LICENSE is MIT. Active repo. Text-to-gloss-to-pose-to-video pipeline. Not LSQ. Dataset/model licenses must be checked separately. | Clone and run minimal pipeline; inventory model/data dependencies. |
| sign-language-processing/pose | https://github.com/sign-language-processing/pose | Code/library | Multilingual pose format | High tooling reuse | Green for code | LICENSE.txt is MIT. Active repo. Library for viewing, augmenting, and handling `.pose` files. | Inspect API and determine whether it can store LSQ pose data later. |
| sign-language-processing organization | https://github.com/sign-language-processing | Code ecosystem | Multilingual | High tooling reuse | Yellow/Green by repo | Several useful repos; each repo must be checked individually. | Inspect transcription, signwriting, pose, and translation repos. |
| sign.mt | https://arxiv.org/html/2310.05064v2 | Research/app | Multilingual | High architecture reference | Yellow | Paper/application reference found. Code/license not yet confirmed. | Find repository and implementation terms. |
| AWS GenASL | https://github.com/aws-samples/genai-asl-avatar-generator | Code/reference | ASL | High engineering reference, low LSQ content reuse | Green for code; Reference-only for ASL language content | LICENSE is MIT-0. Engineering architecture is useful. ASL signs/translation are not LSQ. | Inspect architecture and dependencies; do not reuse ASL linguistic output as LSQ. |
| SignAvatars | https://github.com/ZhengdiYu/SignAvatars | Dataset/research | Sign language motion | Motion/avatar research | Yellow | GitHub license not detected by API. README/paper exist. Dataset access and terms unclear. | Inspect paper/data access/license before use. Treat as research-only until clarified. |
| HamNoSys2SiGML | https://github.com/carolNeves/HamNoSys2SiGML | Code | HamNoSys/SiGML notation/avatar | Medium avatar pipeline reuse | Green-ish for code; verify packaging | README contains MIT-like permission notice. GitHub API did not detect SPDX license. | Inspect repo locally; confirm license file and dependencies. |
| Signothèque | https://github.com/signotheque | Code/data concept | LSF/open signs | High licensing model reference | Yellow | Website repo lacks detected license. Project claims open-source sign-language orientation, but actual content/license must be verified. | Inspect repos/data; confirm CC0 or other license before reuse. |
| Sign-Kit ISL Toolkit | https://github.com/spectre900/Sign-Kit-An-Avatar-based-ISL-Toolkit | Code/reference | Indian Sign Language | Medium prototype reference | Yellow | No license detected by GitHub API. Useful as UI/prototype reference only until license is clear. | Inspect code and license; likely not core. |
| Lexique LSQ / CCJL Math | https://ccjl.ca/lexique-lsq-mathematiques/ | LSQ educational lexicon | LSQ/French | Very high classroom vocabulary reference | Yellow / Reference-only until permission | Page states math/science LSQ lexicon is a collaboration between Ontario Ministry of Education and CCJL; signs reflect Franco-Ontarian reality and were validated by CCJL. Footer says 2026 Tous droits réservés. | Contact CCJL. Ask about classroom pilot display, internal indexing, video reuse, and AI training. |
| Lexique LSQ / CCJL Sciences | https://ccjl.ca/lexique-lsq-sciences/ | LSQ educational lexicon | LSQ/French | Very high classroom vocabulary reference | Yellow / Reference-only until permission | Same CCJL educational context as math lexicon. Strong domain fit for first MVP. Rights not open by default. | Contact CCJL. Prioritize science/math pilot vocabulary. |
| Mon dictionnaire LSQ-français | https://lsq-fr.ca/ | LSQ dictionary | LSQ/French | High vocabulary reference | Yellow / Reference-only until permission | Site says it is a free bilingual LSQ-French dictionary developed by AQEPA Provinciale, UQAR, and Multi Groupe Conseil. Mentions légales: all content is property of AQEPA and creators; copyright 2023 Tous droits réservés. | Contact AQEPA. Ask for pilot permission and AI/training restrictions. |
| DICO LSQ / RESO | https://www.resosurdite.com/dico-lsq---application-mobile.html | App/media | LSQ/French | High partnership potential | Yellow / likely restricted | App has 1900+ words, 100+ phrases, 2000+ videos. Terms: application is licensed, not sold; RESO/third parties own all rights; copying, distributing, modifying, adapting, displaying, or using content without express authorization is prohibited. Contact: resosurdite@gmail.com. | Contact RESO; do not scrape or reuse videos without written permission. |
| UQAM LSQ research group | https://lsq.uqam.ca/ | Research/contact | LSQ/French | Very high expertise | Contact priority | Important LSQ grammar/corpus expertise. Rights/access unknown. | Contact for advisory/validation and corpus guidance. |
| Marqspat lexicon | https://lsq.uqam.ca/?q=content/lexique-du-projet-marqspat | Research/lexicon | LSQ/French | High linguistic reference | Yellow | Research lexicon; terms and reuse rights not yet established. | Contact UQAM before copying or using beyond reference. |
| CDRIN LSQ API project | https://www.cdrin.com/jeux-video-inclusifs-api-ouverte/ | Project/contact | LSQ | Potentially very high | Yellow | Article describes an open-source LSQ API for video games; repository not yet found. | Find repo or contact CDRIN/Gaëlle Thibaudat. |
| CIUSSS LSQ videos | https://ciusss-centresudmtl.gouv.qc.ca/langue-des-signes-quebecoise-lsq-videos | Public videos | LSQ/French | Reference/potential content | Yellow / Reference-only | Public video availability does not imply training/product rights. | Inspect terms; contact CIUSSS for permissions. |
| OPHQ LSQ materials | https://www.ophq.gouv.qc.ca/ | Government/public resources | LSQ/French | Reference/potential content | Yellow / Reference-only | Government/public material still needs explicit reuse/training rights. | Identify relevant LSQ pages and licensing. |
| Télé-Québec En classe LSQ | https://enclasse.telequebec.tv/lsq | Education videos | LSQ/French | Strong education relevance | Yellow / Reference-only | Strong fit for classroom content, but rights and availability must be confirmed. | Inspect terms/contact Télé-Québec before use. |
| IRIS / IVèS / Sopra Steria / IBM | https://www.soprasteria.com/newsroom/press-releases/details/ives-sopra-steria-and-ibm-join-forces-to-create-the-worlds-first-conversational-assistant-in-sign-language | Vendor | Includes LSQ claim | Vendor/partnership | Commercial / contact required | Potentially strongest existing LSQ avatar/conversational assistant lead. | Contact for LSQ readiness, API/integration, pricing, privacy. |
| SignAvatar | https://www.signavatar.org/ | Vendor | ASL/multilingual/regional options | Vendor/partnership | Commercial / contact required | Commercial speech/audio-to-sign avatar product; LSQ readiness unconfirmed. | Contact for LSQ support and licensing. |

## Initial conclusions

1. Open-source engineering scaffolding is promising.
   - The sign-language-processing ecosystem and AWS GenASL are useful for architecture and code patterns.
   - They do not solve LSQ linguistic correctness.

2. The most useful LSQ classroom vocabulary sources are not automatically reusable.
   - CCJL math/science lexiques are highly relevant to the classroom MVP.
   - AQEPA/lsq-fr and RESO/DICO LSQ contain valuable LSQ vocabulary/media.
   - Current visible terms point to ownership and restrictions, not open reuse.

3. Do not scrape LSQ videos for training.
   - The project should treat LSQ media as reference-only until written permission is obtained.

4. First MVP content may need custom-created or licensed LSQ clips.
   - If permissions are slow or unavailable, create 30-100 validated pilot terms with LSQ experts instead of relying on third-party video reuse.

## Repository inspection checklist

For each repo, collect:

- license
- last commit date
- language/runtime
- install instructions
- model/data dependencies
- input formats
- output formats
- whether French is supported
- whether LSQ is supported
- whether sign gloss/pose/avatar steps are modular
- maturity: demo, research, production, abandoned
- blockers

## Contact checklist for LSQ content owners

Ask:

- Who owns the content?
- Is classroom pilot display allowed?
- Is copying/storage allowed?
- Is metadata annotation allowed?
- Is AI training allowed?
- Is commercial use allowed?
- Is attribution required?
- Are signer consents compatible with reuse?
- Can they provide validation or advisory support?

## Immediate research tasks

1. Contact CCJL about math/science LSQ lexicon use.
2. Contact AQEPA about Mon dictionnaire LSQ-français.
3. Contact RESO about DICO LSQ permission/licensing.
4. Contact UQAM for LSQ linguistic validation guidance.
5. Find CDRIN LSQ API repository or contact.
6. Clone and inspect green/yellow open-source repos for runnable components.
