# Quality gate and recovery

Inspect the generated image itself; do not judge from the prompt alone.

## Pass criteria

All hard checks must pass:

- **Source fidelity:** subject count, identity anchors, pose, expression, crop,
  viewpoint, and major scene layout remain recognizable.
- **True reconstruction:** geometry, materials, lighting, and rendering all changed;
  the result is not merely blurred, pixelated, color-graded, or noise-covered.
- **Angular construction:** silhouettes and faces show deliberate planar turns;
  cheeks, noses/muzzles, eyelids, limbs, foliage, and terrain are not smoothly rounded.
- **Unpolished materiality:** textures look limited, slightly rough, and imperfect;
  surfaces do not read as premium PBR, clay, glossy vinyl, or clean vector art.
- **Mood:** the result feels sincere, blunt, homemade, and slightly awkward while
  respecting the source mood. It is not automatically dark or horrific.
- **No invention:** no unrequested people, props, horns, animal traits, captions,
  logos, interface elements, landmarks, or weather changes.
- **Technical restraint:** noise, color fringe, pixel softness, and aliasing support
  the low-budget render rather than obscuring the image.

## Scored checks

Score each item 0–2. Accept only at 10/12 or above with every hard check passing.

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Identity | changed/generic | partly retained | clearly retained |
| Composition | redesigned | minor drift | tightly preserved |
| Geometry | smooth | mixed | consistently angular |
| Materials | polished/filter-like | partly rough | convincingly limited |
| Light/color | wrong mood | usable | source-led and awkwardly vivid |
| Restraint | gimmicky artifacts | some excess | artifacts subtle |

## Failure recovery

### Looks like a filter

Retry with: “Discard the rendered surface and rebuild every visible object as an
actual simple 3D asset. Make polygon planes visible in silhouette and shading.
Do not rely on blur, mosaic, noise, or color grading.”

### Too polished or cute

Retry with: “Reduce topology and material sophistication. Use chunky asymmetrical
forms, hard normals, crude diffuse textures, basic shadow maps, and inconsistent
specular response. No rounded vinyl toy, clay render, clean isometric art, or
designer low-poly finish.”

### Too dark or cinematic

Retry with: “Restore the source exposure and palette. Use blunt readable daylight
or flat stage light, saturated local colors, simple shadows, no horror grading,
volumetric fog, teal-orange look, sepia, or dramatic rim light.”

### Face became generic

Retry with: “Lock [specific identity anchors]. Preserve face width, hair silhouette,
eye spacing, nose direction, mouth expression, gaze, and head angle. Simplify them
into large angular planes without replacing the person's identity.” Reduce
`reconstruction_strength` from `extreme` to `high` or from `high` to `medium`.

### Composition drifted

Retry with an explicit inventory: subject coordinates, scale within frame, horizon,
camera height, gaze direction, foreground occlusion, and background anchors. State
“no reframing, recropping, camera move, or rearrangement.”

### Unwanted cows, horns, captions, or UI

Retry with: “The style name is not a content instruction. Add no cows, horns,
animal traits, meme captions, subtitles, watermarks, logos, game HUD, or new props.
Render only content evidenced by the source.”

### Artifacts overpower the scene

Remove post effects. Keep only weak antialiasing and limited texture filtering.
Reintroduce at most one subtle capture artifact after the reconstructed scene passes.

## Retry discipline

1. Restate all source locks on every retry.
2. Modify only the failed style dimension.
3. Prefer reducing reconstruction strength over sacrificing identity.
4. Stop after two retries unless the user asks to continue.
5. If a hard failure remains, disclose it plainly rather than describing the image
   as successful.
