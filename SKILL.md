---
name: niu-lai-translator
description: >-
  Reconstructs any supplied image as exaggeratedly failed primitive low-poly 3D:
  extremely sparse meshes, distorted proportions, stiff broken-looking posing,
  visible garment/body clipping, crude faces, repeated tiny textures, reused sparse
  assets, and naive lighting while preserving only semantic and compositional anchors.
  Use when users invoke 牛来低模转译,
  niu-lai-translator, 反向出圈画质, 低画质重制, 粗糙人物低模, 早期 3D 游戏截图,
  primitive folk CGI, bootleg CGI, or ask to make an image look intentionally
  cheap, awkward, poorly modeled, poorly lit, and less faithfully reproduced.
---

# Niu Lai Translator / 牛来低模转译器

> Core principle: **保留大关系，主动放弃精致还原；让低质量来自整套生产能力，而不是后期滤镜。**

Rebuild the source as a scene made by a sincere but technically limited early-3D
team. Keep the image readable and structurally related to the source while making
topology, proportions, rigging, collision, eyes, textures, assets, lighting, and
rendering visibly fail. A merely stylish or attractive low-poly result is a failure.

## Workflow

Track this sequence:

```text
- [ ] 1. Confirm that an input image exists; request one if absent
- [ ] 2. Read explicit parameters and infer the rest from the primitive defaults
- [ ] 3. Extract hard anchors: subject count/type, layout, semantic action, camera, color blocks
- [ ] 4. Release exact anatomy, proportions, joint angles, silhouette, and collision fidelity
- [ ] 5. Build one source-based image-edit prompt in the required order
- [ ] 6. Generate/edit unless the user asked for prompts or options only
- [ ] 7. Inspect against the inverted quality gate; retry polished results
- [ ] 8. Return the image plus one compact treatment note
```

## Interaction

- Require an input image unless the user explicitly asks for a new scene.
- Execute directly when an image is supplied without parameters or the user says
  “默认”, “你来判断”, or equivalent.
- If the user says “先别生成”, “给方案”, or “让我选”, do not generate. Offer at
  most three distinct directions.
- Ask at most one question only when a missing decision materially changes output.
- Use an image-edit tool that receives the source image. Include every target image
  through the tool's supported reference input.
- Treat this as reconstruction, not compression, pixelation, or a polygon overlay.

## Analyze broad anchors internally

Identify without reporting every item unless asked:

- **Subjects:** count, broad type, large hairstyle, garment category, dominant color
  blocks, large props, semantic action, rough facing direction, and social relation.
- **Composition:** crop, camera height, perspective, horizon, relative scale,
  spacing, foreground/midground/background, and occlusion.
- **Scene:** only the major terrain, architecture, or stage masses required for
  the image to remain recognizable.
- **Palette:** three to six source colors worth retaining.
- **Deliberately mutable structure:** limb length, head/body ratio, torso width,
  animal proportions, exact joint angles, balance, silhouette accuracy, garment fit,
  and clean separation between intersecting meshes.
- **Discardable detail:** fine facial likeness, subtle expression, hair strands,
  embroidery, microtexture, unique background assets, small signage, and decoration.

## Use primitive defaults

Use `primitive_folk_cgi` unless the user requests a gentler translation. Read
[references/style-system.md](references/style-system.md) when selecting another preset.

```yaml
preset: primitive_folk_cgi
reconstruction_strength: extreme
anchor_lock: strict
identity_lock: medium
detail_budget: very_low
geometry: primitive_low_poly
polygon_budget: extremely_low
face_geometry: clumsy_asymmetric
gaze_quality: stiff_misaligned
proportion_fidelity: deliberately_broken
pose_lock: semantic_action_only
pose_quality: stiff_failed_rig
collision_quality: visible_clipping
clipping_count: 1_to_3
texture_resolution: very_low
material_model: diffuse_only_mismatched
texture_repetition: obvious
asset_reuse: heavy
background_detail: sparse
lighting: naive_single_light
post_effects: subtle_capture_noise
text_mode: none
ratio: source_ratio
```

These are intentional defaults. Correct anatomy, natural poses, perfectly clean
collision in contact-rich scenes, coherent PBR materials, high facial fidelity,
rich backgrounds, unique textures, attractive eyes, or professional lighting are
failures unless requested.

## Preserve meaning, not anatomy

- Strictly preserve subject count and type, broad left-to-right arrangement, crop,
  camera, scene category, semantic action, major props, and dominant color blocks.
- Preserve what the action means, not the exact source pose. A wave should remain a
  wave and an embrace an embrace, but elbows, shoulders, wrists, knees, weight,
  balance, and torso twist should become stiff, simplified, and slightly wrong.
- Preserve identity anchors such as species, hair mass, clothing category, and
  markings, but do not lock the source silhouette or body proportions.
- Deliberately change human and animal proportions. Use mismatched limb lengths,
  oversized or undersized heads, short rigid necks, broad or pinched torsos, chunky
  joints, crude paws/hooves, or uneven body masses. Keep subjects recognizable and
  non-horrific; do not change a real person's apparent age, ethnicity, or body category.
- Introduce one to three readable collision failures when people, animals, clothing,
  or props make contact: sleeves may sink into elbows, upper arms may cut through
  shoulders or loose clothing, hands may intersect sleeves or held objects, and fur
  or garments may penetrate nearby meshes. Do not hide faces, erase whole limbs,
  imply injury, expose the body, or turn every contact into clipping.
- Raise `identity_lock` to `high` only when the user requests likeness or the task
  is identity-sensitive; reduce reconstruction strength if necessary.
- Do not change a real person's apparent age, ethnicity, body category, or
  relationship to others merely to create the style.
- Add no people, animals, horns, cow traits, weapons, props, logos, subtitles,
  interface, meme text, landmarks, or weather not evidenced by the source.

## Rebuild all production layers

Apply all layers together:

1. **Topology:** use an extremely low polygon budget with large planar sections.
   A head, torso, or animal body must read as a handful of crude masses rather than
   a smooth mesh covered in small facets. Avoid silhouette-smoothing support loops.
2. **Proportions:** break source-faithful anatomy while keeping subject category and
   action readable. Prefer visibly mismatched primitive parts over elegant caricature.
3. **Pose and rigging:** reduce each joint to one crude rotation. Use locked torsos,
   kinked elbows, elevated shoulders, straight wrists, planted feet, poor balance,
   floating hands, and weak contact. Avoid natural counter-pose and weight transfer.
4. **Collision:** show a small number of intentional mesh penetrations at shoulders,
   upper arms, elbows, sleeves, garments, fur, hands, or held props when plausible.
5. **Faces and gaze:** reuse simple eye construction; allow unequal eye size,
   slightly off-center pupils, imperfect gaze alignment, stiff lids, flat mouth
   slits, and frozen expressions. Keep intent readable, not professionally acted.
6. **Materials:** use diffuse/base color as the dominant or only material channel.
   Remove normal, displacement, subsurface, clearcoat, layered roughness, fabric,
   skin, fur, and realistic reflection models. Use tiny blurry maps, seams, UV
   stretching, mirrored details, crude painted shadows, flat matte areas, and a few
   wrongly shiny patches. Materials on nearby objects may respond inconsistently.
7. **Repetition:** visibly tile textures and reuse a very small library of trees,
   posts, rocks, buildings, props, hair cards, cloth maps, or eye assets.
8. **Background:** remove incidental detail. Repeat a few primitive assets with
   minimal variation; avoid rich set dressing or individually authored objects.
9. **Lighting:** use one blunt directional/overhead-front light plus weak flat
   ambient fill. Allow clipped highlights, muddy dark patches, hard low-resolution
   shadows, weak contact, and exposure mismatch between nearby subjects.
10. **Rendering:** use weak antialiasing, limited texture filtering, simple shadow
   maps, fine noise, mild color fringe, and modest screen-capture softness.

Do not use darkness, horror grading, VHS damage, heavy JPEG corruption, or mosaic
as shortcuts. “Bad” must come primarily from limited scene production.

## Build the edit prompt

Read [references/prompt-blueprint.md](references/prompt-blueprint.md) for the full
schema and reusable clauses. Construct prompts in this order:

1. Declare source-based primitive 3D reconstruction.
2. Lock semantic/compositional anchors while releasing exact pose, silhouette, and anatomy.
3. Set an extremely low polygon budget and deliberately broken proportions.
4. Specify stiff failed rigging plus one to three plausible clipping locations.
5. Specify crude faces, eyes, hair, hands, paws, and joints.
6. Require very-low-resolution maps, obvious tiling, and heavy asset reuse.
7. Strip background detail to repeated scene primitives.
8. Specify naive lighting, uneven exposure, and basic render limitations.
9. State ratio, text behavior, and source-tailored prohibitions.

Prefer observable flaws over labels such as “ugly” or “bad quality”. Mention a
named game, engine, or film only when the user asks; always translate the name into
construction, material, lighting, and rendering properties.

## Inspect and recover

Read [references/quality-and-recovery.md](references/quality-and-recovery.md) before
judging output. Retry whenever the result is too faithful, attractive, detailed,
varied, or professionally lit. In particular, reject results where:

- geometry uses many small facets or preserves smooth source-faithful silhouettes;
- human or animal proportions remain correct, flattering, or source-faithful;
- poses retain natural balance, joint flow, weight transfer, or clean contact;
- a contact-rich image offers plausible intersections but all garments, limbs, fur,
  and held objects remain perfectly collision-free;
- faces retain polished animation acting or appealing aligned eyes;
- textures are clean, unique, high-resolution, or subtly varied;
- background objects are numerous, detailed, and individually modeled;
- lighting uses cinematic separation, rim light, soft bounce, or volumetric depth;
- geometry resembles fashionable designer low-poly art;
- the effect is only blur, pixelation, noise, or color grading.

On retry, change only the failed dimension and restate all anchor locks. Stop after
two retries unless the user asks to continue.

## Output

For a completed edit, return the generated image and one sentence naming the
preset plus the main retained anchors. Include YAML only when requested.

For prompt-only requests, return one production prompt and one negative block.

## Minimal invocation

```text
/niu-lai-translator
启用牛来低模转译器
把这张图重制成制作能力很差的早期 3D 动画截图
```

```yaml
skill: niu-lai-translator
preset: primitive_folk_cgi
reconstruction_strength: extreme
identity_lock: medium
asset_reuse: heavy
lighting: naive_single_light
ratio: source_ratio
```

**不是做得像“低模艺术”，而是像真的只有少量模型、少量贴图、简单灯光和有限技术。**
