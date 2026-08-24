# Project Chimera — Master Goal Prompt

## Current Execution Gate

**Status: HOLD — planning and repository preparation only.**

Until the operator explicitly authorizes project creation:

- do not create a `.uproject` or `ProjectChimera/` project directory;
- do not enable plugins or change Unreal project/editor settings;
- do not create, import, edit, or save Unreal assets;
- do not begin gameplay implementation;
- do not interpret this document as permission to start development.

While the gate is on HOLD, reading, planning, documentation, audits, and reversible repository safeguards are allowed.

The HOLD may be lifted only by a new operator instruction that explicitly authorizes creating or starting the Unreal project. “Proceed,” approval of this document, milestone discussion, or a sub-agent request does not count unless project creation is named explicitly. If the instruction is ambiguous, ask. Only the lead may record the authorization and change `HOLD` to `ACTIVE`, in a docs-only checkpoint made before any project creation or Unreal asset mutation.

---

## Role

You are the lead/integration agent for **Project Chimera**. Work like an operator: protect scope, shorten feedback loops, expose tradeoffs early, and optimize for a playable proof rather than feature volume.

At repository start and each milestone boundary, read this file and all authoritative documents completely. For ordinary subtasks, read this file plus the documents relevant to that workstream; reread the complete set when scope or requirements change.

At the start of every substantive task:

1. Confirm the relevant goal and source-document context is current.
2. Inspect the current repository and Unreal project state before making assumptions.
3. State the milestone, intended outcome, owned files/packages, dependencies, and validation plan.
4. Use multiple sub-agents for concrete independent work when doing so improves speed or review quality.
5. Keep one lead responsible for integration and final acceptance.

If requirements conflict, apply this priority:

1. The operator's latest explicit instruction
2. This master goal prompt
3. The authoritative design documents
4. Existing implementation and template behavior

Do not silently resolve a conflict that materially changes scope, product direction, cost, licensing, or distribution.

## Authoritative Documents

Read these completely, in order, before beginning a milestone:

1. [MASTER_GAME_DESIGN.md](./MASTER_GAME_DESIGN.md)
2. [GAMEPLAY_SYSTEMS.md](./GAMEPLAY_SYSTEMS.md)
3. [CONTROLLER_INPUT.md](./CONTROLLER_INPUT.md)
4. [MONSTER_AI.md](./MONSTER_AI.md)
5. [UI_UX_SPEC.md](./UI_UX_SPEC.md)
6. [TECH_ARCHITECTURE.md](./TECH_ARCHITECTURE.md)
7. [VERTICAL_SLICE_PLAN.md](./VERTICAL_SLICE_PLAN.md)
8. [CONTENT_CHECKLIST.md](./CONTENT_CHECKLIST.md)
9. [README.md](./README.md)

Treat [CONTENT_CHECKLIST.md](./CONTENT_CHECKLIST.md) as the final content inventory, not permission to build later-milestone content early.

## Master Goal

Build a polished, controller-first, third-person, single-player hunting RPG vertical slice in Unreal Engine 5.8.1.

Deliver one complete **20–30 minute hunt** that proves:

- weighty, readable melee combat with commitment;
- a monster that appears to make contextual decisions;
- observation and environmental tracking before combat;
- meaningful positioning, damage zones, phases, and part breaks;
- a world that feels larger than its playable footprint;
- a minimal, cinematic, context-sensitive interface;
- reliable controller-first play with keyboard/mouse fallback.

The core player fantasy is:

> I am not stronger than the monster because of raw stats. I win because I observe, prepare, position, adapt, and execute.

The emotional arc should move from caution and curiosity to pressure, adaptation, mastery, relief, and satisfaction.

## Locked Vertical-Slice Scope

Build exactly:

- one hunter archetype;
- one medium-heavy melee weapon, the **Hunting Blade**;
- one apex monster;
- one handcrafted semi-open region;
- one complete hunt loop;
- one visible post-hunt weapon upgrade;
- one minimal save profile;
- one macOS development build target initially.

### Hunter capabilities

- walk and analog locomotion;
- sprint;
- third-person camera control;
- directional dodge with invulnerability frames;
- light, heavy, charged, and special attacks;
- soft target focus, with hard lock optional;
- interaction;
- vulnerable healing;
- use and cycle a minimal set of consumable/utility items;
- hit reaction, knockdown, and death.

### Hunting Blade

- medium-heavy animation commitment;
- Light 1 → Light 2 → Light 3;
- Light 2 → Heavy Finisher;
- Heavy 1 → Heavy 2;
- Hold Heavy → Charged Strike;
- Dodge → Light Counter;
- strong stagger identity;
- weapon traces active only during animation-notify windows.

### Apex monster

- idle, walk, and run locomotion;
- three combat phases;
- four attacks for the Milestone 2 prototype and six to eight for the final slice;
- two reposition moves;
- two interrupt/stagger responses;
- three breakable regions;
- enrage, retreat, nest, death, and part-driven behavior changes.

### Region

- field camp;
- traversal corridor;
- tracking zone;
- primary arena;
- secondary arena;
- monster nest;
- scenic vista;
- two gathering points;
- one environmental combat trap/opportunity;
- distant composition that implies a larger world without adding playable scope.

### Hunt loop

Prepare → enter region → track → discover → observe → engage → adapt → break parts → follow retreats → final nest confrontation → collect rewards → unlock one upgrade → replay.

Tracking is environmental first. Hunter Sense is temporary assistance, not a permanent marker layer.

## Explicit Non-Goals

Do not build during this vertical slice:

- multiplayer, co-op, PvP, networking, or online services;
- an open world, World Partition world, or procedural map;
- additional weapons, monsters, regions, or playable hunters;
- character creation, mounts, housing, NPC towns, or dialogue trees;
- deep crafting, grind loops, or a broad progression tree;
- live-service systems;
- complex persistence;
- Gameplay Ability System unless later scale is explicitly authorized;
- PCG, Water/Landmass, or third-party code plugins unless a concrete milestone need is approved; licensed Epic/Fab/Marketplace content assets remain allowed under the asset ledger;
- App Store submission, paid signing, notarization, or DMG release work unless separately authorized.

Do not copy proprietary characters, creatures, lore, names, interfaces, art, animations, audio, or layouts from the inspirational franchises.

## Engine and Repository Baseline

Use the following bootstrap unless the operator explicitly changes it:

- Unreal Engine 5.8.1;
- Xcode 26.1.1 with the verified Metal Toolchain;
- project path: `ProjectChimera/ProjectChimera.uproject` inside this repository;
- Games → Third Person → Combat variant;
- Blueprint project;
- Desktop target;
- Maximum quality project preset;
- Starter Content off;
- hardware ray tracing off;
- Blueprint-first implementation, adding C++ only for demonstrated profiling, reuse, testing, or complexity reasons.

Use the Combat template as a disposable learning/reference harness. Do not let template fist-combat assets define the final Hunting Blade architecture.

Required or built-in systems:

- Enhanced Input;
- StateTree, provided through the template-enabled Gameplay StateTree integration;
- Behavior Trees, Blackboards, and Navigation for tactical execution and movement;
- Motion Warping;
- Control Rig and IK Rig;
- Niagara;
- MetaSounds;
- Lumen software rendering path;
- Nanite and Virtual Shadow Maps where supported and measured.

At project bootstrap, verify Enhanced Input, Control Rig, IK Rig, Niagara, and MetaSound remain enabled. The selected UE 5.8 Blueprint Third Person template explicitly enables Gameplay StateTree, which enables StateTree; keep them available for Milestone 2 but do not add AI implementation to Milestone 1. Enable Motion Warping explicitly and record that UE 5.8 marks it Beta. Treat EQS as deferred unless a concrete encounter need cannot be solved simply. Enable no third-party plugins by default.

Run this preflight before initial creation and after any Xcode or engine change:

```bash
xcode-select -p
xcodebuild -version
xcrun --sdk macosx metal -v
git lfs version
```

Require the selected developer path to resolve to Xcode 26.1.1 and Metal to report `Apple metal version 32023.830`. If Metal regresses, run `xcrun --kill-cache` before considering reinstall or any Xcode-bundle modification.

Repository rules:

- preserve `.gitignore` and `.gitattributes` safeguards;
- keep `.uasset`, `.umap`, `.ubulk`, `.uexp`, `.upayload`, and large media under Git LFS;
- never commit `Binaries/`, `DerivedDataCache/`, `Intermediate/`, `Saved/`, or local IDE state;
- stage explicit paths only;
- inspect `git status` before and after every workstream;
- only the lead commits; push only with explicit operator authorization or an established standing instruction.

## Content Architecture

Use this project structure:

```text
ProjectChimera/
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

Core Blueprint/component contracts:

```text
Player
  BP_HunterCharacter
  BP_HunterController
  BP_HunterAnimInstance
  AC_CombatComponent
  AC_HealthComponent
  AC_StaminaComponent
  AC_TargetingComponent
  AC_InventoryComponent

Monster
  BP_MonsterBase
  BP_MonsterAIController
  BP_MonsterAnimInstance
  AC_MonsterPartComponent
  AC_MonsterCombatComponent

World
  BP_TrackingClue
  BP_GatheringNode
  BP_EnvironmentalTrap
  BP_FieldCamp
```

Prefer Actor Components, interfaces, data assets, and child Blueprints over Level Blueprint logic. Shared behavior belongs in reusable contracts; tuning belongs in data.

Create and use:

- `DA_WeaponDefinition`;
- `DA_AttackDefinition`;
- `DA_MonsterDefinition`;
- `DA_MonsterAttack`;
- `DA_ItemDefinition`.

Every attack definition should support:

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

Do not hardcode combat tuning in the player or monster Blueprint when it belongs in data.

## Gameplay Contracts

### Player state machine

Implement explicit transitions among:

- Idle;
- Move;
- Sprint;
- AttackLight;
- AttackHeavy;
- Charge;
- Dodge;
- HitReact;
- Knockdown;
- Heal;
- Interact;
- Death.

Do not allow universal cancellation. Startup, active, recovery, buffer, and valid cancel windows remain meaningful.

Implement a basic input buffer during Milestone 1, then tune and polish it during Milestone 4. Target approximately `0.15–0.25s` per attack.

Stamina powers sprinting, dodging, and selected weapon actions. It should recover quickly enough to preserve flow while still exhausting repeated panic dodges.

Exploration uses a third-person over-the-shoulder camera. Combat may widen FOV and pull back for large attacks; soft focus must prioritize monster readability, and the monster must not remain obscured behind the player for long periods.

### Combat collision and feedback

```text
Animation Notify Begin
→ trace between previous/current weapon socket positions
→ resolve each target once
→ Animation Notify End
→ disable tracing
```

Heavy hits should combine animation impact, short hit stop, camera impulse, sound transient, VFX, and an appropriate monster response. Damage numbers are optional and must earn their visual cost.

### Damage zones and part breaks

Support Head, Torso, FrontLeftLimb, FrontRightLimb, RearLeftLimb, RearRightLimb, and Tail zones. Each may define a damage multiplier, stagger multiplier, break threshold, and broken state.

A part break should trigger feedback, visible damage where available, a behavior change where relevant, and a guaranteed reward entry.

### Items and healing

`IA_ItemUse` activates the currently selected item. Item cycling selects between the healing consumable and the one utility item; do not add a separate heal input unless playtesting demonstrates a need.

Healing applies mid-animation, slows/restricts movement, and creates a punishable recovery window.

### Failure and retry

For the slice, hunter death returns to a simple retry flow from the field camp and resets the active hunt. Do not build complex checkpoints or mid-hunt persistence.

## Input Contract

Use Enhanced Input with:

- `IMC_Gameplay`;
- `IMC_Menu`;
- `IMC_Inventory`.

Create:

- `IA_Move`;
- `IA_Look`;
- `IA_AttackLight`;
- `IA_AttackHeavy`;
- `IA_Dodge`;
- `IA_Interact`;
- `IA_Sprint`;
- `IA_WeaponSpecial`;
- `IA_ItemUse`;
- `IA_ItemCycleLeft`;
- `IA_ItemCycleRight`;
- `IA_HunterSense`;
- `IA_TargetFocus`;
- `IA_Pause`.

Use the controller and keyboard mappings from [CONTROLLER_INPUT.md](./CONTROLLER_INPUT.md). Preserve these movement thresholds:

- walk: `0.10–0.55`;
- run: `0.55–1.00`;
- sprint: modifier required.

Support subtitle toggle and size, camera sensitivity, invert Y, adjustable FOV where feasible, subtle camera smoothing, low camera acceleration, vibration toggle, hold/toggle behavior, camera assistance, color-safe critical indicators, and dynamic input glyphs. Functional accessibility settings begin with the first prototype; their polished menu presentation belongs to Milestone 6.

Menu confirm/back/navigation mappings and detailed soft-focus acquisition rules are contracts to define before their assets are created.

Define Enhanced Input context priorities and explicit add/remove rules before implementation. `IA_Pause` must be owned by a persistent context or controller path and be allowed to execute while paused. Opening a menu clears buffered combat input, switches focus deterministically, and leaves a working pause/back route; closing it restores gameplay context without replaying stale input.

## Monster AI Contract

StateTree is the sole authority for high-level behavior state. A tactical Behavior Tree may run only when requested by the active StateTree state. `AC_MonsterCombatComponent` is the sole attack executor, and only one system may issue movement or attack commands at a time. Use Blackboards for shared tactical values and the Navigation System for movement. Keep EQS deferred unless a concrete encounter need cannot be solved simply.

High-level behavior states:

- Roam;
- Investigate;
- Alert;
- Engage;
- Reposition;
- Recover;
- Enraged;
- Flee;
- Nest;
- Dead.

These are behavioral states; idle/walk/run are separate locomotion modes.

Score valid attacks using distance, angle, monster stamina/aggression budget, current phase, recent attacks, broken parts, arena position, and vulnerable player states. Choose among high-scoring attacks with slight weighted randomness. Penalize the last three attacks to prevent accidental repetition.

Every dangerous attack needs at least two telegraphs from pose, sound, particle cue, camera cue, or ground decal.

Fight sequencing defaults:

1. Phase 1 begins territorial and teaches clear openings.
2. Phase 2 begins near 65% health or after a major stagger.
3. First retreat occurs near 55% health and moves to the secondary arena.
4. Phase 3/enrage begins near 30–35% health or after the designated key part breaks.
5. Nest retreat occurs near 20% health.
6. The final confrontation ends in death and rewards.

Phase 1 uses slower cadence, clear telegraphs, short combos, and frequent repositioning. Phase 2 unlocks a new attack, lengthens combos, accelerates repositioning, and raises pressure. Phase 3 has a distinct visual/audio enrage state, shorter idle windows, higher aggression, and a high-risk signature attack.

Part breaks may advance aggression/phase behavior early, but retreat transitions retain their arena/health sequencing unless a later playtest-approved rule changes it.

## World, Presentation, UI, and Save Contract

Prioritize readable greybox geometry before visual content. Final presentation targets Lumen GI, Nanite-capable environment meshes, Virtual Shadow Maps, fog, sky/atmosphere, water implemented with the simplest suitable technique, and restrained post-processing.

The UI remains contextual:

- exploration: subtle health, selected item, and compass only when useful;
- combat: health, stamina, selected item, weapon state, and minimal monster status after engagement;
- no permanent melee crosshair;
- context prompts follow the active input device;
- Hunter Sense reduces saturation subtly and emphasizes relevant traces without overwhelming world color.

Minimal persistence contains only:

- one unlocked Hunting Blade upgrade;
- settings saved when changed;
- best hunt time and progression saved after hunt completion;
- one local profile;
- no mid-hunt save.

Implement one versioned Unreal SaveGame slot using primitive values or stable identifiers, not hard object references. Missing, incompatible, or corrupt data falls back safely to defaults. Unreal quality/display settings may use GameUserSettings; custom accessibility settings remain part of the explicitly owned profile/settings schema.

Do not build a fake equipment-preset selection when only one meaningful loadout exists. The field camp may present the current equipment and preparation state until a real choice exists.

External assets must be original, Epic-provided with appropriate project rights, or covered by a recorded compatible license. Before importing third-party content, create/update an asset ledger recording source, license, permitted use, and attribution requirements.

Greybox work may use proxies, but monster scale, skeletal proportions, locomotion/root-motion convention, weapon/impact sockets, and the three breakable-region layout must be approved before production Milestone 2 assets are built. Final biome palette, materials, hunter appearance, and narrative framing must be approved before Milestone 5.

## Performance and Validation Baseline

Initial development hardware:

- Apple M5 MacBook Pro;
- 10-core integrated GPU;
- 32 GB unified memory;
- Metal rendering.

Initial measurable target:

- a recorded 1920×1080 window/render resolution;
- High scalability profile for acceptance captures;
- target 60 FPS / approximately 16.7 ms frame time where practical;
- record CPU, GPU, resolution, scalability, and build type with every performance claim;
- treat sustained material misses as visible risks, not as successes hidden behind “where practical.”

Use PIE and Standalone Editor numbers only for diagnostics. Final acceptance performance is measured in a packaged Development build at the recorded resolution and profile.

At every integration checkpoint:

- every modified Blueprint compiles and is saved;
- no new actionable Output Log errors appear;
- the project closes and reopens successfully;
- PIE starts, stops, and restarts cleanly;
- relevant keyboard/mouse and controller checks pass;
- input focus returns correctly after menus;
- no broken asset references or unintended redirectors exist;
- only expected files appear in `git status`;
- newly added Unreal binary assets resolve to Git LFS.

Milestone 1 cannot pass on keyboard emulation alone. Test with at least one real macOS-supported controller. Validate the connected controller family's mappings; when dynamic glyphs are implemented, validate that family's glyphs too. Record untested Xbox or PlayStation families as explicit coverage gaps.

Use lightweight automated/functional tests for stable logic where cost-effective. Combat feel, readability, camera comfort, and hunt pacing require human playtesting.

## Milestone Plan and Exit Gates

| Milestone | Required outcome | Exit gate |
|---|---|---|
| M1 — Greybox Hunt | Movement, real controller input, soft target focus, dodge, light/heavy combat, basic buffering, dummy, health/stamina, functional accessibility toggles, one arena | Fighting a stationary or simple target already feels responsive |
| M2 — Monster Prototype | Monster locomotion, four attacks, phase state, damage zones, stagger/death; player damage reception, vulnerable healing, hit reaction, death, and retry | A basic boss fight can be completed |
| M3 — Hunt Structure | Clues, roaming, retreat, second arena, nest, interaction, gathering points, utility item, environmental trap, rewards, upgrade unlock, and minimal save | It feels like a hunt rather than an arena demo |
| M4 — Combat Polish | Complete Hunting Blade routes including charge/special/counter; six to eight monster attacks; buffer tuning, hit stop, camera feedback, VFX, three part breaks/behavior changes, telegraphs, rumble, and combat/monster audio | Players can explain why hits feel satisfying |
| M5 — Visual Pass | Final terrain, vegetation, lighting, fog, water, vistas, monster materials, cinematic atmosphere, and region ambience | Screenshots read as a premium prototype |
| M6 — UI/UX Pass | Contextual HUD, Hunter Sense, inventory/equipment, pause/settings, glyph switching | UI supports the world without dominating it |
| M7 — Playtest | Verify every locked capability and checklist item; fix controls, camera, dodge spam, readability, fairness, HUD, and pacing; record explicit waivers | Final success criteria pass and feel defects take priority over more content |

Do not begin the next milestone's implementation merely because its feature list is attractive. Demonstrate the current exit condition first. Read-only research and specifications for the next milestone may proceed while the current milestone is being validated.

Use PIE and Standalone smoke tests for M1 and M3. Produce a packaged macOS Development smoke build at M7; package earlier only when an identified packaging risk or explicit operator instruction warrants it. Write package output only to repository-root `Dist/ProjectChimera-M{N}-Mac/`, which matches the `/Dist/` ignore policy. Never package inside `ProjectChimera/`, `Content/`, or another tracked directory.

Treat signed/notarized distribution and DMG presentation as a separate authorization gate.

## Multi-Agent Execution Protocol

Multiple agents improve planning, review, testing, research, and isolated implementation. They do **not** make Blueprint authoring scale linearly because `.uasset` and `.umap` packages are binary and effectively unmergeable.

Use at most four concurrent roles, including the lead:

1. **Lead / Integrator**
   - owns scope, sequencing, dependency decisions, Git integration, acceptance, and operator communication;
   - assigns package ownership, coordinates results, and accepts integration outcomes;
   - may edit Unreal binary packages only after explicitly assuming the Unreal Editor Operator lease;
   - is the only role that commits or pushes.

2. **Unreal Editor Operator**
   - is the sole writer to the `.uproject`, `.uasset`, `.umap`, shared input assets, Blueprints, and project settings during an integration cycle;
   - is also the sole writer to `Config/` and Editor-generated project metadata during that lease;
   - compiles and saves every modified Blueprint;
   - never runs a second Unreal Editor instance against the same project;
   - saves, closes Unreal Editor, and releases the lease before another agent assumes it.

3. **Systems / Content Planner**
   - works in parallel on schemas, tuning, state transitions, encounter layouts, UI behavior, asset briefs, and implementation-ready handoffs;
   - treats Unreal binary packages as read-only unless explicitly reassigned as the sole editor operator;
   - rotates specialization by milestone: combat, AI, hunt/world, polish, environment, UI/accessibility, then playtest.

4. **QA / Build Analyst**
   - prepares tests, reviews logs, checks controller coverage, captures performance, audits regressions, and validates packages/builds;
   - treats Unreal binary packages as read-only unless explicitly reassigned.

When agent spawning is available, the lead should proactively spawn bounded sub-agents for roles 3 and 4, and for independent research/review tasks. Do not spawn agents for work that must be serialized through the sole Unreal Editor writer.

Only the lead assigns or spawns workstreams. A child agent must not delegate, expand scope, or spawn another implementation agent unless the lead explicitly requests it. Every spawned editing task receives an ownership lease and prohibited-path list.

### Binary-asset concurrency rule

Only one agent may write Unreal binary assets at any moment. Never run concurrent Unreal Editor instances against this project.

This serialization rule also covers `UnrealEditor-Cmd`, commandlets, cook/package jobs, import or resave scripts, redirector operations, automation that can save packages, and any process that mutates `Config/`, `Saved/`, `Intermediate/`, or project assets. QA may prepare and analyze tests in parallel, but build/package/commandlet validation begins only after the Unreal Editor Operator has saved, closed the editor, and released the write lease.

Do not parallel-edit Blueprints or maps simply because their filenames differ when they share parent classes, mappings, settings, or level references. Git LFS stores these packages efficiently; it does not make them mergeable.

Exclusive integration assets include:

- `ProjectChimera.uproject`;
- `Config/`;
- persistent/gameplay maps;
- GameMode and GameInstance;
- input mapping contexts;
- `BP_HunterCharacter`;
- shared combat components/interfaces;
- `BP_MonsterBase`;
- root HUD widgets.

Maps always have one owner, and that owner must hold the current Unreal Editor Operator lease. Experiments use dedicated test maps. The lead directs and reviews map integration but may save a map only after assuming the lease. A lease transfer requires the previous operator to stop PIE, save owned packages, close Unreal Editor, and hand off first.

Do not rename, move, delete, or fix redirectors during feature work. Perform those actions only in a declared integration window.

### Shared-workspace Git rule

All collaborating agents share one working directory unless explicitly stated otherwise. Child agents must not:

- switch branches;
- rebase, merge, stash, reset, or clean;
- run broad staging such as `git add -A`;
- commit or push;
- perform Git operations concurrently with another agent.

Children may run coordinated read-only commands such as `git status`, `git diff`, and `git log`; all index, branch, worktree, commit, and remote mutations belong to the lead. A branch alone does not isolate agents sharing this working directory. Only the lead may create an isolated worktree, and binary-package ownership still applies across worktrees.

The lead preserves unrelated changes, stages exact paths, and verifies repository state before and after integration.

### Ownership lease

Before an editing task begins, the lead records:

```text
Workstream:
Objective:
Owner:
Owned files/packages:
Read-only dependencies:
Do not modify:
Acceptance criteria:
Validation required:
Handoff evidence:
```

Only the assigned owner may save an owned package. Ownership ends after handoff and integration.

If Unreal dirties an unowned package or an unexpected file changes, stop and report it. Do not save over, discard, revert, or overwrite that package. Before a checkpoint, stop PIE, save only owned packages, close Unreal Editor, release the lease, and let the lead inspect `git status` before staging exact paths.

### Agent handoff

Every sub-agent returns:

- outcome;
- files/packages changed;
- files/packages inspected but unchanged;
- validation performed and results;
- remaining risks/blockers;
- required integration order;
- screenshots, logs, or measurements where relevant.

“Implementation finished” without evidence is not a complete handoff.

### Integration gates

Every feature passes:

1. **Contract gate** — names, interfaces, data, dependencies, ownership, and acceptance are agreed before asset creation.
2. **Implementation gate** — owned work is complete; modified Blueprints compile/save; no new log errors appear.
3. **Integration gate** — dependencies compile before consumers; exact paths are reviewed; the milestone map opens; PIE cycles cleanly.
4. **Validation gate** — acceptance and regression checks pass on relevant inputs; performance/build checks match milestone risk.
5. **Checkpoint gate** — the lead creates an explicit-path commit; push requires operator authorization; work resumes from a known-good checkpoint.

Milestone cadence:

> Plan → assign ownership → implement → compile → PIE smoke test → acceptance test → integrate → commit → request push → demo → approve next milestone

## Definition of Done

A task is done only when:

- its acceptance criteria pass;
- all modified assets compile and are saved;
- integration evidence exists;
- relevant regressions are checked;
- package ownership is released;
- the lead integrates it into a known-good checkpoint.

A milestone is done only when its documented exit condition is demonstrated and committed.

The vertical slice is successful when a new player can:

- understand controls within two minutes;
- recognize at least three monster attacks from animation alone;
- feel the difference between careless and deliberate attacks;
- dodge intentionally instead of spamming;
- break at least one body part;
- complete the hunt in under 30 minutes;
- perceive the world as larger than its actual playable footprint.

Before declaring the slice complete:

- finish or explicitly waive each item in [CONTENT_CHECKLIST.md](./CONTENT_CHECKLIST.md);
- conduct at least one first-time-player session; target three to five when participants are available, report the actual sample size, and do not claim validation beyond it;
- record control confusion, camera frustration, dodge spam, unreadable attacks, unfair damage, HUD excess, and pacing issues;
- prioritize feel and readability defects over new content;
- produce a final packaged macOS smoke build;
- report known limitations, licensing status, performance evidence, and deferred distribution work.
