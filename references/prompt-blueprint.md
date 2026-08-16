# Prompt blueprint and parameters

Use this reference to convert source analysis and user choices into one executable
image-edit prompt. Replace variables; do not paste the schema into a generation tool.

## Parameter schema

```yaml
skill: niu-lai-translator
preset: primitive_folk_cgi | bright_folk_cgi | sunlit_game_map | community_cgi_stage | rough_night_render
reconstruction_strength: medium | high | extreme
anchor_lock: strict | high
identity_lock: medium | high
detail_budget: very_low | low
geometry: primitive_low_poly | visibly_low_poly
face_geometry: clumsy_asymmetric | strongly_faceted | angular_readable
gaze_quality: stiff_misaligned | crude_readable | source_faithful
texture_resolution: very_low | low
texture_repetition: obvious | strong | moderate
asset_reuse: heavy | strong | moderate
background_detail: sparse | reduced
lighting: naive_single_light | flat_stage_light | hard_awkward_daylight | crude_point_lights
palette: source_anchored_blunt | source_anchored_saturated
post_effects: none | subtle_capture_noise | mild_color_fringe
text_mode: none | preserve_exact | user_text
ratio: source_ratio | 1:1 | 3:4 | 4:3 | 9:16 | 16:9
```

## Production prompt template

```text
Rebuild the supplied image as a primitive, visibly low-budget 3D scene. This is
not a blur filter, compression pass, or fashionable low-poly illustration.

BROAD ANCHOR LOCK — Preserve [subject count/types], [left-to-right arrangement],
[major pose/gesture], [crop/camera/perspective], [occlusion/depth layers], [scene
category], and [three to six dominant color blocks]. Preserve large silhouettes,
garment categories, and major props. Do not pursue exact fine facial or background
detail; the source should remain recognizable through its large relationships.

DETAIL BUDGET — Use [preset], [reconstruction_strength], and [detail_budget].
Remove subtle facial acting, hair strands, fingers, embroidery, microtexture,
decorative architecture, small signs, and incidental set dressing.

GEOMETRY AND PEOPLE — Rebuild forms with [geometry]: few large awkward planes,
hard normals, lumpy proportions, block joints, wedge hands, crude face planes, and
thick hair clumps/cards. For faces use [face_geometry] and [gaze_quality]: simple
reused eye construction, unequal eye sizes, slightly off-center pupils, imperfect
gaze convergence, stiff lids, block noses, flat mouth slits, and frozen expressions.
Keep broad intent readable without professional animation polish.

TEXTURES AND REUSE — Use [texture_resolution] diffuse maps with [texture_repetition]
tiling, seams, UV stretching, mirrored details, inconsistent scale, noisy pixels,
crude painted shadows, and weak specular response. Use [asset_reuse]: visibly reuse
a tiny library of skin, eye, hair, cloth, fur, scale, plank, bark, grass, stone,
wall, and ground assets as relevant.

BACKGROUND — Set [background_detail]. Keep only essential setting masses. Reuse
two or three primitive background models repeatedly with minimal variation; remove
unique clutter and decorative detail.

LIGHT AND RENDER — Use [lighting]: one blunt directional or overhead-front light
plus weak flat ambient fill. Allow clipped highlights, muddy dark patches, hard
low-resolution shadows, weak contact, and inconsistent nearby exposure. Use weak
antialiasing, limited filtering, basic shadow maps, [post_effects] kept secondary,
and no professional scene separation.

OUTPUT — [ratio]. [text instruction].

DO NOT — [source-tailored prohibitions], exact premium reproduction, attractive
aligned eyes, refined facial acting, smooth subdivision, clean designer facets,
unique high-resolution materials, rich detailed background, rim light, beauty
light, three-point lighting, volumetric beams, cinematic depth, PBR, glossy toys,
photorealism, modern game polish, darkness as a shortcut, VHS/CRT/glitch/mosaic,
random text, UI, characters, props, logos, or cow traits absent from the source.
```

## Compact prompt

Use only when the editor follows source images reliably:

```text
Rebuild the supplied image as sincere but technically poor primitive folk CGI.
Lock only subject count, broad arrangement, poses, camera, scene category, large
silhouettes and color blocks; deliberately reduce fine likeness and background
detail. Use very few awkward polygons, stiff unequal eyes with slightly misaligned
pupils, crude face wedges, thick hair cards, wedge hands, tiny blurry diffuse maps,
obvious repeated tiling, and a tiny background asset library copied many times.
Light everything with one blunt overhead-front light plus weak flat ambient: clipped
faces, muddy eye sockets, hard cheap shadows, uneven exposure, no rim or cinematic
separation. Weak antialiasing and filtering only. No polished low-poly art, detailed
sets, unique clean textures, professional facial acting, PBR, beauty light, horror,
VHS, text, UI, new subjects, props, logos, cows, or horns.
```

## Negative constraint block

```text
Avoid: fine likeness; attractive aligned eyes; expressive professional facial
animation; correct smooth anatomy; clean triangular facets; rounded toy forms;
unique high-resolution textures; hidden tiling; procedural background variety;
rich set dressing; cinematic lighting; three-point light; rim light; soft bounce;
global illumination; volumetric fog; depth of field; premium game graphics;
photorealism; darkness or horror as a shortcut; heavy blur; large pixelation;
JPEG damage; VHS; CRT; glitch; invented text, UI, logos, characters, or props.
```

## Text handling

- `none` (default): omit incidental signs, subtitles, watermarks, and interface text.
- `preserve_exact`: quote exact source text and inspect character by character.
- `user_text`: include only exact user-supplied text; invent nothing.

## Source recipes

### Portrait or group

Use `community_cgi_stage` for groups and `primitive_folk_cgi` for a single figure.
Lock count, spacing, pose, hair mass, garment categories, and color blocks. Reuse
eyes, skin, hair, and cloth maps. Emphasize stiff gaze, frozen faces, and wedge hands.

### Animal scene

Use `primitive_folk_cgi`. Lock species, count, stance, markings, and composition.
Reuse fur/scale/eye maps and reduce facial refinement, paws, joints, and background variety.

### Architecture or landscape

Use `sunlit_game_map`. Lock perspective, horizon, landform, massing, and openings.
Reuse a tiny module library and visibly tile wall, ground, grass, tree, and rock maps.

### Lighting-only follow-up

Lock all geometry, materials, poses, and composition. Replace only lighting with
`naive_single_light`: blunt overhead-front direction, weak ambient, clipped faces,
muddy creases, hard low-resolution shadows, weak contact, and uneven exposure.
