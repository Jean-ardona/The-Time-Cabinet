# Hackathon Registration, Eligibility & Submission Checklist

**Project:** The Time Cabinet  
**Hackathon:** Reddit's Game of the Day Hackathon (2026)  
**Task reference:** `TC-001`  
**Last updated:** 2026-11-16

---

## 1. Registration & Eligibility Status (`TC-001`)

- [x] **Devpost registration:** Confirmed by the project owner on 2026-11-16 — joined <https://redditgameofday2026.devpost.com/> as an **Individual** entrant (Devpost's individual participant directory is login-gated; public page checked live on 2026-11-16 with participant count incremented from 1,434 to 1,435).
- [x] **Eligibility review:** Confirmed by the entrant on 2026-11-16 against Section 3 of the Official Rules (at least legal age of majority in country of residence; not resident in a US/OFAC-restricted or local-law-prohibited jurisdiction; not a Sponsor/Administrator employee, agent, judge, affiliate, or household/immediate-family member; not a prior Reddit Hackathon winning project; no Sponsor financial/preferential support).
- [x] **Entrant identity:** Confirmed on 2026-11-16 as **Individual** (solo entry under a single personal Devpost account; no Team/Organization Representative appointment required).

> Do not store passwords, session cookies, OAuth tokens, or private account details in this file or repository.

---

## 2. Official Schedule & Deadlines

Verified against Section 1 of the live Official Rules on 2026-11-16:

| Milestone | Pacific Time (Official) | UTC | Burundi Time (CAT, UTC+2) |
|---|---|---|---|
| **Submission & Feedback Period Opens** | Wed, 11 Nov 2026, 12:00 p.m. PST | Wed, 11 Nov 2026, 20:00 UTC | Wed, 11 Nov 2026, 22:00 CAT |
| **Internal Submission Target (24h early)** | Mon, 7 Dec 2026, 6:00 p.m. PST | Tue, 8 Dec 2026, 02:00 UTC | **Tue, 8 Dec 2026, 04:00 CAT** |
| **Official Submission Deadline** | **Tue, 8 Dec 2026, 6:00 p.m. PST** | **Wed, 9 Dec 2026, 02:00 UTC** | **Wed, 9 Dec 2026, 04:00 CAT** |
| **Judging Period Opens** | Wed, 9 Dec 2026, 12:00 a.m. PST | Wed, 9 Dec 2026, 08:00 UTC | Wed, 9 Dec 2026, 10:00 CAT |
| **Judging Period Closes** | Wed, 16 Dec 2026, 6:00 p.m. PST | Thu, 17 Dec 2026, 02:00 UTC | Thu, 17 Dec 2026, 04:00 CAT |
| **Winners Announced (approx.)** | Thu, 17 Dec 2026, 3:00 p.m. PST | Thu, 17 Dec 2026, 23:00 UTC | Fri, 18 Dec 2026, 01:00 CAT |

*Note:* Devpost's overview header may display the deadline in EST (`Dec 8, 2026 @ 9:00pm EST`), which is the exact same instant as **8 December 2026, 6:00 p.m. Pacific Time / 9 December 2026, 04:00 Burundi time**.

---

## 3. Official Hackathon & Platform Links

- **Hackathon overview:** <https://redditgameofday2026.devpost.com/>
- **Official rules:** <https://redditgameofday2026.devpost.com/rules>
- **Manage Devpost submissions:** <https://devpost.com/submit-to/31644-reddit-s-game-of-the-day-hackathon/manage/submissions>
- **Reddit Developer Platform:** <https://developers.reddit.com/>
- **Create a Devvit app:** <https://developers.reddit.com/new>
- **Devvit Quickstart:** <https://developers.reddit.com/docs/quickstart>
- **Devvit Web overview:** <https://developers.reddit.com/docs/capabilities/devvit-web/devvit_web_overview>
- **Devvit Rules:** <https://developers.reddit.com/docs/devvit_rules>
- **Developer Terms:** <https://redditinc.com/policies/developer-terms>
- **Optional feedback survey (Most Valuable Feedback bonus):** <https://forms.gle/dW45UgK6SctevE756>

---

## 4. Required Submission Links (Populate as Tasks Complete)

| Item | Requirement | Recorded Value | Roadmap Task |
|---|---|---|---|
| **App listing URL** | `https://developers.reddit.com/apps/{app-name}` (created on `devvit upload`; keep app **private**, do **not** submit for broad App Review publishing during the hackathon) | _TBD_ | `TC-005`, `TC-076` |
| **Public test subreddit URL** | Public subreddit moderated by app owner, kept **under 200 members/subscribers** through judging | _TBD_ | `TC-003`, `TC-063` |
| **Public demo post URL** | Direct link to a playable Reddit Interactive Post in the public test subreddit, available free without restriction until judging ends | _TBD_ | `TC-059`, `TC-063` |
| **Public repository URL** *(optional)* | GitHub repo containing root English `README.md` | `https://github.com/Jean-ardona/The-Time-Cabinet` *(confirm visibility before submitting)* | `TC-009`, `TC-075` |
| **Demo video URL** *(optional)* | Public video `< 1 minute` showing the live game running on Reddit (YouTube, Vimeo, Facebook Video, or Youku) | _TBD_ | `TC-078` |

---

## 5. Submission Compliance Checklist (Tracked Through `TC-079`)

- [ ] Built on Reddit's Developer Platform using **Devvit Web** and runs natively inside a **Reddit Interactive Post** (compliant with Devvit Rules).
- [ ] Uploaded and playtested via Devvit, kept private (not submitted for broad App Review publishing for the hackathon).
- [ ] Root `README.md` in English describing the game and how to play (`TC-075`).
- [ ] Devpost text description in English explaining features, functionality, and clear testing instructions (`TC-077`).
- [ ] Unique app listing link included (`developers.reddit.com/apps/{app-name}`) (`TC-076`).
- [ ] Public test subreddit link (`< 200` members) and live playable demo post link included (`TC-063`, `TC-077`).
- [ ] All code, text, images, fonts, icons, and optional audio are original or carry verified compatible licences and attribution (`TC-017`, `TC-049`).
- [ ] Optional demo video is under 60 seconds, shows the real game on Reddit, and is publicly visible on an accepted host (`TC-078`).
- [ ] Project and public demo post remain freely accessible through the end of the Judging Period (16 December 2026, 6:00 p.m. PT / 17 December 2026, 04:00 Burundi time) (`TC-080`).

---

## 6. Judging Criteria Reference

- **Stage 1 (Pass/Fail):** Baseline viability — fits the daily game theme and uses Reddit's Developer Platform / Devvit SDKs.
- **Stage 2 (Equally Weighted):**
  1. **Delightful UX** — inviting, intuitive layout and theme; easy and enjoyable to play.
  2. **Polish** — stable, self-explanatory inside example posts, compliant with Devvit Rules, close to publishable quality.
  3. **Reddit-y** — distinct identity built around Reddit community participation and discussion.
  4. **Daily Content** — recurring fresh daily mysteries and well-calibrated variety that bring players back.
