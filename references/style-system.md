# Style system

Use this reference to choose a preset or tune a difficult source. Define the look
through observable production limits rather than one film, game, engine, or meme.

## Visual thesis

Aim for **sincere technical insufficiency**: an understandable scene built with too
few polygons, too few textures, too few assets, and lighting placed without mature
cinematography. The charm should be accidental, direct, and slightly awkward.

## Eight style pillars

### 1. Coarse geometry

- Use few large planes, awkward edge flow, hard normals, and lumpy silhouettes.
- Build joints from blocks, hands from wedges or rectangular fingers, and faces
  from crude cheek, brow, nose, jaw, and mouth planes.
- Avoid clean triangular mosaics, elegant facets, smooth subdivision, and toy forms.

### 2. Unrefined faces and gaze

- Reuse simple eyeball and eye-texture construction across multiple characters.
- Allow unequal eye sizes, slightly off-center pupils, imperfect gaze convergence,
  stiff eyelids, crude brows, flat mouth slits, and frozen expressions.
- Keep the broad emotion readable; remove professional subtle acting and beauty polish.

### 3. Tiny rough textures

- Use visibly small, blurry diffuse maps with seams, mirrored details, UV stretching,
  inconsistent scale, crude painted shadows, and limited color steps.
- Replace hair strands, fur grooming, pores, fabric weave, and fine embroidery with
  noisy repeated patches or a few thick texture cards.

### 4. Obvious repetition

- Reuse the same bark, grass, plank, stone, wall, fur, scale, cloth, skin, hair,
  and eye maps where plausible.
- Make tiling visible. Repetition is evidence of a small asset budget, not a flaw
  to hide with procedural variation.

### 5. Sparse repeated background

- Keep only the minimum scene masses required to identify the setting.
- Reuse two or three tree, bush, post, rock, building, beam, or prop models many times.
- Remove small signs, decorative trim, incidental set dressing, and unique clutter.
- Avoid both detailed environments and deliberately clean voxel worlds.

### 6. Naive lighting

- Prefer one blunt directional or overhead-front light plus weak ambient fill.
- Allow flat local color, clipped foreheads/noses/hands, muddy eye sockets and necks,
  hard low-resolution shadows, weak contact shadows, and exposure mismatch.
- Avoid rim lights, beauty lights, three-point setups, soft bounce, global illumination,
  volumetric beams, bloom, cinematic fog, and carefully shaped facial light.

### 7. Cheap rendering and capture

- Use weak antialiasing, limited texture filtering, basic shadow maps, jagged edges,
  mild pixel crawl, fine noise, slight color fringe, and screen-capture softness.
- Keep these effects secondary. Do not substitute VHS, CRT, glitch, mosaic, or
  heavy JPEG damage for actual primitive assets.

### 8. Plain mood and color

- Anchor three to six large colors in the source, then render them bluntly.
- Favor sincere, homemade, literal, slightly washed-out or overexposed color.
- Keep dark scenes readable. Do not default to horror, sepia, teal-orange cinema,
  dramatic desaturation, or premium atmospheric depth.

## Presets

### `primitive_folk_cgi` — default

For general images, animals, people, landscapes, objects, and mixed scenes.

- extreme reconstruction; medium identity lock; very-low detail budget;
- crude asymmetrical meshes and stiff gaze;
- obvious texture tiling and heavy asset reuse;
- sparse repetitive background;
- one naive light plus flat ambient;
- low production value that remains readable.

### `bright_folk_cgi`

Use when the user wants more likeness or a gentler result.

- high reconstruction; high identity lock;
- readable angular faces with fewer intentional gaze errors;
- rough textures and repeated background assets, but less aggressively;
- bright simple daylight with awkward exposure.

### `sunlit_game_map`

For architecture, streets, travel photos, and spatial scenes.

- modular block geometry; repeated facade and ground maps;
- very small prop library and sparse set dressing;
- blunt sky light plus one direction light; simple baked-looking shadows;
- no automatic dark industrial mood.

### `community_cgi_stage`

For portraits, dialogue, group shots, performances, and frontal compositions.

- exact head count and spacing; medium identity lock;
- shared eye, skin, cloth, and hair assets; stiff hands and frozen expressions;
- shallow staged depth and repeated beams/backdrops;
- plain overhead-front light, uneven faces, and no cinematic separation.

### `rough_night_render`

Use only for genuine night sources or explicit night requests.

- a few crude point lights, short falloff, hard shadow maps, and dark gaps;
- repeated emissive maps; readable local colors;
- no horror treatment unless requested.

## Source adjustments

| Source | Lock | Deliberately reduce | Reuse |
|---|---|---|---|
| Portrait | silhouette, head angle, hair mass, clothing blocks | face planes, eye alignment, skin detail, hands | eye/skin/hair maps |
| Group | count, spacing, gestures, color blocks | individual face acting, fingers, garment detail | eyes, skin, cloth, hair assets |
| Animal | species, markings, stance, muzzle direction | fur, paws, joints, facial refinement | fur/scale/eye maps |
| Landscape | horizon, landform, palette | foliage variety, rock detail, atmosphere | trees, bushes, grass, rocks |
| Architecture | massing, openings, perspective | trim, glass, facade detail, clutter | wall, roof, ground modules |
| Food/object | silhouette, count, arrangement | curves, labels, microtexture, reflections | surface and label-free maps |

## Strength and fidelity

- `medium`: recognizable and restrained; use only when likeness dominates.
- `high`: every object reads as rebuilt low-poly; detail remains moderately faithful.
- `extreme` (default): preserve broad anchors only; use primitive geometry, repeated
  maps, sparse assets, stiff gazes, and naive lighting.

Use `identity_lock: medium` by default. Raise to `high` only for explicit likeness;
never lower broad composition and subject-count locks.
