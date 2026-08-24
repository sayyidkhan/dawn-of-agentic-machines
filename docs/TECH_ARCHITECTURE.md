# TECH ARCHITECTURE — UNREAL ENGINE 5

## Recommended Project Structure

```text
Content/
  Characters/
    Player/
    Monsters/
  Combat/
    Animations/
    Data/
    Effects/
  Input/
  UI/
  World/
    Region01/
  Items/
  Audio/
  Materials/
  VFX/
  Blueprints/
  DataAssets/
```

## Core Classes

### Player

- BP_HunterCharacter
- BP_HunterController
- BP_HunterAnimInstance

### Combat

- AC_CombatComponent
- AC_HealthComponent
- AC_StaminaComponent
- AC_TargetingComponent
- AC_InventoryComponent

### Monster

- BP_MonsterBase
- BP_MonsterAIController
- BP_MonsterAnimInstance
- AC_MonsterPartComponent
- AC_MonsterCombatComponent

### World

- BP_TrackingClue
- BP_GatheringNode
- BP_EnvironmentalTrap
- BP_FieldCamp

## Data-Driven Design

Avoid hardcoding combat values directly into player blueprints.

Create data assets:

- DA_WeaponDefinition
- DA_AttackDefinition
- DA_MonsterDefinition
- DA_MonsterAttack
- DA_ItemDefinition

## Attack Data

Suggested `DA_AttackDefinition` fields:

```text
AttackName
AnimationMontage
Damage
PoiseDamage
StaminaCost
StartupTime
ActiveTime
RecoveryTime
InputBufferWindow
MovementCurve
HitStopDuration
CameraShake
VFX
SFX
CanChainInto[]
```

## Combat Collision

Prefer weapon traces during active frames rather than permanently active overlap colliders.

Flow:

Animation Notify Start
→ begin weapon trace
→ trace between previous/current weapon socket positions
→ resolve unique target hits
→ Animation Notify End
→ disable trace

## Animation

Use:

- animation montages
- root motion selectively
- motion warping for attacks
- IK for feet
- aim/look offsets for creature awareness

## Save Data

Vertical slice save:

- unlocked upgrade
- settings
- best hunt time

Do not build a complex persistence layer yet.

## Rendering

Target:

- Nanite environment meshes
- Lumen GI
- virtual shadow maps
- high quality fog
- cinematic sky/atmosphere
- restrained post processing

Performance goal:

60 FPS on target development hardware where practical.

Build quality settings early instead of optimizing only at the end.
