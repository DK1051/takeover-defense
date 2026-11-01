# What Claude did vs what Eojin did

The hub holds no code. Its "projects" are the starter kit (the files you are reading) and the three hub sessions. Each track repo keeps its own `AI-USE.md` for its projects. The honesty rule: every line here is filled in at `wrap`, from what actually happened, not from the plan.

## Starter kit (CLAUDE.md, agents, briefs, run sheets, README skeleton)
Claude (models used)
- Drafted every kit file from Eojin's written plan (director: Opus 5.5; kit writer: Fable 5.1). Confirm at H00.
Eojin
- Wrote the plan the kit was generated from; reviewed and uploaded the kit. Confirm at H00.

## H00 — calibrate
Claude (models used)
- Director (Opus 5.5): ran the 21-file kit check and the three content checks, ran `probe` plus the extra GitHub line, wrote the plain-English explanations and the track implications in `docs/PROBES.md`, logged caveats, updated the run sheet and `COSTS.md` placeholders. H00 ran in one cloud session together with T1-S01, T2-S01, T3-S01 and T4-S01 at Eojin's request.
- `verifier` (Opus 5.5): checked the acceptance criteria and wrote `docs/verify/H00.md`.
- No `builder`, `chores` or `redteam` run: there was no code or document build to review, and the file check was a few shell commands.
Eojin
- Uploaded the kit and asked for the D0 launch. Still to do: give the credit balances for `COSTS.md`, read "What this means for the tracks" in `docs/PROBES.md`, and squash-merge the PR.

## H01 — portfolio README + index
Claude (models used)
- Director (Opus 5.5): read each track README on `main` (all four repos attached), copied the four status cells, added verify-report links, updated the Status paragraph with the merged sessions, ran the link checks. Done inline without `chores` because it was a handful of commands.
- `verifier` (Opus 5.5): final check, `docs/verify/H01.md`.
Eojin
- Asked for H01 to run on D0. Still to do: record the H01 cost in `COSTS.md`, open the five `docs/STORY.md` source links in a browser, pick allowed status words for 3E and 4E.

## H99 — final gate + credit sink plan
Claude (models used)
- Director (Opus 5.5): checked the Needs list, inventoried the five repos, wrote the exclusion list and the five reviewer path lists, wrote `docs/FINAL-GATE.md` (12-row verdict table, per-repo issues and claims to soften, credit-sink plan), chose the status words (`In progress` for 1E/2E/3E) and added three STORY.md softenings the hub reviewer could not see (marked "director").
- `redteam` (Fable 5.1): five calls, one per repo, documents only (READMEs, verify reports, the T3-C1 transcript, CAVEATS). None refused. Its verdicts are the gate verdicts.
- `chores` (Haiku 5.5): applied the hub README status cells and the softened wording in `README.md` and `docs/STORY.md`.
- `verifier` (Opus 5.5): checked AC1–AC7 and wrote `docs/verify/H99.md`.
- No track repo was edited.
Eojin
- Approved a one-time exception to "one repo per session" for H99, ruled that the deferred evals and their classes count as CUT, and approved the plan and exclusion list. Still to do: give the credit balance (`COSTS.md` and the credit-sink section), make the judgement calls at the end of `docs/FINAL-GATE.md`, and run the fix sessions in order.
