# Avatar Signing Demo Plan

## Purpose

Create a stakeholder demo where a user enters text and sees an avatar sign something on screen.

This is a demonstration of the technical direction, not proof of LSQ translation quality. The demo must be labelled carefully.

## Demo framing

Safe wording:

> This demo shows the kind of interface and avatar pipeline we want: text in, sign-support animation out. The first version may use a non-LSQ sample pipeline or finger-spelling/known signs. It does not claim validated LSQ translation until LSQ content is permissioned and reviewed by LSQ experts.

Unsafe wording:

> This translates French classroom speech into LSQ.

Do not say that yet. A pretty avatar signing nonsense is still nonsense, merely better dressed.

## What the demo should show

Minimum demo:

1. Text input box.
2. Submit button.
3. Processing step: text -> gloss/sign lookup/intermediate representation.
4. Avatar/media panel showing signing output.
5. Caption/transcript panel showing the input text and detected vocabulary.
6. Clear badge: `Prototype demo — not validated LSQ` unless the content is validated.

Preferred stakeholder script:

1. Type a short classroom phrase or term.
2. Show that the system identifies key vocabulary.
3. Show that it can map known vocabulary to sign media/avatar motion.
4. Explain that validated LSQ resources are the missing partnership piece.

## Candidate technical paths

### Path A: Open-source spoken-to-signed pipeline demo

Candidate:

- `sign-language-processing/spoken-to-signed-translation`
- License: MIT
- Pipeline: text -> gloss -> pose -> video
- Existing demos: Swiss German Sign Language, Swiss French Sign Language, Swiss Italian Sign Language
- Reuse value: strongest engineering architecture match

Pros:

- Modern architecture matching the long-term system.
- Produces a pose/video pipeline, not just static images.
- MIT licensed.
- Good for showing the technical path from text to signing-like motion.

Cons:

- Not LSQ.
- Existing lexicons are not classroom LSQ.
- Needs adaptation for French/LSQ vocabulary and validated content.

Best use:

- Technical feasibility demo: “this is the class of pipeline we can adapt.”

### Path B: JASigning / SiGML WebGL avatar demo

Candidates:

- JASigning / CWA Signing Avatars
- Old GitHub projects using SiGML, including YouTube-caption-to-sign demos

Pros:

- Browser-friendly avatar concept.
- Text/sign lookup can drive avatar animation if SiGML signs exist.
- Useful visual demo for stakeholders.

Cons:

- Many example repos are old, unlicensed, or student projects.
- Often word-by-word or finger-spelling, not true sign-language translation.
- SiGML/HamNoSys content must exist for the target signs.
- Licensing/redistribution of avatar assets must be checked.

Best use:

- Fast visual proof-of-concept if the avatar libraries still run locally.

### Path C: Media-card demo with approved or placeholder videos

Candidate:

- Web app maps recognized terms to video clips or placeholder animations.

Pros:

- Closest to responsible MVP.
- Does not pretend to generate grammar.
- Works immediately once a few validated signs are permissioned or custom-recorded.
- Strong for CCJL/stakeholder discussion.

Cons:

- Less flashy than full avatar generation.
- Requires approved media for a true LSQ demo.

Best use:

- First classroom MVP and first stakeholder-safe demo.

### Path D: Custom placeholder avatar/finger-spelling demo

Candidate:

- Simple 3D or 2D avatar that finger-spells or plays canned motions for a few demo terms.

Pros:

- Fully controllable.
- Avoids third-party LSQ content rights.
- Can demonstrate UI and orchestration while waiting for LSQ permission.

Cons:

- Not real LSQ vocabulary unless validated.
- Must be labelled as placeholder.

Best use:

- Early demo before CCJL/content partnership is approved.

## Recommended demo sequence

### Demo 0: Stakeholder-safe mock demo

Build a browser page with:

- text input;
- detected vocabulary list;
- placeholder LSQ support panel;
- a mock avatar/video panel;
- warning badge: `Prototype only — LSQ content not validated`.

This can be ready quickly and is safe to show without rights risk.

### Demo 1: Engineering pipeline spike

Use `sign-language-processing/spoken-to-signed-translation` to generate a signing-like video/pose output for one of its supported demo languages.

Goal:

- prove that text-to-gloss-to-pose-to-video can run locally;
- document install/runtime friction;
- capture screenshots/video for internal explanation.

Acceptance criteria:

- command-line text input produces a pose or rendered video;
- output can be displayed in a simple web page;
- limitations are documented.

### Demo 2: LSQ vocabulary-card demo

Once permission or custom pilot content exists:

- define 30-100 classroom terms;
- map terms to validated LSQ media;
- enter French classroom text;
- show matching terms and play validated sign clips/cards.

This is the first demo that can honestly be called an LSQ classroom-support demo.

### Demo 3: Avatar/pose LSQ research demo

Only after LSQ representation and validation are solved:

- map LSQ vocabulary/gloss/intermediate representation to pose/avatar motion;
- validate with LSQ experts;
- avoid public claims until accuracy is reviewed.

## First spike proposal

Create `spikes/001-avatar-demo-options/` to test two things:

1. Can the MIT spoken-to-signed pipeline run locally and produce a visual output?
2. Can a small browser page accept text and show either a generated video or placeholder signing panel?

Verdict target:

- `VALIDATED` if text input can produce/display signing-like output locally.
- `PARTIAL` if pipeline runs but output is not browser-ready or requires too much dependency work.
- `INVALIDATED` if current tooling is too brittle for demo use.

## Stakeholder caveat

For stakeholder meetings, the demo must separate:

- interface capability;
- text/caption processing capability;
- sign-display capability;
- validated LSQ correctness.

The first three can be demonstrated early. The fourth requires LSQ partners.
