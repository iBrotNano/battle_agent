# Requirements - Issue #36: Core Beat 'em Up Movement and Combat

| Field | Value |
|---|---|
| Issue | #36 |
| Epic | #35 - Cyberpunk beat 'em up prototype with endless run-based progression |
| Status | Final draft for review |
| Date | 2026-11-26 |
| Owner | Marcel Melzig |
| Scope type | Foundation / playable combat slice |

## 1. Business Goal

Deliver the testable foundation of the game: a player can move through a scrolling street in the classic beat 'em up manner and fight hand-to-hand with a moveset that already feels responsive, readable and impactful. This issue proves the core combat feel before enemy variety, progression, loot, level generation and final presentation are added.

Success means a player can walk the street, attack, block, dodge, grab, throw, deal and receive damage, and clearly feel that combat responds immediately and reads well, using placeholder visuals.

## 2. Stakeholders

| Stakeholder | Interest |
|---|---|
| Project owner (Marcel Melzig) | Defines scope, accepts the result, decides whether development continues. |
| Player / playtester | Plays the foundation build and judges whether movement and combat feel good. |
| Game design and balancing | Tunes timings, damage, guard break and feedback; owns parameter values. |
| Downstream issue owners (#37 to #45) | Build enemy variety, bosses, progression, loot, level generation, UI and presentation on top of these mechanics. |
| Art and audio (#44) | Replaces placeholder visuals and sounds later. |

## 3. Scope / Out of Scope

### In Scope

- A scrolling test street with a defined beginning and end and placeholder visuals.
- Lane-based movement left and right plus into and out of the screen within a limited walkable depth band, with a following camera.
- Facing toward movement or the nearest opponent.
- A three-hit basic attack chain with a stronger knockdown finisher.
- A separate heavy attack with no resource cost and longer recovery.
- Front-facing block with reduced damage, chip damage from heavy attacks and guard break.
- Directional dodge with brief invulnerability and no cooldown.
- Grab and throw of any adjacent opponent.
- Hit reactions: flinch, knockback and knockdown for player and opponents.
- Health, damage and defeat; player defeat leads to a quick restart of the test street.
- Impact feedback through hit-stop and a small screen shake.
- At least one placeholder opponent that can take damage, be grabbed and thrown, and damage the player.
- Keyboard and gamepad support with default bindings.

### Out of Scope

- Jumping, aerial combat, platforms or any vertical platforming.
- Enemy variety and full enemy behavior (owned by #37).
- Boss encounters (owned by #39).
- XP, levels, stats and enemy scaling (owned by #40).
- Loot, implants and inventory (owned by #41).
- Procedural level generation (owned by #38).
- Run lifecycle, death reset, high score and persistence (owned by #42).
- Main menu, HUD, pause, settings, control remapping and run summary (owned by #43).
- Final art, animation, audio and music (owned by #44).
- Balancing and full playtest validation (owned by #45).
- Multiplayer, narrative, localization, saving and online features.

## 4. Functional Requirements

| ID | Requirement |
|---|---|
| FR-36-01 | The player shall move left and right and into and out of the screen within a limited walkable depth band. The player shall not leave the walkable band. |
| FR-36-02 | The camera shall follow the player along the scrolling street. The street shall have a defined beginning and end that constrain movement and camera travel. |
| FR-36-03 | The player shall face the direction of movement or the nearest opponent. Attacks shall affect only the side the player faces. |
| FR-36-04 | The player shall execute a three-hit basic attack chain on repeated attack input. The third hit shall be stronger than the first two and shall be able to knock an opponent down. |
| FR-36-05 | The player shall have a separate heavy attack. It shall not consume a resource and shall have a longer recovery than any basic chain hit. |
| FR-36-06 | The player shall block attacks from the front. Blocking shall reduce most incoming damage. Heavy attacks shall cause chip damage through the block, and sustained blocking shall be guard-breakable. |
| FR-36-07 | The player shall perform a directional dodge with brief invulnerability. The dodge shall have no cooldown. |
| FR-36-08 | The player shall grab any adjacent opponent. A grabbed opponent shall be restrained until thrown or until the player is interrupted. The player shall throw the grabbed opponent, knocking it down. Grabbed opponents shall not free themselves. |
| FR-36-09 | Player and opponents shall react to hits with flinch, knockback and, where the attack warrants it, knockdown. A knocked-down character shall recover after a short time. |
| FR-36-10 | Player and opponents shall have health and shall deal damage. Reaching zero health shall defeat the character. On player defeat, a clear defeated state shall be shown and the player shall restart the test street quickly with restored health and reset position. |
| FR-36-11 | Every successful hit shall produce hit-stop and a small screen shake. Feedback shall distinguish normal hits, heavy hits and knockdowns. |
| FR-36-12 | The test street shall contain at least one placeholder opponent that can take damage, be grabbed and thrown, and damage the player. Minimal behavior is sufficient in this issue. |
| FR-36-13 | All combat actions shall be performable with keyboard and gamepad using default bindings. Remapping is not part of this issue. |
| FR-36-14 | The player and opponents shall remain within the street boundaries and shall not leave the playable area. |
| FR-36-15 | The test street shall allow repeated combat testing without reloading or leaving the build, including recovery after player defeat. |

## 5. Non-Functional Requirements

| ID | Requirement |
|---|---|
| NFR-36-01 | Combat shall respond immediately to input, with no perceptible delay between command and action. |
| NFR-36-02 | With placeholder visuals, all combat states shall remain distinguishable by pose and animation alone: blocking, dodging, stunned, knocked down and defeated. Color alone shall not carry meaning. |
| NFR-36-03 | A ten-minute combat session with repeated movement, attacks, blocks, dodges, grabs and hits shall run without crashes or blocking defects. |
| NFR-36-04 | Combat shall run at a smooth frame rate on a typical Windows desktop without stutter during multi-hit exchanges. The exact numeric target is left to validation. |
| NFR-36-05 | The foundation build shall run on Windows desktop and support both keyboard and gamepad. |
| NFR-36-06 | Any visible placeholder text shall be in English. Final audio and music are not required in this issue. |
| NFR-36-07 | The build shall be fully offline and shall collect no personal data. |
| NFR-36-08 | Combat timings, damage, guard break and dodge behavior shall remain adjustable without redesign, so that #45 can tune them. |

## 6. User Stories

### US-36-01 - Move through the street

As a player, I want to walk left, right, toward and away from the camera within a bounded street so that I can approach and evade opponents like in a classic arcade beat 'em up.

### US-36-02 - Fight hand-to-hand

As a player, I want a fast three-hit combo, a heavy blow, a block and a dodge so that I can express skill and feel powerful in close combat.

### US-36-03 - Grab and throw

As a player, I want to grab an opponent and throw them so that I can control the crowd and create space.

### US-36-04 - Impact and defeat

As a player, I want hits to feel impactful and defeat to be clear, with a quick restart, so that I can keep testing and improving.

## 7. Acceptance Criteria

- [ ] AC-36-01: Given the player is on the test street, when moving left, right, into and out of the screen, then the player stays within the walkable band, the camera follows along the street, and movement stops at the street ends.
- [ ] AC-36-02: Given the player attacks repeatedly, when the chain executes, then three hits occur in sequence and the third hit is stronger and can knock an opponent down.
- [ ] AC-36-03: Given an opponent is adjacent, when the player grabs, then the opponent is restrained until thrown or until the player is interrupted; when thrown, the opponent is knocked down.
- [ ] AC-36-04: Given the player blocks a frontal attack, when it lands, then damage is reduced; heavy attacks cause chip damage; sustained blocking can be guard-broken.
- [ ] AC-36-05: Given the player dodges, when an attack would connect during the dodge, then no damage is taken; the dodge can be repeated without waiting for a cooldown.
- [ ] AC-36-06: Given a hit lands, when impact occurs, then the target flinches or is knocked back; heavy hits and the chain finisher can knock the target down, and knocked-down characters recover after a short time.
- [ ] AC-36-07: Given player health reaches zero, when defeat occurs, then a defeated state is shown and the player can quickly restart the test street with restored health and reset position.
- [ ] AC-36-08: Given the player uses the heavy attack, when it executes, then it costs no resource and has a longer recovery than any basic chain hit.
- [ ] AC-36-09: Given the player moves or an opponent is nearby, when the player acts, then the player faces the relevant direction and attacks affect only that side.
- [ ] AC-36-10: Given a hit lands, when the hit connects, then hit-stop and a small screen shake occur, and normal hits, heavy hits and knockdowns are distinguishable.
- [ ] AC-36-11: Given the test street, when the player engages, then at least one placeholder opponent can take damage, be grabbed and thrown, and damage the player.
- [ ] AC-36-12: Given keyboard or gamepad, when the player plays, then all combat actions are performable with default bindings.
- [ ] AC-36-13: Given a ten-minute combat session, when played repeatedly, then no crash or blocking defect occurs and controls remain responsive.
- [ ] AC-36-14: Given placeholder visuals, when a character blocks, dodges, is stunned, is knocked down or is defeated, then the state is recognizable from pose or animation alone.

## 8. Constraints

| ID | Constraint |
|---|---|
| C-36-01 | No jumping, aerial attacks or platforming are part of this issue. |
| C-36-02 | Single player, offline, Windows desktop; keyboard and gamepad. |
| C-36-03 | Placeholder visuals only; no final art, animation, audio or music. |
| C-36-04 | Exactly one scrolling test street is sufficient; no procedural generation. |
| C-36-05 | Only minimal placeholder opponent behavior is allowed; full enemy behavior belongs to #37. |
| C-36-06 | No progression, loot, boss, UI shell or persistence in this issue. |
| C-36-07 | Combat values are provisional and shall be tuned later in #45. |
| C-36-08 | Technical implementation deliberately left open. |

## 9. Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Combat feel cannot be judged with placeholder visuals. | The foundation may look technically correct but feel wrong. | Conduct an early playtest with placeholders; treat feel as the primary acceptance signal. |
| A dodge without cooldown may allow permanent evasion. | Combat could become trivial or degenerate. | Keep dodge timing as a tuning parameter; validate in #45; revisit the rule if it breaks combat. |
| Guard break and chip damage may frustrate players if mistuned. | Blocking may feel unusable or too strong. | Treat values as provisional; tune in #45; verify in playtests. |
| Grabbing all enemies, including heavy robots, may look or feel implausible. | Visual and gameplay dissonance. | Revisit enemy-specific grab rules in #37 while keeping the current foundation requirement. |
| The placeholder opponent may expand into full enemy AI. | Scope creep delays the foundation. | Keep behavior minimal and hand enemy roster work to #37. |
| Street and lane boundaries may have edge cases. | Player or opponents can leave the playable area. | Explicit boundary acceptance criterion; test at both street ends and both depth edges. |
| Responsiveness is subjective. | Acceptance may be disputed. | Validate through playtest in this issue and formalize criteria in #45. |
| Scope creep into HUD, settings or progression. | Foundation delivery slips. | Out-of-scope list is binding; those items belong to #40, #42 and #43. |
| Numeric tuning may conflict with later scaling. | Rework in progression. | Keep all values adjustable and documented as provisional. |

## 10. Traceability Matrix

| Source | Requirement(s) | Acceptance Criterion |
|---|---|---|
| Issue #36 AC 1 - movement and camera | FR-36-01, FR-36-02, FR-36-14 | AC-36-01 |
| Issue #36 AC 2 - attack chain | FR-36-04 | AC-36-02 |
| Issue #36 AC 3 - grab and throw | FR-36-08 | AC-36-03 |
| Issue #36 AC 4 - block | FR-36-06 | AC-36-04 |
| Issue #36 AC 5 - dodge | FR-36-07 | AC-36-05 |
| Issue #36 AC 6 - hit reactions | FR-36-09 | AC-36-06 |
| Issue #36 AC 7 - health and defeat | FR-36-10 | AC-36-07 |
| Interview - heavy attack | FR-36-05 | AC-36-08 |
| Interview - facing | FR-36-03 | AC-36-09 |
| Interview - hit feedback | FR-36-11 | AC-36-10 |
| Issue #36 scope - test opponent | FR-36-12 | AC-36-11 |
| Issue #36 scope - controls | FR-36-13 | AC-36-12 |
| NFR-36-01 and NFR-36-03 - responsiveness and stability | NFR-36-01, NFR-36-03 | AC-36-13 |
| NFR-36-02 - state readability | NFR-36-02 | AC-36-14 |
| Issue #36 scope - repeat testing | FR-36-15 | AC-36-07 |
| Constraints C-36-01 to C-36-08 | Scope boundaries | Verified by review |
