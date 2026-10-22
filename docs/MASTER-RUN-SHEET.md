# Master run sheet — all five repos

Days are relative: **D0 = the day the kit is uploaded.** The date column assumes D0 = Thursday, Oct 22, 2026; shift every date by the same amount if D0 moves. Each repo also has its own `docs/RUN-SHEET.md` with live status — this file is the plan, those are the truth.

Credit: $250 of cloud-session credit, expiring Nov 4 11:59 PM Pacific = **Nov 5 4:59 PM KST**. **Hard stop: Nov 5 (D14) 4:00 PM KST.** Credit caps below are planning numbers — recalibrate after H00 and the first build (T1-S01).

"Merged" in the Needs column means Eojin has squash-merged that session's pull request in the GitHub web UI before the next session starts — usually the same evening.

## Sessions

| ID | Repo | Day | Date if D0 = Oct 22 | What | Needs | Cap |
|---|---|---|---|---|---|---|
| H00 | hub | D0 | Thu Oct 22 | calibrate: a kit check across all 5 repos is NOT possible from one repo — verify the hub kit, run `probe`, record the first cost | kit uploaded | $3 |
| T1-S01 | td-1 | D0 | Thu Oct 22 | 1E scaffold | kit | $5 |
| T2-S01 | td-2 | D0 | Thu Oct 22 | probe + 2E generator + sealed key + fixtures | kit | $8 |
| T1-S02 | td-1 | D1 | Fri Oct 23 | 1H core service | T1-S01 merged | $12 |
| T3-S01 | td-3 | D1 | Fri Oct 23 | 3E scaffold + trial runbook | kit | $5 |
| T4-S01 | td-4 | D1 | Fri Oct 23 | 4E scaffold | kit | $5 |
| T1-S03 | td-1 | D2 | Sat Oct 24 | 1H replay tests + docs | T1-S02 merged | $10 |
| T2-S02 | td-2 | D2 | Sat Oct 24 | 2H detections + Kusto CI | T2-S01 merged | $15 |
| T3-S02 | td-3 | D2 | Sat Oct 24 | 3H engine core | T3-S01 merged | $12 |
| T3-S03 | td-3 | D3 | Sun Oct 25 | 3H attestation, SoD, proofing gate | T3-S02 merged | $10 |
| T4-S02 | td-4 | D3 | Sun Oct 25 | 4H Bicep + OIDC workflow + cannot-do tests | T4-S01 merged | $12 |
| T1-C1 | td-1 | D3 | Sun Oct 25 | class 1E + 1H | T1-S03 merged, Eojin's 1E done | $5 |
| H01 | hub | D4 | Mon Oct 26 | portfolio README + index | track READMEs exist | $4 |
| T1-S04 | td-1 | D5 | Tue Oct 27 | 1A harness + eval (redteam design review first) | T1-S03 merged, Eojin's 40 attack scripts + 20 genuine requests (minimum 10 EN + 10 KO attacks + 10 genuine) | $20 |
| T2-S03 | td-2 | D6 | Wed Oct 28 | 2A triage + eval (redteam design review first) | T2-S02 merged, Eojin's 2E labels committed, his 10 injection strings | $20 |
| T3-C1 | td-3 | D6 | Wed Oct 28 | class 3H | T3-S03 merged | $5 |
| T4-S03 | td-4 | D7 | Thu Oct 29 | 4A containment copilot + eval (redteam first) | T4-S02 merged, 2E labels committed | $15 |
| T1-C2 | td-1 | D7 | Thu Oct 29 | class 1A | T1-S04 merged | $4 |
| T2-C1 | td-2 | D7 | Thu Oct 29 | class 2E + 2H | T2-S02 merged, Eojin's 2E labels committed | $5 |
| T4-C1 | td-4 | D8 | Fri Oct 30 | class 4E + 4H | T4-S02 merged | $4 |
| T3-S04 | td-3 | D9 | Sat Oct 31 | 3A Agent Passport (redteam first) — FIRST TO CUT | T3-S03 merged, Eojin's 30 requests (minimum 15, at least 5 in Korean) | $18 |
| T2-C2 | td-2 | D9 | Sat Oct 31 | class 2A | T2-S03 merged | $4 |
| T3-C2 | td-3 | D10 | Sun Nov 1 | class 3A | T3-S04 merged | $4 |
| T4-C2 | td-4 | D10 | Sun Nov 1 | class 4A | T4-S03 merged | $4 |
| — | — | D11 | Mon Nov 2 | buffer (catch-up, re-runs, cut decisions) | — | — |
| H99 | hub | D12 | Tue Nov 3 | final Fable gate across all repos + credit sink plan | all merged | $12 |
| — | — | D13 | Wed Nov 4 | buffer (credit sink from H99's list) | — | — |
| — | — | D14 | **Thu Nov 5 — hard stop 4:00 PM KST** | credit expires 4:59 PM KST; nothing starts after 4:00 PM | — | — |

Total caps **$221**; reserve **$29**.

## Load per day (sum of caps)

| Day | Date | Sessions | Caps |
|---|---|---|---|
| D0 | Thu Oct 22 | H00, T1-S01, T2-S01 | $16 |
| D1 | Fri Oct 23 | T1-S02, T3-S01, T4-S01 | $22 |
| D2 | Sat Oct 24 | T1-S03, T2-S02, T3-S02 | $37 |
| D3 | Sun Oct 25 | T3-S03, T4-S02, T1-C1 | $27 |
| D4 | Mon Oct 26 | H01 | $4 |
| D5 | Tue Oct 27 | T1-S04 | $20 |
| D6 | Wed Oct 28 | T2-S03, T3-C1 | $25 |
| D7 | Thu Oct 29 | T4-S03, T1-C2, T2-C1 | $24 |
| D8 | Fri Oct 30 | T4-C1 | $4 |
| D9 | Sat Oct 31 | T3-S04, T2-C2 | $22 |
| D10 | Sun Nov 1 | T3-C2, T4-C2 | $8 |
| D11 | Mon Nov 2 | buffer | — |
| D12 | Tue Nov 3 | H99 | $12 |
| D13 | Wed Nov 4 | buffer | — |
| D14 | Thu Nov 5 | **hard stop 4:00 PM KST** | — |

D2 and D3 are the heaviest days (three sessions each, plus the PR reviews they depend on). If a day slips, the buffer days absorb it; if two slip, use the cut order.

## Cut order (when time or credit runs short)

Move to after Nov 5, on plan usage, in this order: **T3-S04 → T1-S04 → T4-S03 → T4-S02 → T2-S03.** Never cut T1-S01, T2-S01, T3-S01, T4-S01. A cut session's class (T3-C2 for T3-S04, T1-C2 for T1-S04, T4-C2 for T4-S03) moves with it.
