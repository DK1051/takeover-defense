## Probe 2026-10-22T09:47Z
- arch: x86_64
- cpus: 4  memory: 15 GB
- avx2 flags: 4
- python: Python 3.13.16
- java: Picked up JAVA_TOOL_OPTIONS: [proxy settings removed before commit — they list internal proxy hosts]
- docker:   not available
- pwsh: not installed
- keycloak: /opt/keycloak
- reach https://repo1.maven.org/maven2/ -> HTTP 429
- reach https://mcr.microsoft.com/v2/ -> HTTP 200
- reach https://packages.microsoft.com/ -> HTTP 200
- reach https://pypi.org/simple/ -> HTTP 200
- reach https://www.powershellgallery.com/ -> HTTP 000
- reach https://graph.microsoft.com/v1.0/ -> HTTP 000
- reach https://management.azure.com/ -> HTTP 000
- reach https://github.com/ -> HTTP 400

Notes on this run (added by the director, not by `probe.sh`):
- The `java:` line shows a JVM notice instead of the version because the script keeps only the first line of `java -version`. Checked separately: `openjdk version "21.0.12.1" 2026-08-18`.
- The `docker:` line printed a blank version, then `not available`: the Docker program is installed (`Docker version 29.9.1`) but no Docker engine is running, so containers cannot start. The script printed this on two lines (`- docker:  ` then `not available`); they are joined into one line here.
- `keycloak: /opt/keycloak` appears because this launch ran the Track 1 and Track 3 setup scripts on the same machine just before the probe. The probe's version check printed nothing; `/opt/keycloak/bin/kc.sh --version` run separately printed `Keycloak 26.8.1`. In a hub-only environment this line would read `not installed`.

### What each line means
- `## Probe 2026-10-22T09:47Z` — the date and time (UTC) the probe ran.
- `arch: x86_64` — the processor is the standard 64-bit Intel/AMD type, which most server software is built for.
- `cpus: 4  memory: 15 GB` — the machine has 4 processor cores and about 15 GB of working memory, TODO(verify): whether that is enough to run Keycloak and an emulator together.
- `avx2 flags: 4` — all 4 cores support AVX2, a set of fast maths instructions the Kusto emulator needs.
- `python: Python 3.13.16` — Python is installed and newer than the 3.12 the tracks require.
- `java:` — Java is installed (version 21, checked separately), which Keycloak needs.
- `docker: not available` — containers cannot run here because no Docker engine is running.
- `pwsh: not installed` — PowerShell was not yet installed when the probe ran (Track 3's setup was still installing it); the hub itself does not need it.
- `keycloak: /opt/keycloak` — Keycloak (an open-source login server used in Tracks 1 and 3) is installed on this machine.
- `reach https://repo1.maven.org/maven2/ -> HTTP 429` — Maven Central answered but said "too many requests", so a download from it may fail right now.
- `reach https://mcr.microsoft.com/v2/ -> HTTP 200` — Microsoft's container registry is reachable.
- `reach https://packages.microsoft.com/ -> HTTP 200` — Microsoft's Linux package site (where PowerShell comes from) is reachable.
- `reach https://pypi.org/simple/ -> HTTP 200` — the Python package index is reachable, so `pip install` should work (T2-S01 tests it).
- `reach https://www.powershellgallery.com/ -> HTTP 000` — PowerShell Gallery is blocked, as expected; PowerShell modules install only in GitHub Actions or on Eojin's PC.
- `reach https://graph.microsoft.com/v1.0/ -> HTTP 000` — Microsoft Graph (the Microsoft 365 API) is blocked, as expected and as the safety rules require.
- `reach https://management.azure.com/ -> HTTP 000` — the Azure management API is blocked, as expected; nothing in a cloud session can touch Azure.
- `reach https://github.com/ -> HTTP 400` — GitHub answered (a 4xx code still means the host is reachable), so it works as the Keycloak download source.

### What this means for the tracks
- **Track 2 (Kusto emulator): partly.** `arch: x86_64` and `avx2 flags: 4` (greater than 0) meet the processor need, so the answer to the brief's question is **yes**. But `docker: not available` means the emulator container cannot start on this machine as it is. T2-S01 re-runs the probe in its own environment; a caveat was written for T2-S02.
- **Track 1 and 3 (Keycloak download): yes.** `reach https://github.com/ -> HTTP 400` shows GitHub answered, and Keycloak 26.8.1 was installed by the setup script, which tries GitHub first (the setup log does not record which source answered). Note: the brief names Maven Central as the main source and GitHub as the fallback; `environment/setup.sh` in Tracks 1 and 3 does the opposite. Maven Central answered `HTTP 429` (too many requests), so it is not a reliable fallback today; a caveat was written. `pwsh: not installed` is expected here.
- **Assumption:** the track environments run on the same machine class as this one. In this launch all five repos ran in one session on this same machine, so T1-S01 and T2-S01 re-run `probe` to confirm.
