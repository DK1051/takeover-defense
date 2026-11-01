# Final gate: H99 (2026-11-01)

This is the last check before the Nov 5 hard stop. A reviewer read every claim in the repo and project READMEs of the five repos (not the fixtures README in td-2-soc) and compared it with the evidence in those repos: verify reports, test results quoted in them, class transcripts and CAVEATS. The reviewer was the `redteam` subagent, running Claude Fable 5.1. It gave each project a verdict:
- **ship**: the claims match the evidence
- **fix first**: small wording or status fixes are needed before a hiring manager reads it
- **cut**: the project is moved to after Nov 5

Fable answered all five calls; none were refused or redirected. Where the director (Claude Opus 5.5, the main session) changed or added something, it is marked "director".

Decisions Eojin made at the start of this session:
- **Deferred counts as CUT.** T1-S04, T2-S03, T3-S04 and T4-S03 (the four AI projects' real evaluations) and their classes T1-C2, T2-C2, T3-C2 and T4-C2 count as CUT.
- **One-time exception.** H99 may read all five repos in one session.

**Status words.** `Verified` means a verify report shows PASS on every acceptance criterion in scope, with no open NEEDS-EOJIN. NEEDS-EOJIN marks a check only Eojin can do. Every verify report in the four tracks still has at least one open NEEDS-EOJIN item, nearly always "record the credit balance in `COSTS.md`". So **no project is `Verified` today.** 1H, 2H and 3H are one small step away; see the judgement calls at the end.

## The twelve projects

| Project | Verdict | Top issue | Fix | Where (repo/path) | Who |
|---|---|---|---|---|---|
| 1E Front Desk Casebook | fix first | READMEs say the tickets are solved and the KB (knowledge-base) articles exist. Only the scaffold exists, and Eojin's half has not started (evidence: `td-1-helpdesk/docs/verify/T1-S01.md` AC3 NEEDS-EOJIN) | Describe it as ten ticket scaffolds and KB templates; status `In progress` | td-1-helpdesk/README.md l.15 | Claude session (td-1) |
| 1H Verified Reset Service | ship | Root README says it alerts on "any MFA change" within 24 h. It only sees requests made through the service or reported to it (evidence: `td-1-helpdesk/docs/verify/T1-S03.md`, 93 passed; 1H README l.170) | Narrow that sentence; set status `Built` | td-1-helpdesk/README.md l.16 | Claude session (td-1) |
| 1A Helpdesk Bot Stress Test | cut | Present tense implies the evaluation ran; no cases and no model runs exist (evidence: `td-1-helpdesk/docs/verify/T1-S04.md` AC1, AC5–7 DEFERRED) | Status `Cut`; future-tense wording | td-1-helpdesk/README.md l.17; 1a-bot-stress-test/README.md l.5 | Claude session (td-1) |
| 2E Blind Hunt | fix first | Status says it "waits for step 8", but step 8 was done on Oct 23. Sealing the answer key has no verify record (evidence: `td-2-soc/docs/verify/T2-S01.md` AC3/6/7/12 NEEDS-EOJIN; `td-2-soc/docs/CAVEATS.md` 2026-10-23) | Status `In progress`; add a step-8 addendum to T2-S01.md | td-2-soc/README.md l.19; docs/verify/T2-S01.md | Claude session (td-2) |
| 2H Takeover Detection Pack | fix first | Track README still says `Planned`, although it was built and passed AC1–AC8 (evidence: `td-2-soc/docs/verify/T2-S02.md`) | Status `Built` (or `Verified` once AC9 closes) | td-2-soc/README.md l.20 | Claude session (td-2) + Eojin (AC9) |
| 2A Injection-Proof Triage | cut | README says the evaluation is "scheduled after his CompTIA A+ exam" (evidence: `td-2-soc/docs/verify/T2-S03.md` AC2/4/5/6/8/9 DEFERRED) | Status `Cut`; "no evaluation was run" | td-2-soc/README.md l.21, l.34; 2a-triage/README.md l.3 | Claude session (td-2) |
| 3E Anti-Takeover Tenant | ship | "Scaffolded" is not an allowed status word; the tenant is not configured yet (evidence: `td-3-iam/docs/verify/T3-S01.md` AC1–9, 11 PASS, AC10 NEEDS-EOJIN) | Status `In progress` (director: Eojin is still configuring); describe the report as a template | td-3-iam/README.md l.15 | Claude session (td-3) |
| 3H Lifecycle | fix first | README says "Eojin can rebuild and explain it"; the class transcript shows 5/20 (evidence: `td-3-iam/docs/learning/T3-C1.md`; `docs/verify/T3-C1.md`) | Honest process wording; "class held (T3-C1)" | td-3-iam/README.md l.35, l.9, l.16 | Claude session (td-3) |
| 3A Agent Passport | cut | README says "Tested against 30 malicious requests"; no cases and no runs exist (evidence: `td-3-iam/docs/verify/T3-S04.md` AC7/AC9 DEFERRED) | Status `Cut`; "harness built, evaluation not run" | td-3-iam/README.md l.17; 3a-agent-passport/README.md l.3–5 | Claude session (td-3) |
| 4E Canada-Only Landing Zone | fix first | "Built (Claude's work verified)" reads as `Verified`; nothing has been applied to Azure yet (evidence: `td-4-cloud/docs/verify/T4-S01.md` AC1–8 PASS, AC9–10 NEEDS-EOJIN) | Status `Built`; "wrote and tested the configuration; applying it is pending" | td-4-cloud/README.md l.3, l.11, l.15 | Claude session (td-4) |
| 4H Secretless Deploy | fix first | Same status wording. Fix round 1 was re-checked only by the director (evidence: `td-4-cloud/docs/verify/T4-S02.md` AC1–8 PASS, AC9 NEEDS-EOJIN) | Status `Built`; add a Limits bullet for check (a) failing safe | td-4-cloud/README.md l.12; 4h-secretless-deploy/README.md | Claude session (td-4) |
| 4A Containment Runbook Copilot | cut | README says plans "will be scored" and refers to a T4-C2 manual grade that will not happen (evidence: `td-4-cloud/docs/verify/T4-S03.md` AC4–6 N/A deferred) | Status `Cut`; remove the T4-C2 references | td-4-cloud/README.md l.13, l.26; 4a-containment-copilot/README.md l.4, 17, 38, 45, 50 | Claude session (td-4) |

Totals: 2 ship, 6 fix first, 4 cut. The two "ship" rows still carry small wording items in the per-repo sections; they can go in the same short sessions.

How verdicts were mapped (director): the table uses each reviewer's per-project verdict line. 1E is fix first, not ship, because its top issue is HIGH: the root README says the tickets are solved. 3E's issues are all MEDIUM or LOW. Where a reviewer's summary sentence said "ships" for a fix-first project, the per-project line wins.

---

## Hub (takeover-defense)
Fable's verdict: **fix first**. The hub-side fixes are made in this PR.

**Issues, ranked**
1. HIGH: the status table and paragraph are stale ("as of Oct 22", D0 merges only). This was flagged in `docs/CAVEATS.md` (H01 line). **Done in this PR.**
2. HIGH: 1A/2A/3A/4A read `Planned`. **Done:** `Cut`.
3. HIGH: the class-transcript claims (README "How AI was used" and "How to verify") say transcripts exist for every project; only T3-C1 exists. **Done:** softened.
4. MEDIUM: 3E and 4E use words outside the allowed list (CAVEATS H01 line, `needs Eojin: yes`). **Done:** gate words used.
5. MEDIUM: "one branch and one pull request per session (`t1-s02-…`)". Cloud sessions used `claude/…` branches (CAVEATS H01 branch line). **Done:** softened.
6. MEDIUM: "`COSTS.md` logs the AI credit spent per session". Most lines are still placeholders. **Done:** softened. **Eojin:** fill the balances.
7. MEDIUM: none of the five source URLs has been opened since H01; their hosts are blocked from cloud sessions (CAVEATS H01 line). **Done:** one `TODO(verify)` note added. **Eojin:** open each link in a browser.
8. LOW: `TODO: LinkedIn URL` in the Contact section. **Eojin:** fill it in or delete the section.
9. LOW: "blunt design reviews before each AI build". H00 and H01 had no redteam review. **Done:** "where the brief called for one".
10. LOW: `docs/STORY.md` cites a Reuters article but links carriermanagement.com. Not changed. **Eojin:** check the link and name the site that published it.

**Claims to soften (hub; all changed in this PR)**

| File | Quoted line | Changed to (summary) | Evidence |
|---|---|---|---|
| README.md | "This portfolio is twelve small projects built around one real attack" … "The projects show how…" | Twelve planned projects: five built, three scaffolds with Eojin's part in progress, four AI projects cut after their frameworks were built | Gate table above |
| README.md | "**In progress (as of Oct 22, 2026).** Merged so far: H00 …" | Status as of Nov 1, 2026 | Track run sheets |
| README.md | "writing every attack script and injection string used in testing" | Written for the AI projects, which were not run before Nov 5 | T1-S04, T2-S03, T4-S03 verify reports |
| README.md | "sitting the "class" sessions where I explain each project back and get graded" | One class held so far (T3-C1) | `td-3-iam/docs/learning/T3-C1.md` |
| README.md | "I can explain and rebuild every piece — the class transcripts are where I prove it" | The transcripts record honestly how far I can explain it; one so far | same |
| README.md | "my answers to ten "why" questions per project, graded honestly, plus one live code change I drove" | One transcript so far (T3-C1) | same |
| README.md | "one branch and one pull request per session (`t1-s02-…`, `h01-…`)" | One PR per session; cloud sessions used `claude/…` branches | `docs/CAVEATS.md` H01 branch line |
| README.md | "`COSTS.md` logs the AI credit spent per session" | Adds "where I recorded the balance; some lines are still placeholders" | `COSTS.md` |
| README.md | "blunt design reviews before each AI build" | "where the brief called for one" | `docs/verify/H00.md`, `H01.md` |
| docs/STORY.md | "# The story: one attack chain, twelve defences" | "twelve planned defences" | Gate table |
| docs/STORY.md | "**1A** runs the same kind of scripted calls…" | "was built to run… (cut: not evaluated before Nov 5)" | `td-1-helpdesk/docs/verify/T1-S04.md` |
| docs/STORY.md | "**1H** raises an alert for any MFA-method change within 24 hours of a reset" | MFA requests made through the service, or reported to it, within 24 hours of a reset it completed | `td-1-helpdesk/1h-verified-reset/README.md` l.17, l.170 |
| docs/STORY.md | "**2A** is an AI triage assistant that must not be fooled…" | "was built to test…; cut" | `td-2-soc/docs/verify/T2-S03.md` |
| docs/STORY.md | "**3A** makes sure an AI assistant…" | "was built so that…; cut, not evaluated" | `td-3-iam/docs/verify/T3-S04.md` |
| docs/STORY.md | "**4A** drafts a containment checklist … scored against my answer keys" | "was built to draft…; cut, no plans scored" | `td-4-cloud/docs/verify/T4-S03.md` |
| docs/STORY.md (verifier) | "a temporary password that dies after 60 minutes" | "a temporary password that a maintenance job rotates after 60 minutes (the job is not scheduled yet)" | `td-1-helpdesk/1h-verified-reset/README.md` l.16, Limits l.166 |
| docs/STORY.md (director) | "**2E** is me hunting that activity…" | "is my hunt for that activity… (data sealed; my hunt is still to do)" | `td-2-soc/docs/verify/T2-S01.md` AC3 NEEDS-EOJIN |
| docs/STORY.md (director) | "**3E** configures the identity tenant…" | adds "I am still configuring it" | `td-3-iam/docs/verify/T3-S01.md`; 3E README Results |
| docs/STORY.md (director) | "**4E** locks the Azure subscription…" | adds "(written and tested; not yet applied to Azure)" | `td-4-cloud/docs/verify/T4-S01.md` AC9 |

Checked and kept, because the evidence supports it:
- STORY.md "ten practice tickets, four of them exactly this call" (`td-1-helpdesk/1e-front-desk-casebook/README.md` l.23)

## Track 1: td-1-helpdesk
Fable's verdict: **fix first** (wording and status words only). 1H ships, 1E ships as a scaffold, 1A is cut.

**Issues, ranked**
1. HIGH: the status words break the rule. README l.17: 1A shows `In progress`, should be `Cut`. README l.16: 1H shows `In progress`, should be `Built`. `1h-verified-reset/README.md` has no status line. `1a-bot-stress-test/README.md` l.5 never says `Cut`.
2. HIGH: README l.21 and l.27 promise class transcripts ("transcript published", `docs/learning/<session>.md`). None exist: T1-C1 was not held and T1-C2 is cut.
3. HIGH: README l.15 says the tickets are "that I solve myself" and the KB articles exist. Nothing is solved yet (`docs/verify/T1-S01.md` AC3; 1E README l.50).
4. MEDIUM: README l.28, the COSTS claim. Every verify report has COSTS as NEEDS-EOJIN.
5. MEDIUM: README l.5 quotes AL26-010 without the live page having been re-checked (`docs/CAVEATS.md` T1-S01 line).
6. MEDIUM: the 1A README is in present tense ("This project finds out", "It reports four things", l.11, l.16). Root l.17 says "cost per run"; the renderer shows cost per model (`docs/verify/T1-S04.md` V6).
7. MEDIUM: root l.16 says 1H "alerts on any MFA change within 24 hours"; 1H README l.170 limits it to the service's own resets.
8. LOW: l.30 "Running the code (once it exists)" is stale. `1h-verified-reset/README.md` l.142 "he reviews the code and explains it back": no class has been held. `docs/verify/T1-S02.md` nits 12–17 were never recorded item by item, so don't claim every review comment was answered.

**Claims to soften (track-side; fix in a td-1 session)**

| File | Quoted line | Replace with | Evidence |
|---|---|---|---|
| README.md l.15 | "ten realistic helpdesk tickets … that I solve myself, and knowledge-base articles in English and Korean" | "ten ticket scaffolds I will solve myself, and knowledge-base templates (articles to follow)" | `docs/verify/T1-S01.md` AC3 |
| README.md l.16 | "alerts on any MFA change within 24 hours of a reset" | "alerts on MFA requests made through the service, or reported to it, within 24 hours of a reset it completed" | 1H README l.170 |
| README.md l.16 | "Tested against the four social-engineering tickets" | "Tested against replay cases built from the four tickets' pressure types (transcripts still to be written)" | 1H README l.146 |
| README.md l.17 | "run against 40 attack scripts … Scored on … with cost per run" | "designed to run against … and score …; the evaluation is cut (after Nov 5) and no results exist" | `docs/verify/T1-S04.md` AC5–7 |
| README.md l.17 status | "In progress (T1-S04: framework built; evaluation deferred)" | "Cut (framework built, T1-S04; evaluation moved past Nov 5, 2026)" | Eojin's decision |
| README.md l.21 | "sit two 'class' sessions … graded honestly, transcript published" | "plan to sit class sessions … none held yet" | no transcript in `docs/learning/` |
| README.md l.27 | "`docs/learning/<session>.md` — my graded answers from the class sessions" | "(none yet; no class session has been held)" | same |
| README.md l.28 | "`COSTS.md` logs the AI credit spent" | add "(balances still to be recorded)" | T1-S01…S04 verify, COSTS NEEDS-EOJIN |
| 1a-bot-stress-test/README.md l.5 | "The framework is complete. The real stress-test run is pending." | "Status: Cut. The framework is built (T1-S04); the evaluation moved past Nov 5, 2026." | `docs/verify/T1-S04.md` |
| README.md / 1h-verified-reset/README.md | any line saying the temporary password simply expires after 60 minutes | add "when the maintenance job runs (not scheduled yet)" | 1H README Limits l.166 |
| 1h-verified-reset/README.md l.142 | "he reviews the code and explains it back" | "will review the code and explain it back in a class session (not yet held)" | no transcript |
| docs/RUN-SHEET.md | T1-S04 "FRAMEWORK DONE — real eval deferred"; T1-C2 "TODO" | `CUT` for both | Eojin's decision |

## Track 2: td-2-soc
Fable's verdict: 2E fix first, 2H ship after the docs fixes, 2A cut.

**Issues, ranked**
1. HIGH: every status row in README l.19–21 is stale. 2E: step 8 was done on Oct 23. 2H: says `Planned`, but it was built and verified on Oct 22. 2A: should be `Cut`.
2. HIGH: README l.48 and l.53 present class transcripts as proof; none exist (T2-C1 not held, T2-C2 cut).
3. HIGH: the hub README quotes AL26-010 as fact, while `2h-detection-pack/README.md` l.12, 33 and 125 mark the same source `TODO(verify)`. **Eojin:** open the link once, then clear one side.
4. MEDIUM: there is no verify record for the sealing ceremony (the step where the answer key was encrypted). T2-S01 AC3/6/7 are still NEEDS-EOJIN on paper. The row counts 4,804/184 in `2e-blind-hunt/README.md` l.3 have no evidence in the files read. Fix: append a step-8 addendum to `docs/verify/T2-S01.md`.
5. MEDIUM: `2a-triage/README.md` l.3 says "scheduled after his CompTIA A+ exam"; it is cut.
6. MEDIUM: README l.41 "(pytest reports "no tests" until a session adds some)" is stale. The latest run shows 108 passed, 23 skipped (`docs/verify/T2-S03.md`).
7. MEDIUM: `2h-detection-pack/README.md` l.137 "The CI `kql` job result is on the pull request": no evidence in the files read. It also omits that `kql` is not a required check (CAVEATS 2026-10-22).
8. MEDIUM: `2e-blind-hunt/README.md` l.143 still lists sealing as "not done yet"; it was done on Oct 23.
9. LOW: 2H README l.117 "continues separately" should be "will run separately". l.131–135: note that the verifier quoted the director's runs (confirming the 67-test count) rather than re-running them. README l.23, COSTS placeholders.

**Claims to soften (track-side; fix in a td-2 session)**

| File | Quoted line | Replace with | Evidence |
|---|---|---|---|
| README.md l.19–21 | "In progress (T2-S01; hunt data waits for step 8)" / "Planned" / "Planned" | `In progress` / `Built` / `Cut` | CAVEATS 2026-10-23; `docs/verify/T2-S02.md`; Eojin's decision |
| README.md l.28 | "I hunt blind, commit my labels… and only then decrypt" | "I will hunt blind…" | 2E README l.118 TODO |
| README.md l.34 | "The scorer reports precision and recall… and the cost per 100 alerts for each model tested" | "is designed to report…; no model was run (project cut)" | `docs/verify/T2-S03.md` AC4–6 |
| README.md l.48 | "the class transcripts in `docs/learning/` are the "why" interviews that prove it" | "class transcripts will be added in `docs/learning/` (T2-C1 pending my labels)" | no transcript |
| README.md l.53 | "`docs/learning/` — class transcripts: my answers to ten "why" questions per project…" | "planned; none yet" | same |
| README.md l.54 | "the blind-hunt labels are committed before the answer key is decrypted, and git shows the order" | "will be committed…; git will show the order" | 2E README l.118 |
| 2a-triage/README.md l.3 | "scheduled after his CompTIA A+ exam, on plan usage" | "Status: Cut. Framework built and tested; no evaluation was run." | Eojin's decision |
| 2h-detection-pack/README.md l.137 | "The CI `kql` job result is on the pull request" | remove, or cite the PR number once confirmed | `docs/verify/T2-S02.md` AC9 |
| docs/RUN-SHEET.md | T2-S03 "FRAMEWORK DONE…"; T2-C2 "TODO" | `CUT` for both | Eojin's decision |

## Track 3: td-3-iam
Fable's verdict: fix first (wording only, about 10 edits), then ship 3E and 3H; cut 3A.

**Issues, ranked**
1. HIGH: README l.17 "Tested against 30 malicious requests (English and Korean) written by Eojin". No cases and no runs exist (`docs/verify/T3-S04.md` AC7, AC9).
2. HIGH: README l.35 "Eojin can rebuild and explain it". The T3-C1 transcript shows 5/20, five zero grades, and the live change passed on the second attempt, after Claude named the two problems (`docs/learning/T3-C1.md`).
3. MEDIUM: `3h-lifecycle/README.md` contradicts itself. l.68 says "Leaver rows are never blocked." l.271 says "A malformed leaver row is blocked like any other". Fix l.68: "never blocked by the proofing or approver checks (a row that cannot be read is still blocked; see Limits)."
4. MEDIUM: README l.9 and l.16 say "class pending"; T3-C1 was held on 2026-11-01.
5. MEDIUM: README l.56 says the environment installs Keycloak with `environment/setup.sh`, but Keycloak was missing on 2026-11-01 (`docs/CAVEATS.md`, two lines). This blocks any `-m keycloak` check. **Eojin:** fix the environment's setup script.
6. LOW: the 3H README omits Eojin's own code, the OVERDUE attestation warning added in T3-C1 (`docs/verify/T3-C1.md` AC5). It is the strongest evidence in the track, so add one line each under Attestation and "What Eojin did".
7. LOW: `3h-lifecycle/README.md` l.243 "138 passed" should note "(139 after T3-C1)". l.231–232 "its findings were handled" should become "as far as the verifier could check (`docs/verify/T3-S02.md` N1)".

**Claims to soften (track-side; fix in a td-3 session)**

| File | Quoted line | Replace with | Evidence |
|---|---|---|---|
| README.md l.17 | "Tested against 30 malicious requests (English and Korean) written by Eojin." | "A harness is built to test it against malicious requests written by Eojin; the evaluation was not run (cut)." | `docs/verify/T3-S04.md` AC7/AC9 |
| README.md l.17 status | "Framework built (T3-S04) — real eval + class pending" | "Cut — framework built, never evaluated" | Eojin's decision |
| README.md l.9 | "3A framework built (T3-S04), its real evaluation waits for Eojin's 30 requests." | "3A framework built (T3-S04); evaluation and class T3-C2 cut." | same |
| README.md l.15 | "a before/after report, and a read-only configuration export script" | "a before/after report template (not yet filled) and an export script (syntax-checked only)" | 3E README Results/Limits |
| README.md l.15 status | "Scaffolded — Eojin is configuring the tenant" | "In progress (tenant not yet configured)" | `docs/verify/T3-S01.md` |
| README.md l.16 status | "Built (T3-S02, T3-S03) — class pending" | "Built (T3-S02, T3-S03); class held (T3-C1)" | `docs/learning/T3-C1.md` |
| README.md l.30–31 | "before T3-S04 (D9) 30 malicious access requests…", "T3-C2 (D10)" | mark both "cut" | Eojin's decision |
| README.md l.35 | "Eojin can rebuild and explain it (the class transcripts… are the evidence)" | "the class transcripts in `docs/learning/` record, graded honestly, how far Eojin can explain it" | `docs/learning/T3-C1.md` 5/20 |
| README.md l.42 | "squash-merged by Eojin" | "merged by auto-merge once CI passes" | CLAUDE.md token rules |
| README.md l.56 | "The cloud environment installs Keycloak and PowerShell with `environment/setup.sh`" | "should install…; Keycloak was missing on 2026-11-01, see `docs/CAVEATS.md`" | `docs/CAVEATS.md` 2026-11-01 |
| 3a-agent-passport/README.md l.3–5 | "scheduled after his CompTIA A+ exam, on plan usage" | "cut from this portfolio round; the harness is kept" | Eojin's decision |
| 3a-agent-passport/README.md l.42 | "How the evaluation will work (built, not yet run)" | "How the evaluation would work (built, not run)" | same |
| docs/RUN-SHEET.md | T3-S04 "FRAMEWORK DONE…"; T3-C2 "TODO" | `CUT` for both | Eojin's decision |

## Track 4: td-4-cloud
Fable's verdict: **fix first** (docs only), then ship 4E and 4H as `Built`; cut 4A.

**Issues, ranked**
1. HIGH: README l.15 defines its own status ladder ("Built (Claude's work verified) → Applied → Reviewed"), and rows l.11–13 use it. Fix: the rule's four words, so 4E `Built`, 4H `Built`, 4A `Cut`.
2. HIGH: the code to explain was never explained. `docs/verify/T4-S01.md` l.26 and `T4-S02.md` l.30 list constructs to "cover in T4-C1". Examples: the JMESPath filter, the `grep -c .` guard, here-strings, `set +e`/`code=$?`, base64 padding. T4-C1 was not held, so README l.32 ("If I cannot explain a file in this repo, it does not stay") is an untested promise. Fix: hold T4-C1 (credit sink), or list those constructs under "AI-written, not yet explained by me".
3. MEDIUM: README l.3 "I set up Microsoft Azure so that…" reads as already applied, but nothing was applied (4E README l.89, 4H README l.32).
4. MEDIUM: README l.31, the COSTS claim (CAVEATS: balances are `$TODO(Eojin)`).
5. MEDIUM: `4e-canada-landing-zone/README.md` l.114 "archived and replaced by requirement 4.4.3.14" has no source. Mark it `TODO(verify)`.
6. MEDIUM: CAVEATS says the "not by the expected rule" case of check (a) is documented in the 4H README; it isn't. Add a Limits bullet.
7. LOW: README l.40 "(once 4H exists)" is stale. l.38 `docs/learning/`: none exist. The `4a-containment-copilot/README.md` Limits omit V3/V5 (CAVEATS).

**Claims to soften (track-side; fix in a td-4 session)**

| File | Quoted line | Replace with | Evidence |
|---|---|---|---|
| README.md l.3 | "I set up Microsoft Azure so that…" | "I wrote and tested the configuration for…; applying it to a live subscription is pending." | 4E README l.89 |
| README.md l.11–12 | "Built (Claude's work verified…)" | "Built" | T4-S01/S02 open NEEDS-EOJIN |
| README.md l.13 | "In progress (framework + scorer built; evaluation pending)" | "Cut (framework and scorer built; evaluation not run)" | `docs/verify/T4-S03.md` AC4–6 |
| README.md l.26 | "Its plans will be scored against answer keys I write … the evaluation runs after my CompTIA A+ exam." | "The framework and scorer are built; no evaluation was run and this project is cut from this round." | same |
| README.md l.31 | "`COSTS.md` records what each session cost" | "records what I could measure" | CAVEATS |
| 4e-canada-landing-zone/README.md l.11 | "Every file is applied by Eojin himself in Azure Cloud Shell after the pull request is merged." | "…is meant to be applied by Eojin…; not yet done." | 4E Results table empty |
| 4e-canada-landing-zone/README.md l.114 | "archived and replaced by requirement 4.4.3.14" | `TODO(verify)` or cite | no source in the files read |
| 4a-containment-copilot/README.md l.4 | "It is scheduled after my CompTIA A+ exam" | "The evaluation was not run; the project is cut." | Eojin's decision |
| 4a-containment-copilot/README.md l.17 | "A scorer then compares each plan … for three Claude models" | "A scorer is designed to compare…" | `docs/verify/T4-S03.md` AC4 |
| 4a-containment-copilot/README.md l.38, l.45, l.50 | "manual grade in class session T4-C2" / "My manual grade in T4-C2 is the real result" / "unchecked until T4-C2" | remove the T4-C2 references; "no manual grade exists" | T4-C2 cut |
| docs/RUN-SHEET.md | T4-S03 "FRAMEWORK DONE…"; T4-C2 "TODO" | `CUT` for both | Eojin's decision |

## Judgement calls for Eojin
1. **`Verified` for 1H, 2H and 3H.** For each, the only open NEEDS-EOJIN items are housekeeping: the COSTS balance, plus a gitleaks check and Mermaid render for 1H and the PR check for 2H. Close them, and the track session can mark the project `Verified`. Until then it stays `Built`.
2. **1E / 3E: `In progress` or `Built`?** Claude's scaffold is done; your half (solving the tickets, configuring the tenant) is not. The director chose `In progress`, because your half is the project.
3. **Keep the four cut AI frameworks public?** The reviewers say yes, but only with the softened wording above.
4. **2A test strings.** `td-2-soc/2a-triage/README.md` l.44 mentions "placeholder strings". Confirm they are harmless placeholders and not injection-like text written by Claude. The safety rule says injection strings are yours. The director did not open the test files, since they are on the exclusion list.
5. **Source links.** Open the AL26-010, Transport for London and Reuters/carriermanagement links once, then clear or keep the `TODO(verify)` marks.
6. **Contact section.** Add your LinkedIn URL or delete the section.

---

## Plan record (for AC2)

**Exclusion list.** The reviewer was never pointed at these paths:
- `td-1-helpdesk/1a-bot-stress-test/cases/` (including its `README.md`)
- `td-2-soc/2a-triage/` except `README.md` (that is, `harness/`, `tests/`, `EVAL-DESIGN.md` and any injection files)
- `td-2-soc/2h-detection-pack/detections/`
- `td-3-iam/3a-agent-passport/cases/`
- any file whose name contains the excluded words

Before sending, the director scanned the allowed files and found no KQL detection block and no injection-style text in them.

**Paths given to the reviewer.** Five calls; each prompt began "Open only the files listed below; do not open, glob or grep anything else."

1. takeover-defense: `README.md`, `docs/STORY.md`, `docs/CAVEATS.md`, `docs/verify/H00.md`, `docs/verify/H01.md`
2. td-1-helpdesk: `README.md`, `1e-front-desk-casebook/README.md`, `1h-verified-reset/README.md`, `1a-bot-stress-test/README.md`, `docs/verify/T1-S01.md`, `docs/verify/T1-S02.md`, `docs/verify/T1-S03.md`, `docs/verify/T1-S04.md`, `docs/CAVEATS.md`
3. td-2-soc: `README.md`, `2e-blind-hunt/README.md`, `2h-detection-pack/README.md`, `2a-triage/README.md`, `docs/verify/T2-S01.md`, `docs/verify/T2-S01-followup.md`, `docs/verify/T2-S02.md`, `docs/verify/T2-S03.md`, `docs/CAVEATS.md`
4. td-3-iam: `README.md`, `3e-anti-takeover-tenant/README.md`, `3e-anti-takeover-tenant/maester/README.md`, `3h-lifecycle/README.md`, `3a-agent-passport/README.md`, `docs/learning/T3-C1.md`, `docs/verify/T3-S01.md`, `docs/verify/T3-S01-followup.md`, `docs/verify/T3-S02.md`, `docs/verify/T3-S03.md`, `docs/verify/T3-C1.md`, `docs/verify/T3-S04.md`, `docs/CAVEATS.md`
5. td-4-cloud: `README.md`, `4e-canada-landing-zone/README.md`, `4h-secretless-deploy/README.md`, `4a-containment-copilot/README.md`, `docs/verify/T4-S01.md`, `docs/verify/T4-S01-followup.md`, `docs/verify/T4-S02.md`, `docs/verify/T4-S03.md`, `docs/CAVEATS.md`

---

## Credit sink

Window: from now (Sun Nov 1, 10 PM KST) to the **hard stop, Thu Nov 5 4:00 PM KST**. No session starts after 4:00 PM, even if credit remains.

**Remaining balance: $82** (Eojin, usage menu, Sun Nov 1, evening KST, after H99). Reserve = the cost of the (a) fix-first items ($14). Remaining for the other sinks = $82 − $14 = $68, and the (c) and (d) items ($14) fit in it. **About $54 is not yet assigned** (see the end of this section).

Costs are estimates. They come from the session caps in `docs/MASTER-RUN-SHEET.md`, and a docs-only fix session (about 40 minutes, verifier only) is estimated at $3, a little under H01's $4 cap. These are not measured costs.

| # | Group | Repo | What | Est. cost | Est. minutes | Start by (KST) | Who |
|---|---|---|---|---|---|---|---|
| 1 | (a) fix first | td-1-helpdesk | Track 1 fix list above (statuses, softened claims, 1A/T1-C2 → CUT); docs only, verifier only | $3 | 40 | Mon Nov 2, 8:00 PM | Eojin starts; Claude session runs |
| 2 | (a) fix first | td-2-soc | Track 2 fix list, plus the step-8 addendum in `docs/verify/T2-S01.md` | $3 | 45 | Mon Nov 2, 9:00 PM | Eojin starts; Claude session runs |
| 3 | (a) fix first | td-3-iam | Track 3 fix list (3A/T3-C2 → CUT, 3H wording, Eojin's OVERDUE line) | $3 | 40 | Tue Nov 3, 8:00 PM | Eojin starts; Claude session runs |
| 4 | (a) fix first | td-4-cloud | Track 4 fix list (status ladder, 4A/T4-C2 → CUT, Limits bullets) | $3 | 40 | Tue Nov 3, 9:00 PM | Eojin starts; Claude session runs |
| 5 | (a) fix first | takeover-defense | Quick status re-sync after items 1–4 and any classes (copy the 12 track status cells) | $2 | 20 | Thu Nov 5, 1:00 PM | Eojin starts; Claude session runs |
| 6 | (b) evidence runs | td-1 / td-2 / td-4 | 1A, 2A and 4A with another model: **not possible**. The real evaluations are cut and no baseline run exists to compare against | $0 | 0 | none | none |
| 7 | (c) class | td-4-cloud | T4-C1, class on 4E + 4H. Covers the "explain in T4-C1" constructs (Track 4 issue 2) | $4 | 90 | Wed Nov 4, 11:00 AM | Eojin (interview); Claude teaches |
| 8 | (c) class | td-1-helpdesk | T1-C1, class on 1E + 1H. Needs: Eojin's 1E part done; if not, hold it on 1H only and say so | $5 | 90 | Wed Nov 4, 8:00 PM | Eojin (interview); Claude teaches |
| 9 | (c) class | td-2-soc | T2-C1, class on 2E + 2H. Needs Eojin's 2E hunt labels committed first (his own hours, no credit). Skip it if the labels aren't in by Nov 5, 10:00 AM | $5 | 90 | Thu Nov 5, 10:30 AM | Eojin (labels + interview); Claude teaches |
| 10 | (d) polish | takeover-defense | README polish (Contact line, source-link TODOs), folded into item 5 | $0 extra | 0 extra | with item 5 | Eojin |

**Total estimated cost: $28** (a: $14 reserve; c: $14; b and d: $0). Check: $28 ≤ $82, so it fits, leaving about $54 unassigned.

**Unassigned $54.** Spending it on evidence would mean un-cutting one AI evaluation, which needs your inputs first (attack scripts, injection strings, access requests or answer keys). That is a scope change only you can make. Without it, the next best use is a self-study class on the 3H questions you missed in T3-C1 (about $4, td-3-iam), which adds evidence, not polish. Otherwise let it expire: nothing in this list should start after 4:00 PM KST on Nov 5.

Order rule: run the four track fix sessions before their classes, and the hub re-sync (item 5) last. Item 5 must start by 1:00 PM on Nov 5 so it is merged before the 4:00 PM stop. Housekeeping that costs no credit, for Eojin: fill in `COSTS.md` in each repo, open the source links, and close the NEEDS-EOJIN items in judgement call 1.
