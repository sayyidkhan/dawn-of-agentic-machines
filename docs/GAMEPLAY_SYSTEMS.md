# GAMEPLAY SYSTEMS

## Player State Machine

States:

- Idle
- Move
- Sprint
- AttackLight
- AttackHeavy
- Charge
- Dodge
- HitReact
- Knockdown
- Heal
- Interact
- Death

Transitions must be explicit.

Do not allow free cancellation between all states.

## Combat Timing

Every attack data asset should define:

- startup duration
- active frame duration
- recovery duration
- stamina cost
- damage
- poise damage
- movement distance
- cancel window
- camera impulse strength

## Suggested Combo

Light 1 → Light 2 → Light 3

Light 2 → Heavy Finisher

Heavy 1 → Heavy 2

Hold Heavy → Charged Strike

Dodge → Light Counter

## Dodge

Dodge should include:

- directional movement
- configurable invulnerability window
- stamina cost
- recovery period

Recommended feel target:

- responsive enough to trust
- not so generous that timing becomes irrelevant

## Lock-On

Two modes:

1. Free camera
2. Soft target focus

Hard lock should be optional because very large monsters can make strict lock-on uncomfortable.

## Damage Zones

Monster body regions:

- Head
- Torso
- FrontLeftLimb
- FrontRightLimb
- RearLeftLimb
- RearRightLimb
- Tail

Each region can have:

- damage multiplier
- stagger multiplier
- break threshold
- broken state

## Part Breaks

On threshold:

1. trigger hit stop
2. play break VFX
3. play break audio
4. switch mesh/material/geometry if available
5. update monster behavior where relevant
6. add guaranteed reward entry

## Healing

Healing should create vulnerability.

Flow:

Press heal → animation starts → movement slows → heal applies mid-animation → recovery

This creates a tactical decision rather than a free reset.

## Environmental Interaction

For the first region include one combat interaction.

Example:

Hanging rock formation can be dropped on the monster after baiting it into position.

This creates memorable emergent-feeling gameplay without requiring systemic open-world simulation.
