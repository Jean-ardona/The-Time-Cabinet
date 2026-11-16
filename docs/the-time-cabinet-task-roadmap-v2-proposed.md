# THE TIME CABINET
## Proposed Roadmap V2 — Consolidation Audit

**Proposal date:** 16 November 2026  
**Status:** Draft for user review — **does not replace Roadmap V1**  
**Current branch:** `arena/501d32bc-the-time-cabinet`  
**Current progress:** `TC-001` complete; `TC-002` not started  
**Source backlog:** [`the-time-cabinet-task-roadmap-v1.md`](the-time-cabinet-task-roadmap-v1.md)  
**Product authority:** [`the-time-cabinet-game-bible-v1.md`](the-time-cabinet-game-bible-v1.md)

> This is a proposed execution plan, not authorization to begin work. No application code was changed, no implementation task was started, and Roadmap V1 remains unchanged. The proposal must be approved before it replaces V1 or before `TC-002` begins.

---

## 1. Executive Summary

Roadmap V1 contains 85 useful traceable tasks, but many are sub-steps of the same workflow and currently imply too many separate approval/checkpoint cycles. V2 groups all 85 task IDs into **10 execution batches**. Original IDs remain the acceptance-criteria references; no ID is silently dropped.

The proposed critical path is:

1. Get the official Devvit starter running in a real Reddit post.
2. Establish only the shared contracts and accessible visual shell needed for the game.
3. Author one verified, date-matched event for the live demo.
4. Deliver the full Letter Mixer → server-validated clue → guess → sourced reveal → Redis resume loop in Reddit.
5. Expand that working loop into a frozen multi-clue daily case and create a public demo post.
6. Add the remaining five core puzzles and enough verified content for the intended V1, then run full QA and submit.

**Important distinction:** the first playable gate is a **vertical slice** using Letter Mixer; it is not permission to claim the full six-puzzle V1 is complete. The full V1 scope is retained as important P1 work.

### Proposed execution control

Instead of requesting authorization for every small TC-ID, V2 proposes **one explicit authorization per batch**, with a stop/report at that batch's acceptance gate. Each task ID keeps its individual acceptance criteria and dependencies. This changes the approval cadence only if you approve V2; until then, the existing one-task-at-a-time instruction remains in force.

---

## 2. Priority Rules for V2

### P0 — Mandatory MVP and submission gates

A player must be able to open a native Reddit Interactive Post, solve a complete date-matched daily mystery, receive clues only after server-validated solves, guess without losing progress, see a sourced reveal, and resume safely. The shared case, user-isolated Redis progress, trusted Devvit identity, date rules, public demo post, required links, and final submission checks remain mandatory.

### P1 — Important V1 improvements

Complete the intended six-puzzle library, seven unique verified dossier target, locally bundled/licensed typography, broader polished UI states, scheduled posting (if retained at P1), external playtesting, and visual refinement after the P0 loop is working. These are not allowed to delay the first complete playable Reddit mystery. Any proposed cut below the V1 target must be explicit and approved; it is not silently waived.

### P2 — Optional / post-MVP

Features that can be postponed past hackathon submission without compromising the central mystery loop. They never block the first Reddit build or the required Devpost submission.

---

## 3. The 10 Proposed Execution Batches

### Batch 1 — Account access, Devvit starter, and clean baseline

**Source IDs:** `TC-002–TC-010` (with `TC-001` recorded as the completed prerequisite).  
**Priority:** P0.

**Combine:** Reddit Developer onboarding; public test subreddit; Node/npm/Git checks; official Devvit React app creation; dependency/template inspection; CLI authentication; first starter playtest; Git hygiene; technical constraints and scripts.

**Dependencies:** `TC-001` is complete. Within the batch, `TC-003` follows Reddit Developer access; `TC-005` follows environment setup; `TC-006` and `TC-009` follow project creation; `TC-007` requires Reddit access and the project; `TC-008` requires the public subreddit, installed starter and CLI login; `TC-010` follows template inspection. Environment preparation (`TC-004`) may be done while account onboarding is pending.

**Batch gate:** The official generated Devvit Web starter builds and renders in a real Reddit playtest post on the public test subreddit. The required Node version and actual template scripts/framework are recorded; the repository has a clean baseline and excludes secrets/auth files.

**Acceptance criteria retained:** The subreddit must be public, moderated by the owner, and kept below 200 members/subscribers. Do not substitute a standalone Vite site for the Devvit template. Do not commit CLI credentials or auth files.

---

### Batch 2 — Shared domain contracts and engineering guardrails

**Source IDs:** `TC-011–TC-015`, `TC-026`.  
**Priority:** P0.

**Combine:** Shared event/clue/progress types; validated dossier and puzzle payload contracts; deterministic answer normalization; seeded PRNG; a single test/lint/type-check/build gate; typed puzzle-template registry.

**Dependencies:** Batch 1 (`TC-010`); `TC-012–TC-014` build on `TC-011`; `TC-015` builds on the actual template scripts; `TC-026` builds on the shared types.

**Batch gate:** The same typed definitions are used by client, server, content and generator; invalid dossier/puzzle fixtures fail clearly; normalized aliases behave deterministically; the same date/event/version yields the same seed output; the project has one repeatable test/build path, not overlapping test frameworks.

**Acceptance criteria retained:** Client-safe case data remains separate from server-held answer/alias data. Do not use unseeded randomness for a shared daily puzzle sequence. Preserve tests for answer edge cases and changed/repeated seeds.

---

### Batch 3 — Minimum cosy investigation UI and accessibility

**Source IDs:** `TC-016–TC-025`.  
**Priority mix:** P0 core shell and accessibility; P1 visual expansion and polish.

**P0 slice:** `TC-016`, the minimum reusable subset of `TC-018`, `TC-020–TC-023`, and `TC-025`. Build the tokenized visual base, investigation shell, clue shelf/progress, guess panel, solved dossier, responsive layout, keyboard focus, semantic controls, usable touch targets, reduced-motion behavior, and non-drag alternatives.

**P1 remainder:** `TC-017` bundled fonts/licence records; the fuller shared component set in `TC-018`; a dedicated cover/open-case screen in `TC-019`; and the complete set of loading/empty/offline/error states in `TC-024`. The first playable slice still needs visible loading/submission/error feedback; the P1 designation does not excuse blank or frozen UI.

**Dependencies:** Batch 1 for project files; `TC-018` follows tokens; `TC-020–TC-024` follow the shared shell/components; `TC-021` also uses Batch 2 types.

**Batch gate:** The core investigation can be played in a narrow Reddit mobile webview and on desktop; clue content is not shown before unlock; guesses remain editable after an incorrect answer; the result view shows the sourced historical dossier. No long tutorial or separate polished cover is required before the first loop works.

---

### Batch 4 — Verified demo content and content validation

**Source IDs:** `TC-027`, `TC-041`, `TC-042`, `TC-050`.  
**Priority:** P0.

**Combine:** Apollo 11 as a development/reference fixture; the editorial verification checklist; one actual date-matched playable event; schema/content checks for required fields, sources, clue coverage, puzzle payloads, and leakage.

**Dependencies:** Batch 2 (`TC-012`); `TC-041` precedes the playable dossier; `TC-050` depends on the schema and editorial rules.

**Batch gate:** The Apollo fixture validates for development, and a separate live-demo event has a historical month/day matching the challenge date on its Reddit post. The live event has a sourced short story, canonical answer/curated aliases, at least four viable clue/puzzle pairs, at least three supported clue categories where available, broad-to-decisive clues, and no unsupported claims. The live case must not silently use Apollo 11 on an unrelated daily date.

**Asset rule:** Every asset used by this batch must have provenance before it is bundled. The full inventory audit remains in `TC-049` (Batch 7). The early slice can avoid image assets and use CSS/text controls.

---

### Batch 5 — First full playable Reddit vertical slice

**Source IDs:** `TC-028–TC-034`, `TC-057–TC-058`, `TC-066`.  
**Priority:** P0.

**Combine:** Letter Mixer interaction and server validation; Devvit Redis repository; `/api/init`, solve and guess routes; trusted user identity; answer secrecy and request validation; API/Redis integration tests; full wiring of the investigation loop.

**Dependencies:** Batches 1–4. More specifically, `TC-030` needs Devvit authentication and domain types; `TC-031` needs the validated fixture and repository; `TC-032–TC-033` need the validation and API base; identity/security hardening follows those routes.

**Batch gate (TC-034):** Inside a real Reddit Interactive Post, a player can open the case, solve Letter Mixer, receive exactly one server-approved clue, make a wrong guess without losing/editing progress, later guess correctly and see the sourced dossier, then refresh/reopen and resume. The server—not client state—decides puzzle success and answer correctness. A client-supplied `userId` is never trusted; accepted aliases and locked clues are not leaked before solving.

**Date clarification proposed:** Retain Apollo 11 as the `TC-027` test fixture and validate it in tests. For the live Reddit daily experience, use the `TC-042` event whose month/day matches the displayed challenge date. This resolves the tension between the original `TC-034` Apollo test fixture and the locked daily-date rule without pretending a mismatched date is a valid daily case.

**Early checkpoint:** This is the earliest intended end-to-end product gate. Do not wait for all six puzzles, the full dossier library, a scheduler, or optional effects before reaching it.

---

### Batch 6 — Deterministic multi-clue daily case and public manual demo post

**Source IDs:** `TC-051–TC-055`, `TC-059`, `TC-061`, `TC-063–TC-064`.  
**Priority:** P0.

**Combine:** Compatibility filter; seeded sequence and progression/fallback rules; frozen shared daily case; UTC/leap-day selection; unit tests for domain/answers/generation; moderator manual post action; idempotent creation; public demo-sub/date verification.

**Dependencies:** Batch 2 (`TC-014`, `TC-026`), Batch 4 (`TC-050`), and Batch 5 (`TC-030`, `TC-054` persistence needs). `TC-059` also requires the real starter playtest from Batch 1. `TC-061` follows the manual route. `TC-063` follows the subreddit and manual post.

**Batch gate:** The public demo post opens one frozen event/puzzle sequence shared by all players; the daily ID uses UTC; Feb 29 is explicit; the event date matches the challenge date; sequence choices only use compatible authored options; ordering starts broad and becomes more identifying; repeated templates are avoided when alternatives exist; invalid content is rejected rather than fabricated. Repeated moderator/scheduler requests do not create duplicate posts. The public test post is playable without joining a private subreddit and the subreddit remains below 200 members.

**First-post strategy:** Create the public demo as soon as this gate passes, using the already validated demo event and the currently supported puzzle pool. Before Batch 7 adds variety, reuse a template only where the documented fallback allows it; do not claim six-template variety yet. The full content/variety experience is a later P1 gate.

**Acceptance criteria retained:** No per-user generation of the shared case; no runtime invented fallback clue; exact UTC behavior and explicit leap-day handling; `postData` stays small; manual moderator creation is the reliable fallback.

---

### Batch 7 — Complete core puzzle library and V1 content breadth

**Source IDs:** `TC-035–TC-040`, `TC-043–TC-049`, `TC-056`, `TC-065`.  
**Priority mix:** P1 for additional puzzles/content/integration/tests; P0 for rights and provenance checks in `TC-049` before any corresponding asset ships.

**Combine:** Connections, Cipher Wheel, Who Am I?, Timeline Sort, Pixel Reveal and shared retry/feedback; connecting all core templates to the frozen generator; puzzle tests; completing the Apollo reference dossier and authored event library; final asset/font provenance inventory.

**Dependencies:** Batch 2 registry; Batch 4 editorial checklist/first event; Batch 5 Letter Mixer/API contract; Batch 6 generator/frozen case. `TC-056` must wait for the added puzzle templates and frozen case. `TC-065` tests the complete six-template set.

**Batch gate:** All six core puzzles are complete and server-validated; Timeline Sort has keyboard/tap arrow controls (not drag-only); Who Am I? is solvable from the supplied evidence; Pixel Reveal uses an identifiable, licensed local asset with non-spoiling alt text; all templates work with the clue shelf/guess flow; all six pass correct/incorrect/incomplete/retry/forged-answer tests.

**Content target:** Preserve the Game Bible's target of **at least seven unique complete verified dossiers**, including the actual demo event. Keep the required facts, sources, aliases, minimum clue/puzzle coverage, and calendar-date accuracy. `TC-043–TC-048` are a pool of authored content, not permission to duplicate one event or inflate the count with the same record twice. See the explicit `TC-048` sizing recommendation in Section 5.

**Asset acceptance:** No uncertain images, fonts, or sounds. Record creator, source URL, licence, attribution and local path. Start provenance when each asset is introduced; complete the full audit before release.

---

### Batch 8 — Optional post automation and community-post refinements

**Source IDs:** `TC-060`, `TC-062`.  
**Priority:** P1 in V1; proposed to be treated as non-blocking, with `TC-060` considered for P2 reclassification.

**Combine:** Scheduled daily post creation, using the same idempotent service as the moderator action; concise Reddit fallback post text and a spoiler-safe discussion prompt.

**Dependencies:** Batch 6's date selection/manual post/idempotency work. Keep scheduling disabled until duplicate prevention is verified.

**Batch gate:** If implemented, the scheduled task uses the current documented Devvit Scheduler, UTC date selection, useful logs, and the same creation path as the manual action. The manual moderator route remains usable if scheduling fails. The post explains play in plain language and invites theories without exposing answers.

**Critical-path note:** Neither the scheduler nor extra post-copy polish may delay the first public playable post or the submission. The manual daily-post action is the P0 recovery path.

---

### Batch 9 — End-to-end QA, accessibility, security, playtest and polish

**Source IDs:** `TC-067–TC-074`.  
**Priority mix:** P0 `TC-067–TC-072`; P1 `TC-073–TC-074`.

**Combine:** Full Reddit player-journey tests; two-account fairness/isolation; refresh/resume/duplicate/solved-return tests; mobile/desktop/accessibility QA; historical fact/source QA; performance/failure/security review; small uncoached playtest; final restrained visual polish.

**Dependencies:** Batches 5–8; in particular, `TC-067` needs all six generated templates and the public post, `TC-068` needs trusted identity and the frozen sequence, and `TC-073` follows the critical P0 QA.

**Batch gate:** Two Reddit accounts see the same frozen case but independent progress; refresh, repeated solve/guess, solved return, and reopening after UTC midnight restore safe state; no answer/locked clue leaks; no critical historical or accessibility issue remains; the public Reddit flow succeeds on mobile and desktop; external findings are recorded and critical problems fixed or explicitly documented.

**Continuous-testing rule:** Unit, integration, puzzle, build, lint and type checks run in the batch that introduces the feature. Batch 9 is the integrated release gate, not the first time the project is tested.

---

### Batch 10 — Submission, deadline and judging availability

**Source IDs:** `TC-075–TC-080`.  
**Priority mix:** P0 `TC-075–TC-077`, `TC-079`; P1 `TC-080`; optional video recommendation for `TC-078` is in Section 5.

**Combine:** English root README; stable private Devvit upload and app URL; complete Devpost text and required links; final submission receipt; optional short demo video; maintain the public demo during judging.

**Dependencies:** Batches 6 and 9. Keep the app uploaded/private as the hackathon requests; do not initiate broad App Review publishing unless official rules change or the user explicitly approves it.

**Batch gate:** Devpost confirms receipt before **8 Dec 2026, 6:00 p.m. Pacific / 9 Dec 2026, 04:00 Burundi time**; app listing, public subreddit and direct demo post links are correct; README and Devpost instructions are clear and in English; assets are licensed; the demo remains free and accessible through judging.

**Proposed dependency correction:** `TC-079` must **not** depend on `TC-078` because the video is optional under the official submission rules. Proposed P0 dependency: `TC-063`, `TC-075–TC-077`; include `TC-078` only if voluntarily completed. The 24-hour-early target remains **8 Dec 2026, 04:00 Burundi time**.

---

## 4. Task-ID Crosswalk

Every V1 task remains represented in a proposed batch. The V1 document retains the detailed per-task actions and acceptance criteria until V2 is approved.

| V1 task IDs | Proposed batch | V2 priority treatment |
|---|---:|---|
| `TC-001` | Completed prerequisite | Already `[x]`; no new action proposed. |
| `TC-002`, `TC-003`, `TC-004`, `TC-005`, `TC-006`, `TC-007`, `TC-008`, `TC-009`, `TC-010` | 1 | P0 setup and first real Reddit starter gate. |
| `TC-011`, `TC-012`, `TC-013`, `TC-014`, `TC-015`, `TC-026` | 2 | P0 domain, generator primitive, test gate and template contract. |
| `TC-016`, `TC-017`, `TC-018`, `TC-019`, `TC-020`, `TC-021`, `TC-022`, `TC-023`, `TC-024`, `TC-025` | 3 | P0 minimum game shell/accessibility; P1 font, dedicated cover and fuller state/component polish. |
| `TC-027`, `TC-041`, `TC-042`, `TC-050` | 4 | P0 fixture, editorial rules, one live event and validation. |
| `TC-028`, `TC-029`, `TC-030`, `TC-031`, `TC-032`, `TC-033`, `TC-034`, `TC-057`, `TC-058`, `TC-066` | 5 | P0 first Reddit vertical slice, security and API/Redis integration tests. |
| `TC-051`, `TC-052`, `TC-053`, `TC-054`, `TC-055`, `TC-059`, `TC-061`, `TC-063`, `TC-064` | 6 | P0 daily sequence/date/freeze, manual public post, idempotency, verification and logic tests. |
| `TC-035`, `TC-036`, `TC-037`, `TC-038`, `TC-039`, `TC-040`, `TC-043`, `TC-044`, `TC-045`, `TC-046`, `TC-047`, `TC-048`, `TC-049`, `TC-056`, `TC-065` | 7 | P1 full core library/content; P0 licence/provenance compliance before release. |
| `TC-060`, `TC-062` | 8 | P1 V1 refinements; scheduling is proposed as non-blocking and considered for P2. |
| `TC-067`, `TC-068`, `TC-069`, `TC-070`, `TC-071`, `TC-072`, `TC-073`, `TC-074` | 9 | P0 integrated QA; P1 external testing and finishing polish. |
| `TC-075`, `TC-076`, `TC-077`, `TC-078`, `TC-079`, `TC-080` | 10 | P0 submission; P1 judging availability; optional video not a submission dependency. |
| `TC-081`, `TC-082`, `TC-083`, `TC-084`, `TC-085` | Post-submission backlog | P2; do not start before stable submission. |

---

## 5. Merge, Defer, Reclassify — Explicit Recommendations

### Workflows merged to reduce overhead

1. **Setup:** `TC-002–TC-010` become one setup batch, while retaining the dependency order and the real Reddit starter-post gate (`TC-008`).
2. **Domain and guardrails:** `TC-011–TC-015` plus registry `TC-026` become one technical foundation batch; no separate approval for every type/test script.
3. **UI build:** `TC-016–TC-025` become one UI workflow. MVP essentials are delivered first; fonts, cover polish, and comprehensive states remain visible P1 work.
4. **Content workflow:** `TC-027`, `TC-041`, `TC-042`, and `TC-050` are grouped around one validated live event. Content authoring does not happen before source/editorial rules exist.
5. **First playable loop:** `TC-028–TC-034` are treated as one vertical slice, with identity/security (`TC-057–TC-058`) and API/Redis tests (`TC-066`) inside the same implementation workflow.
6. **Daily case pipeline:** `TC-051–TC-055`, unit tests `TC-064`, and the manual/idempotent/public-post path (`TC-059`, `TC-061`, `TC-063`) become a single daily-case release gate.
7. **Six-puzzle expansion:** `TC-035–TC-040`, `TC-056`, `TC-065` move together, after the first playable slice and generator contract.
8. **Release QA and submission:** QA (`TC-067–TC-074`) and submission (`TC-075–TC-080`) each become one release workflow, with P0 checks clearly separated from optional polish.

### Work explicitly deferred, not deleted

- Dedicated cover polish (`TC-019`), bundled typefaces (`TC-017`), comprehensive secondary loading/empty states (`TC-024`), automated scheduling (`TC-060`), and the other five puzzles are not prerequisites to the first Letter Mixer loop. Complete them in their listed batches before calling the intended V1 done, according to the approved priority.
- Seven dossiers remain the **V1 target**; only one verified, date-matched event is required for the first playable demo gate. Do not author several events before the full Reddit loop works.
- Map Hunt, Cause & Effect, hints, sound and retention features (`TC-081–TC-085`) remain post-MVP P2.
- No Pixel Reveal image, external media, font, or audio should be pulled into the early slice simply for decoration. Use safe CSS/system fallbacks until a licensed asset is ready.

### Priority changes proposed for approval (not silently applied)

1. **`TC-060` scheduled post job:** Recommend P1 → **P2** if a verified manual moderator post action is sufficient for the hackathon demo. Keep the scheduler task and its acceptance criteria; defer it unless daily operations or the judges require automation.
2. **`TC-078` demo video:** Recommend P1 → **P2 / optional** because the official rules make it optional. Keep it on the backlog, but do not let it block `TC-079`.
3. **`TC-048` two additional dossiers:** Keep the task ID but size its work to **top up to seven unique dossiers**, rather than unconditionally authoring two more. If the first daily event, Apollo dossier and four named dossiers are all distinct, one additional dossier reaches seven; the other is optional. This does not reduce the Game Bible's minimum-seven target.
4. **`TC-018`, `TC-024`:** The minimal reusable components and basic loading/pending/error handling required for a safe first playthrough are part of P0; the broader component/state inventory remains P1. No core error handling is removed.
5. **`TC-076` dependency:** Recommend allowing a tested P0 build to be uploaded once P0 release checks pass, without making optional/P1 video or non-critical polish a hard gate. Re-upload/re-smoke-test after any later changes.

### No tasks are removed in this proposal

All `TC-001–TC-085` are mapped. P2 means explicitly deferred until after the mandatory submission path is stable, not erased. Any task that the user ultimately decides to remove should be marked `[-]` in the approved roadmap with a brief rationale.

---

## 6. Audit Findings Requiring a Clear Decision

### A. Seven dossiers vs. every calendar day

The Game Bible requires one event for each UTC daily challenge whose historical month/day matches that challenge date, while the content target says at least seven complete dossiers. Seven events alone do not provide year-round date coverage. V1 does not define how dates with no matching authored event are handled.

**Safe interim behavior:** For the hackathon demo, choose and verify an event matching the displayed demo date; create only posts for dates with a valid matching dossier; never silently reuse a different-date event, shift the date, or invent a fallback. Before implementing `TC-055` as an unrestricted daily service, approve whether the intended release needs year-round date coverage or only the planned hackathon/demo dates. If year-round coverage is required, the content scope must be expanded beyond seven; this proposal does not pretend that it is solved.

### B. Demo date and Apollo fixture

`TC-027` expressly calls Apollo 11 a development fixture, not automatically the current daily event. Keep it for deterministic testing and use `TC-042` for the date-matched live demo. This is an acceptance clarification, not deletion of the Apollo fixture or historical content.

### C. Optional video dependency

`TC-078` is optional but currently appears in `TC-079`'s dependency range. V2 proposes to remove that hard dependency while keeping the task available. Skipping the video must not make a compliant project late or incomplete.

### D. Number of dossiers

The current named content tasks can produce more than seven dossiers, depending on whether the demo event overlaps Apollo 11. Count **unique event records**; avoid a second copy of the same story. The minimum seven is retained; the 10–14 target remains optional.

---

## 7. Locked Requirements Preserved in V2

The following are not cut by consolidation or scope reduction:

- Native Reddit Interactive Post using the generated Devvit Web architecture; no standalone replacement.
- One date-matched historical event for a playable daily case; explicit UTC and leap-day rules.
- A frozen shared sequence per post/day and independent trusted-user Redis progress.
- Server-validated puzzle solves and guesses; no client-supplied identity; no answer/locked-clue leakage.
- Guess after the first clue and after later clues; wrong guesses preserve editable input and progress; correct guess reveals story, facts, sources, clue count and safe share text.
- Letter Mixer vertical slice before implementing the other five core puzzle types.
- At least seven unique verified dossiers for the intended V1 target; all facts sourced and all shipped assets licensed/attributed.
- Public test subreddit with fewer than 200 members, public playable post, app URL, English README/description, and submission before the official deadline.
- Build/type/lint/test gates and real Reddit playtests; no test is reported as passed until actually run.
- Keep authentication tokens, Devvit auth files and passwords out of source, Git and chat.

---

## 8. Proposed Approval Point

Please review this proposal, especially:

1. The proposed **10-batch** execution model and one authorization per batch.
2. The P2 reclassification recommendations for `TC-060` and `TC-078`.
3. The `TC-048` adjustment to author only enough unique dossiers to reach seven.
4. The unresolved year-round calendar coverage requirement.
5. The live-slice date clarification: Apollo 11 remains the test fixture; the actual public demo uses the verified event matching its challenge date.

Until you approve Roadmap V2, **Roadmap V1 remains the active plan, `TC-002` remains not started, and no implementation work should begin.**
