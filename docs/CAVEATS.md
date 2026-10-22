# Caveats found during execution

One line per caveat, newest last, in this exact format (from CLAUDE.md):

`- YYYY-MM-DD <ID> | what happened | impact: this session / <later IDs> / plan | what I did | needs Eojin: yes/no`

- 2026-10-22 H00 | Eojin asked for all five D0 sessions (H00, T1-S01, T2-S01, T3-S01, T4-S01) to run in one cloud session without stopping for plan approval; this session can push only to `claude/friendly-heisenberg-seafff`, not to the brief's `h00-calibrate` | impact: this session | used `claude/friendly-heisenberg-seafff` in all five repos, one PR per repo | needs Eojin: no
- 2026-10-22 H00 | Credit balances before/after were not available (Eojin was not in the loop during the run) | impact: this session / plan | `COSTS.md` H00 line has placeholders; calibration note left open | needs Eojin: yes
- 2026-10-22 H00 | Probe: x86_64 and avx2 4 are fine for the Kusto emulator, but `docker: not available` (Docker program installed, no engine running) | impact: T2-S02 | recorded here; T2-S01 decides its fallback | needs Eojin: yes
- 2026-10-22 H00 | Probe: Maven Central answered HTTP 429 (too many requests); GitHub answered and Keycloak 26.8.1 installed from it | impact: T1-S02, T3-S02 (fallback source unreliable today) | none needed now | needs Eojin: no
- 2026-10-22 H00 | Probe output's `java:` line contained the proxy's internal host list (JAVA_TOOL_OPTIONS notice); `probe.sh` keeps only that first line | impact: this session / later probes | replaced the host list with a note in `docs/PROBES.md`; checked the Java version separately; `probe.sh` not edited | needs Eojin: no
- 2026-10-22 H00 | `probe.sh` output quirks: the docker line splits over two lines when no engine runs, the keycloak version prints on a second line, and the java line carries the proxy host list | impact: T1-S01, T2-S01 and later probes | each session joins/redacts before committing; `probe.sh` not edited | needs Eojin: no
- 2026-10-22 H00 | Brief says Keycloak comes from Maven Central with GitHub as fallback; the Track 1 and 3 `environment/setup.sh` try GitHub first | impact: plan (docs only) | noted in `docs/PROBES.md`; scripts unchanged | needs Eojin: no
- 2026-10-22 H00 | gitleaks is not installed locally and its download was refused (403); `detect-secrets` 1.5.0 found 0 issues instead | impact: this session | CI on the PR runs gitleaks | needs Eojin: no
- 2026-10-22 H01 | Ran on D0 (planned D4) at Eojin's request, right after the D0 merges; all four track repos were attached, so no pasted text was needed | impact: plan (H01 statuses will be stale by D4) | re-run the status sync at H99 or ask for a quick refresh | needs Eojin: no
- 2026-10-22 H01 | Two track status cells use words outside the allowed list, copied verbatim: 3E "Scaffolded — Eojin is configuring the tenant", 4E "Built (Claude's work verified)"; 2E "In progress (T2-S01; hunt data waits for step 8)" adds a note | impact: T3-S02, T4-S02, T2-S02 | flagged; each track fixes its wording in its next session | needs Eojin: yes (pick the allowed word)
- 2026-10-22 H01 | td-1-helpdesk README: the Status paragraph still says "Planned. Nothing is built yet" while its table says 1E "In progress (T1-S01)" | impact: T1-S02 | not changed from the hub | needs Eojin: no (fix in T1-S02)
- 2026-10-22 H01 | All five source URLs in `docs/STORY.md` returned HTTP 000 from this session (the Trusted network blocks those news and government hosts), so they could not be checked | impact: this session | not replaced; listed in `docs/verify/H01.md` | needs Eojin: yes (open each link in a browser)
- 2026-10-22 H01 | Eojin asked not to touch `COSTS.md`; the H01 line is left for him | impact: this session | none | needs Eojin: yes
