# MONSTER AI SPEC

## Design Goal

The monster should appear to make decisions rather than cycle through attacks.

## High-Level States

- Roam
- Investigate
- Alert
- Engage
- Reposition
- Recover
- Enraged
- Flee
- Nest
- Dead

## Decision Inputs

AI evaluates:

- distance to player
- player angle relative to monster
- monster stamina/aggression budget
- current phase
- recent attacks used
- damaged body parts
- arena position
- player healing
- player knocked down

## Attack Selection

Avoid pure random selection.

Each attack receives a contextual score.

Example:

Tail Swipe score increases when player is behind monster.

Charge score increases when player is far away.

Bite Combo score increases when player is directly in front.

Leap Slam score increases in phase 3.

Then choose among top-scoring valid attacks with slight weighted randomness.

## Anti-Repetition

Track last 3 attacks.

Reduce score for recently repeated attacks unless the behavior is intentionally oppressive in an enraged phase.

## Example Attack Set

1. Front Bite
2. Double Claw
3. Tail Sweep
4. Shoulder Bash
5. Forward Charge
6. Leap Slam
7. Roar Shockwave
8. Enraged Ground Burst

## Telegraph Rules

Every dangerous attack needs at least two signals from:

- pose
- sound
- particle cue
- camera cue
- ground decal

Signature attacks should have the clearest telegraphs.

## Retreat Logic

At approximately 55% health:

Monster disengages and travels to secondary arena.

At approximately 20% health:

Monster retreats to nest.

These transitions should feel like creature behavior, not level scripting.

## Part-Driven Behavior

Breaking parts can alter behavior.

Examples:

Broken tail:
- tail sweep range reduced

Broken forelimb:
- charge recovery becomes longer

Broken horn:
- enraged roar loses secondary shockwave

## Implementation Recommendation

Use StateTree for high-level state and Behavior Tree / utility scoring for tactical decisions.

Blackboard-style values:

- TargetActor
- DistanceToTarget
- AngleToTarget
- CurrentPhase
- IsEnraged
- CurrentArena
- LastAttack
- HealthRatio
- BrokenParts
