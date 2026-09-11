# TaskFlow — Live Assessment for Test / QA Engineers

**Use this file instead of the main README engineer path.**  
Same app under test. Different job and pass bar.

| | Full Stack engineer | Test / QA engineer |
|---|---|---|
| Goal | Find bugs, propose fixes, implement highest-priority code changes | Find what would hurt users; produce solid bug reports + a risk-based test plan |
| Pass on | Investigation + code quality | Investigation quality, severity judgment, clear reports |
| Do **not** | — | Treat “implement the Java/React fixes” as the bar |

---

## Timebox (60–75 minutes)

1. **Brief (5m)** — You’re QA on TaskFlow before a release. Find what would hurt users.
2. **Explore (25–35m)** — UI + seeded logins + a few API calls (`curl` / Postman / browser network tab).
3. **Artefacts (20m)** — At least **3** solid bugs in bug-report format; a short risk-based test plan (what you’d cover vs skip overnight).
4. **Optional stretch (10m)** — One smoke-test idea or sketch (API or UI). Nice-to-have.
5. **Debrief (10m)** — Priority order and release go / no-go with the interviewer.

---

## Setup

Follow the main repo README to bring TaskFlow up (Docker / Codespaces / Cursor as documented there).

You do **not** need to fix production code to pass. You may skim code to understand behaviour; grading is on QA artefacts, not a merge-ready PR.

---

## What to produce

### Bug reports (minimum 3)

For each bug, write:

- **Title**
- **Severity** (blocker / major / minor / cosmetic) and **why**
- **Steps to reproduce** (exact)
- **Expected** vs **Actual**
- **Evidence** (screenshot note, response body, console/network observation)
- **Who is hurt** (end user, admin, data integrity, etc.)

Put them in `FINDINGS-QA.md` (create it) or a shared doc the interviewer names. Do not only say “it doesn’t work.”

### Risk-based test plan (1 page max)

- What you would cover before release overnight
- What you would **skip** and why
- Highest risks if we ship as-is
- Suggested go / no-go

### Optional stretch

One concrete smoke check (e.g. happy-path API assertion or UI flow outline). Sketch is enough; full automation is bonus, not required.

---

## Interviewer rubric (do not show candidates)

**Pass**

- Reproduces clearly with steps
- Severity judgment matches impact
- Reports are usable by an engineer without a live replay
- Calm under ambiguity; prioritises user/business risk

**Fail**

- “It doesn’t work” with no steps
- Only theorises the testing pyramid with no product exploration
- Severity all “critical” or all “low” with no reasoning
- Ignores API/data issues and only clicks randomly

**Probe ideas**

- “If we can only fix one bug before Friday, which and why?”
- “What would you automate first in week 1 on this squad?”
- “Release tonight with these findings — go or no-go?”

---

## Notes for hiring managers

- Same TaskFlow environment as Full Stack; schedule Codespace/Cursor warm-up the same way.
- Do **not** grade QA candidates on implementing Spring/React fixes.
- Link this path from the master live-assessments guidance Doc.
