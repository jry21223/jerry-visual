---
name: jerry-visual
description: "Create a consistent Jerry visual system in two modes: finished explanatory images with short accurate labels generated directly inside the scene, and transparent reusable character illustrations. Preserve the original minimal manga-ink language: a round-headed glasses character and a compact, slightly plump silver-gray cat companion rendered with confident black lines, circular halftone, warm off-white paper, and restrained semantic colors."
---

# Jerry Visual

Create raster visuals in one shared manga-ink language. This Skill is a narrow adaptation of the original character system, not a new portrait style.

Keep four invariants:

- preserve the minimal round-headed protagonist;
- adjust only the glasses, from circular to softly rectangular dark frames;
- replace the former dog companion with Jerry's cat 花仔;
- preserve the confident line work, circular halftone, restrained palette, composition rhythm, and editorial proportions.

Do not turn Jerry into a semi-realistic portrait. Do not turn 花仔 into a photorealistic pet portrait.

Choose one output mode before generating. Do not mix the two production paths.

## Canonical character system

### Jerry — minimal line character

Keep these traits stable:

- round head;
- dot eyes;
- simple small smile;
- thin line-drawn body and limbs;
- only a few controlled black hair strokes when useful;
- softly rectangular or rounded-square dark glasses, only slightly wider and squarer than the former circular frames;
- no realistic facial anatomy, nose modeling, skin rendering, detailed hair mass, portrait shading, or anime-style facial detail;
- no hat unless explicitly requested.

The glasses are the main personal adjustment. They should read as a subtle evolution of the original character, not a redesign.

Reference photos may guide glasses shape, hair direction, and explicit exclusions. Do not copy photographic perspective, lighting, temporary accessories, blemishes, or facial detail. The hat in the supplied reference photo is non-canonical and must be ignored.

### 花仔 — line-art cat companion

花仔 is a **Bengal-cat × Chinese Li Hua cat mix**, simplified into the same mascot language as Jerry.

Keep these traits stable:

- compact and slightly plump silhouette; never thin, lanky, or kitten-like;
- upright triangular ears;
- warm yellow or amber eyes with dark pupils;
- pale muzzle and chin;
- a few long, clean whisker lines;
- mostly smooth silver-gray body represented through a gray base and restrained circular halftone;
- sparse forehead and cheek lines, light leg bands, subtle irregular body markings, and a clearly ringed tail;
- calm, intelligent, slightly serious expression;
- small collar and warm-gold tag whenever the neck is visible;
- render the tag text `花仔` only when it remains legible; otherwise use a plain gold tag rather than tiny or corrupted text.

The body must remain mostly gray. Do not cover it with dense black tabby stripes or exaggerated Bengal rosettes.

Reject these outcomes:

- generic gray tabby with no distinctive face, tail, or tag;
- blue British Shorthair proportions;
- orange cat;
- purebred Bengal covered in leopard-like rosettes;
- thin or long-legged cat;
- kitten-like oversized head;
- realistic cat pasted beside a minimal line character;
- any dog.

The reference photos take priority over breed stereotypes, but every trait must be translated into the established line-and-halftone abstraction.

### Pair relationship

- Jerry and 花仔 are recurring collaborators.
- Keep their scale and simplification level consistent.
- Use natural interactions: inspecting a diagram, sitting beside a laptop, following a workflow, checking a result, or reacting to the same object.
- Keep them secondary when the image's main purpose is explanation.

## Choose the output mode

### Mode A — explanatory image

Use when the image must explain a concept, mechanism, workflow, comparison, or tradeoff by itself.

- Deliver a complete PNG or WebP with a finished warm off-white scene.
- Generate every essential title and label directly inside the bitmap.
- Make the relation visible through objects, paths, states, or repeated materials; labels identify the evidence but do not replace it.
- Do not generate an unlabeled base and add essential words in a separate rendering step.

### Mode B — transparent illustration

Use when the character scene will be composed into a README Hero, document, card, slide, or another layout.

- Generate the subject on a perfectly uniform chroma-key background that does not occur in the artwork. Default to `#00FF00`; use `#FF00FF` when the subject contains green.
- Do not include explanatory labels unless explicitly requested.
- Remove the background with `scripts/cutout.py` and deliver a transparent PNG.
- Keep the transparent artwork reusable; the surrounding layout supplies titles and explanatory copy.

If the destination is unclear, choose Mode A when the image itself must communicate the idea and Mode B when another layout carries the explanation.

## Shared visual language

- Draw confident black manga/comic ink outlines with varied line weight.
- Use restrained circular halftone screentone for gray surfaces and shadows.
- Keep Jerry minimal: round head, dot eyes, simple smile, thin limbs, few hair strokes, and softly rectangular glasses.
- Keep 花仔 compact and slightly plump, with a mostly silver-gray body, sparse markings, yellow eyes, pale muzzle, ringed tail, and gold tag.
- Keep characters secondary to the subject's evidence or action.
- Use black, white, and halftone gray as the base.
- Use warm yellow or muted gold for 花仔's eyes and tag, small light patches, and sparse star accents.
- Add at most two muted semantic colors. Suggested mapping: blue = input/content, orange = action/warning/cost, purple = process, green = successful result.
- Use a lightly textured warm off-white paper environment for finished scenes.
- Keep props concrete and useful: laptop, monitor, document, blueprint, terminal, flowchart, folder, tool, meter, lane, or result artifact.
- Avoid 3D, glossy gradients, photorealism, airbrushed shading, detailed portrait anatomy, realistic fur, wobbly sketch lines, generic card grids, dashboards, decorative clutter, and watermarks.

## Mode A workflow — explanatory image

### 1. Write the visual brief

```text
viewer_question: what should be understood in 10 seconds?
concrete_claim: one-sentence conclusion
real_objects: visible objects, interfaces, documents, tools, or states
relation: comparison, transformation, causality, sequence, hierarchy, feedback, tradeoff, or pipeline
visual_evidence: what must remain understandable when labels are ignored?
character_action: what Jerry and 花仔 are doing, if present
scene: believable setting and 2–4 useful environmental cues
semantic_colors: what each accent color means
labels: exact short strings plus the evidence surface for each label
```

Show the input, action or relation, and result. Keep one dominant focal action and no more than three major visual regions. For multiple steps, use a simple left-to-right or top-to-bottom sequence.

### 2. Design the labels

- Prefer 2–6 labels.
- Keep each label short and concrete: role, action, state, or outcome.
- Place every label on or immediately beside its evidence surface.
- Use modern Chinese sans-serif typography, medium or bold, large enough to read at the intended display size.
- Do not turn body copy, commands, tables, or long paragraphs into image text.

Add this block to the generation prompt:

```text
Text (verbatim): Render these exact labels as part of the bitmap illustration:
"<label 1>", "<label 2>", "<label 3>".
Use each phrase exactly once. Do not translate, paraphrase, misspell, repeat,
or add any other text. Place each label on its specified evidence surface.
```

### 3. Build the prompt

Use this order:

1. State the concrete claim and shared task.
2. Describe the real setting and character action.
3. Describe the evidence objects and their geometry.
4. Repeat the canonical Jerry and 花仔 traits that are visible in this scene.
5. Assign semantic colors.
6. Quote the exact labels and specify each placement.
7. Add the Mode A style anchor.
8. End with exclusions.

Mode A style anchor:

```text
Professional editorial manga/comic ink illustration in the established Jerry Visual style. Clean confident black ink outlines with varied line weights and controlled circular halftone screentone. Jerry is a cute minimal line character with a round head, dot eyes, a simple smile, thin line-drawn limbs, only a few restrained black hair strokes, and softly rectangular dark glasses that remain close to the original round-glasses design. No hat. Beside him is 花仔, a compact and slightly plump Bengal-cat × Chinese Li Hua cat mix simplified into the same mascot language: mostly silver-gray halftone body, warm yellow eyes, pale muzzle, a few clean whisker lines, sparse forehead and leg stripes, subtle irregular body markings, ringed tail, and a small warm-gold collar tag. The body must remain mostly gray; do not make the cat thin or cover it with dense tabby stripes or Bengal rosettes. Use an off-white lightly textured real environment. Color is restrained: black, white, halftone gray, warm yellow or muted gold, plus at most two muted semantic accent colors. No realistic human portrait, no realistic fur, no dog, no hat, no 3D, no glossy gradients, no dashboard clutter, no decorative excess, no tiny essential text, no long paragraphs, no watermark.
```

### 4. Inspect and retry

1. Confirm Jerry remains a minimal round-headed line character.
2. Confirm the glasses adjustment is subtle.
3. Confirm Jerry and 花仔 share the same simplification level.
4. Confirm 花仔 is slightly plump and mostly silver-gray, with yellow eyes, pale muzzle, restrained markings, ringed tail, and gold tag where visible.
5. Reject thin cats, dense tabby striping, exaggerated rosettes, realistic portraits, detailed fur, dogs, or hats.
6. Compare every required label character by character and reject missing, duplicated, invented, or misspelled labels.
7. Regenerate with one targeted correction while repeating all scene and identity invariants.

## Mode B workflow — transparent illustration

### 1. Describe one reusable scene

Use one character action and only the objects needed to establish it. Leave generous padding around the subject so the cutout can be composed safely.

### 2. Build the prompt

Describe the subject first, repeat the canonical identity constraints, then append:

```text
Style: professional manga/comic ink illustration in the established Jerry Visual style. Clean confident ink outlines with varying line weights, thick for contours and thin for details, not wobbly or sketchy. Use classic circular halftone screentone for gray and shadow areas. Jerry is a cute minimal line character with a round head, dot eyes, simple smile, thin line-drawn limbs, a few black hair strokes, and softly rectangular dark glasses. No hat. Include 花仔 as a compact, slightly plump silver-gray line-art cat with warm yellow eyes, pale muzzle, sparse restrained markings, ringed tail, and a small gold tag. Do not render a realistic person or realistic cat. The background must be a perfectly uniform flat <KEY_COLOR> rectangle with zero gradient, texture, noise, speckles, shadows, floor plane, or lighting variation. Do not let halftone, ink, props, or the subject touch the image border. Keep generous padding. No dog, no text, no watermark. PNG format.
```

### 3. Validate the source

- Confirm Jerry remains minimal rather than portrait-like.
- Confirm 花仔 is slightly plump, mostly gray, and uses the same line-and-halftone abstraction.
- Confirm all four corners are uniform and visually match the selected key color.
- Reject backgrounds with gradients, texture, shadows, speckles, or artwork touching the border.
- Preserve the source image until the transparent result is approved.

### 4. Remove the background

```bash
python3 scripts/cutout.py source.png transparent.png
```

Optional tuning:

```bash
python3 scripts/cutout.py source.png transparent.png \
  --transparent-threshold 12 \
  --opaque-threshold 220
```

The script samples the image border, builds a soft alpha matte from color distance, and removes key-color spill from antialiased edges.

### 5. Validate the transparent result

- Confirm the output is RGBA and all four corners have alpha `0`.
- Confirm glasses, thin limbs, cat ears, whiskers, tail, tag, and small props remain complete.
- Check for a gray or green fringe at 100% zoom.
- Confirm internal white and halftone areas were not erased.
- Regenerate the source instead of forcing the algorithm when the background is visibly uneven.

## README asset workflow

For repository-homepage work:

1. Inspect the real repository and existing README.
2. Define the content hierarchy and asset inventory.
3. Freeze the visual system: same original line language, subtly adjusted glasses, dog replaced by 花仔.
4. Decide whether each asset is Mode A or Mode B.
5. Generate one small identity test.
6. Obtain approval before generating the full Hero or supporting set.
7. Save approved assets under `assets/readme/` and maintainable example sources under `examples/`.
8. Update README references only after asset approval.
9. Preview at desktop and narrow GitHub widths.
10. Commit on a branch and use a draft PR unless explicitly instructed otherwise.

## Output handling

- Save approved project assets inside the project or output directory.
- Do not leave referenced images only in the generator's default storage.
- Use versioned filenames instead of overwriting approved assets unless replacement is explicitly requested.
- Do not store raw personal reference photos in the repository by default.
- Report the final prompt, output mode, source path when Mode B is used, final path, and non-default cutout options.

## Quality gate

For every output:

- The image visibly belongs to the same family as the repository examples.
- Jerry remains a minimal line character, not a portrait.
- The glasses adjustment is subtle.
- 花仔 is compact, slightly plump, mostly silver-gray, and not over-striped.
- Jerry and 花仔 remain at the same abstraction level.
- Line work, circular halftone, warm gold, and semantic accents remain consistent.
- Characters support the content instead of becoming generic decoration.

For Mode A:

- One claim, one focal action, and no more than three major visual regions.
- The relation remains understandable when labels are ignored.
- Every required label is exact, appears once, and remains readable.

For Mode B:

- Background removal is clean and genuinely transparent.
- Thin details and internal halftone regions remain intact.
- No source background, fringe, shadow, or border artifact remains.
