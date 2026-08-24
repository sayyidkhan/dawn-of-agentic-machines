# MASTER GAME DESIGN — Project Chimera

## 1. High Concept

Project Chimera is a third-person single-player hunting RPG built around preparation, tracking, observation, deliberate combat, monster part damage, and post-hunt progression.

The gameplay philosophy takes inspiration from Monster Hunter:

- attacks carry commitment
- monsters have readable behaviors
- positioning matters
- the player studies the creature rather than button-mashing
- hunts have phases
- targeted body parts matter
- preparation gives meaningful advantages

The presentation philosophy takes inspiration from Horizon Zero Dawn:

- minimal HUD
- cinematic world presentation
- contextual information instead of permanent screen clutter
- strong environmental storytelling
- elegant inventory and equipment screens
- readable iconography
- subtle tracking overlays

This is not intended to copy either franchise's characters, creatures, lore, art, interface assets, animations, names, or proprietary content.

---

## 2. Vertical Slice Scope

### Player

One hunter archetype.

Core capabilities:

- walk
- sprint
- camera control
- dodge
- light attack
- heavy attack
- charged attack
- weapon special
- lock-on / target camera
- interact
- heal
- use one utility item

### Weapon

Start with one large melee weapon.

Recommended first weapon: **Hunting Blade**

Characteristics:

- medium-heavy commitment
- clear light/heavy combo routes
- charged finisher
- strong stagger potential
- easy to understand with controller

Do not build multiple weapons until this one feels excellent.

### Monster

One apex creature with:

- 3 locomotion states
- 3 combat phases
- 6–8 attacks
- 2 reposition moves
- 2 interrupt/stagger responses
- 3 breakable body regions
- enraged state
- flee/reposition behavior
- death sequence

### Region

One semi-open hunting region containing:

- spawn camp
- traversal corridor
- tracking zone
- primary combat arena
- secondary combat arena
- monster nest
- scenic vista
- 2 gathering points
- 1 environmental combat opportunity

The world should look much larger than the actual playable footprint.

---

## 3. Core Player Fantasy

> I am not stronger than the monster because of raw stats. I win because I observe, prepare, position, adapt, and execute.

The player should feel:

- cautious before first contact
- curious while tracking
- pressured during combat
- rewarded for understanding patterns
- powerful when executing a learned opening
- relieved after surviving an enraged phase
- satisfied when breaking a monster part

---

## 4. Primary Gameplay Loop

### Macro Loop

Prepare → Enter Region → Track → Discover → Engage → Adapt → Break Parts → Finish Hunt → Collect Rewards → Upgrade

### Vertical Slice Loop

1. Spawn at field camp
2. Select equipment preset
3. Follow physical/environmental clues
4. Locate monster
5. Observe monster behavior
6. Initiate engagement
7. Fight through phase 1
8. Monster retreats
9. Player follows
10. Fight through enraged phase
11. Break key body part
12. Final confrontation at nest
13. Defeat monster
14. Reward summary
15. Return to title / restart

---

## 5. Combat Design Principles

### Commitment

Attacks must have start-up, active, and recovery windows.

The player should not be able to cancel every action instantly.

### Readability

Monster attacks should communicate intent through:

- pose
- animation silhouette
- audio cue
- movement direction
- environmental response

### Positioning

Different monster zones should create different risk/reward profiles.

Example:

- Head: highest damage, highest danger
- Flank: safer, moderate damage
- Tail: breakable, medium danger
- Rear legs: lower damage, good stagger pressure

### Hit Feel

Every successful heavy hit should combine:

- animation impact
- short hit stop
- camera impulse
- sound transient
- particle effect
- monster reaction where appropriate
- damage number only when useful

### Stamina

Stamina powers:

- sprinting
- dodge
- selected weapon actions

Stamina should recover quickly enough to preserve flow, but punish panic rolling.

---

## 6. Monster Fight Structure

### Phase 1 — Territorial

Monster tests the player.

Behavior:

- slower attack cadence
- clear telegraphs
- short combos
- frequent repositioning

Goal: teach the player.

### Phase 2 — Threatened

Triggered around 65% health or after a major stagger.

Behavior:

- new attack added
- longer combo chains
- faster repositioning
- increased pressure

Goal: force adaptation.

### Phase 3 — Enraged

Triggered around 30–35% health or after a key part break.

Behavior:

- unique visual/audio state
- aggression rises
- shorter idle windows
- high-risk signature attack unlocked

Goal: climax.

---

## 7. Tracking System

Tracking should be environmental first and UI-assisted second.

Clues:

- footprints
- damaged vegetation
- claw marks
- feeding remains
- audio calls
- disturbed wildlife

The player can activate a temporary **Hunter Sense** overlay.

Hunter Sense may highlight:

- recent tracks
- climbable paths
- interactable objects
- wounded monster traces

Avoid covering the screen permanently with markers.

---

## 8. Progression

For the first slice, progression is intentionally simple.

Rewards can include:

- monster scale
- fang
- broken horn
- rare core material

Use materials to unlock one visible upgrade after the hunt.

Example:

Hunting Blade I → Hunting Blade II

Stat improvements should be modest. Mastery must matter more than grinding.

---

## 9. Camera

Third-person over-the-shoulder exploration camera.

During combat:

- slightly widened FOV
- camera pulls back for large attacks
- soft lock-on optional
- camera should prioritize monster readability

Never let the monster disappear behind the player for long periods.

---

## 10. UI Philosophy

Default state should show as little UI as possible.

During exploration:

- compass only when useful
- subtle health display
- contextual interactions

During combat:

- health
- stamina
- selected consumable
- monster status only after combat begins

Avoid a screen full of MMO-style cooldowns, quest markers, and numbers.

---

## 11. Success Criteria

The slice succeeds if a new player can:

- understand controls within 2 minutes
- identify at least 3 monster attacks by animation alone
- feel the difference between careless and deliberate attacks
- use dodge intentionally rather than spam it
- break one body part
- complete the hunt in under 30 minutes
- describe the world as larger than the playable area actually is

---

## 12. Explicit Non-Goals

Do not build initially:

- multiplayer
- online services
- large open world
- procedural maps
- 10+ monsters
- character creator
- mount system
- deep crafting tree
- housing
- NPC towns
- dialogue trees
- live service systems
- PvP

First prove the hunt.
