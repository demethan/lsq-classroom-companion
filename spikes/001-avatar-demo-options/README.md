# 001: Avatar Demo Options

## Question

Can we build a stakeholder demo where text input produces visible signing-like output or a credible placeholder signing panel?

## Scope

This spike is not an LSQ translator. It tests demo mechanics:

- text input;
- text-to-signing pipeline feasibility;
- browser display;
- clear warnings that output is not validated LSQ.

## Verdict

Validated for stakeholder-safe demo mechanics.

The local `sign-language-processing/spoken-to-signed-translation` stack can generate pose output from text using its included fingerspelling lexicon. The generated output can be rendered to GIF and displayed in a static browser demo.

This does **not** validate LSQ translation quality. It proves only that the interface and text-to-pose/display mechanics are feasible.

## Files

- `demo.html` — static browser demo with text input, vocabulary detection, warning labels, generated sample GIF, and placeholder avatar panel.
- `output_hello.pose` — generated pose output for `HELLO`.
- `output_hello.gif` — rendered GIF for browser display.
- `output_abc.pose` / `output_abc.gif` — earlier pipeline test output.

## GitHub Pages

This spike is published as a static GitHub Pages site from `.github/workflows/pages.yml`.

Public URL:

```text
https://demethan.github.io/lsq-classroom-companion/
```

The workflow copies `demo.html` to `index.html` and publishes the browser assets needed by the page.

## Pipeline notes

Environment:

```bash
cd spikes/001-avatar-demo-options
. .venv/bin/activate
```

The included lexicon path can be discovered with:

```bash
python - <<'PY'
import pathlib, spoken_to_signed
print(pathlib.Path(spoken_to_signed.__file__).parent / 'assets/fingerspelling_lexicon')
PY
```

Example generation command:

```bash
LEX=$(python - <<'PY'
import pathlib, spoken_to_signed
print(pathlib.Path(spoken_to_signed.__file__).parent / 'assets/fingerspelling_lexicon')
PY
)
text_to_gloss_to_pose --text "HELLO" --glosser simple --spoken-language en --signed-language ase --lexicon "$LEX" --pose output_hello.pose
```

Render pose to GIF:

```bash
python - <<'PY'
from pose_format.pose import Pose
from pose_format.pose_visualizer import PoseVisualizer
with open('output_hello.pose', 'rb') as f:
    pose = Pose.read(f.read())
v = PoseVisualizer(pose)
v.save_gif('output_hello.gif', v.draw())
PY
```

## Verification

Observed outputs:

- `output_abc.pose`: 80 frames, 25 fps, 512x512
- `output_hello.pose`: 131 frames, 25 fps, 512x512
- `output_hello.gif`: generated and browser-displayable

Serve locally:

```bash
python -m http.server 8765
```

Open:

```text
http://127.0.0.1:8765/demo.html
```

## Recommendation

Use this as Demo 0 / Demo 1 material only:

- Safe stakeholder interface demo.
- Engineering proof that a text-to-pose-to-browser-display path can run locally.
- Not an LSQ translation demo.

For real LSQ classroom support, replace the generated/fingerspelling sample with licensed or commissioned LSQ vocabulary clips/cards validated by LSQ experts.
