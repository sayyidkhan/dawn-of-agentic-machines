# CONTROLLER INPUT SPEC

Controller-first design using Unreal Engine Enhanced Input.

## Core Mapping

| Action | Xbox | PlayStation | Keyboard Fallback |
|---|---|---|---|
| Move | Left Stick | Left Stick | WASD |
| Camera | Right Stick | Right Stick | Mouse |
| Light Attack | X | Square | Left Mouse |
| Heavy Attack | Y | Triangle | Right Mouse |
| Dodge | A | Cross | Space |
| Interact | B | Circle | E |
| Sprint | LB | L1 | Left Shift |
| Weapon Special | RB | R1 | Q |
| Item Use | D-Pad Up | D-Pad Up | R |
| Item Cycle | D-Pad Left/Right | D-Pad Left/Right | Mouse Wheel |
| Hunter Sense | LT | L2 | Ctrl |
| Lock / Focus | Right Stick Click | R3 | Middle Mouse |
| Pause | Menu | Options | Esc |

## Unreal Input Actions

Create:

- IA_Move
- IA_Look
- IA_AttackLight
- IA_AttackHeavy
- IA_Dodge
- IA_Interact
- IA_Sprint
- IA_WeaponSpecial
- IA_ItemUse
- IA_ItemCycleLeft
- IA_ItemCycleRight
- IA_HunterSense
- IA_TargetFocus
- IA_Pause

Create input mapping contexts:

- IMC_Gameplay
- IMC_Menu
- IMC_Inventory

## Input Rules

Input must be buffered for combat.

Recommended buffer window:

0.15–0.25 seconds depending on attack.

Example:

Player presses Light Attack during recovery → store request → execute when valid cancel window opens.

This creates responsiveness without removing animation commitment.

## Analog Movement

Use analog magnitude for locomotion speed.

Walk zone: 0.1–0.55

Run zone: 0.55–1.0

Sprint requires sprint modifier.

## Camera Settings

Recommended baseline:

- horizontal sensitivity: adjustable
- vertical sensitivity: adjustable
- invert Y: optional
- aim acceleration: low
- camera smoothing: subtle
- FOV: adjustable where feasible

## Rumble

Use controller vibration for:

- heavy attack impact
- player receiving damage
- monster roar
- part break
- monster landing nearby

Avoid continuous excessive rumble.
