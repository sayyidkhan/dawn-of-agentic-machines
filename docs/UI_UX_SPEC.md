# UI / UX SPEC

## Direction

Cinematic, minimal, contextual, nature-integrated.

Inspired by the restraint and clarity of premium third-person action RPG interfaces rather than copying any specific game's assets or layout.

## HUD — Exploration

Default visible:

- small health element
- minimal compass only when navigation matters
- selected utility item

Hidden unless needed:

- quest text
- contextual action prompts
- tracking information

## HUD — Combat

Visible:

Top/upper edge:
- optional monster name/status

Lower left:
- player health
- stamina

Lower right:
- selected consumable
- contextual weapon state

Center:
- no permanent crosshair for melee
- temporary interaction prompt only

## Hunter Sense Overlay

Activation should:

- slightly reduce saturation
- emphasize traces/clues
- highlight relevant environmental objects
- preserve enough world color that it still looks cinematic

Do not turn the entire experience into bright neon outlines.

## Menus

### Equipment

Left:
- equipment categories

Center:
- character / weapon preview

Right:
- selected item stats and perks

### Inventory

Grid or list with strong icon hierarchy.

Prioritize:

- item image/icon
- item name
- quantity
- one-line purpose

Avoid dense spreadsheet presentation.

## Accessibility

Include from the first prototype:

- subtitle toggle
- subtitle size
- controller vibration toggle
- hold/toggle options
- camera sensitivity
- invert Y
- aim assist / camera assistance setting
- color-safe critical indicators

## Interaction UX

Context prompts should use the currently active input device.

Example:

Controller active → show `X`

Keyboard active → show `E`

Switch automatically when input source changes.

## UI Motion

Use:

- short fades
- restrained slides
- subtle scale changes

Avoid overly animated menus.

The world should remain the visual focus.
