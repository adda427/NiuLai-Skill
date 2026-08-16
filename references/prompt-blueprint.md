# Prompt blueprint and parameters

Use this reference to turn source analysis and user parameters into one executable
image-edit prompt. Replace bracketed variables; do not dump the schema verbatim
into a generation tool.

## Parameter schema

```yaml
skill: niu-lai-translator
preset: bright_folk_cgi | sunlit_game_map | community_cgi_stage | rough_night_render
reconstruction_strength: medium | high | extreme
geometry: visibly_low_poly | primitive_low_poly
face_geometry: angular_readable | strongly_faceted
texture_resolution: low | very_low
texture_finish: rough_repeating | blurry_painted | noisy_fuzzy
lighting: hard_awkward_daylight | flat_stage_light | baked_map_light | crude_point_lights
palette: source_anchored_saturated | source_anchored_neutral
post_effects: none | subtle_capture_noise | mild_color_fringe
composition_lock: strict | high
identity_lock: high | medium
text_mode: none | preserve_exact | user_text
ratio: source_ratio | 1:1 | 3:4 | 4:3 | 9:16 | 16:9
```

## Production prompt template

```text
Reconstruct the supplied source image as a newly modeled low-budget 3D scene;
this is not a filter and not simple image degradation.

SOURCE LOCK — Preserve exactly the [subject count and subject description], their
[pose/expression/gaze], the [crop/camera height/viewpoint], and the placement of
[foreground, midground, background anchors]. Keep [identity anchors and source
colors]. Do not redesign the scene.

TREATMENT — Use [preset] with an earnest, homemade, awkwardly vivid mood. Rebuild
every visible subject and object with [geometry]: visibly planar silhouettes,
hard changes of angle, chunky joints, and simplified construction. For faces or
animals, keep the expression readable while replacing smooth cheeks, eyelids,
nose/muzzle, lips, ears, and limbs with angular polygonal planes; no rounded toy forms.

MATERIALS — Apply [texture_finish] low-resolution diffuse textures with limited
detail, slightly uneven mapping, small-scale pixel softness, occasional stretching
or repetition, crude specular response, and no polished PBR finish.

LIGHT AND COLOR — Use [lighting]. Anchor all colors to the source, retaining
[three to six palette anchors]. Allow simple shadows, flat regions, clipped or
uneven highlights, and slightly imperfect subject/background integration. Keep
the image [bright/readable/night-readable as appropriate], not automatically dark.

RENDER AND CAPTURE — Modest render resolution, weak antialiasing, basic shadow
maps, limited texture filtering, [post_effects] kept subtle. The low quality must
come primarily from geometry, materials, lighting, and rendering—not blur alone.

OUTPUT — [ratio]. [text instruction].

DO NOT — [source-tailored prohibitions], photorealism, smooth subdivision surfaces,
modern polished low-poly illustration, glossy toy rendering, cinematic color grade,
dramatic volumetric fog, excessive darkness, heavy VHS/CRT/glitch artifacts,
random UI, new characters, new props, logos, subtitles, or cow traits not present
in the source.
```

## Short prompt

Use only when the editing model follows source images reliably:

```text
Rebuild the supplied image as a bright, sincere low-budget early-3D scene. Strictly
preserve subject identity, count, pose, expression, composition, crop, viewpoint,
and scene layout. Replace every form with visibly hard-edged low-poly geometry;
make faces readable but angular, never round or toy-like. Use rough low-resolution
diffuse textures, simple uneven daylight, basic shadow maps, weak antialiasing,
source-anchored saturated colors, and subtle pixel-grid noise/color fringing. The
result must look newly modeled with limited tools, not blurred or filtered. No
photorealism, polished modern low-poly art, automatic dark horror mood, extra
objects, text, interface, logos, or cow features absent from the source.
```

## Negative constraint block

```text
Avoid: identity drift; changed pose or camera; added or missing subjects; smooth
faces and limbs; rounded toy aesthetics; polished PBR materials; clean vector-like
facets; photorealism; premium game graphics; cinematic depth of field; teal-orange
grading; automatic darkness; sepia; horror styling; heavy blur; large pixelation;
JPEG corruption; VHS scanlines; CRT frame; glitch overlays; invented captions,
watermarks, logos, UI, horns, animals, characters, or props.
```

## Text handling

- `none` (default): remove incidental subtitles, watermarks, and interface text;
  do not add new text.
- `preserve_exact`: quote the exact source text in the prompt. Inspect the result
  character by character; if exactness fails, regenerate or report the limitation.
- `user_text`: include only the exact supplied text. Never invent a slogan, date,
  film title, studio mark, or platform logo.

## Example decisions

### Daylight portrait

Use `bright_folk_cgi`, `medium` or `high` strength, `angular_readable` face geometry,
and strict identity/composition locks. Spend the prompt budget on silhouette, gaze,
hair mass, clothing color blocks, and facial planes.

### Street or building

Use `sunlit_game_map`, high strength, baked-looking light, modular geometry, and
repeated low-resolution facade/ground textures. Preserve perspective and openings.

### Dialogue or performance frame

Use `community_cgi_stage`, high strength, exact head count and spacing, shallow
staged depth, stiff angular hands, flat scenic assets, and uneven frontal exposure.
