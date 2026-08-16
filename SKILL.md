---
name: niu-lai-translator
description: >-
  Reconstructs any supplied image as a deliberately crude, bright low-poly 3D
  game or folk-CGI frame while preserving the source subject, composition,
  viewpoint, pose, and scene identity. Use when users invoke 牛来低模转译,
  niu-lai-translator, 反向出圈画质, 低画质重制, 早期 3D 游戏截图,
  rough low-poly remake, bootleg CGI, primitive game-engine render, or ask to
  make a photo or image look intentionally cheap, angular, low-resolution, and
  awkwardly charming rather than polished or photorealistic.
---

# Niu Lai Translator / 牛来低模转译器

> Core principle: **原图提供事实，新图把事实重新建模成笨拙、生猛、明亮的低模世界。**

Treat the task as image-to-scene reconstruction, not a filter, compression pass,
or generic polygon effect. Preserve what the source depicts; replace how that
world appears to have been modeled, textured, lit, rendered, and captured.

## Workflow

Track this sequence:

```text
- [ ] 1. Confirm that an input image exists; request one if absent
- [ ] 2. Read explicit parameters and infer safe defaults for the rest
- [ ] 3. Analyze subject, composition, depth layers, pose, palette, and identity anchors
- [ ] 4. Choose a scene preset and reconstruction strength
- [ ] 5. Build one image-edit prompt using the required order
- [ ] 6. Generate/edit the image unless the user asked for prompts or options only
- [ ] 7. Inspect the result against the quality gate and retry if needed
- [ ] 8. Return the image plus a compact record of the chosen treatment
```

## Interaction

- Require an input image. Do not invent a source scene from a text-only request
  unless the user explicitly asks for a new image rather than a translation.
- Prefer direct execution when the user uploads an image without parameters or
  says “默认”, “你来判断”, or equivalent.
- If the user says “先别生成”, “给方案”, or “让我选”, do not generate. Offer at
  most three clearly distinct directions.
- Ask at most one question only when a missing decision would materially change
  the result. Otherwise use the defaults below.
- Use an image-editing or image-generation tool that can receive the source image.
  Include every target image through the tool's supported reference-image input.
- Never claim pixel-perfect identity preservation. Report any material deviation
  after inspecting the output.

## Analyze the source internally

Identify without narrating every item unless asked:

- **Identity anchors:** silhouette, face shape, hairstyle, clothing blocks,
  species, distinctive objects, architecture, signage, and landmark geometry.
- **Composition:** crop, camera height, focal length impression, horizon, subject
  scale, gaze, pose, foreground/midground/background, and occlusion.
- **Color anchors:** three to six dominant colors that should survive translation.
- **Lighting:** direction, time-of-day evidence, contrast, and exposure.
- **Text:** retain only when the user requests exact text; otherwise omit UI,
  subtitles, watermarks, and newly invented lettering.

## Choose the treatment

Use `bright_folk_cgi` by default. Read [references/style-system.md](references/style-system.md)
when selecting another preset or tuning a difficult scene.

```yaml
preset: bright_folk_cgi
reconstruction_strength: high
geometry: visibly_low_poly
face_geometry: angular_readable
texture_resolution: low
texture_finish: rough_repeating
lighting: hard_awkward_daylight
palette: source_anchored_saturated
post_effects: subtle_capture_noise
composition_lock: strict
identity_lock: high
text_mode: none
ratio: source_ratio
```

Do not default to a dark horror or dystopian look. Early Source-engine games may
be used as a technical analogy for asset limitations, but they are not the main
color or mood reference. Prefer bright daylight, blunt colors, uneven exposure,
and homemade theatrical charm.

## Reconstruct, do not degrade mechanically

Apply all five layers together:

1. **Geometry:** visibly reduce forms to planar masses with hard silhouette turns.
2. **Materials:** rebuild surfaces with small, blurry, slightly repeating textures.
3. **Lighting:** use simple, imperfect, occasionally overexposed illumination.
4. **Rendering:** reduce polish, reflections, antialiasing, and physically accurate shading.
5. **Capture:** add restrained pixel-grid texture, noise, mild color fringing, or
   screen-capture softness only after the 3D reconstruction is convincing.

A low-resolution overlay alone is failure. A polished modern low-poly illustration
is also failure.

## Preserve source truth

- Preserve subject count, role, pose, gaze direction, gesture, framing, viewpoint,
  camera distance, major object placement, terrain, and weather unless instructed.
- Preserve recognizable identity through silhouette and large facial planes while
  converting curved cheeks, noses, lips, eyes, and limbs into angular geometry.
- Keep people at their apparent age and do not change body type, ethnicity,
  clothing category, expression, or relationships without instruction.
- Do not add horns, animal traits, game weapons, props, characters, logos, subtitles,
  interface elements, or meme text merely because the skill name references 牛来.
- Do not turn every subject into a cow. The name describes the visual movement,
  not the content.
- Do not reproduce a named film's characters, logos, or exact frame. Translate
  general visual traits from the supplied image and user intent.

## Build the edit prompt

Read [references/prompt-blueprint.md](references/prompt-blueprint.md) for the full
schema and reusable clauses. Construct prompts in this order:

1. Declare source-based scene reconstruction.
2. Lock subject, count, composition, viewpoint, pose, and scene layout.
3. State the chosen preset and mood.
4. Specify low-poly geometry, including angular faces when people or animals appear.
5. Specify low-resolution materials and limited surface detail.
6. Specify lighting, palette, rendering limitations, and restrained capture artifacts.
7. State aspect ratio and requested text behavior.
8. End with explicit prohibitions tailored to the source.

Prefer concrete visual instructions over aesthetic labels. Mention a named engine,
game, or film only when the user explicitly asks; translate it into observable
properties rather than relying on the name alone.

## Inspect and recover

Read [references/quality-and-recovery.md](references/quality-and-recovery.md) before
judging a generated result. Retry when any hard failure occurs, especially:

- source composition or identity drifted;
- geometry remained smooth or became polished modern low-poly art;
- the result is merely blurry, pixelated, or filtered;
- the image became needlessly dark, cinematic, horrific, or sepia;
- text, props, characters, or cow features were invented.

On retry, change only the failed dimension and restate all preservation locks.
Stop after two retries unless the user asks to continue.

## Output

For a completed edit, return:

1. the generated image;
2. one sentence naming the selected preset and the main preservation choice;
3. optional compact YAML only when the user asks for parameters or reproducibility.

For prompt-only requests, return one production-ready prompt and one negative
constraint block. Do not pad the answer with process notes.

## Minimal invocation

```text
/niu-lai-translator
启用牛来低模转译器
把这张图做成反向出圈的低画质 3D 截图
```

```yaml
skill: niu-lai-translator
preset: bright_folk_cgi
reconstruction_strength: high
composition_lock: strict
identity_lock: high
text_mode: none
ratio: source_ratio
```

**不是把清晰图片压糊，而是把画面中的现实重新做成一套能力有限、审美直给、意外鲜活的旧 3D 资产。**
