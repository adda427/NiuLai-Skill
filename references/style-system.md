# Style system

Use this reference when selecting a preset or translating the look of a difficult
source. The style is defined by observable construction choices, not by one film,
game, engine, meme, or character.

## Visual thesis

Aim for **earnest technical limitation**: a scene made with visibly limited 3D
resources, direct color choices, imperfect lighting, and unintended charm. It
should feel authored and rebuilt, not vandalized with a “bad quality” filter.

The key tension is:

- recognizable source truth versus simplified construction;
- cheerful or ordinary subject matter versus awkward rendering;
- vivid color versus cheap material response;
- readable emotion versus stiff facial geometry.

## Six style pillars

### 1. Geometry

- Use low segment counts and visible planar turns.
- Favor chunky silhouettes, wedge-like fingers, blocky joints, faceted cheeks,
  sharp eyelids, polygonal muzzles/noses, and hard-edged foliage or terrain.
- Keep enough topology to preserve pose, expression, and identity.
- Avoid smooth spheres, subdivision surfaces, rounded toy proportions, and clean
  contemporary “designer low-poly” tessellation.

### 2. Materials

- Use low-resolution diffuse textures with soft pixels, uneven scale, limited
  detail, mild stretching, and occasional repetition.
- Allow rough fur or grass to read as a flat or noisy texture pasted onto simple geometry.
- Keep specular response crude and inconsistent; avoid ray-traced realism, glossy
  product rendering, perfect subsurface scattering, or pristine PBR materials.

### 3. Lighting

- Prefer simple daylight or blunt ambient-plus-directional lighting.
- Allow hard transitions, underfilled shadows, clipped highlights, flat local
  regions, and slightly mismatched subject/background illumination.
- Bright does not mean soft or polished. Preserve awkwardness and readability.

### 4. Color

- Anchor the palette in the source image.
- Permit strong grass green, cyan sky, orange, ochre, yellow, beige, and other
  plainspoken colors when the source supports them.
- Use limited grading. Avoid default teal-orange cinema, sepia nostalgia, smoky
  horror green, or desaturation unless requested.

### 5. Rendering and capture

- Use modest render resolution, weak antialiasing, simple shadows, short texture
  filtering, and limited atmospheric effects.
- Add only subtle noise, fine pixel-grid texture, mild chromatic fringing, edge
  shimmer, or screen-recorded softness.
- Do not add scanlines, VHS damage, heavy JPEG blocks, CRT curvature, or glitch
  effects unless requested; those describe a display artifact, not the core style.

### 6. Mood

- Favor sincere, homemade, strangely vivid, awkwardly theatrical, and faintly comic.
- Keep humor emergent from rendering limitations. Do not force parody faces,
  slapstick props, meme captions, or grotesque horror.

## Presets

### `bright_folk_cgi` — default

For portraits, animals, landscapes, casual snapshots, and general scenes.

- open daylight or simple bright interior light;
- saturated source-anchored colors;
- rough fuzzy/noisy diffuse textures;
- obvious but readable facial planes;
- basic vegetation and terrain assets;
- imperfect exposure and simple shadows;
- earnest, low-budget animated-film charm.

### `sunlit_game_map`

For architecture, streets, travel photos, interiors with strong spatial layout,
and scenes that benefit from a game-map reading.

- modular block geometry and repeated map textures;
- baked-looking light, blunt sky illumination, limited reflections;
- sparse prop detail and simple collision-like shapes;
- mild early-3D screenshot artifacts without default darkness.

### `community_cgi_stage`

For dialogue, group portraits, performances, ceremonies, and frontal compositions.

- shallow staged depth and flat scenic backdrops;
- stiff pose transitions and simple costume geometry;
- basic spotlight or ambient fill with uneven face exposure;
- theatrical framing and local-production sincerity.

### `rough_night_render`

Use only when the source is genuinely night-time or the user requests night.

- retain readable saturated local colors;
- use hard point lights, shallow light falloff, simple shadow maps, and dark gaps;
- avoid turning the frame into horror unless requested.

## Source-specific adjustments

| Source | Preserve most | Simplify visibly | Avoid |
|---|---|---|---|
| Face/portrait | silhouette, gaze, expression, hair mass | cheeks, nose, lips, eyelids, ears | generic face, toy smoothness |
| Animal | species, markings, stance, muzzle | fur, paws, joints, horns if present | adding human traits or new horns |
| Landscape | horizon, landform, palette | foliage cards, rock planes, tiled ground | fantasy landmarks |
| Architecture | massing, openings, perspective | trim, glass, facade textures | warped layout |
| Food/object | silhouette, count, arrangement | curved surfaces, labels, microtexture | plastic product polish |
| Group scene | head count, spacing, gestures | faces, hands, garments | merging or adding people |

## Strength scale

- `medium`: source remains easy to recognize; geometry changes are visible mainly
  on contours and large planes. Use for identity-sensitive portraits.
- `high` (default): all objects read as rebuilt low-poly assets; key identity and
  composition remain stable.
- `extreme`: primitive geometry, very small textures, stiff forms, and stronger
  rendering faults. Use only when the user prioritizes comic crudeness over likeness.
