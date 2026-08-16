# Inverted quality gate and recovery

Inspect the generated image itself. Success means controlled low production value,
not conventional visual polish.

## Hard pass criteria

- **Broad anchor fidelity:** subject count, arrangement, pose, crop, camera, scene
  category, and dominant color blocks remain recognizable.
- **Fidelity ceiling:** fine faces, eyes, hair, hands, garments, and background are
  visibly simplified; a near-exact polished reproduction fails.
- **Primitive geometry:** silhouettes, joints, hands, faces, foliage, terrain, and
  architecture show few awkward planes rather than elegant designer facets.
- **Crude gaze:** character eyes are stiff, slightly unequal or imperfectly aligned,
  and lack professional animation subtlety while remaining non-horrific.
- **Texture poverty:** maps are visibly tiny, blurry, stretched, mirrored, tiled,
  and inconsistent in scale; surfaces are not clean PBR or clay.
- **Asset poverty:** background and repeated objects visibly come from a very small
  reused library; detailed unique set dressing fails.
- **Naive lighting:** illumination is blunt, uneven, and simple, with clipped local
  highlights, muddy patches, basic hard shadows, and no cinematic separation.
- **True reconstruction:** low quality comes from geometry, materials, repetition,
  lighting, and rendering—not only blur, noise, pixelation, or grading.
- **No invention:** add no unrequested subjects, props, horns, cow traits, captions,
  logos, interface, landmarks, or weather changes.

## Scored checks

Score each dimension 0–2. Accept at 14/18 or above only when all hard checks pass.

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Broad anchors | lost | partly retained | clearly retained |
| Fidelity ceiling | too exact | mixed | detail clearly reduced |
| Geometry | smooth/polished | mixed | awkward primitive |
| Faces/gaze | refined | partly stiff | crudely convincing |
| Textures | clean/unique | some roughness | tiny and repeated |
| Asset reuse | rich variety | some reuse | visibly limited library |
| Background | detailed | reduced | sparse and repetitive |
| Lighting | cinematic | simple | naively uneven |
| Capture restraint | gimmicky | some excess | secondary and subtle |

## Failure recovery

### Too faithful, attractive, or polished

Retry with: “Lock only count, layout, pose, camera, scene category, silhouettes,
and large color blocks. Discard fine likeness. Reduce topology, proportions,
facial refinement, garment detail, unique assets, and material sophistication.”

### Eyes still look professionally animated

Retry with: “Reuse one crude eye model. Make eye sizes slightly unequal, pupils
off-center, gaze convergence imperfect, eyelids rigid, brows simple, and expression
frozen. Keep it readable and awkward, not grotesque or horrific.”

### Background is too detailed

Retry with: “Delete incidental set dressing. Keep only essential scene masses.
Reuse two or three tree/building/beam/post/rock models many times with minimal
variation. No individually authored clutter or atmospheric depth.”

### Textures are too clean or varied

Retry with: “Replace surfaces with tiny blurry diffuse maps. Make tiling, seams,
UV stretch, mirrored details, inconsistent scale, and reuse clearly visible.
Reuse the same map across multiple compatible objects.”

### Lighting is too professional

Retry with: “Change lighting only. Use one blunt overhead-front directional light
plus weak flat ambient. Create clipped foreheads/noses/hands, muddy eye sockets and
necks, hard low-resolution shadows, weak contact, and uneven nearby exposure. Remove
rim, beauty, three-point, bounce, global illumination, volumetrics, bloom, and depth.”

### Result becomes dark, horrific, or grotesque

Restore source-led color and readable exposure. Keep awkward eyes and crude faces
within ordinary stylization. Remove horror grading, extreme distortion, deep black
voids, dramatic fog, and threatening light.

### Broad composition drifts

Restate subject count, approximate coordinates, relative scale, pose, camera height,
horizon, foreground occlusion, and background masses. Say “no reframing, recropping,
camera move, subject merge, or rearrangement.”

### Result looks like a filter

Say: “Rebuild every object as an actual primitive 3D asset. Make low polygon count,
repeated maps, reused models, and naive shadowing visible before adding any capture noise.”

### Unwanted cows, horns, captions, or UI

Say: “The skill name is not a content instruction. Render only source-evidenced
content. Add no cows, horns, animal traits, meme text, subtitles, watermarks, logos,
HUD, or new props.”

## Retry discipline

1. Restate all broad anchor locks on every retry.
2. Change only the failed dimension.
3. Prefer lowering fine-detail fidelity over weakening composition locks.
4. Stop after two retries unless the user asks to continue.
5. Disclose remaining hard failures rather than calling the result successful.
