# THE TIME CABINET
## Master Task Roadmap — Version 1.0

**Document date:** 16 November 2026  
**Project:** The Time Cabinet  
**Platform:** Reddit / Devvit Web / Interactive Posts  
**Base specification:** `the-time-cabinet-game-bible-v1.md`  
**Purpose:** A complete, ordered backlog that can be executed **one task at a time**.  
**Status:** In execution — task completion tracked in Section 2 (`TC-001` complete).

---

# 0. How to use this roadmap

This file is the execution plan. The Game Bible defines **what the game is**; this roadmap defines **what must be built and in what order**.

## 0.1 The one-task-at-a-time rule

- Work on exactly **one Task ID per execution session**.
- Do not silently start the next task when the current one is complete.
- A task is complete only when its acceptance criteria have been checked.
- If a task reveals a blocker, stop at that task, explain the blocker and define the smallest action needed to unblock it.
- Do not refactor unrelated code while completing a task.
- Keep the project buildable after each meaningful task.
- Update this roadmap's checkbox only when the result has actually been verified.

To start work, send one command such as:

> **Lance TC-001**

To continue after a task is complete:

> **Lance TC-002**

If a task requires access to the local computer, Reddit account, Kiro or the Devvit dashboard that is not available in the conversation, provide the exact commands or clicks needed and ask for the resulting output. Do not pretend that an external action has been completed.

## 0.2 Task status markers

- `[ ]` Not started.
- `[/]` In progress.
- `[x]` Complete and verified.
- `[-]` Deliberately deferred or removed from V1 scope.
- `[!]` Blocked; a dependency or external action is missing.

## 0.3 Priority levels

| Priority | Meaning | Rule |
|---|---|---|
| **P0 — Critical** | The game cannot be submitted or tested without it. | Must complete. |
| **P1 — V1** | Required for the intended polished V1 experience. | Complete after P0. |
| **P2 — Stretch** | Improves the game but is not necessary for a reliable submission. | Only start after P0 and P1 are stable. |

## 0.4 What counts as a completed task

Every task must produce a tangible result: a committed code change, a tested screen, a validated event dossier, a working Reddit post, a documented decision or a submission asset. “Looked at it” is not completion.

A normal task should end with:

1. What changed.
2. Files created or modified.
3. Commands/tests run and their results.
4. Acceptance criteria passed or failed.
5. Any remaining blocker.
6. Roadmap status updated.

---

# 1. Locked product scope

These decisions are inherited from Game Bible V1. They are not reopened during implementation unless a technical or rules-based blocker makes a change necessary.

## 1.1 Product

**The Time Cabinet** is a cosy daily historical mystery inside a Reddit Interactive Post. Every daily post contains one shared event and one shared puzzle sequence. Each successful puzzle unlocks a verified clue. Players may guess the event after any clue. A correct answer reveals the complete historical dossier.

## 1.2 Visual direction

- Cosy archive desk.
- Warm paper, cream, oat, sage, dusty blue, muted terracotta and honey accents.
- Soft wood details used sparingly.
- Atkinson Hyperlegible for interface text; Fraunces used sparingly for editorial headings, subject to font licence verification.
- Clear, readable typography; body text around 16 px on mobile.
- Soft transitions; no timers, aggressive effects or pressure mechanics.
- Optional sound off by default. Sound is not a launch blocker.

## 1.3 V1 puzzle library

**Six core puzzles — implement these first:**

1. Letter Mixer
2. Connections
3. Cipher Wheel
4. Who Am I?
5. Timeline Sort
6. Pixel Reveal

**Two approved extensions — only after the core game works:**

7. Map Hunt
8. Cause & Effect

Do not expand the library beyond these eight during the hackathon. A small polished collection is better than many incomplete games.

## 1.4 Clue categories

- `location`
- `people`
- `time`
- `object`
- `circumstances`
- `impact`

A category describes the historical information being revealed. It is not a puzzle template.

## 1.5 Core gameplay rules

- One canonical event per UTC calendar day.
- One frozen puzzle sequence shared by everyone in the same daily post.
- Individual player progress is separate.
- A correct puzzle solution unlocks exactly one clue.
- The guess field is available after the first clue.
- A wrong guess never erases progress or blocks the player.
- A correct guess reveals the event dossier.
- V1 answer checking is deterministic and uses curated aliases. No live AI calls.
- Normal session target: 3–6 minutes; generally 4–6 clue opportunities, not a hard puzzle limit.
- Restore progress after a refresh or reopening the post.

## 1.6 Definition of the first playable milestone

Before expanding the puzzle library, the project must achieve this complete vertical slice:

1. A real Reddit Interactive Post opens the game.
2. The player sees the cosy game shell.
3. The player completes Letter Mixer.
4. The server validates the solution.
5. One clue is unlocked and saved.
6. The player can submit a guess.
7. A wrong guess preserves progress.
8. A correct guess reveals the event dossier.
9. Refreshing the post restores the player's state.

This is the first major quality gate. Do not build all six puzzles before this flow works.

---

# 2. Master task register

| ID | Task | Priority | Depends on | Status |
|---|---|---:|---|:---:|
| TC-001 | Confirm hackathon registration and eligibility | P0 | — | [x] |
| TC-002 | Prepare Reddit Developer account | P0 | TC-001 | [ ] |
| TC-003 | Create the public test subreddit | P0 | TC-002 | [ ] |
| TC-004 | Prepare local development environment | P0 | — | [ ] |
| TC-005 | Create the Devvit React project | P0 | TC-004 | [ ] |
| TC-006 | Install dependencies and inspect the generated template | P0 | TC-005 | [ ] |
| TC-007 | Authenticate the Devvit CLI | P0 | TC-002, TC-005 | [ ] |
| TC-008 | Run the first Devvit playtest | P0 | TC-003, TC-006, TC-007 | [ ] |
| TC-009 | Establish Git and project hygiene | P0 | TC-005 | [ ] |
| TC-010 | Freeze technical constraints and project scripts | P0 | TC-006 | [ ] |
| TC-011 | Define shared domain types | P0 | TC-010 | [ ] |
| TC-012 | Define and validate the event dossier schema | P0 | TC-011 | [ ] |
| TC-013 | Implement answer normalization | P0 | TC-011 | [ ] |
| TC-014 | Implement deterministic seeded randomness | P0 | TC-011 | [ ] |
| TC-015 | Establish test, lint, type-check and build gates | P0 | TC-010 | [ ] |
| TC-016 | Create design tokens and global styles | P0 | TC-005 | [ ] |
| TC-017 | Bundle and verify typography | P1 | TC-016 | [ ] |
| TC-018 | Build shared cosy UI components | P1 | TC-016 | [ ] |
| TC-019 | Build the cover / open-case screen | P1 | TC-018 | [ ] |
| TC-020 | Build the investigation screen shell | P0 | TC-018 | [ ] |
| TC-021 | Build the clue shelf and progress display | P0 | TC-020, TC-011 | [ ] |
| TC-022 | Build the always-available guess panel | P0 | TC-020 | [ ] |
| TC-023 | Build the solved dossier screen | P0 | TC-018, TC-011 | [ ] |
| TC-024 | Build loading, empty and error states | P1 | TC-020 | [ ] |
| TC-025 | Establish responsive and accessible layout rules | P0 | TC-018 | [ ] |
| TC-026 | Create the puzzle template contract and registry | P0 | TC-011 | [ ] |
| TC-027 | Create the Apollo 11 reference fixture | P0 | TC-012 | [ ] |
| TC-028 | Implement Letter Mixer UI | P0 | TC-026 | [ ] |
| TC-029 | Implement Letter Mixer server validation | P0 | TC-028, TC-012 | [ ] |
| TC-030 | Implement Redis repository for daily case and player progress | P0 | TC-011, TC-007 | [ ] |
| TC-031 | Implement the initial case / progress API | P0 | TC-027, TC-030 | [ ] |
| TC-032 | Implement puzzle solve and clue unlock API | P0 | TC-029, TC-030, TC-031 | [ ] |
| TC-033 | Implement event guess API | P0 | TC-013, TC-030, TC-031 | [ ] |
| TC-034 | Complete the first end-to-end vertical slice | P0 | TC-019–TC-033 | [ ] |
| TC-035 | Implement Connections | P1 | TC-026, TC-034 | [ ] |
| TC-036 | Implement Cipher Wheel | P1 | TC-026, TC-034 | [ ] |
| TC-037 | Implement Who Am I? | P1 | TC-026, TC-034 | [ ] |
| TC-038 | Implement Timeline Sort | P1 | TC-026, TC-034 | [ ] |
| TC-039 | Implement Pixel Reveal | P1 | TC-026, TC-034 | [ ] |
| TC-040 | Implement shared puzzle retry and feedback behaviour | P1 | TC-035–TC-039 | [ ] |
| TC-041 | Define the historical content editorial checklist | P0 | TC-012 | [ ] |
| TC-042 | Author and verify the first playable daily event | P0 | TC-041 | [ ] |
| TC-043 | Complete the Apollo 11 reference dossier | P1 | TC-027, TC-041 | [ ] |
| TC-044 | Author the iPhone introduction dossier | P1 | TC-041 | [ ] |
| TC-045 | Author the Berlin Wall opening dossier | P1 | TC-041 | [ ] |
| TC-046 | Author the Sputnik 1 launch dossier | P1 | TC-041 | [ ] |
| TC-047 | Author the Wright brothers' first-flight dossier | P1 | TC-041 | [ ] |
| TC-048 | Author two additional verified event dossiers | P1 | TC-041 | [ ] |
| TC-049 | Audit historical assets, licences and attribution | P0 | TC-042–TC-048 | [ ] |
| TC-050 | Build event dossier validation and clue coverage checks | P0 | TC-012, TC-041 | [ ] |
| TC-051 | Build the clue-to-puzzle compatibility filter | P0 | TC-026, TC-050 | [ ] |
| TC-052 | Build the daily puzzle sequence generator | P0 | TC-014, TC-051 | [ ] |
| TC-053 | Add progression, variety and fallback rules | P0 | TC-052 | [ ] |
| TC-054 | Freeze the generated daily case | P0 | TC-030, TC-052, TC-053 | [ ] |
| TC-055 | Implement UTC daily date selection and date edge cases | P0 | TC-050, TC-054 | [ ] |
| TC-056 | Connect the six core puzzles to generated event data | P1 | TC-035–TC-039, TC-054 | [ ] |
| TC-057 | Secure player identity and progress isolation | P0 | TC-030, TC-031 | [ ] |
| TC-058 | Harden server validation and prevent answer leakage | P0 | TC-032, TC-033, TC-057 | [ ] |
| TC-059 | Create the moderator manual daily-post action | P0 | TC-008, TC-054 | [ ] |
| TC-060 | Create the scheduled daily-post job | P1 | TC-055, TC-059 | [ ] |
| TC-061 | Make daily-post creation idempotent | P0 | TC-054, TC-059 | [ ] |
| TC-062 | Add post fallback text and Reddit discussion prompt | P1 | TC-059 | [ ] |
| TC-063 | Verify the public demo post and subreddit requirements | P0 | TC-003, TC-059 | [ ] |
| TC-064 | Add unit tests for domain, answer and generator logic | P0 | TC-013, TC-014, TC-050–TC-053 | [ ] |
| TC-065 | Add puzzle-level tests for all six core templates | P1 | TC-028–TC-040 | [ ] |
| TC-066 | Add API and Redis integration tests | P0 | TC-030–TC-033, TC-057 | [ ] |
| TC-067 | Test the complete player journey in Reddit | P0 | TC-034, TC-056, TC-059 | [ ] |
| TC-068 | Test two players against the same daily case | P0 | TC-054, TC-057, TC-067 | [ ] |
| TC-069 | Test refresh, resume, duplicate requests and solved return | P0 | TC-032–TC-034, TC-066 | [ ] |
| TC-070 | Run mobile, desktop and accessibility QA | P0 | TC-025, TC-040, TC-067 | [ ] |
| TC-071 | Run historical accuracy and content QA | P0 | TC-042–TC-050 | [ ] |
| TC-072 | Run performance, failure-state and security QA | P0 | TC-058, TC-066, TC-067 | [ ] |
| TC-073 | Conduct a small external playtest and fix critical findings | P1 | TC-067–TC-072 | [ ] |
| TC-074 | Apply final visual polish and motion restraint | P1 | TC-070, TC-073 | [ ] |
| TC-075 | Write the root README in English | P0 | TC-034, TC-059, TC-063 | [ ] |
| TC-076 | Upload a stable app build and record the app listing URL | P0 | TC-067–TC-074 | [ ] |
| TC-077 | Prepare the Devpost project description and required links | P0 | TC-075, TC-076 | [ ] |
| TC-078 | Record the optional sub-60-second demo video | P1 | TC-077, TC-076 | [ ] |
| TC-079 | Complete final submission checks and submit | P0 | TC-063, TC-075–TC-078 | [ ] |
| TC-080 | Keep the demo available and monitored during judging | P1 | TC-079 | [ ] |
| TC-081 | Implement Map Hunt | P2 | TC-079 or all P0/P1 stable | [ ] |
| TC-082 | Implement Cause & Effect | P2 | TC-079 or all P0/P1 stable | [ ] |
| TC-083 | Add optional hints | P2 | TC-079 or all P0/P1 stable | [ ] |
| TC-084 | Add optional sound and small tactile effects | P2 | TC-074 | [ ] |
| TC-085 | Add streaks or a weekly archive | P2 | TC-080 | [ ] |

---

# 3. Detailed execution tasks

## Phase A — Access, environment and project bootstrap

### TC-001 — Confirm hackathon registration and eligibility `[P0]`

**Depends on:** None.  
**Goal:** Make sure the entrant is registered and can participate before investing implementation time.

**Actions:**
- Open the official Devpost hackathon page and rules.
- Join/register for the hackathon with the intended Devpost account.
- Review the eligibility section, including age-of-majority and restricted-country rules.
- Confirm that the submission will be made under the correct individual/team identity.
- Save the deadline and required submission links in a local project note.

**Done when:**
- Devpost shows the project owner as joined/registered.
- Eligibility has been checked against the official rules; do not assume eligibility from location alone.
- The deadline is recorded as 8 December 2026, 6:00 p.m. Pacific Time / 9 December 2026, 04:00 Burundi time.

**Deliverable:** Registration confirmation and a short `notes/hackathon-checklist.md`.

### TC-002 — Prepare Reddit Developer account `[P0]`

**Depends on:** TC-001.  
**Goal:** Ensure the Reddit account can access Reddit for Developers and Devvit.

**Actions:**
- Sign in to the Reddit account that will own the app.
- Open <https://developers.reddit.com/> and complete the developer onboarding.
- Confirm access to the app creation flow at <https://developers.reddit.com/new>.
- Keep account credentials private. Never paste passwords or authentication tokens into chat or source code.

**Done when:** The developer dashboard and app creation flow are accessible.

### TC-003 — Create the public test subreddit `[P0]`

**Depends on:** TC-002.  
**Goal:** Have a subreddit that satisfies the hackathon demo requirement and can be used for playtesting.

**Actions:**
- Create or select a dedicated test subreddit.
- Make it **public**.
- Keep it below 200 members/subscribers during judging.
- Ensure the app owner has moderator permissions.
- Record its exact subreddit name and URL in a local note.

**Done when:** The subreddit is public, accessible to judges, has fewer than 200 members/subscribers and the app owner can moderate it.

**Important:** Devvit's automatically generated playtest subreddit may be private. Do not assume that it alone satisfies the hackathon's public demo-post requirement. Use a public test subreddit for the submitted demo link.

### TC-004 — Prepare local development environment `[P0]`

**Depends on:** None.  
**Goal:** Create a reliable local environment for Devvit Web.

**Actions:**
- Install Node.js **24.18.0 or newer**, following the current Devvit quickstart at the time of setup.
- Install and verify npm.
- Verify Git is available.
- Open the project in the selected editor (Kiro or VS Code).
- Record versions with `node -v`, `npm -v` and `git --version`.

**Done when:** All commands run successfully and Node meets the current official minimum.

### TC-005 — Create the Devvit React project `[P0]`

**Depends on:** TC-004.  
**Goal:** Generate the official React-based Devvit Web starter instead of creating a standalone Vite app.

**Actions:**
- Open <https://developers.reddit.com/new>.
- Select the current React/Devvit Web template.
- Choose the final app slug carefully; avoid spaces and unnecessary renaming later.
- Generate the project into its own folder.
- Preserve the generated Devvit configuration and entrypoint structure.

**Done when:** The project contains a valid `devvit.json`, client and server folders, package manifest and generated template files.

### TC-006 — Install dependencies and inspect the generated template `[P0]`

**Depends on:** TC-005.  
**Goal:** Confirm the unmodified starter works before adding game code.

**Actions:**
- Install dependencies using the package manager and lockfile selected by the generated template.
- Inspect the current client/server entrypoints.
- Inspect scripts in `package.json` and build settings in `devvit.json`.
- Identify the template's actual server framework and test/build commands. Do not replace it just to match the conceptual structure in the Game Bible.
- Run the generated build/type-check commands.

**Done when:** Dependencies install cleanly and the untouched project builds successfully.

### TC-007 — Authenticate the Devvit CLI `[P0]`

**Depends on:** TC-002, TC-005.  
**Goal:** Connect the local project to the correct Reddit developer account.

**Actions:**
- Use the CLI authentication flow documented by Reddit.
- Confirm the CLI can read the app identity.
- Do not commit authentication files or tokens.

**Done when:** The CLI is authenticated and a non-destructive command such as `npx devvit help` runs.

### TC-008 — Run the first Devvit playtest `[P0]`

**Depends on:** TC-003, TC-006, TC-007.  
**Goal:** Prove that the generated app runs inside a real Reddit post before building the game.

**Actions:**
- Configure the intended public test subreddit in the template or playtest command.
- Follow the current Devvit CLI/playtest workflow. If the current workflow requires it, upload the starter build first, then run `npx devvit playtest <subreddit-name>`.
- Open the returned Reddit post/subreddit link.
- Confirm the React client is rendered inside Reddit, not only in a local browser.
- Check terminal/server logs for errors.

**Done when:** A real Reddit playtest opens and displays the starter UI successfully.

### TC-009 — Establish Git and project hygiene `[P0]`

**Depends on:** TC-005.  
**Goal:** Make work recoverable and reviewable.

**Actions:**
- Initialise Git if the template has not already done so.
- Verify `.gitignore` excludes `node_modules`, build outputs, local secrets and Devvit auth files.
- Create a first baseline commit.
- Create a `notes/` folder for research and non-secret setup notes.
- Optionally create a private or public GitHub repository; public repository is optional for the hackathon.

**Done when:** A clean baseline commit exists and no secrets are tracked.

### TC-010 — Freeze technical constraints and project scripts `[P0]`

**Depends on:** TC-006.  
**Goal:** Avoid unnecessary architecture changes while building the MVP.

**Actions:**
- Record the actual generated template structure and server framework.
- Keep the official Devvit client/server/configuration model.
- Keep all client-originated network calls on the app's own `/api/` endpoints; no direct external API calls from the webview.
- Do not use WebSockets, streaming, long-running server processes or packages requiring native binaries unless official Devvit support is confirmed.
- Use Redis for data that must survive app updates; do not rely on `localStorage` for canonical progress.
- Ensure `build`, `dev/playtest`, `typecheck`, `lint` and `test` scripts are available, adapting to the template.

**Done when:** A short architecture note exists and the project has repeatable build and playtest scripts.

---

## Phase B — Domain model, visual foundation and shared screens

### TC-011 — Define shared domain types `[P0]`

**Depends on:** TC-010.  
**Goal:** Define the common language used by client, server, generator and content.

**Actions:**
- Define `ClueCategory`, `PuzzleType` and `RevealTier` unions.
- Define `HistoricalEvent`, `HistoricalClue`, `PuzzleOption`, `SourceReference` and asset metadata.
- Define `DailyCase` and `PlayerDailyProgress`.
- Keep client-safe public case data separate from secret answer/validation data.
- Use the Game Bible's schema as the starting point, adapting only where the generated template requires it.

**Done when:** Shared types compile and have no duplicated conflicting definitions.

### TC-012 — Define and validate the event dossier schema `[P0]`

**Depends on:** TC-011.  
**Goal:** Make invalid or incomplete event content impossible to schedule silently.

**Actions:**
- Define required fields for event title, historical date, summary, themes, accepted answers, clues and sources.
- Require each clue to have category, tier, reveal text, source IDs and at least one puzzle option.
- Require each puzzle option to have a known template ID and valid payload.
- Require asset provenance for every image/audio asset.
- Decide how draft, verified and scheduled content states are represented.

**Done when:** Valid fixture data passes and deliberately malformed fixtures fail with actionable errors.

### TC-013 — Implement answer normalization `[P0]`

**Depends on:** TC-011.  
**Goal:** Accept sensible aliases without relying on live AI or dangerously loose fuzzy matching.

**Actions:**
- Trim whitespace and normalize case.
- Normalize Unicode and diacritics.
- Standardize punctuation and repeated whitespace.
- Compare normalized guesses to curated accepted aliases.
- Keep fuzzy matching disabled in V1 unless a later test suite proves it safe.
- Add unit tests for accents, punctuation, abbreviations and common aliases.

**Done when:** Equivalent spellings match, unrelated answers do not, and tests cover edge cases.

### TC-014 — Implement deterministic seeded randomness `[P0]`

**Depends on:** TC-011.  
**Goal:** Ensure the daily puzzle sequence is reproducible for every player.

**Actions:**
- Implement a small deterministic PRNG or seeded shuffle in pure TypeScript.
- Build the seed from the UTC daily date, event ID and generator version.
- Never use unseeded `Math.random()` for the shared daily sequence.
- Add repeatability and changed-seed tests.

**Done when:** The same inputs always produce the same output across repeated runs.

### TC-015 — Establish test, lint, type-check and build gates `[P0]`

**Depends on:** TC-010.  
**Goal:** Catch breakage after every single task.

**Actions:**
- Use the test framework already supported by the generated template where possible.
- Add scripts for tests, lint, type-check and production build.
- Ensure one command can run the required local checks.
- Do not add several overlapping test frameworks.

**Done when:** The checks run from a clean install and return a non-zero status when a deliberate test/type error is introduced.

### TC-016 — Create design tokens and global styles `[P0]`

**Depends on:** TC-005.  
**Goal:** Translate the cosy art direction into reusable CSS tokens.

**Actions:**
- Add the Bible's warm paper, cream, oat, deep ink, slate, sage, dusty blue, terracotta, honey, border and walnut tokens.
- Define spacing, radius, shadow, typography scale and focus styles.
- Ensure text/background contrast is readable; pastel colours are surfaces, not body text.
- Set consistent focus, hover, selected, success, warning and disabled states.

**Done when:** A sample screen uses tokens rather than scattered arbitrary colour values.

### TC-017 — Bundle and verify typography `[P1]`

**Depends on:** TC-016.  
**Goal:** Use clear, licensed typography without runtime CDN dependency.

**Actions:**
- Obtain Atkinson Hyperlegible and Fraunces from trustworthy sources.
- Verify and retain font licence files/attribution.
- Bundle font assets locally.
- Add sensible system fallbacks.
- Check body text at mobile size and heading readability.

**Done when:** Fonts load in the Reddit webview without external font requests and licence records are stored.

### TC-018 — Build shared cosy UI components `[P1]`

**Depends on:** TC-016.  
**Goal:** Create consistent paper/archive components before assembling screens.

**Components:**
- `PaperCard`
- `PrimaryButton` and `QuietButton`
- `FileTab` or clue/category badge
- `ProgressDots` or case progress strip
- `PuzzleInstruction`
- `InlineFeedback`
- `Modal/Drawer` only if genuinely needed

**Done when:** Shared components are responsive, keyboard focusable and use design tokens.

### TC-019 — Build the cover / open-case screen `[P1]`

**Depends on:** TC-018.  
**Goal:** Make the daily experience inviting and immediately understandable.

**Actions:**
- Show The Time Cabinet wordmark.
- Show today's daily date.
- Show a one-sentence promise that a historical mystery is waiting.
- Show the shared daily-case concept.
- Add one primary action: `Open today's case`.
- Avoid a long onboarding sequence.

**Done when:** A first-time player understands what to do without a tutorial.

### TC-020 — Build the investigation screen shell `[P0]`

**Depends on:** TC-018.  
**Goal:** Create the main reusable layout that hosts any puzzle template.

**Actions:**
- Header with game name, daily date and sound toggle placeholder (sound can remain inactive/off until TC-084).
- Case progress display.
- Puzzle title and one-sentence instructions.
- Dynamic puzzle render area.
- Clue shelf.
- Guess panel.
- Calm no-timer reassurance.

**Done when:** A placeholder puzzle can be rendered inside a complete, responsive investigation screen.

### TC-021 — Build the clue shelf and progress display `[P0]`

**Depends on:** TC-020, TC-011.  
**Goal:** Keep every unlocked clue visible during the investigation.

**Actions:**
- Display unlocked clues as ordered archive notes.
- Display category labels and clue text.
- Keep future clues hidden.
- Show progress without revealing the event title or final answer.
- Preserve clue order after reload.

**Done when:** The clue shelf correctly renders zero, one and multiple clues without exposing locked clues.

### TC-022 — Build the always-available guess panel `[P0]`

**Depends on:** TC-020.  
**Goal:** Let players submit an event guess as soon as they earn the first clue.

**Actions:**
- Show the input after the first clue is unlocked.
- Keep it available after every later clue.
- Provide a clear submit action.
- Preserve a wrong guess so it can be edited.
- Show a calm incorrect message; do not erase progress.
- Prevent duplicate rapid submissions while a request is pending.

**Done when:** The player can guess after one clue and after each later clue.

### TC-023 — Build the solved dossier screen `[P0]`

**Depends on:** TC-018, TC-011.  
**Goal:** Deliver a satisfying and educational final reveal.

**Actions:**
- Show the canonical event title and historical date.
- Show the short plain-language story (target 80–140 words).
- Show three key facts.
- Show trustworthy source links.
- Show how many clues the player used and a friendly result label.
- Show a spoiler-safe share string.
- Invite discussion in Reddit comments without automatically posting on the player's behalf.

**Done when:** The screen can render a solved event without requiring a reload.

### TC-024 — Build loading, empty and error states `[P1]`

**Depends on:** TC-020.  
**Goal:** Make failures understandable rather than leaving blank panels.

**Actions:**
- Loading state for case initialization and puzzle submission.
- Retry state for a transient API failure.
- Missing/invalid daily case state with a useful recovery message.
- Already-completed state.
- Network/offline message appropriate to Devvit Web.

**Done when:** Every async screen has an explicit loading, success and failure state.

### TC-025 — Establish responsive and accessible layout rules `[P0]`

**Depends on:** TC-018.  
**Goal:** Make the game playable in Reddit's narrow mobile webview and on desktop.

**Actions:**
- Mobile-first single-column layout.
- Touch targets around 44 × 44 CSS px or larger where practical.
- Visible keyboard focus.
- Semantic buttons and labels.
- Meaningful image alt text.
- No instruction that relies only on colour.
- Reduced-motion handling.
- No drag-only interaction; every reorder/move has an accessible alternative.

**Done when:** The shell can be used on mobile and desktop with keyboard-only navigation for core controls.

---

## Phase C — First playable vertical slice

### TC-026 — Create the puzzle template contract and registry `[P0]`

**Depends on:** TC-011.  
**Goal:** Make puzzle templates plug into the investigation screen through a common contract.

**Actions:**
- Define a discriminated union for the eight approved puzzle types.
- Define the payload shape for each type.
- Create a registry/renderer that maps a `puzzleType` to its React component.
- Keep puzzle UI separate from clue text and event identity.
- Create a shared submission result shape.

**Done when:** The investigation screen can render a registered template from a typed puzzle payload.

### TC-027 — Create the Apollo 11 reference fixture `[P0]`

**Depends on:** TC-012.  
**Goal:** Provide a known, testable event fixture for the first end-to-end slice.

**Actions:**
- Use the Apollo 11 lunar landing as a development fixture, not automatically as the current daily challenge.
- Include canonical answer and curated aliases.
- Include a short sourced summary and several clue facts.
- Include at least one Letter Mixer payload and one clue associated with it.
- Keep the canonical answer on the server side; do not send it in pre-solve client data.

**Done when:** The fixture passes event validation and contains a complete playable Letter Mixer clue.

### TC-028 — Implement Letter Mixer UI `[P0]`

**Depends on:** TC-026.  
**Goal:** Build the first real puzzle interaction.

**Actions:**
- Render shuffled letter/digit tiles and answer slots.
- Let the player tap/click a tile to place it.
- Let a placed tile be returned to the tray.
- Support reset and incomplete state.
- Show a check/submit button only when appropriate.
- Keep the layout comfortable on mobile.

**Done when:** A player can complete the puzzle using only taps/clicks and can correct a mistaken placement.

### TC-029 — Implement Letter Mixer server validation `[P0]`

**Depends on:** TC-028, TC-012.  
**Goal:** Ensure the server, not the browser, decides whether a puzzle is solved.

**Actions:**
- Define the minimal answer payload sent by the client.
- Validate the answer against the server-held puzzle payload.
- Reject missing, malformed, extra or forged fields.
- Return a typed success/failure response.
- Add tests for correct, incorrect and incomplete answers.

**Done when:** Editing client-side state cannot grant a clue without a valid server response.

### TC-030 — Implement Redis repository for daily case and player progress `[P0]`

**Depends on:** TC-011, TC-007.  
**Goal:** Persist the shared daily case and each player's progress.

**Actions:**
- Use namespaced, versioned keys.
- Store the frozen daily case separately from per-player progress.
- Keep keys predictable; do not rely on global Redis key scans.
- Store JSON with explicit type parsing and defensive error handling.
- Handle missing records by creating a valid initial progress object.

**Done when:** Daily case and player progress can be saved, read and updated in Redis from Devvit server code.

### TC-031 — Implement the initial case / progress API `[P0]`

**Depends on:** TC-027, TC-030.  
**Goal:** Load the correct case and current player's progress.

**Actions:**
- Implement the initial `/api/init` endpoint following the generated server framework.
- Resolve the current post/daily case from trusted Devvit context and stored post data.
- Load the frozen daily case and the current player's progress.
- Return only public puzzle payloads and already-unlocked clues.
- Do not return canonical answer or secret accepted aliases.

**Done when:** The client can reload and render the current puzzle plus the player's progress from server data.

### TC-032 — Implement puzzle solve and clue unlock API `[P0]`

**Depends on:** TC-029–TC-031.  
**Goal:** Turn a valid puzzle solution into one permanent clue unlock.

**Actions:**
- Implement the solve endpoint.
- Validate that the submitted puzzle is the player's current puzzle in the frozen case.
- Validate its response on the server.
- Save completion and clue unlock together as safely as possible.
- Make repeated submissions idempotent; do not duplicate clues.

**Done when:** A successful solve persists exactly one clue; invalid and repeated requests do not corrupt progress.

### TC-033 — Implement event guess API `[P0]`

**Depends on:** TC-013, TC-030, TC-031.  
**Goal:** Validate the player's free-form event guess.

**Actions:**
- Implement the guess endpoint.
- Require at least one unlocked clue.
- Normalize the guess and compare it with server-held accepted answers.
- On wrong guess, preserve progress and return a calm response.
- On correct guess, save the solved state and timestamp.
- Reveal the full dossier only after successful validation.

**Done when:** Correct aliases are accepted, wrong answers do not end the case, and the answer is not leaked before solving.

### TC-034 — Complete the first end-to-end vertical slice `[P0]`

**Depends on:** TC-019–TC-033.  
**Goal:** Prove the full product loop before scaling content or puzzle count.

**Actions:**
- Wire cover screen to investigation screen.
- Load the Apollo reference fixture.
- Complete Letter Mixer.
- Unlock and display one clue.
- Submit one wrong guess, then a correct guess.
- Reveal the solved dossier.
- Refresh/reopen the Reddit post and confirm progress remains.

**Done when:** All nine steps in Section 1.6 work inside a real Reddit Interactive Post. This is the first major go/no-go checkpoint.

---

## Phase D — Complete the six core puzzle templates

Each task below must be implemented as a complete template, not as a static mockup. Each must validate on the server, handle retry/incomplete/error states and fit the responsive investigation screen.

### TC-035 — Implement Connections `[P1]`

**Depends on:** TC-026, TC-034.  
**Goal:** Let the player group related archive cards.

**Required behaviour:** 12 shuffled cards; three authored groups of four; selected-card state; submit group; correct groups lock together; incorrect groups receive gentle feedback; no ambiguous grouping; completion only after all three groups.

**Done when:** A fixture can be solved, incorrect groups can be retried, and the server independently validates the intended groups.

### TC-036 — Implement Cipher Wheel `[P1]`

**Depends on:** TC-026, TC-034.  
**Goal:** Decode a short Caesar-shift message with a tactile wheel interaction.

**Required behaviour:** visible alphabet/shift control; live decoded preview; clear direction; short phrase; submit decoded answer; no need for cryptography knowledge beyond the provided rule.

**Done when:** The player can decode a fixture and the server verifies the result from the payload rather than trusting a client success flag.

### TC-037 — Implement Who Am I? `[P1]`

**Depends on:** TC-026, TC-034.  
**Goal:** Identify a historical person using evidence provided within the puzzle.

**Required behaviour:** four candidate cards; three concise evidence cards; one unambiguous correct candidate; selectable answer; accessible feedback.

**Done when:** The right person can be deduced without outside knowledge and distractors are defensible but clearly wrong.

### TC-038 — Implement Timeline Sort `[P1]`

**Depends on:** TC-026, TC-034.  
**Goal:** Put three or four historical steps in chronological order.

**Required behaviour:** shuffled cards; arrow controls to reorder; optional drag interaction only as an enhancement; unambiguous order; validation on server.

**Done when:** The complete puzzle can be solved using keyboard/tap arrow controls without drag-and-drop.

### TC-039 — Implement Pixel Reveal `[P1]`

**Depends on:** TC-026, TC-034.  
**Goal:** Identify a licensed historical image hidden behind a pixel/tile mask.

**Required behaviour:** initially masked image; controlled reveal actions; minimum fair reveal threshold; guess/selection UI; clue unlock after correct image identification; alt text that does not spoil the answer.

**Done when:** The asset loads inside Reddit, the image is recognisable at the intended point, and its provenance is recorded.

### TC-040 — Implement shared puzzle retry and feedback behaviour `[P1]`

**Depends on:** TC-035–TC-039.  
**Goal:** Make all puzzle templates feel like one coherent game.

**Actions:**
- Standardise instructions, submit, success, incorrect, incomplete and retry states.
- Prevent repeated clicks while the request is pending.
- Use calm feedback and accessible state announcements.
- Keep the current clue locked until the server confirms success.

**Done when:** All six core templates share the same interaction conventions without losing their unique mechanics.

---

## Phase E — Historical content and asset preparation

### TC-041 — Define the historical content editorial checklist `[P0]`

**Depends on:** TC-012.  
**Goal:** Establish the verification standard for every event before authoring the daily library.

**Rules:**
- Verify the exact event date, not merely a related anniversary.
- Distinguish presentation, announcement, launch, first use, landing, commercial release and later consequences.
- Use at least one authoritative primary or institutional source; use a second independent source where the date, cause or interpretation is contested.
- Keep short source excerpts/notes, not copied articles.
- Never fabricate a quotation.
- Mark uncertainty where historians disagree.
- Avoid turning recent tragedy or ongoing suffering into a cute score challenge.
- Ensure every clue fact is supported by one or more source IDs.

**Done when:** `notes/editorial-checklist.md` exists and is used for every dossier.

### TC-042 — Author and verify the first playable daily event `[P0]`

**Depends on:** TC-041.  
**Goal:** Create the actual event dossier intended for the public demo post.

**Actions:**
- Choose a well-documented event with a compelling story and enough different clue types.
- Ensure its historical month/day matches the daily post date on which it will be demonstrated.
- Prepare canonical title, aliases, summary, themes, at least four clue facts, reveal tiers and puzzle options.
- Ensure the first clue is broad and later clues become more identifying.
- Verify every fact and source.

**Done when:** The event passes schema/editorial validation and supports at least four playable clue/puzzle pairs.

### TC-043 — Complete the Apollo 11 reference dossier `[P1]`

**Depends on:** TC-027, TC-041.  
**Goal:** Turn the existing Apollo 11 example into a verified fixture for puzzle testing.

**Actions:**
- Verify the 20 July 1969 lunar landing date separately from the first human step on the lunar surface, which crossed into 21 July UTC.
- Verify the landing site, crew roles, spacecraft modules and mission chronology.
- Add sources, accepted aliases and clue facts.
- Add puzzle payloads that exercise several templates.

**Done when:** The Apollo 11 fixture passes editorial and automated dossier validation.

### TC-044 — Author the iPhone introduction dossier `[P1]`

**Depends on:** TC-041.  
**Goal:** Add a technology event with clear people, object, date and impact clues.

**Accuracy rule:** Distinguish the public presentation on 9 January 2007 from the commercial release on 29 June 2007.

**Done when:** The dossier has verified sources, aliases and at least four clue/puzzle pairs.

### TC-045 — Author the Berlin Wall opening dossier `[P1]`

**Depends on:** TC-041.  
**Goal:** Add a political/social event with location, people, circumstances and impact clues.

**Accuracy rule:** Distinguish the 9 November 1989 opening of border crossings from the subsequent physical dismantling and later German reunification.

**Done when:** The dossier uses careful wording, verified sources and at least four clue/puzzle pairs.

### TC-046 — Author the Sputnik 1 launch dossier `[P1]`

**Depends on:** TC-041.  
**Goal:** Add a science/space event with strong object, time, location and impact clues.

**Done when:** Launch date, place, object and historical significance have source support and at least four clue/puzzle pairs.

### TC-047 — Author the Wright brothers' first-flight dossier `[P1]`

**Depends on:** TC-041.  
**Goal:** Add an engineering/transport event with people, location, object and time clues.

**Accuracy rule:** Use the documented date and distinguish the first powered flights from earlier glider experiments.

**Done when:** The event facts and chronology are verified and the dossier has at least four clue/puzzle pairs.

### TC-048 — Author two additional verified event dossiers `[P1]`

**Depends on:** TC-041.  
**Goal:** Reach the Game Bible's minimum content target of seven complete dossiers, including the actual demo event and Apollo reference fixture.

**Actions:**
- Select two events from different themes.
- Prefer events whose calendar dates are useful for the available daily challenge dates.
- Verify exact month/day/year and all clue facts.
- Create at least four clue/puzzle pairs per event.

**Done when:** Both event dossiers pass the automated and editorial checks. The target is seven total complete dossiers; 10–14 is optional only if time remains.

### TC-049 — Audit historical assets, licences and attribution `[P0]`

**Depends on:** TC-042–TC-048.  
**Goal:** Ensure every visual asset can legally be included in the app and demo.

**Actions:**
- Prefer original CSS/SVG illustrations or assets with explicit public-domain/open licences.
- For every image, record creator, exact source URL, licence, attribution text and local path.
- Avoid assuming that an image is reusable just because it appears in search results or on a museum website.
- Confirm font licences as part of TC-017.
- Keep an asset manifest.
- Replace any uncertain asset with original artwork or a safer licensed alternative.

**Done when:** Every bundled asset has complete provenance and the asset manifest contains no unknown licences.

---

## Phase F — Event validation and daily generator

### TC-050 — Build event dossier validation and clue coverage checks `[P0]`

**Depends on:** TC-012, TC-041.  
**Goal:** Reject events that cannot produce a fair, varied investigation.

**Validation must check:**
- Unique event and clue IDs.
- Valid historical date.
- Valid clue category and reveal tier.
- All clue source IDs exist.
- Every clue has at least one compatible puzzle option.
- Every puzzle payload matches its template schema.
- No duplicate clue facts or accidental answer leakage.
- At least four viable clue/puzzle pairs for a scheduled event.
- At least three clue categories where the event reasonably supports them.
- Every selected image asset exists and has rights metadata.

**Done when:** All completed dossiers pass and a deliberately incomplete dossier fails with a useful error.

### TC-051 — Build the clue-to-puzzle compatibility filter `[P0]`

**Depends on:** TC-026, TC-050.  
**Goal:** Only offer mechanics that have all required information for a given clue.

**Actions:**
- Define required payload fields and asset requirements per template.
- Filter puzzle options by template validity and data availability.
- Remove templates already used in the same case when alternatives exist.
- Return a clear reason if no eligible template remains.

**Done when:** The filter never selects an unusable puzzle and its results are unit tested.

### TC-052 — Build the daily puzzle sequence generator `[P0]`

**Depends on:** TC-014, TC-051.  
**Goal:** Generate a shared but surprising sequence from a verified event dossier.

**Actions:**
- Choose 4–6 clues when available; this is a target, not a mandatory fixed count.
- Start with broad clues and move toward more identifying information.
- Select one compatible puzzle option per clue using deterministic randomness.
- Prefer different templates in one case.
- Use at least three clue categories where possible.
- Permit early correct guesses; later rounds are never mandatory.

**Done when:** The same date/event/version always produces the same sequence and the sequence is playable from start to finish.

### TC-053 — Add progression, variety and fallback rules `[P0]`

**Depends on:** TC-052.  
**Goal:** Prevent awkward sequences and prevent an invalid event from breaking the daily game.

**Rules:**
- No decisive clue at the very beginning unless the event has no fair alternative.
- No repeated clue fact.
- No same puzzle template twice in a case unless the eligible pool is too small.
- If an option is invalid, use another authored option or reject the event before scheduling.
- Do not fabricate a fallback clue or puzzle at runtime.

**Done when:** Edge-case tests cover small pools, missing assets, repeated templates and insufficient clue coverage.

### TC-054 — Freeze the generated daily case `[P0]`

**Depends on:** TC-030, TC-052, TC-053.  
**Goal:** Guarantee that everyone opening the same post sees the same challenge.

**Actions:**
- Generate the puzzle sequence once for a daily event.
- Save date, event ID, sequence, generator version and creation timestamp.
- Reuse the saved case on every player request.
- Do not regenerate the sequence independently per user.

**Done when:** Repeated requests from different users return an identical daily sequence.

### TC-055 — Implement UTC daily date selection and date edge cases `[P0]`

**Depends on:** TC-050, TC-054.  
**Goal:** Make the daily case boundary predictable worldwide.

**Actions:**
- Use UTC for the canonical daily ID.
- Show the selected date clearly in the UI.
- Test requests on both sides of UTC midnight.
- Handle leap day explicitly; never silently substitute February 28 for February 29.
- Ensure an already-created post remains attached to its frozen date/event even after UTC midnight.

**Done when:** Date-selection tests prove consistent results across time zones and day boundaries.

### TC-056 — Connect the six core puzzles to generated event data `[P1]`

**Depends on:** TC-035–TC-039, TC-054.  
**Goal:** Replace development fixtures with the actual generated puzzle payloads.

**Actions:**
- Render the selected template from the frozen daily sequence.
- Load only that puzzle's public payload.
- Keep clue text hidden until completion.
- Validate success against the matching server-held clue/payload.
- Confirm switching between template types does not reset the clue shelf or guess panel.

**Done when:** One case can include several different core templates and the game transitions through them without special-case screen code.

---

## Phase G — Reddit identity, persistence hardening and daily posts

### TC-057 — Secure player identity and progress isolation `[P0]`

**Depends on:** TC-030, TC-031.  
**Goal:** Keep each player's progress separate and prevent client identity spoofing.

**Actions:**
- Resolve the Reddit user identity from trusted Devvit server request context/auth middleware.
- Never trust a `userId` sent by the browser.
- Decide and test logged-out behaviour; if the chosen post experience requires authentication, explain it clearly rather than failing silently.
- Scope all progress keys by daily date and trusted user ID.
- Do not store birthdays or unnecessary profile data.

**Done when:** A client cannot read/write another player's progress by changing request payloads.

### TC-058 — Harden server validation and prevent answer leakage `[P0]`

**Depends on:** TC-032, TC-033, TC-057.  
**Goal:** Protect the game state and prevent cheating through client inspection.

**Actions:**
- Validate request body shapes and size.
- Validate the current post, daily date, clue and puzzle index.
- Validate puzzle answers server-side.
- Do not send the canonical event answer, full accepted alias list or locked clue texts before a correct guess.
- Make solve/guess requests safe against replay and duplicate clicks.
- Return friendly client errors without stack traces.

**Done when:** Forged requests cannot unlock clues or reveal the final answer.

### TC-059 — Create the moderator manual daily-post action `[P0]`

**Depends on:** TC-008, TC-054.  
**Goal:** Provide a reliable human-operated recovery path for the daily game.

**Actions:**
- Add a moderator-only menu action in `devvit.json`.
- Implement its server endpoint.
- Resolve the target subreddit from trusted context.
- Create a custom post using the configured entrypoint.
- Attach only a small daily case identifier in post data; keep larger content in Redis/bundled content.
- Provide a clear success/failure result to the moderator.

**Done when:** A moderator can create the daily Interactive Post from Reddit without manually editing Redis.

### TC-060 — Create the scheduled daily-post job `[P1]`

**Depends on:** TC-055, TC-059.  
**Goal:** Automate daily post creation once the manual route works.

**Actions:**
- Declare a scheduled task in `devvit.json` using the currently documented Devvit Scheduler format.
- Implement the `/internal/...` endpoint.
- Compute the intended daily date in UTC.
- Call the shared daily-post creation service used by the moderator action.
- Keep the scheduled task disabled or unactivated for regular use until TC-061 proves duplicate prevention.
- Test the scheduler execution and logs in playtest.

**Done when:** The scheduled task reaches the correct post-creation service and can be safely enabled after TC-061 passes. Manual post creation remains available as fallback.

### TC-061 — Make daily-post creation idempotent `[P0]`

**Depends on:** TC-054, TC-059.  
**Goal:** Prevent duplicate posts if a scheduler or moderator retries.

**Actions:**
- Check the stored daily-post record before creation.
- Store the resulting Reddit post ID after success.
- Handle concurrent attempts safely as far as the platform APIs allow.
- Provide a deliberate moderator recovery path when a post record exists but the post is unavailable.

**Done when:** Repeated calls for the same date create at most one valid daily post in normal operation.

### TC-062 — Add post fallback text and Reddit discussion prompt `[P1]`

**Depends on:** TC-059.  
**Goal:** Make the Reddit post meaningful if the interactive webview cannot load and encourage community conversation.

**Actions:**
- Write concise fallback text explaining the game and how to play.
- Include a no-spoiler community prompt such as “What's your theory? Keep the answer hidden until you've solved it.”
- Use consistent post title formatting.
- Do not automatically publish player guesses or spoilers in comments.

**Done when:** The post remains understandable even when the interactive view is unavailable.

### TC-063 — Verify the public demo post and subreddit requirements `[P0]`

**Depends on:** TC-003, TC-059.  
**Goal:** Satisfy the public demo testing requirement in the hackathon rules.

**Actions:**
- Confirm the subreddit is public.
- Confirm it has fewer than 200 members/subscribers.
- Confirm the test post is visible without joining a private community.
- Confirm the game loads from that exact post.
- Record direct links to the subreddit and playable post.

**Done when:** A judge with an ordinary Reddit account can open the public post and play the app.

---

## Phase H — Testing, accessibility, polish and release quality

### TC-064 — Add unit tests for domain, answer and generator logic `[P0]`

**Depends on:** TC-013, TC-014, TC-050–TC-053.  
**Goal:** Protect the logic that determines fairness and correctness.

**Required cases:**
- Normalized answer aliases.
- Wrong answer remains wrong.
- Seed repeatability.
- Different seeds may produce different sequences.
- Incompatible puzzle options are filtered out.
- No duplicate clue facts.
- Insufficient dossier is rejected.
- Leap-day and UTC date behaviour.

**Done when:** Tests pass and cover normal plus edge cases.

### TC-065 — Add puzzle-level tests for all six core templates `[P1]`

**Depends on:** TC-028–TC-040.  
**Goal:** Ensure every template can be solved and validated fairly.

**For each template test:**
- Correct solution.
- Incorrect solution.
- Empty/incomplete input.
- Retry after incorrect input.
- Server validation rejects a forged success claim.
- Clue unlocks exactly once.
- Mobile-sized layout and keyboard/tap interaction.

**Done when:** All six core templates pass their test matrix.

### TC-066 — Add API and Redis integration tests `[P0]`

**Depends on:** TC-030–TC-033, TC-057.  
**Goal:** Verify real persistence and route behaviour.

**Required cases:**
- New player receives empty progress.
- Progress saves after a successful puzzle.
- Wrong guess leaves progress unchanged.
- Correct guess records solved state.
- Repeated solve does not duplicate clue IDs.
- Refresh reads saved state.
- Player A cannot access Player B's progress.

**Done when:** Integration tests pass against the supported Devvit test/playtest environment.

### TC-067 — Test the complete player journey in Reddit `[P0]`

**Depends on:** TC-034, TC-056, TC-059.  
**Goal:** Test the actual app inside a Reddit post, not only in a local browser.

**Actions:**
- Open the public test post.
- Start a fresh case.
- Solve at least two different puzzle templates.
- Guess incorrectly once.
- Guess correctly later.
- Verify clue shelf and solved dossier.
- Read server/client logs.

**Done when:** The complete daily loop works in Reddit without a local-only assumption.

### TC-068 — Test two players against the same daily case `[P0]`

**Depends on:** TC-054, TC-057, TC-067.  
**Goal:** Prove shared challenge fairness and isolated progress.

**Actions:**
- Open the same daily post from two Reddit accounts.
- Confirm same event and same puzzle sequence.
- Solve a different number of puzzles on each account.
- Confirm each account's clue shelf/progress is independent.
- Confirm one player's solve does not reveal the answer to the other player.

**Done when:** Shared case data is identical while player progress is separate.

### TC-069 — Test refresh, resume, duplicate requests and solved return `[P0]`

**Depends on:** TC-032–TC-034, TC-066.  
**Goal:** Ensure real users never lose progress or get inconsistent states.

**Test cases:**
- Refresh before solving.
- Refresh after one clue.
- Refresh after a wrong guess.
- Reopen after solving.
- Double-click solve.
- Submit the same guess twice.
- Reopen the same post after UTC midnight.

**Done when:** All cases restore the correct state and never duplicate clues or create an accidental second daily case.

### TC-070 — Run mobile, desktop and accessibility QA `[P0]`

**Depends on:** TC-025, TC-040, TC-067.  
**Goal:** Make the game comfortable in the Reddit mobile webview and desktop layout.

**Check:**
- Narrow phone width.
- Typical desktop width.
- Text scaling/browser zoom.
- Touch target size.
- Keyboard navigation and visible focus.
- Reduced motion.
- Meaningful image alternatives.
- No horizontal overflow.
- No controls obscured by Reddit's post frame.

**Done when:** No critical usability/accessibility blocker remains.

### TC-071 — Run historical accuracy and content QA `[P0]`

**Depends on:** TC-042–TC-050.  
**Goal:** Protect historical credibility.

**Actions:**
- Recheck dates, times, names, places and chronology against sources.
- Check clue wording does not overstate cause or impact.
- Check event title and aliases match the intended historical event.
- Check no clue accidentally gives away the canonical answer before the player earns it.
- Check source URLs are reachable and specific to the fact cited.

**Done when:** Every event scheduled for the demo is approved against the editorial checklist.

### TC-072 — Run performance, failure-state and security QA `[P0]`

**Depends on:** TC-058, TC-066, TC-067.  
**Goal:** Ensure the app behaves reliably within Devvit Web constraints.

**Actions:**
- Inspect bundle size and asset loading.
- Ensure endpoints finish within current Devvit request limits.
- Ensure no unsupported long-lived connection or direct client external fetch is required.
- Test missing Redis records and malformed content.
- Test server error responses and retry UI.
- Confirm no secret answer data is present in client payloads or static assets before completion.

**Done when:** No critical crash, performance or answer-leak issue remains.

### TC-073 — Conduct a small external playtest and fix critical findings `[P1]`

**Depends on:** TC-067–TC-072.  
**Goal:** Find confusion that the developer is too familiar with the game to notice.

**Actions:**
- Ask a small group of testers to play without live coaching.
- Observe whether they understand the objective and each puzzle's instructions.
- Record confusion, unfair ambiguity, slow interactions and technical failures.
- Fix critical blockers first; avoid adding new features based on one person's preference.

**Done when:** A short findings note exists and all critical issues are fixed or explicitly documented as non-blocking.

### TC-074 — Apply final visual polish and motion restraint `[P1]`

**Depends on:** TC-070, TC-073.  
**Goal:** Bring the product close to a coherent publishable experience.

**Actions:**
- Refine spacing, typography, card borders, paper details and hierarchy.
- Add restrained paper/card transitions only where they clarify state changes.
- Keep animation short and calm; respect reduced motion.
- Keep sound off by default and do not spend time on sound until all blockers are solved.
- Remove placeholder copy, debug labels and inconsistent icon styles.

**Done when:** All major screens look like one intentional product and remain readable.

---

## Phase I — Hackathon submission and judging readiness

### TC-075 — Write the root README in English `[P0]`

**Depends on:** TC-034, TC-059, TC-063.  
**Goal:** Satisfy the required repository README and let judges understand the game quickly.

**Include:**
- The Time Cabinet overview and daily-game premise.
- How to play.
- Screenshots or a short visual preview.
- Reddit app/test subreddit/demo post links when available.
- Stack and high-level architecture.
- Development/playtest instructions that are safe to publish.
- Asset/font attribution and licences.
- Known limitations, if any.

**Done when:** A new reader can understand and test the project from the README without private instructions.

### TC-076 — Upload a stable app build and record the app listing URL `[P0]`

**Depends on:** TC-067–TC-074.  
**Goal:** Obtain the app link required by Devpost and freeze a known working build.

**Actions:**
- Run all release checks.
- Use the current Devvit CLI upload flow to create the installable/private app build.
- Record the official `developers.reddit.com/apps/{app-name}` link.
- Verify the uploaded version can be installed/tested.
- Do not submit for broad app publication review unless required by the hackathon or a later launch decision; distinguish upload from publish/review.

**Done when:** The app listing URL exists and corresponds to a tested version.

### TC-077 — Prepare the Devpost project description and required links `[P0]`

**Depends on:** TC-075, TC-076.  
**Goal:** Make the submission self-explanatory to judges.

**Include:**
- Problem/experience and what makes the game a daily mystery rather than generic trivia.
- How the shared daily case works.
- Puzzle variety and clue progression.
- Reddit-native integration and community discussion.
- App listing URL.
- Public test subreddit URL.
- Direct demo post URL.
- English text and clear testing instructions.

**Done when:** All required Devpost fields are complete and links point to the correct live project.

### TC-078 — Record the optional sub-60-second demo video `[P1]`

**Depends on:** TC-077, TC-076.  
**Goal:** Show the actual game running on Reddit in a short, clear clip.

**Suggested shot order:**
1. Open the Reddit post and show the game identity.
2. Solve one quick puzzle.
3. Reveal a clue.
4. Show the guess panel and correct guess.
5. Show the final historical dossier and source links.

**Rules:** Keep the video under 60 seconds, show the real game on its intended platform, upload it to an accepted public video platform and add the link to Devpost. Do not use a mock browser screen as a substitute for the actual Reddit experience.

**Done when:** The public video link works and is included in Devpost.

### TC-079 — Complete final submission checks and submit `[P0]`

**Depends on:** TC-063, TC-075–TC-078.  
**Goal:** Submit a complete, judgeable project before the deadline.

**Final checklist:**
- [ ] Devpost registration is complete.
- [ ] App is built on Reddit's Developer Platform and runs in an Interactive Post.
- [ ] App listing link is included.
- [ ] Public test subreddit link is included.
- [ ] Direct public demo post link is included.
- [ ] Public test subreddit has fewer than 200 members/subscribers.
- [ ] Root `README.md` is present and explains how to play.
- [ ] Devpost description explains features and functionality.
- [ ] Submission material is in English or has the required English translations.
- [ ] All assets have usage rights and attribution.
- [ ] The project is available free of charge for judges during judging.
- [ ] Demo video is under one minute if included.
- [ ] Every link has been opened from a logged-out/ordinary test account where practical.

**Timing:** Actual deadline is **8 December 2026 at 6:00 p.m. Pacific Time = 9 December 2026 at 04:00 in Burundi**. Internal target: submit at least 24 hours earlier, by **8 December 2026 at 04:00 Burundi time**.

**Done when:** Devpost confirms the submission was received and the final submission page displays the correct project and links.

### TC-080 — Keep the demo available during judging `[P1]`

**Depends on:** TC-079.  
**Goal:** Avoid breaking the judge's access after submission.

**Actions:**
- Keep the app and public demo post available through the judging period.
- Monitor critical error reports and the demo post.
- Fix only clear blocking defects; avoid major feature changes that could destabilise the submitted version.
- Keep the test subreddit public and under the member limit.

**Done when:** The app remains playable and the submitted links remain valid through the judging period.

---

## Phase J — Stretch tasks (not allowed to delay submission)

### TC-081 — Implement Map Hunt `[P2]`

**Depends on:** TC-079 or all P0/P1 tasks stable.  
**Goal:** Add a location-specific map interaction.

**Constraints:** Use a bundled/local simplified SVG map; no live map tile API. Use clear tap targets and a fair region acceptance rule. Test mobile carefully.

**Done when:** A location clue can be earned reliably through a map puzzle. If this risks core stability, defer it.

### TC-082 — Implement Cause & Effect `[P2]`

**Depends on:** TC-079 or all P0/P1 tasks stable.  
**Goal:** Let players connect verified causes, circumstances and consequences.

**Constraints:** Use careful historical language. Avoid reducing complex events to one simplistic cause. All relationships need source support.

**Done when:** A complete cause/effect chain can be solved and validated. If it risks core stability, defer it.

### TC-083 — Add optional hints `[P2]`

**Depends on:** TC-079 or all P0/P1 tasks stable.  
**Goal:** Help a stuck player without punishing them.

**Rules:** One authored hint per puzzle where available; no paid hints; no lives or lockouts; record hint use only if useful. Do not invent hints automatically.

**Done when:** A hint can be requested and progress remains fair.

### TC-084 — Add optional sound and small tactile effects `[P2]`

**Depends on:** TC-074.  
**Goal:** Add paper-slide, pencil-tap or soft success feedback only if it improves the cosy experience.

**Rules:** Sound is off by default; use original or properly licensed audio; offer a visible toggle; respect reduced-motion and user preferences.

**Done when:** Sound can be enabled/disabled and never blocks gameplay. Skip if there is any schedule risk.

### TC-085 — Add streaks or a weekly archive `[P2]`

**Depends on:** TC-080.  
**Goal:** Add gentle retention after the daily game is stable.

**Rules:** No pressure mechanics, punishments or complex global leaderboards. Respect Reddit installation/subreddit data scope.

**Done when:** A small retention feature works without affecting the core daily investigation. This is explicitly post-MVP.

---

# 4. Recommended execution calendar

This is a suggested order relative to the 8 December Pacific deadline. It is a planning aid, not permission to skip dependencies.

| Window (Burundi time) | Focus | Target checkpoint |
|---|---|---|
| 16–17 November | TC-001 to TC-010 | Real Devvit starter post works in the public test subreddit. |
| 17–19 November | TC-011 to TC-027 | Domain model, visual shell and first event fixture ready. |
| 19–21 November | TC-028 to TC-034 | First complete vertical slice playable in Reddit. |
| 21–25 November | TC-035 to TC-040 | Six core puzzle templates working. |
| 24–29 November | TC-041 to TC-056 | Event library, validation and deterministic daily generator. |
| 28 November–2 December | TC-057 to TC-063 | Persistence/security hardening and daily Reddit post workflow. |
| 2–5 December | TC-064 to TC-074 | QA, real playtesting and polish. |
| 6–7 December | TC-075 to TC-078 | README, app URL, Devpost copy and optional video. |
| By 8 December 04:00 | TC-079 | Internal submission target — 24 hours before official close. |
| 8 December–16 December | TC-080 | Keep demo accessible during judging. |

If the schedule slips, protect the vertical slice and submission requirements. Defer P2 work first, then optional hints/sound, then extra content beyond the minimum. Do not cut the working Reddit post, player progress, clue unlock, guess/reveal loop or submission links.

---

# 5. Global Definition of Done

The project is ready for submission only when all statements below are true:

## Product
- [ ] A new player can understand the game without an explanation from the developer.
- [ ] A player can play one complete historical mystery in Reddit.
- [ ] A completed puzzle reveals exactly one useful historical clue.
- [ ] The player can guess after the first clue and after each later clue.
- [ ] Wrong guesses preserve progress.
- [ ] Correct guesses reveal the historical dossier, facts and sources.

## Puzzle library
- [ ] All six core templates are implemented and server-validated.
- [ ] No puzzle requires the player to already know the historical answer.
- [ ] Each puzzle has clear instructions, correct/incorrect feedback and retry behaviour.
- [ ] The two extension puzzles are optional and do not delay the core build.

## Daily system
- [ ] Same daily post = same event and puzzle sequence for everyone.
- [ ] Each player's progress is independent and persistent.
- [ ] Sequence generation is deterministic and based on compatible puzzle payloads.
- [ ] Daily date uses UTC and leap day is handled explicitly.
- [ ] No answer or locked clue leaks to the client.

## Content
- [ ] At least seven complete event dossiers are available as the target in the Game Bible.
- [ ] The public demo event matches the day/date represented by its post.
- [ ] All historical facts and source references have been checked.
- [ ] Every image/font/sound asset has a recorded licence and attribution.

## Reddit and submission
- [ ] The app runs inside a Reddit Interactive Post.
- [ ] A public subreddit under 200 members/subscribers contains the demo post.
- [ ] The app listing URL, subreddit URL and direct post URL are included in Devpost.
- [ ] Root README explains the project and how to play.
- [ ] Devpost description and instructions are in English or include the required English translations.
- [ ] Submission is received before the deadline.

---

# 6. Cut list if time becomes critical

Remove or defer in this order:

1. TC-085 — streaks/weekly archive.
2. TC-084 — sound.
3. TC-083 — hints.
4. TC-081 and TC-082 — Map Hunt and Cause & Effect.
5. Any decorative animation beyond the basic calm transitions.
6. Event dossiers beyond the minimum seven.

Do **not** cut:

- Real Devvit Interactive Post integration.
- Letter Mixer vertical slice.
- Server-side puzzle validation.
- Redis progress persistence.
- Guess-after-each-clue behaviour.
- Final sourced event reveal.
- Same daily sequence for everyone.
- Public demo subreddit/post and required Devpost links.

---

# 7. Official references

Check the live official documentation again when a task reaches implementation. Devvit APIs and CLI details can evolve; the generated template and current docs take precedence over assumptions in this roadmap.

## Hackathon

- Reddit Game of the Day Hackathon: <https://redditgameofday2026.devpost.com/>
- Official rules and deadline: <https://redditgameofday2026.devpost.com/rules>

## Devvit setup and Web architecture

- Devvit Web overview: <https://developers.reddit.com/docs/capabilities/devvit-web/devvit_web_overview>
- React app quickstart: <https://developers.reddit.com/docs/quickstart>
- Devvit CLI: <https://developers.reddit.com/docs/guides/tools/devvit_cli>
- Playtest guide: <https://developers.reddit.com/docs/guides/tools/playtest>
- Devvit Web configuration: <https://developers.reddit.com/docs/capabilities/devvit-web/devvit_web_configuration>

## Interactive posts, storage and scheduling

- Interactive Posts overview: <https://developers.reddit.com/docs/capabilities/interactive-posts/interactive_posts_overview>
- Creating a Custom Post: <https://developers.reddit.com/docs/capabilities/creating_custom_post>
- Redis: <https://developers.reddit.com/docs/capabilities/server/redis>
- Scheduler: <https://developers.reddit.com/docs/capabilities/server/scheduler>
- Devvit FAQ: <https://developers.reddit.com/docs/guides/faq>

---

# 8. Final execution instruction

The next implementation action is **TC-001**. Do not jump directly to building puzzles. First establish the hackathon account, developer access, environment and a real Reddit playtest.

After that, execute tasks strictly by ID unless a dependency forces a documented adjustment. One task, one verified result, then stop. This roadmap is the work queue for The Time Cabinet V1.
