---
name: jerry-visual
description: "Create a consistent Jerry visual system in two modes: finished explanatory images with short accurate labels generated directly inside the scene, and transparent reusable character illustrations. Preserve the original minimal manga-ink language: a round-headed glasses stick figure and a compact cat companion rendered with confident black lines, circular halftone, warm off-white paper, and restrained accent colors."
---

# Jerry Visual

Create raster visuals in one shared manga-ink language. This Skill is an adaptation of the original character system, not a new portrait style.

Keep the original visual grammar stable. The intended change is narrow:

- preserve the minimal round-headed stick-figure protagonist;
- slightly adjust the glasses to resemble Jerry's softly rectangular dark frames;
- replace the warm-yellow Border Collie with Jerry's Bengal-cat × Chinese Li Hua cat mix;
- keep the same confident line work, circular halftone, restrained colors, composition rhythm, and cute editorial proportions.

Do not turn Jerry into a semi-realistic human portrait. Do not turn the cat into a photorealistic pet portrait.

Choose one output mode before generating; do not mix the two production paths.

## Canonical character system

### Jerry — minimal line character

Jerry remains the original simplified protagonist:

- round head;
- dot eyes;
- simple small smile;
- thin line-drawn body and limbs;
- minimal black hair cue when useful, using only a few controlled strokes;
- softly rectangular or rounded-square dark glasses, slightly wider than the former circular glasses;
- no realistic facial anatomy, skin rendering, nose modeling, detailed hair mass, or portrait shading;
- no hat unless explicitly requested.

The glasses are the main personal adjustment. They should read as a subtle evolution of the original round glasses, not a redesign of the character.

When reference photos are supplied, use them only to guide stable details such as glasses shape, hair direction, and explicit exclusions. Do not copy photographic perspective, lighting, temporary accessories, or facial detail. The hat in the supplied photo is non-canonical and must be ignored.

### Cat — line-art companion

The companion is Jerry's **Bengal-cat × Chinese Li Hua cat mix**, simplified into the same compact mascot language as the former dog.

Stable traits:

- compact, slightly sturdy cat silhouette;
- upright triangular ears;
- yellow or amber eyes;
- pale muzzle and chin;
- long whisker cues drawn with a few clean thin lines;
- gray-silver body represented mainly through halftone;
- dark forehead, cheek, leg, body, and ringed-tail markings represented through sparse controlled black stripes and irregular patches;
- small collar and gold tag when visible;
- calm, intelligent, slightly serious expression.

The cat must remain simple enough to sit naturally beside the stick figure. Do not render individual hairs, realistic fur volume, photographic anatomy, or dense breed-specific pattern detail.

Avoid these incorrect outcomes:

- generic gray tabby with no distinctive markings;
- blue British Shorthair proportions;
- orange cat;
- purebred Bengal covered in exaggerated rosettes;
- kitten-like oversized head;
- realistic cat pasted beside a minimal stick figure;
- any dog.

Reference photos take priority over breed stereotypes, but every feature must be translated into the established line-and-halftone system.

### Pair relationship

- Jerry and the cat are recurring collaborators.
- Keep their scale and simplification level consistent.
- Use natural actions: inspecting a diagram, sitting beside a laptop, following a workflow, checking a result, or reacting to the same object.
- Keep characters secondary when the image's main purpose is explanation.

## Choose the output mode

### Mode A — explanatory image

Use when the image must explain a concept, mechanism, workflow, comparison, or tradeoff by itself.

- Deliver a complete PNG or WebP with a finished off-white scene.
- Generate every essential title and label directly inside the bitmap.
- Make the relation visible through objects, paths, states, or repeated materials; labels identify the evidence but do not replace it.
- Do not generate an unlabeled base and add essential words in a separate rendering step.

### Mode B — transparent illustration

Use when the character scene will be composed into a hero, document, card, slide, or other layout.

- Generate the subject on a perfectly uniform chroma-key background that does not occur in the artwork. Default to `#00FF00`; use `#FF00FF` when the subject contains green.
- Do not include explanatory labels unless explicitly requested.
- Remove the background with `scripts/cutout.py` and deliver a transparent PNG.
- Keep the transparent artwork reusable; the surrounding layout supplies titles and explanatory copy.

If the destination is unclear, choose Mode A when the image itself must communicate the idea and Mode B when another layout will carry the explanation.

## Shared visual language

- Draw confident black manga/comic ink outlines with varied line weight.
- Use restrained circular halftone screentone for all gray surfaces and shadows.
- Keep the protagonist minimal: round head, dot eyes, simple smile, thin limbs, and softly rectangular dark glasses.
- Keep the cat compact and line-based, with gray halftone, sparse dark markings, yellow eyes, and a small gold tag.
- Keep characters secondary to the subject's evidence or action.
- Use black, white, and halftone gray as the base.
- Use warm yellow or muted gold for the cat's eyes, tag, small light patches, and sparse star accents.
- Add at most two muted semantic colors. Common mapping: blue = input/content, orange = action/warning/cost, purple = process, green = successful result.
- Use a lightly textured warm off-white paper environment for finished scenes.
- Avoid 3D, glossy gradients, photorealism, smooth airbrushing, detailed portrait anatomy, realistic fur, wobbly sketch lines, generic card grids, dashboards, decorative clutter, and watermarks.

## Mode A workflow — explanatory image

### 1. Write the visual brief

```text
viewer_question: what should be understood in 10 seconds?
concrete_claim: one-sentence conclusion
real_objects: visible objects, interfaces, documents, tools, or states
relation: comparison, transformation, causality, sequence, hierarchy, feedback, tradeoff, or pipeline
visual_evidence: what must remain understandable when labels are ignored?
character_action: what the stick figure and cat are doing, if present
scene: believable setting and 2–4 useful environmental cues
semantic_colors: what each accent color means
labels: exact short strings plus the evidence surface for each label
```

Show the input, action or relation, and result. Keep one dominant focal action and no more than three major visual regions. For multiple steps, use a simple left-to-right or top-to-bottom sequence.

### 2. Design the labels

- Prefer 2–6 labels.
- Keep each label short and concrete: role, action, state, or outcome.
- Place every label on or immediately beside its evidence surface.
- Use modern Chinese sans-serif typography, medium or bold, large enough to read.
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
4. Assign semantic colors.
5. Quote the exact labels and specify each placement.
6. Add the Mode A style anchor.
7. End with exclusions.

Mode A style anchor:

```text
Professional editorial manga/comic ink illustration in the established Jerry Visual style. Clean confident black ink outlines with varied line weights and controlled circular halftone screentone. The recurring protagonist is a cute minimal stick figure with a round head, dot eyes, a simple smile, thin line-drawn limbs, a few restrained black hair strokes when useful, and softly rectangular dark glasses that remain close to the original round-glasses design. No hat. Beside him is a compact Bengal-cat × Chinese Li Hua cat mix simplified into the same mascot language: upright ears, warm yellow eyes, pale muzzle, a few long whisker lines, gray halftone body, sparse dark mixed stripes and irregular markings, ringed tail, and a small gold collar tag. Preserve the original simple character proportions and line-based style. Use an off-white lightly textured real environment. Color is restrained: black, white, halftone gray, warm yellow or muted gold for the cat's eyes and tag, plus at most two muted semantic accent colors. No realistic human portrait, no realistic fur, no exaggerated Bengal rosettes, no generic gray tabby, no dog, no 3D, no glossy gradients, no dashboard clutter, no decorative excess, no tiny text, no long paragraphs, no watermark.
```

### 4. Inspect and retry

1. Confirm the protagonist is still a minimal round-headed line character.
2. Confirm the glasses are only a subtle softly rectangular adjustment.
3. Confirm the cat and protagonist share the same simplification level.
4. Confirm the cat has yellow eyes, pale muzzle, sparse mixed markings, ringed tail, and gold tag where visible.
5. Reject realistic portraits, detailed fur, generic tabbies, exaggerated purebred Bengal spots, dogs, or hats.
6. Compare every label character by character and reject missing, duplicated, invented, or misspelled labels.
7. Regenerate with one targeted correction while repeating all scene and style invariants.

## Mode B workflow — transparent illustration

### 1. Describe one reusable scene

Use one character action and only the objects needed to establish it. Leave generous padding around the subject so the cutout can be composed safely.

### 2. Build the prompt

Describe the subject first, then append this fixed anchor:

```text
Style: professional manga/comic ink illustration in the established Jerry Visual style. Clean confident ink outlines with varying line weights, thick for contours and thin for details, not wobbly or sketchy. Heavy use of classic circular halftone screentone for all gray and shadow areas. The main character is a cute minimal stick figure with a round head, dot eyes, simple smile, thin line-drawn limbs, and softly rectangular dark glasses that remain close to the original round-glasses design. No hat. Include a compact Bengal-cat × Chinese Li Hua cat mix companion simplified into the same mascot language: upright ears, warm yellow eyes, pale muzzle, a few long whisker lines, gray halftone body, sparse dark mixed stripes and irregular markings, ringed tail, and a small gold collar tag. Do not render a realistic person or realistic cat. Color usage is extremely restrained: 90% black, white, and gray halftone; warm yellow or muted gold only on the cat's eyes, tag, small light patches, and sparse star accents. The background must be a perfectly uniform flat <KEY_COLOR> rectangle with zero gradient, texture, noise, speckles, shadows, floor plane, or lighting variation. Do not let halftone, ink, props, or the subject touch the image border. Keep generous padding. No dog, no hat, no text, no watermark. PNG format.
```

### 3. Validate the source

- Inspect the image before removal.
- Confirm the protagonist remains minimal rather than portrait-like.
- Confirm the cat uses the same line-and-halftone abstraction.
- Confirm all four corners are uniform and visually match the chosen key color.
- Reject backgrounds with gradients, texture, shadows, speckles, or artwork touching the border.
- Preserve the source image alongside the transparent result until approval.

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

### 5. Validate the transparent result

- Confirm the output is RGBA and all four corners have alpha `0`.
- Confirm glasses, thin limbs, cat ears, whiskers, tail, tag, and small props remain complete.
- Check for a gray fringe at 100% zoom.
- Confirm internal white and halftone areas were not erased.
- Regenerate the source instead of forcing the algorithm when the background is visibly uneven.

## README asset workflow

For repository-homepage work, follow this order:

1. Inspect the real repository and existing README.
2. Define the content hierarchy and asset inventory.
3. Confirm this narrow identity adaptation: same original style, adjusted glasses, dog replaced by cat.
4. Decide whether each asset is Mode A or Mode B.
5. Generate one small identity test showing only the stick figure and cat.
6. Obtain user approval before generating the full hero or supporting asset set.
7. Save approved assets under `assets/readme/`.
8. Update README references only after asset approval.
9. Preview desktop and narrow-width rendering.
10. Commit on a branch and use a draft PR unless explicitly instructed otherwise.

## Output handling

- Save approved project assets inside the current project or output directory.
- Do not leave referenced images only in the generator's default storage.
- Use versioned filenames instead of overwriting approved assets unless replacement is explicitly requested.
- Do not store raw personal photos in the repository by default.
- Report the final prompt, output mode, source path when Mode B is used, final path, and non-default cutout options.

## Quality gate

For every output:

- The image is visibly part of the same family as the original visual system.
- The protagonist remains a minimal line character, not a portrait.
- The glasses adjustment is subtle.
- The dog has been replaced by a compact line-art cat without changing the overall visual grammar.
- The cat reflects the supplied Bengal/Li Hua mix through a few controlled traits rather than realism.
- Line work, halftone, warm yellow, and semantic accents remain consistent.
- Characters support the subject instead of becoming generic decoration.

For Mode A:

- One claim, one focal action, and no more than three major visual regions.
- The visual evidence still shows the relation when labels are ignored.
- Every required label is exact, appears once, and remains readable.

For Mode B:

- Background removal is clean and the output has real transparency.
- Thin details and internal halftone regions remain intact.
- No source background, fringe, shadow, or border artifact remains.
