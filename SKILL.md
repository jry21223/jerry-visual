---
name: jerry-visual
description: "Create a consistent Jerry-native visual system for explanatory images, README heroes, editorial scenes, and transparent reusable illustrations. The recurring character pair is Jerry—a young East Asian man with short black hair and round glasses—and his Bengal-cat × Chinese Li Hua cat mix, identified by a silver-gray coat, dark wild-pattern markings, warm yellow eyes, pale muzzle, long white whiskers, and a small gold collar tag."
---

# Jerry Visual

Create raster visuals in one shared editorial manga-ink language. The visual identity belongs to Jerry and his cat. Do not reuse the former stick figure or Border Collie character system.

Choose one output mode before generating. Do not generate finished assets until the mode, destination, visual brief, and identity constraints are established.

## Canonical character system

### Jerry

Keep these traits stable across outputs:

- Young East Asian man.
- Short, naturally textured black hair with a soft fringe.
- Large round or softly rectangular dark-rimmed glasses.
- Calm, thoughtful, friendly expression; avoid exaggerated anime proportions.
- Light-colored T-shirt, sweatshirt, or simple shirt unless the scene requires otherwise.
- Slim, natural build and relaxed posture.
- No hat by default.

When a reference photo contains a temporary accessory that the user explicitly asks to ignore—such as a hat, headpiece, mask, costume item, or background object—exclude it from the canonical design and every generated output.

Do not overfit to camera distortion, unusual lighting, temporary blemishes, or accidental facial expressions. Preserve recognizable structure while simplifying it into the shared illustration language.

### Cat

The cat is a **Bengal-cat × Chinese Li Hua cat mix**, not a generic tabby and not a purebred Bengal.

Keep these traits stable across outputs:

- Silver-gray short coat with a cool gray base.
- Dark charcoal markings combining Li Hua-style facial and leg striping with a more irregular, wild-looking Bengal influence across the body.
- Distinct forehead markings, cheek lines, striped legs, and a ringed tail.
- Warm yellow to amber eyes with dark rims.
- Pale gray-white muzzle, chin, chest, and lower face.
- Long, prominent white whiskers.
- Upright triangular ears with softly warm inner-ear tones.
- Compact, sturdy body; cute but not excessively round or kitten-like.
- Calm, intelligent, slightly serious expression.
- Collar with a small gold tag whenever the neck is visible.

Do not simplify the cat into a generic gray tabby, blue British Shorthair, orange tabby, leopard-spotted Bengal, or cartoon kitten. Preserve the mixed lineage through the combination of striped Li Hua features, subtle wild-pattern irregularity, yellow eyes, and the cat's real facial structure. The reference photos take priority over breed stereotypes.

### Pair relationship

- Jerry and the cat are companions and collaborators, not owner-and-prop decoration.
- Use natural interactions: working beside a laptop, inspecting a diagram, watching a process, sitting together, or reacting to the same result.
- Keep the pair secondary when the image's main purpose is to explain a mechanism.
- For identity-led README heroes or editorial portraits, the pair may be the primary focal subject.

## Reference-image protocol

When the user asks for a personalized image of Jerry or the cat:

1. Confirm that usable reference photos are present in the current conversation.
2. Use multiple views to infer stable identity traits rather than copying one pose.
3. Treat the photos as the primary source of appearance; breed labels are secondary guidance.
4. Respect explicit exclusions such as “ignore the hat.”
5. Establish the visual brief, output mode, destination, composition, and identity constraints before generating.
6. Generate an identity test or character sheet before producing a complete README asset set.
7. Do not commit raw personal reference photos into a public repository unless explicitly requested.
8. Store only approved generated derivatives in the project assets directory.

## Choose the output mode

### Mode A — explanatory image

Use when the image must explain a concept, mechanism, workflow, comparison, or tradeoff by itself.

- Deliver a complete PNG or WebP with a finished off-white scene.
- Generate every essential title and label directly inside the bitmap.
- Make the relation visible through objects, paths, states, or repeated materials; labels identify evidence but do not replace it.
- Do not generate an unlabeled base and add essential words in a separate rendering step.

### Mode B — transparent illustration

Use when the character scene will be composed into a README hero, document, card, slide, or other layout.

- Generate the subject on a perfectly uniform chroma-key background that does not occur in the artwork. Default to `#00FF00`; use `#FF00FF` when the subject contains green.
- Do not include explanatory labels unless explicitly requested.
- Remove the background with `scripts/cutout.py` and deliver a transparent PNG.
- Keep the transparent artwork reusable; the surrounding layout supplies titles and explanatory copy.

If the destination is unclear, choose Mode A when the image itself must communicate the idea and Mode B when another layout will carry the explanation.

## Shared visual language

- Draw confident black manga/comic ink outlines with varied line weight.
- Use restrained circular halftone screentone for gray surfaces and shadows instead of glossy gradients.
- Use black, white, warm off-white, charcoal gray, and muted silver-gray as the base.
- Reserve warm ochre or gold for the cat's eyes, collar tag, small light accents, and sparse star marks.
- Add at most two muted semantic colors: blue for input/content, orange for action/warning/cost, purple for process, and green for successful results.
- Use a lightly textured warm paper background for finished scenes.
- Keep props concrete and useful: laptop, monitor, document, blueprint, terminal, flowchart, folder, tool, or result artifact.
- Avoid 3D, glossy rendering, smooth airbrushed gradients, photorealism, wobbly sketch lines, generic card grids, dashboard clutter, decorative filler, and watermarks.

## Mode A workflow

### 1. Write the visual brief

```text
viewer_question: what should be understood in 10 seconds?
concrete_claim: one-sentence conclusion
real_objects: visible objects, interfaces, documents, tools, or states
relation: comparison, transformation, causality, sequence, hierarchy, feedback, tradeoff, or pipeline
visual_evidence: what remains understandable when labels are ignored?
character_role: what Jerry and the cat are doing, if present
scene: believable setting and 2–4 useful environmental cues
semantic_colors: what each accent color means
labels: exact short strings and the evidence surface for each label
identity_constraints: stable Jerry/cat traits and explicit exclusions
```

Show the input, action or relation, and result. Keep one dominant focal action and no more than three major visual regions.

### 2. Design labels

- Prefer 2–6 short, concrete labels.
- Place each label on or immediately beside its evidence surface.
- Use modern Chinese sans-serif typography, medium or bold, large enough to read.
- Do not place body copy, commands, tables, or long paragraphs inside the image.

```text
Text (verbatim): Render these exact labels as part of the bitmap illustration:
"<label 1>", "<label 2>", "<label 3>".
Use each phrase exactly once. Do not translate, paraphrase, misspell, repeat,
or add other text. Place each label on its specified evidence surface.
```

### 3. Build the prompt

Use this order:

1. State the concrete claim and task.
2. Describe the real setting and action.
3. Describe Jerry and the cat using the canonical identity block when present.
4. Repeat explicit exclusions such as “no hat.”
5. Describe evidence objects and their geometry.
6. Assign semantic colors.
7. Quote exact labels and placements.
8. Add the Mode A style anchor.
9. End with exclusions.

Mode A style anchor:

```text
Professional editorial manga/comic ink illustration. Clean confident black ink
outlines with varied line weights and controlled circular halftone screentone.
When present, Jerry is a young East Asian man with short textured black hair,
dark round glasses, a calm friendly expression, and a light simple shirt; no hat
unless explicitly requested. His companion is a Bengal-cat × Chinese Li Hua cat
mix matching the supplied references: silver-gray short coat, dark charcoal mixed
wild-and-striped markings, warm yellow eyes, pale muzzle and chest, long white
whiskers, upright ears, ringed tail, and a small gold collar tag. Do not exaggerate
Bengal rosettes or reduce the cat to a generic tabby. Use an off-white lightly
textured environment. Color is restrained: black, white, charcoal and silver-gray
halftone, warm ochre/gold for the cat's eyes and tag, plus at most two muted
semantic accent colors. No old stick figure, no Border Collie, no hat, no 3D,
no glossy gradients, no photorealism, no dashboard clutter, no tiny text,
no long paragraphs, no watermark.
```

### 4. Inspect and retry

- Verify Jerry's hair, glasses, expression, and accessory exclusions.
- Verify the cat matches the reference photos: mixed Bengal/Li Hua patterning, yellow eyes, pale muzzle, whiskers, ringed tail, and gold tag.
- Reject purebred-looking leopard rosettes, a generic tabby appearance, the old stick figure, or any dog.
- Compare every required label character by character and reject missing, duplicated, invented, or misspelled text.
- Retry with one targeted correction while repeating all identity and style invariants.

## Mode B workflow

### 1. Describe one reusable scene

Use one character action and only the objects needed to establish it. Leave generous padding around the subject for safe composition.

### 2. Build the prompt

Describe the subject, repeat identity constraints and exclusions, then append:

```text
Style: professional editorial manga/comic ink illustration. Clean confident ink
outlines with varying line weights and circular halftone screentone for gray and
shadow areas. Jerry is a young East Asian man with short textured black hair,
dark round glasses, a calm friendly expression, and a light simple shirt. He
wears no hat unless explicitly requested. His companion is a Bengal-cat × Chinese
Li Hua cat mix matching the reference photos: silver-gray short coat, dark mixed
wild-and-striped markings, warm yellow eyes, pale muzzle and chest, long white
whiskers, upright ears, ringed tail, and a small gold collar tag. Do not depict a
generic tabby or exaggerated purebred Bengal rosettes. The background must be a
perfectly uniform flat <KEY_COLOR> rectangle with zero gradient, texture, noise,
speckles, shadows, floor plane, or lighting variation. Keep generous padding.
No old stick figure, no Border Collie, no hat, no text, no watermark. PNG format.
```

### 3. Validate and remove the background

- Confirm all four corners are uniform and match the selected key color.
- Confirm Jerry and the cat match the canonical identity block.
- Reject artwork touching the border or backgrounds with texture, shadows, or lighting variation.
- Run:

```bash
python3 scripts/cutout.py source.png transparent.png
```

- Confirm the result is RGBA, corners have alpha `0`, and glasses, hair, ears, whiskers, tail, collar, and small props remain intact.

## README asset workflow

For repository-homepage work, follow this order:

1. Inspect the real repository and existing README.
2. Define the content hierarchy and asset inventory.
3. Update this Skill or the project-specific identity specification before generating personalized assets.
4. Decide whether each asset is Mode A or Mode B.
5. Generate one identity test or character sheet.
6. Obtain user approval for the identity direction.
7. Generate the hero and supporting assets.
8. Save approved assets under `assets/readme/` with source variants when available.
9. Update README references only after asset approval.
10. Preview desktop and narrow-width rendering.
11. Commit on a branch and open a draft PR; do not publish directly to the default branch unless explicitly requested.

## Output handling

- Save approved project assets inside the project or output directory.
- Do not leave referenced images only in the generator's default storage.
- Use versioned filenames instead of overwriting approved assets unless replacement is explicitly requested.
- Do not store raw personal photos in the repository by default.
- Report the final prompt, output mode, source path when Mode B is used, final path, and non-default cutout options.

## Quality gate

For every output:

- The subject is recognizable in about 3 seconds.
- The main action or relation is clear in about 10 seconds.
- Jerry and the cat remain consistent with the canonical identity system.
- The cat looks like the supplied Bengal/Li Hua mix rather than a breed stereotype.
- Line work, halftone, restrained color, and semantic accents remain consistent.
- Characters support the content instead of becoming generic decoration.

For Mode A:

- One claim, one focal action, and no more than three major visual regions.
- Visual evidence remains understandable without labels.
- Every required label is exact, appears once, and is readable.

For Mode B:

- Background removal is clean and genuinely transparent.
- Thin details and internal halftone regions remain intact.
- No source background, fringe, shadow, or border artifact remains.
