# THE TIME CABINET
## Game Bible — Version 1.0

**Tagline:** *A little mystery from history, every day.*  
**Document date:** 16 November 2026  
**Target platform:** Reddit — Devvit Web / Interactive Posts  
**Status:** Product direction and V1 decisions locked. Ready to start implementation.

---

# 0. Executive decision

**The Time Cabinet** is a cosy daily historical mystery game embedded directly in a Reddit post.

Every day, the community receives the same hidden historical event. Players investigate it by solving short mini-puzzles. Each completed puzzle reveals one verified historical clue. Players may submit a guess after any clue, without waiting for a fixed number of puzzles. A correct guess opens the complete story, its key facts and its sources.

The central design decision is to separate three things:

1. **The event:** the historical truth the player is trying to identify.
2. **The clue:** a verified piece of information about that event.
3. **The puzzle template:** the activity used to earn that clue.

A clue category can be paired with several puzzle templates. The daily generator chooses a compatible template from the library. The same daily post uses the same chosen puzzle sequence for everyone, so the community shares one fair challenge.

## Locked decisions

| Decision | Locked choice |
|---|---|
| Working title | **The Time Cabinet** |
| Core fantasy | Opening a cosy archive and investigating one historical mystery a day |
| Daily content | One shared event per UTC calendar day |
| Guessing | A player may guess after every unlocked clue |
| Puzzle count | Event-dependent; normally 4–6 clues, never forced to a fixed count |
| Clue categories | Location, People, Time, Object, Circumstances, Impact |
| Puzzle V1 library | 8 templates: 6 core + 2 stretch |
| Puzzle selection | Seeded random selection from compatible, available templates |
| Fairness | All players in the same daily post receive the same puzzle sequence |
| Answer validation | Curated accepted answers and aliases; no live AI dependency |
| Visual direction | Cosy, calm, tactile archive desk; pastel paper, soft wood, clear typography |
| Platform | Devvit Web, React and TypeScript inside Reddit Interactive Posts |
| MVP priority | A complete polished daily loop beats a large unfinished puzzle collection |

---

# 1. Product vision

## 1.1 The promise

**Every day has a story. Can you uncover it?**

The player should feel like they have opened a small archive drawer, found a mysterious case file, and are gradually piecing together what happened in history.

This is not a history exam. Players should not need to know the answer already. The game supplies the evidence through puzzles, and curiosity does the rest.

## 1.2 Experience principles

1. **Curiosity before knowledge.** The game teaches the player enough to solve the mystery; it does not punish them for not knowing historical trivia.
2. **Small satisfying actions.** A puzzle should take roughly 30–60 seconds to understand and solve.
3. **Every action matters.** A completed puzzle always unlocks a useful, sourced clue.
4. **Player-controlled discovery.** The player can guess at any time and is never forced to complete every puzzle.
5. **A shared daily ritual.** Everyone in the same daily post faces the same event and puzzle sequence.
6. **Quiet polish.** The experience feels tactile, warm and relaxing, not noisy, frantic or competitive.
7. **Historical trust.** Dates, names, locations, answers and images are checked before they enter the game.

## 1.3 What this game is not

- Not a general-knowledge quiz with a historical skin.
- Not a trivia list where the player only taps A, B, C or D.
- Not a long escape room with dozens of arbitrary steps.
- Not an AI-generated history feed.
- Not a standalone website that merely links to Reddit. The actual game must run inside Reddit through Devvit.

---

# 2. Audience, platform and daily format

## 2.1 Target player

A Reddit user who enjoys short puzzles, surprising facts, history, discovery and sharing a result with a community. The player may know a lot about history or almost nothing. Both should be able to enjoy the same case.

## 2.2 Daily format

- One canonical event is selected for each calendar date.
- The event must have happened on the same month/day as the daily challenge date. The event's year is historical and may be any year.
- The editorial database chooses one event when multiple events are possible on a date. Do not select an event only because its title sounds exciting; it must have a strong puzzle dossier.
- Use **UTC** for the daily challenge ID and reset so everyone shares the same daily case. Show the date clearly in the interface.
- February 29 is a special content date. It can be handled by a dedicated leap-day event bank; it must not silently fall back to February 28.

## 2.3 Session length

Target a typical session of **3–6 minutes**. Most cases should contain approximately 4–6 unlockable clues. This is a content guideline, not a hard-coded puzzle limit. A simple event can need fewer clues; a complex event can have more. The player can finish early at any point by guessing correctly.

## 2.4 Language

- First release and hackathon demo: English UI and English puzzle content.
- Keep the code and content structure ready for localization later.
- The project README, Devpost description, testing instructions and demo video must be in English or have English translations, as required by the hackathon rules.

---

# 3. The two kinds of categories

Do not confuse **historical themes** with **clue categories**.

## 3.1 Historical themes — what kind of event is this?

These are editorial tags used to diversify the daily calendar:

- Technology and invention
- Science and discovery
- Space and exploration
- Politics and society
- Arts and culture
- Sport
- Engineering and transport
- Environment and nature
- Business and economy
- Human achievement

An event can have several tags. Themes do not determine the puzzle by themselves.

## 3.2 Clue categories — what information are we revealing?

Every fact revealed by a puzzle belongs to one of these six categories. An event does not need to contain all six.

| ID | Category | What it can reveal | Examples |
|---|---|---|---|
| `location` | **Location** | Country, city, region, building, site, destination | Berlin, Kitty Hawk, CERN, Sea of Tranquility |
| `people` | **People** | Main person, team, organization, witnesses, opposing figures | Neil Armstrong, the Wright brothers, NASA |
| `time` | **Time** | Year, date, period, sequence, time of day | 1969, 20 July, the 1980s |
| `object` | **Object** | Device, invention, vehicle, document, symbol, artifact | Eagle, Sputnik 1, the first iPhone |
| `circumstances` | **Circumstances** | What was happening, why it happened, immediate context | A crewed lunar mission, a border divided a city |
| `impact` | **Impact** | What changed, what followed, why the event mattered | The beginning of the Space Age |

### Rule

A category is an information dimension, not a puzzle type. For example, `location` can be earned through a map puzzle, a cipher, a word puzzle or a visual puzzle, provided the event dossier contains the data each template needs.

---

# 4. Locked puzzle library — V1

The library contains **eight approved puzzle templates**. The first six are the core implementation target. The final two are approved V1 extensions and should be implemented after the daily loop and core puzzles are stable.

Every template must:

- Have a clear instruction visible before interaction.
- Work with mouse, touch and keyboard where practical.
- Be understandable without a tutorial.
- Give immediate feedback when the player makes a valid move.
- Have a clear success state.
- Unlock one authored clue when completed.
- Allow a retry without resetting the entire daily case.
- Avoid timers and stressful countdowns.

## 4.1 Core template 01 — Letter Mixer

**Interaction:** Reassemble shuffled letter or digit tiles into a target word, name, place or year.

**How it plays:**
1. The answer's letters are displayed as separate tiles in a shuffled order.
2. The player taps tiles to place them into answer slots.
3. Tapping a placed tile returns it to the tray.
4. When all slots are filled, the player checks the answer.
5. A correct answer completes the puzzle and unlocks the clue.

**Supported data:** names, cities, countries, objects, short terms, years and short numeric strings.

**Content constraints:**
- Prefer one word or a short phrase.
- Ideal answer length: 4–14 characters, excluding spaces.
- Do not use names with several equally common spellings unless all variants are handled.
- Avoid obscure spellings that turn the puzzle into a typing test.

**Good categories:** People, Location, Time, Object.

**Why it stays:** Very easy to understand, works well on mobile, quick to implement and can reuse the same interaction for many types of historical data.

## 4.2 Core template 02 — Connections

**Interaction:** Group related archive cards together.

**How it plays:**
1. The player sees 12 cards in a shuffled grid.
2. The cards form three authored groups of four.
3. The player selects four cards they believe share a connection.
4. The game checks the group. Correct groups are pinned together; incorrect selections receive gentle feedback and remain playable.
5. Finding all three groups completes the puzzle and reveals one clue explaining an important relationship.

**Content constraints:**
- Every group must have one defensible intended connection.
- Avoid cards that could reasonably belong to two groups.
- Use clear words or short phrases, not obscure academic vocabulary.
- Add a small number of mistakes (recommended limit: 3) only if the clue remains accessible; do not lock the player out permanently.

**Good categories:** Location, People, Time, Object, Circumstances, Impact.

**Why it stays:** It creates a satisfying “aha” moment and is naturally shareable as a puzzle format. Its content can be adapted to almost any event.

## 4.3 Core template 03 — Cipher Wheel

**Interaction:** Decode a short hidden message using a visual decoder wheel.

**How it plays:**
1. The player receives a short encoded word or phrase.
2. A circular alphabet wheel or shift control lets the player test a Caesar-style letter shift.
3. A decoded preview updates as the wheel moves.
4. The player confirms the meaningful phrase.
5. A correct decode unlocks the associated clue.

**Content constraints:**
- Use a Caesar shift or a simple substitution rule in V1; do not introduce complex cryptographic systems.
- Keep messages short (roughly 3–20 characters before spaces).
- The instructions must explain the rule or provide enough information to discover it.
- The answer must be a meaningful historical term, name, place or phrase.

**Good categories:** Location, People, Time, Object, Circumstances.

**Why it stays:** It feels like genuine investigation and gives the interface a tactile archive-tool interaction.

## 4.4 Core template 04 — Who Am I?

**Interaction:** Identify a historical person by combining evidence and eliminating candidates.

**How it plays:**
1. The player sees four possible identity cards.
2. Three evidence cards describe attributes such as role, nationality, profession, team or action.
3. The player compares the evidence with the candidate cards.
4. They select the only candidate that fits every condition.
5. A correct choice completes the puzzle and unlocks a fact about that person's role in the event.

**Content constraints:**
- All necessary information must be in the puzzle. Never require prior knowledge of the person.
- Candidate names must be visually distinct and readable.
- Distractors must be plausible but unambiguously incorrect.
- Do not use fabricated quotations.

**Good categories:** People and Circumstances.

**Why it stays:** It makes historical figures feel like people in a story rather than names in a textbook.

## 4.5 Core template 05 — Timeline Sort

**Interaction:** Put three or four event steps in chronological order.

**How it plays:**
1. The player receives three or four short timeline cards in a shuffled order.
2. They move cards up or down to build the correct sequence. Drag-and-drop may be offered, but arrow controls must also exist for touch and accessibility.
3. The player checks the order.
4. A correct sequence completes the puzzle and unlocks a time or context clue.

**Content constraints:**
- Use 3–4 steps in V1.
- Every step must have a verified date or order.
- Do not mix time zones or local dates without explaining the reference.
- The order must be unambiguous.

**Good categories:** Time, Circumstances, Impact.

**Why it stays:** Chronology is central to history, and arranging cards is a natural tactile action.

## 4.6 Core template 06 — Pixel Reveal

**Interaction:** Identify a historical image that is initially hidden behind a grid or pixel mask.

**How it plays:**
1. The player sees a masked image with a small number of tiles uncovered.
2. They choose tiles to reveal more of the image.
3. After a minimum reveal threshold, they enter a guess or select from four carefully authored options.
4. Correct identification completes the puzzle and unlocks the historical clue.

**Content constraints:**
- The underlying image must be clearly identifiable at the intended reveal stage.
- Use image assets owned by the project, public-domain assets, or assets with an explicit compatible license.
- Keep the image source, creator, license and attribution in the event dossier.
- Do not use an image merely because it appeared in Google Images.
- Avoid faces or symbols that could be mistaken for several people or objects.

**Good categories:** People, Location, Object.

**Why it stays:** It is visually satisfying, easy to understand and offers a strong reveal moment.

## 4.7 Approved extension 07 — Map Hunt

**Interaction:** Find a place on a simplified, illustrated map.

**How it plays:**
1. The player sees a map of the relevant continent, country or region.
2. The puzzle gives a small geographic clue (neighbours, coastline, region or relative position).
3. The player taps the intended location or region.
4. A correct selection completes the puzzle and reveals a location clue.

**Content constraints:**
- Use bundled SVG maps or self-authored map illustrations; no live map tile API is required.
- The map must be readable on a phone.
- If the target is a city, use a map zoom level that can distinguish it fairly.
- Store the expected coordinates/region and a reasonable acceptance area in the puzzle data.

**Good categories:** Location.

**Why it is approved:** It is a strong, distinctive geographical mechanic. It is a stretch item because accurate maps and tap targets need extra testing.

## 4.8 Approved extension 08 — Cause & Effect

**Interaction:** Match causes, events and consequences into a coherent chain.

**How it plays:**
1. The player sees three cause cards and three effect cards.
2. They connect each cause to the effect it produced, or arrange a short cause → event → consequence chain.
3. The game validates the relationships.
4. A correct result unlocks an impact or circumstances clue.

**Content constraints:**
- The historical relationships must be supported by sources.
- Do not oversimplify a complex historical process into a false one-cause explanation.
- Use wording such as “contributed to” where the evidence does not support a sole cause.

**Good categories:** Circumstances and Impact.

**Why it is approved:** It helps the player understand why an event mattered, not only who and when.

## 4.9 Compatibility matrix

`✓` means the template is a natural fit when the event dossier has suitable data. It does not mean every event must use it.

| Puzzle template | Location | People | Time | Object | Circumstances | Impact |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| Letter Mixer | ✓ | ✓ | ✓ | ✓ |  |  |
| Connections | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Cipher Wheel | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| Who Am I? |  | ✓ |  |  | ✓ |  |
| Timeline Sort |  |  | ✓ |  | ✓ | ✓ |
| Pixel Reveal | ✓ | ✓ |  | ✓ |  |  |
| Map Hunt | ✓ |  |  |  |  |  |
| Cause & Effect |  |  |  |  | ✓ | ✓ |

## 4.10 Deliberately deferred puzzles

These are not part of the V1 build. They may be revisited only after the daily game is stable:

- Large jigsaw puzzles: more asset preparation and slower sessions than their value justifies.
- Word Search: familiar but can become a repetitive tapping exercise and is awkward on small screens.
- Hangman: too close to a basic word quiz and less distinctive.
- Generic multiple-choice trivia: contradicts the “investigate, don't already know” principle.
- Rebus: creative but highly language-dependent and difficult to author consistently.
- Full Logic Grid: often takes too long for the target session length.
- Quote attribution: quotation accuracy, translation and rights need extra care.
- Timed challenges: rejected because the game is meant to feel calm, not stressful.

---

# 5. Clue system and daily investigation

## 5.1 What exactly is a clue?

A clue is a **short, verified historical statement** that narrows the player's search. The puzzle is the activity used to earn it; the clue is the information shown after success.

Example:

- Puzzle: Timeline Sort.
- Player action: put launch, lunar orbit, landing and return in the right order.
- Reward clue: “The landing took place on 20 July 1969.”

Do not confuse the puzzle's answer with the full event answer. Sometimes the puzzle answer is a person's name or a location; the revealed clue should explain why that fact matters to the mystery.

## 5.2 Clue reveal tiers

Each clue receives a `revealTier`:

| Tier | Label | Purpose | Example wording |
|---|---|---|---|
| 1 | Broad | Gives the general direction without solving the mystery | “This story involves a crewed space mission.” |
| 2 | Connecting | Adds a meaningful person, place, object or context | “The mission's commander was Neil Armstrong.” |
| 3 | Decisive | Makes the likely answer much easier to identify | “The landing site was Mare Tranquillitatis, the Sea of Tranquility.” |

The sequence should generally move from broad to specific, but category order can vary. Do not reveal all decisive facts first.

## 5.3 Guessing rules

- A guess field is always available after the first clue.
- A wrong guess does not remove a clue, end the game or block the player.
- After a wrong guess, show a calm message such as: **“Not quite. The file has more to reveal.”**
- The next puzzle becomes available after the current one is solved.
- A correct guess ends the investigation and opens the full event dossier.
- Guessing is free-form text, but V1 validation is deterministic. Do not make an external AI request for every guess.

### Answer normalization

Before comparing a guess:

1. Trim leading/trailing spaces.
2. Convert to lowercase.
3. Normalize Unicode and remove accents for matching.
4. Standardize punctuation and repeated spaces.
5. Compare against the canonical title and curated aliases.

Each event must include accepted aliases such as alternative event names and common short forms. Do not use aggressive fuzzy matching that might accept a different historical event. Add fuzzy matching only after a test suite demonstrates that it does not create false positives.

## 5.4 Hints

V1 includes one optional hint per puzzle only if the author has written a fair hint.

- A hint can reveal one letter, remove one wrong option, show one already-known relation or uncover one extra visual tile.
- Hints are never paid.
- Hints do not prevent a player from completing the case.
- The final result may record whether a hint was used, but there is no punishing score system.

## 5.5 Completion result

Use a friendly result, not a harsh leaderboard:

- **First Look** — solved after 1 clue.
- **Good Instinct** — solved after 2–3 clues.
- **Careful Investigator** — solved after 4 or more clues.

The exact thresholds may be tuned after testing. Do not call a slower solve a failure.

On completion, show:
- Event title and historical date.
- A short plain-language story (roughly 80–140 words).
- Three key facts.
- One or more trustworthy sources.
- Number of clues used.
- A spoiler-safe result string the player can share in Reddit comments.

---

# 6. Random puzzle selection — the central system

## 6.1 How generation works

1. The daily event dossier contains a curated set of clue facts.
2. Each fact has a clue category, reveal tier, reveal text, sources and one or more compatible puzzle payloads.
3. The generator selects a clue fact that fits the next difficulty stage.
4. It filters the puzzle library to templates that are compatible with that fact and have complete data.
5. It chooses one eligible template using a deterministic seeded random function.
6. It stores the selected daily sequence so every player in that post gets the same challenge.
7. When a player solves a puzzle, the server unlocks that fact and lets the player guess.

## 6.2 Why deterministic random?

The player should be surprised by the next type of puzzle, but Reddit users should share the same daily experience. If each player got a different sequence, community discussion and fair comparison would become confusing.

Therefore:

- Randomness chooses the daily puzzle sequence once.
- The seed uses the daily date and event ID.
- The generated selection is saved as the frozen daily case.
- Every player receives the same puzzles in the same order.
- Each player has an independent progress record.

## 6.3 Generator constraints

- Only choose puzzles with all required data and licensed assets present.
- Never choose the same template twice in a case unless there are not enough compatible alternatives.
- Prefer different puzzle interactions in a single case.
- Use a broad-to-specific clue progression.
- Do not repeat the same clue fact under different wording.
- A clue must be available even if a puzzle template fails; provide a curated fallback template.
- If an event cannot support at least four good clue/puzzle pairs across at least three clue categories, do not schedule it.

## 6.4 No AI in the gameplay loop

V1 does not call a language model to create puzzles, validate history or judge guesses in real time.

Why:
- The game must be reliable and fast inside Reddit.
- Historical facts and aliases need predictable validation.
- Live AI adds cost, latency and possible hallucinations.
- Curated event packs make judging and testing much easier.

AI may be used during offline authoring as a drafting assistant, but every date, answer, clue, source and puzzle solution must be checked by a human before release.

---

# 7. Example event dossier — Apollo 11 lunar landing

This is the reference example for how an event should feed the engine. It is not a requirement that Apollo 11 be today's event.

## 7.1 Event facts

- **Canonical title:** Apollo 11 lunar landing
- **Historical date:** 20 July 1969 (landing date)
- **Themes:** Space and exploration, science, engineering
- **Main people:** Neil Armstrong, Edwin “Buzz” Aldrin, Michael Collins
- **Location:** Mare Tranquillitatis / Sea of Tranquility, on the Moon
- **Objects:** Lunar Module *Eagle*, Command Module *Columbia*
- **Accepted answers:** `Apollo 11`; `Apollo 11 lunar landing`; `Apollo 11 Moon landing`; `the first crewed Moon landing`; `the first human Moon landing`

**Accuracy note:** Apollo 11 landed on the Moon on 20 July 1969. The first step on the lunar surface occurred later that evening in US Eastern time and on 21 July UTC. The daily event in this dossier is the lunar landing, not a claim that all mission milestones occurred on the same date.

## 7.2 Example clue records

| Order tier | Category | Clue unlocked after the puzzle |
|---|---|---|
| Broad | Circumstances | “This story involves a crewed mission that travelled beyond Earth orbit.” |
| Broad | Object | “The mission used a spacecraft with two named modules: one for the surface and one for the journey home.” |
| Connecting | People | “The mission's commander was Neil Armstrong.” |
| Connecting | Time | “The lunar landing happened on 20 July 1969.” |
| Decisive | Location | “The landing site was Mare Tranquillitatis, also called the Sea of Tranquility.” |
| Decisive | Impact | “It achieved the first human landing on another celestial body.” |

## 7.3 Example generated case

A valid daily generator might produce:

| Round | Category | Selected puzzle | Resulting clue |
|---|---|---|---|
| 1 | Circumstances | Connections | A crewed mission travelled beyond Earth orbit. |
| 2 | Object | Pixel Reveal | The lunar and command modules had distinct roles. |
| 3 | People | Who Am I? | Neil Armstrong was the mission commander. |
| 4 | Time | Timeline Sort | The lunar landing took place on 20 July 1969. |
| 5 | Location | Cipher Wheel | The landing site was the Sea of Tranquility. |

The player can guess after round 1. If the player identifies Apollo 11 after round 3, rounds 4–5 are not required.

## 7.4 Verified sources for this example

- NASA NSSDCA mission page: <https://nssdc.gsfc.nasa.gov/planetary/lunar/apollo11info.html>
- NASA Apollo 11 mission overview: <https://www.nasa.gov/missions/apollo/apollo-11/apollo-11-mission-overview/>
- NASA Apollo 11 chronology: <https://www.nasa.gov/wp-content/uploads/static/history/ap11ann/introduction.htm>

---

# 8. Event content pipeline

The event database is the most important production asset after the puzzle engine. A beautiful puzzle with incorrect facts is a bad game.

## 8.1 Event authoring workflow

1. **Find candidate events** that happened on a calendar date.
2. **Select one event** that is recognisable, interesting and suitable for a short investigation.
3. **Verify the event** using at least one authoritative primary or institutional source; use a second independent source where facts are disputed or nuanced.
4. **Write the canonical answer** and accepted aliases.
5. **Extract 4–6 useful facts** from different clue categories where possible.
6. **Assign reveal tiers** from broad to decisive.
7. **Create puzzle payloads** for each fact. A fact can have several candidate templates.
8. **Test every puzzle** and every accepted answer.
9. **Check asset rights** for every image, illustration, map and audio file.
10. **Freeze and schedule the daily case.** Never change an already-played daily answer unexpectedly.

## 8.2 Editorial rules

- Prefer well-documented events with an interesting story and several clues.
- Avoid events whose exact date is disputed unless the uncertainty itself is explained.
- Distinguish an event's announcement date, launch date, first public presentation, first use and commercial release. They are not interchangeable.
- Distinguish local time from UTC when a date crosses midnight.
- Avoid fabricated quotations and invented historical details.
- Do not write clue text that accidentally states the full answer too early.
- Respect sensitive history. V1 should favour educational, neutral or constructive events. Do not turn mass casualties or ongoing suffering into a cute competitive score challenge.

## 8.3 Content targets before the demo

- Minimum: **7 complete event dossiers** with different historical themes.
- Recommended: **10–14 complete dossiers** so testing is not limited to one example.
- Every dossier: at least 4 playable clue/puzzle pairs, verified answers, accepted aliases, sources and asset-rights metadata.
- Have at least 3 different historical themes represented in the public demo period.

These are content-production targets, not claims that the game already contains this number of cases.

## 8.4 Initial seed-event candidates

These are good candidates for authoring and testing because reliable institutional sources exist:

| Event | Calendar date | Suggested source |
|---|---|---|
| Apollo 11 lunar landing | 20 July | [NASA NSSDCA](https://nssdc.gsfc.nasa.gov/planetary/lunar/apollo11info.html) |
| Opening of the Berlin Wall crossings | 9 November | [Berlin.de — History of the Berlin Wall](https://www.berlin.de/en/history/8482274-8619314-opening-and-fall-of-the-berlin-wall.en.html) |
| First public introduction of the iPhone | 9 January | [Apple Newsroom, 9 January 2007](https://www.apple.com/newsroom/2007/01/09Apple-Reinvents-the-Phone-with-iPhone/) |
| Wright brothers' first powered flights | 17 December | [Smithsonian National Air and Space Museum](https://www.si.edu/object/nasm_A19610048000) |
| Sputnik 1 launch | 4 October | [NASA — Dawn of the Space Age](https://www.nasa.gov/history/dawn-of-the-space-age/) |
| Tim Berners-Lee's first Web proposal | March (use a precisely documented day only if the dossier source supports it) | [CERN — A short history of the Web](https://home.cern/science/computing/the-birth-of-the-web/short-history-web) |

Do not automatically treat every anniversary or celebration date as the original event date. For example, CERN's 12 March anniversary event is not itself the exact date of the March 1989 proposal.

---

# 9. Visual direction — Cosy Archive Desk

## 9.1 Mood

A quiet afternoon at a small historical archive. Warm paper, a well-kept wooden desk, labelled drawers, soft natural light, pencil marks and small discoveries.

The desired feeling is inspired by the calm, tactile satisfaction of games such as *A Little to the Left* and *Art of Fauna*, without copying their interface, illustrations, assets or distinctive compositions.

**Keywords:** cosy, gentle, tactile, curious, organised, warm, readable, quietly playful.

## 9.2 Colour palette

| Role | Name | Hex |
|---|---|---|
| Main background | Warm Paper | `#F5F1E8` |
| Card surface | Cream | `#FFFCF6` |
| Secondary surface | Oat | `#EAE2D4` |
| Main ink/text | Deep Olive Ink | `#35423A` |
| Secondary text | Soft Slate | `#68736B` |
| Main accent | Sage | `#94A995` |
| Secondary accent | Dusty Blue | `#B8C9CC` |
| Warm accent | Muted Terracotta | `#C98772` |
| Highlight | Soft Honey | `#D9B96F` |
| Borders | Paper Line | `#DDD4C5` |
| Wood detail | Walnut | `#8A6B50` |

**Contrast rule:** pastel colours are for surfaces and decoration, not low-contrast body text. Main text stays deep and readable. Never communicate success, error or selection with colour alone; include an icon, label or state change.

## 9.3 Typography

- **Body and controls:** Atkinson Hyperlegible, with a system sans-serif fallback.
- **Large editorial headings:** Fraunces, used sparingly.
- Bundle font files locally and respect their open font licences. Do not rely on a third-party font CDN at runtime.
- Body text target: 16 px on mobile; secondary labels should remain comfortably readable.
- Use short line lengths and clear hierarchy. Avoid all-caps for long labels.

## 9.4 Materials and components

- Soft paper cards with a thin warm border.
- Subtle wood accents around the archive frame or drawer tabs; no full-screen busy wood texture.
- Rounded corners around 12–16 px.
- Soft, restrained shadows; avoid heavy glassmorphism and glossy gradients.
- Small line icons, paper clips, numbered tabs and file stamps.
- Puzzle surfaces should remain clean and uncluttered. The interaction is the visual focus.

## 9.5 Motion and sound

- Short transitions (roughly 160–240 ms) for card placement, clue reveal and drawer opening.
- No large camera movements, aggressive flashes or constant particle effects.
- Respect `prefers-reduced-motion`.
- Sound is optional and **off by default**. Offer a simple sound toggle.
- Use a few quiet, original sounds only: paper slide, pencil tap, soft success chime. No copyrighted music or recognisable game sound effects.

## 9.6 Responsive and accessibility rules

- Mobile-first. The game must work in a narrow Reddit post webview.
- Main game content uses one column; avoid tiny multi-column layouts.
- Interactive targets should be around 44 × 44 CSS px or larger.
- Every puzzle must be operable without relying exclusively on drag-and-drop.
- Keyboard focus must be visible.
- Provide text alternatives for meaningful images.
- Keep instructions and clue text concise.
- Avoid relying on colour alone to show groups or answers.

---

# 10. UX and screen flow

## 10.1 Entry / cover screen

Show:
- The Time Cabinet logo/wordmark.
- Today's date.
- “A new historical mystery is waiting.”
- A simple case illustration or file card.
- One primary button: **Open today's case**.
- A clear indication that the challenge is shared by the community.

## 10.2 Investigation screen

Recommended layout from top to bottom:

1. Header: The Time Cabinet, daily date, sound toggle.
2. Progress: small numbered file tabs or clue dots, without revealing future clues.
3. Puzzle card: title, one-sentence instruction, interaction area.
4. Action row: Check / Submit / Reset where relevant.
5. Clue shelf: previously earned clues displayed as stacked note cards.
6. Guess panel: always available after the first clue; may be collapsed visually but must remain obvious.
7. Small reassurance: “No timer. Take your time.”

## 10.3 Correct puzzle state

- Gentle visual acknowledgement (paper stamp or card slide).
- Reveal a new clue card with its category label.
- Add it to the clue shelf permanently for this daily case.
- Make the guess field prominent again.
- Show the next puzzle button only after the clue reveal has been read or dismissed.

## 10.4 Wrong guess state

- Do not use a red error screen.
- Keep the entered guess visible so the player can edit it.
- Message: “Not quite. The file has more to reveal.”
- Do not remove progress.

## 10.5 Solved screen

- Reveal the event title, date and place.
- Show a warm “Case solved” stamp.
- Display the event summary, key facts, source links and number of clues used.
- Give a spoiler-safe share result, e.g. “I solved today's Time Cabinet case with 3 clues.”
- Invite the player to discuss their theory or result in the Reddit comments. Avoid automatically posting spoilers on the player's behalf.

## 10.6 Returning player

- Restore the player's current progress from Redis.
- If the case is already solved, show the solved dossier immediately.
- Do not reset their progress on refresh or when they reopen the Reddit post.

---

# 11. Reddit community integration

Reddit is not just the place where the game is hosted. It is the community around the shared daily mystery.

## V1 integration

- One daily Interactive Post in the game's test subreddit.
- The same daily event and puzzle sequence for every user.
- The Reddit comment thread is the discussion space for theories, reactions and spoiler-safe comparisons.
- The post title is consistent and easy to recognise, e.g. **The Time Cabinet — Daily Case #001**.
- The post body fallback explains the game and where to play if the interactive view fails.
- Add a short comment prompt: “What is your theory? Keep spoilers hidden until you've solved it.”

## Not required for the first demo

- Global cross-subreddit leaderboards.
- User-generated historical events.
- Automated posting of user guesses.
- Snoovatar cosmetics or complex flair rewards.
- Multi-player live co-op.

A simple, lively Reddit discussion around one shared mystery is better than several unfinished social features.

---

# 12. Technical architecture

## 12.1 Locked stack

- **Platform:** Devvit Web + Reddit Interactive Posts.
- **Frontend:** React + TypeScript + Vite.
- **Backend:** Node.js server using the framework supplied by the current Devvit React template (Hono or Express, depending on the generated template).
- **Persistence:** Devvit Redis for daily case state and per-player progress.
- **Styling:** CSS variables and component CSS. Use Tailwind only if the generated template already includes it and it helps; do not add a styling framework just for its own sake.
- **Game logic:** pure TypeScript functions shared between client and server where practical.
- **Content:** version-controlled JSON/TypeScript event dossiers bundled with the app.
- **Assets:** local, licensed images and locally bundled fonts/audio.

No separate hosted website, Postgres service, external map service, paid AI API or external puzzle API is required for V1.

## 12.2 Devvit structure

Start with the official React template from <https://developers.reddit.com/new>.

Expected conceptual structure:

```text
src/
  client/
    components/
      ArchiveHeader.tsx
      CaseProgress.tsx
      PuzzleFrame.tsx
      ClueShelf.tsx
      GuessPanel.tsx
      SolvedDossier.tsx
    puzzles/
      LetterMixer.tsx
      Connections.tsx
      CipherWheel.tsx
      WhoAmI.tsx
      TimelineSort.tsx
      PixelReveal.tsx
      MapHunt.tsx
      CauseEffect.tsx
    screens/
      SplashScreen.tsx
      GameScreen.tsx
    styles/
      tokens.css
      global.css
  server/
    routes/
      init.ts
      solve.ts
      guess.ts
      hint.ts
    jobs/
      createDailyCase.ts
    services/
      dailyCaseService.ts
      progressService.ts
      answerService.ts
  shared/
    types.ts
    puzzleValidation.ts
    answerNormalization.ts
    seededRandom.ts
    eventValidation.ts
  content/
    events/
      apollo-11.json
      berlin-wall.json
      iphone-introduction.json
      ...
    assets/
      ...
  tests/
    answerNormalization.test.ts
    puzzleSelection.test.ts
    puzzleValidation.test.ts
    eventValidation.test.ts

devvit.json
README.md
```

Adapt file names to the generated Devvit template. Do not fight the template's build system or move files unnecessarily.

## 12.3 Runtime flow

```text
Reddit daily Interactive Post
        |
        v
React client inside Reddit webview
        |
        | GET /api/init
        v
Devvit server reads trusted post context
        |
        +--> daily case from Redis / bundled event content
        +--> player progress from Redis
        |
        v
Client renders the next frozen puzzle
        |
        | POST /api/solve
        v
Server validates the puzzle result
        |
        +--> saves completed puzzle
        +--> unlocks one clue
        |
        v
Client displays clue and enables event guess
        |
        | POST /api/guess
        v
Server normalizes and validates accepted answer
        |
        +--> wrong: preserve progress
        +--> correct: save solved state and reveal dossier
```

## 12.4 Devvit-specific decisions

- Use a **custom Interactive Post**. The game must run inside a Reddit post.
- Use a splash/entry screen and an expanded game view if the selected template supports those entry points cleanly.
- Create the daily post with `reddit.submitCustomPost()` from a server endpoint or scheduled task.
- Keep `postData` small (the current Interactive Posts documentation describes a 2 KB limit). Store larger event and progress data in Redis.
- Use the authenticated request context for player identity. Do not trust a client-supplied user ID.
- Enable only the Devvit capabilities required by V1, especially Reddit and Redis.
- Redis data is scoped to an app installation/subreddit. A global leaderboard spanning unrelated subreddit installations would need a separate architecture and is out of scope.
- Test real Reddit post context, Redis and authentication in a subreddit playtest. A standalone local browser view is not sufficient to validate Reddit integration.

## 12.5 Daily post creation

For the hackathon MVP:

1. Implement an idempotent server function that creates today's post only once.
2. Add a moderator-only menu action to create or repair today's case manually.
3. Add a scheduled daily job once the manual path is reliable.
4. Store the `dailyDate`, `eventId` and frozen puzzle sequence in Redis. Put only a small identifier in the post data.
5. If the scheduler fails, the moderator action must allow the demo to recover without manually editing Redis.

The daily job must not create duplicate posts if it is retried.

---

# 13. Data model

The exact TypeScript types can be adjusted to the template, but the concepts and required fields are locked.

## 13.1 Event dossier

```ts
export type ClueCategory =
  | "location"
  | "people"
  | "time"
  | "object"
  | "circumstances"
  | "impact";

export type PuzzleType =
  | "letter-mixer"
  | "connections"
  | "cipher-wheel"
  | "who-am-i"
  | "timeline-sort"
  | "pixel-reveal"
  | "map-hunt"
  | "cause-effect";

export type RevealTier = 1 | 2 | 3;

export interface SourceReference {
  id: string;
  title: string;
  publisher: string;
  url: string;
  accessedOn: string;
  notes?: string;
}

export interface PuzzleOption {
  type: PuzzleType;
  payload: Record<string, unknown>;
}

export interface HistoricalClue {
  id: string;
  category: ClueCategory;
  revealTier: RevealTier;
  revealText: string;
  sourceIds: string[];
  puzzleOptions: PuzzleOption[];
}

export interface HistoricalEvent {
  id: string;
  title: string;
  eventDate: { month: number; day: number; year: number };
  themes: string[];
  summary: string;
  keyFacts: string[];
  acceptedAnswers: string[];
  clues: HistoricalClue[];
  sources: SourceReference[];
  assets: Array<{
    id: string;
    path: string;
    creator: string;
    license: string;
    sourceUrl: string;
    attributionText?: string;
  }>;
  editorialStatus: "draft" | "verified" | "scheduled";
}
```

## 13.2 Frozen daily case

```ts
export interface DailyCase {
  dailyDate: string; // YYYY-MM-DD, UTC
  eventId: string;
  sequence: Array<{
    index: number;
    clueId: string;
    puzzleType: PuzzleType;
    puzzleSeed: string;
  }>;
  generatorVersion: number;
  createdAt: string;
}
```

## 13.3 Player progress

```ts
export interface PlayerDailyProgress {
  dailyDate: string;
  userId: string; // obtained from trusted Devvit request context
  completedPuzzleIndexes: number[];
  unlockedClueIds: string[];
  guessesCount: number;
  hintsUsed: number;
  solved: boolean;
  solvedAt?: string;
  solvedAfterClueCount?: number;
  updatedAt: string;
}
```

Do not store birthdays, private profile data or unnecessary personal information in V1.

## 13.4 Redis key pattern

Use namespaced, versioned keys to make future changes safer:

```text
time-cabinet:v1:daily:{YYYY-MM-DD}
time-cabinet:v1:progress:{YYYY-MM-DD}:{userId}
time-cabinet:v1:daily-post:{YYYY-MM-DD}
```

Avoid broad key scans in player request paths. Read only the keys needed for the current daily case.

---

# 14. Core API contract

The route names can change, but the responsibilities must remain separate.

| Endpoint | Method | Responsibility |
|---|---|---|
| `/api/init` | GET | Return daily case, selected puzzle, unlocked clues and player's current state |
| `/api/solve` | POST | Validate current puzzle response and unlock its clue |
| `/api/guess` | POST | Validate an event guess and save a solved result if correct |
| `/api/hint` | POST | Return the authored hint and record its use |
| `/internal/daily/create` | POST | Create today's Interactive Post idempotently |
| `/internal/menu/create-daily` | POST | Moderator fallback to create today's post manually |

### Security and validation rules

- Never accept `userId` from the request body as authority; use the authenticated Devvit context.
- Never trust a client claim that a puzzle is solved. Validate the response on the server.
- Validate that the requested clue/puzzle belongs to today's frozen case.
- Do not return the canonical event answer before a successful guess.
- Limit request payloads to what the puzzle needs.
- Handle repeated solve/guess requests idempotently where possible.
- Provide friendly error messages; do not expose server stack traces to players.

---

# 15. Puzzle generation logic

## 15.1 Compatibility filtering

For each clue:

1. Read its `puzzleOptions`.
2. Remove options whose required data or assets are missing.
3. Remove puzzle templates already used in the current case, unless the remaining pool is empty.
4. Prefer templates that differ from the previous interaction type.
5. Choose from the remaining options with a seeded random function.
6. If no option remains, use a pre-authored fallback or reject the event dossier before scheduling.

## 15.2 Deterministic seed

Use a stable seed such as:

```text
seed = `${dailyDate}:${eventId}:time-cabinet-v1`
```

The seeded selector must produce the same result on every server instance and after an app restart. Do not use `Math.random()` to generate a new sequence for every player.

## 15.3 Suggested sequence rules

- Choose 4–6 clues for a normal case, if the event supports them.
- Use at least 3 clue categories when possible.
- Start with a broad clue, then progress toward more identifying facts.
- Do not place two decisive clues back-to-back at the start.
- Avoid repeating the same puzzle template in one case.
- Do not reveal the canonical event title in a clue before the player has solved the case.

---

# 16. Scoring, streaks and retention

V1 should be calm and satisfying rather than competitive.

## V1

- Record case completion and number of clues used.
- Give one of the friendly result labels described earlier.
- Restore unfinished progress when the player returns.
- Show a simple “Today's case completed” state.

## After the hackathon

- Optional daily streak.
- Weekly archive of solved cases.
- Subreddit-level leaderboard if community feedback asks for it.
- Achievements for puzzle variety or consecutive discoveries.

Do not implement streak pressure, paid hints, energy systems, lives or punitive rankings in V1.

---

# 17. Test strategy and acceptance criteria

## 17.1 Puzzle tests

Each puzzle template needs:
- Correct-answer test.
- Incorrect-answer test.
- Empty/incomplete input test.
- Retry test.
- Mobile viewport test.
- Keyboard/accessibility test where applicable.
- Test proving the clue unlocks only after server validation.

## 17.2 Generator tests

- Same daily date + event ID always produces the same sequence.
- Two users opening the same daily post receive the same puzzle order.
- Different daily cases can produce different puzzle orders.
- The generator never selects a template missing required data.
- No unsupported image asset is selected.
- No clue is repeated in one case.
- The order progresses from broad toward more identifying evidence.

## 17.3 Player-flow tests

- New player opens today's case.
- Player solves first puzzle and receives first clue.
- Player guesses incorrectly; progress remains intact.
- Player solves another puzzle and sees a second clue.
- Player guesses correctly; final dossier appears.
- Player refreshes or reopens the post; progress remains.
- Already-solved player returns and sees the solved result.
- Moderator retries daily-post creation; no duplicate is created.

## 17.4 Definition of done for hackathon demo

The project is ready to submit only when:

- It runs inside a real Reddit Interactive Post using Devvit.
- A public demo subreddit and post are accessible to judges.
- One complete daily mystery is playable from beginning to end.
- At least six core puzzle templates are playable and validated; the two extension templates are included only if stable.
- At least seven verified event dossiers exist, with 10–14 preferred.
- Every puzzle completion reveals a useful clue.
- Players can guess after each clue.
- Correct answer reveals a sourced historical dossier.
- Refreshing the post does not erase progress.
- The UI is readable and works on desktop and mobile.
- There are no broken buttons, placeholder screens or unverified historical statements.
- The root `README.md` explains the game and how to play.
- The Devpost entry includes the app link, public test subreddit and a post running the game.

---

# 18. Development order and schedule

The hackathon submission deadline is **8 December 2026 at 6:00 p.m. Pacific Time**, which is **9 December 2026 at 04:00 in Burundi (UTC+2)**. Aim to submit at least a day early; do not plan to upload at the final minute.

## Phase 1 — Foundation

- Create the Devvit React project.
- Run the official starter post in the test subreddit.
- Confirm the current template's Node version and build commands.
- Build the visual shell: splash, header, puzzle card, clue shelf and guess panel.
- Define TypeScript types for events, clues, puzzle payloads and player progress.

## Phase 2 — Core gameplay

Implement in this order:

1. Letter Mixer
2. Connections
3. Cipher Wheel
4. Who Am I?
5. Timeline Sort
6. Pixel Reveal

Do not start the next template until the current one has a working success state, error state and mobile layout.

## Phase 3 — Daily engine

- Build event dossier validation.
- Build deterministic puzzle selection.
- Freeze one daily case.
- Add server-side puzzle validation.
- Add answer normalization and aliases.
- Store progress in Redis.

## Phase 4 — Content and Reddit integration

- Author 7–10 verified event dossiers.
- Create a moderator menu action to make the daily post.
- Add the scheduled daily post job.
- Make the Reddit comment prompt and post fallback clear.
- Test the same case with two different Reddit accounts.

## Phase 5 — Polish and submission

- Refine cosy visuals and readable type.
- Test desktop and mobile.
- Fix all broken states and loading failures.
- Prepare the English README and Devpost description.
- Record a demo video under one minute, showing the actual game working inside Reddit.
- Submit before the deadline.

### Scope protection

If time becomes tight, cut features in this order:

1. Map Hunt and Cause & Effect extensions.
2. Streaks and leaderboards.
3. Extra decorative animations and sounds.
4. Extra event packs beyond the minimum.

**Never cut:** the working Reddit Interactive Post, the complete daily investigation loop, clue unlocks, guesses, answer reveal, persistence and a polished demo case.

---

# 19. Hackathon requirements checklist

The official challenge asks for a new daily game built on Reddit's Developer Platform using Interactive Posts. Devvit Web is the intended web-technology route.

Before submission, confirm all of the following against the official rules:

- [ ] App is built using Reddit's Developer Platform and runs inside Reddit.
- [ ] App listing link is included (`developers.reddit.com/apps/{app-name}`).
- [ ] Public test subreddit and a post running the game are provided.
- [ ] Test subreddit has fewer than 200 members, as requested in the rules.
- [ ] Root `README.md` explains the game and how to play.
- [ ] Devpost text description explains features and functionality.
- [ ] All submission materials are in English or include English translations.
- [ ] Any demo video is under one minute and publicly accessible if included.
- [ ] Images, fonts, icons, sounds and other media have compatible rights and attribution.
- [ ] App is available for judges to test through the judging period.
- [ ] Do not submit the app for broad publication review just for the hackathon; the event page says the app can remain private and recommends uploading and playtesting rather than publishing.

### Judging criteria to design for

The four equally weighted criteria are:

1. **Delightful UX** — a clear, inviting, satisfying experience.
2. **Polish** — stable, complete and close to publishable.
3. **Reddity** — an identity and community experience that feels native to Reddit.
4. **Daily Content** — fresh daily cases that encourage return visits.

Our product choices directly support these: cosy archive identity, one shared daily mystery, Reddit discussion, reliable sourced event packs and a short repeatable loop.

---

# 20. Risks and mitigations

| Risk | Why it matters | Decision / mitigation |
|---|---|---|
| Weak or ambiguous historical answer | The player may be marked wrong despite a valid guess | Curated aliases, normalization tests and human review |
| Random puzzle has missing data | A daily case may become unplayable | Compatibility filtering and dossier validation before scheduling |
| Image usage rights unclear | Could disqualify or create a rights issue | Original art or verified public-domain/licensed assets with metadata |
| Puzzle sequence too long | Daily game feels like homework | 4–6 clues as normal target; guess is always available |
| Same puzzle repeated | The daily game feels predictable | Avoid template repeats within one case |
| Per-user random sequences | Reddit discussion becomes unfair/confusing | Freeze one seeded sequence per daily post |
| Devvit/Reddit integration fails | A standalone web demo does not meet the challenge | Playtest inside a real subreddit early, not at the end |
| History is trivialized | Cosy tone can feel inappropriate for tragic events | Prefer neutral/constructive events in V1; use respectful editorial rules |
| Feature creep | Deadline and quality are at risk | Six core templates first; extensions only after complete loop |

---

# 21. Out of scope for V1

These ideas are deliberately postponed:

- Birthday-based personalised event reveals.
- User profiles with personal data.
- AI-generated live puzzle content or AI-judged guesses.
- A global leaderboard shared across subreddit installations.
- Multiplayer co-op or real-time player-versus-player competition.
- User-created events and community-authored puzzle packs.
- Paid hints or monetisation.
- A separate public website or mobile app.
- Full translation/localisation.

They can be reconsidered after the core game is playable and user feedback justifies them.

---

# 22. First implementation checklist

Start here. Do not begin by building all eight puzzles at once.

1. [ ] Create the Devvit React app from the official developer portal.
2. [ ] Run the starter interactive post in a public test subreddit.
3. [ ] Create `ClueCategory`, `PuzzleType`, `HistoricalEvent`, `HistoricalClue`, `DailyCase` and `PlayerDailyProgress` types.
4. [ ] Add one verified Apollo 11 event dossier to the content folder.
5. [ ] Build the cosy layout shell with a responsive puzzle card, clue shelf and always-available guess panel.
6. [ ] Implement Letter Mixer end-to-end, including server validation and clue unlock.
7. [ ] Implement answer normalization and accepted aliases.
8. [ ] Implement deterministic puzzle selection from compatible options.
9. [ ] Add Redis persistence and test refresh/resume inside Reddit.
10. [ ] Add the remaining core puzzle templates one by one.
11. [ ] Add more verified event dossiers.
12. [ ] Add daily post creation and the moderator fallback.
13. [ ] Complete the hackathon demo and submission checklist.

**First milestone:** one real Reddit post, one complete historical event, one working puzzle, one unlocked clue, one guess and one final reveal. Once that works, expand the library.

---

# 23. Reference links

## Hackathon

- [Reddit Game of the Day Hackathon — overview](https://redditgameofday2026.devpost.com/)
- [Official hackathon rules](https://redditgameofday2026.devpost.com/rules)

## Devvit

- [Devvit Web overview](https://developers.reddit.com/docs/capabilities/devvit-web/devvit_web_overview)
- [App quickstart](https://developers.reddit.com/docs/quickstart)
- [Interactive Posts overview](https://developers.reddit.com/docs/capabilities/interactive-posts/interactive_posts_overview)
- [Creating a Custom Post](https://developers.reddit.com/docs/capabilities/creating_custom_post)
- [Devvit Redis](https://developers.reddit.com/docs/capabilities/server/redis)
- [Scheduler](https://developers.reddit.com/docs/capabilities/server/scheduler)
- [Reddit API overview](https://developers.reddit.com/docs/capabilities/server/reddit-api)

## Historical sources used in the example and seed list

- [NASA NSSDCA — Apollo 11](https://nssdc.gsfc.nasa.gov/planetary/lunar/apollo11info.html)
- [NASA — Apollo 11 mission overview](https://www.nasa.gov/missions/apollo/apollo-11/apollo-11-mission-overview/)
- [Berlin.de — Opening and fall of the Berlin Wall](https://www.berlin.de/en/history/8482274-8619314-opening-and-fall-of-the-berlin-wall.en.html)
- [Apple Newsroom — iPhone introduction, 9 January 2007](https://www.apple.com/newsroom/2007/01/09Apple-Reinvents-the-Phone-with-iPhone/)
- [Smithsonian National Air and Space Museum — 1903 Wright Flyer](https://www.si.edu/object/nasm_A19610048000)
- [NASA — Dawn of the Space Age / Sputnik 1](https://www.nasa.gov/history/dawn-of-the-space-age/)
- [CERN — A short history of the Web](https://home.cern/science/computing/the-birth-of-the-web/short-history-web)

---

# Final product statement

**The Time Cabinet is a daily historical mystery built around a reusable puzzle library.** Each event is prepared as a verified dossier of facts. Each fact belongs to a clue category and can be delivered through one of several compatible puzzle templates. A seeded generator chooses the daily sequence once for the whole community. Players solve at their own pace, collect clues, guess whenever they are ready and finish by discovering the true story.

The first goal is not to build the biggest puzzle collection. It is to make one complete daily mystery feel so clear, satisfying and polished that a player wants to come back tomorrow.
