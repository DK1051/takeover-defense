# Takeover Defense — stopping the helpdesk-reset account takeover at every layer

I'm Eojin Kim, preparing for IT helpdesk, security operations (SOC) and identity and access management (IAM) roles in Canada. This portfolio is twelve small projects built around one real attack: a criminal phones a company's IT helpdesk, pretends to be an employee who lost their phone, and talks the agent into resetting their password and their MFA (multi-factor authentication — the second check, such as a code on your phone, that protects a login). Once that reset goes through, the criminal owns the account. The projects show how a helpdesk technician, a security analyst, an identity administrator and a cloud administrator each stop that attack at their own layer. Everything runs against a fictional company, Maple Harbour Credit Union in Toronto, so no real people or data are involved.

## Why this attack

On May 1, 2026 the Canadian Centre for Cyber Security published alert **AL26-010** about criminals compromising company cloud (SaaS) environments through social engineering — talking people, not computers, into doing something. The alert warns that attackers "convince support staff to reset MFA or enroll attacker-controlled devices". It recommends "out-of-band verification procedures for identity-related requests" (out-of-band means checking through a second channel the caller did not choose, such as calling back the phone number already on file) and says organisations should "restrict and closely monitor MFA reset, recovery, and device re-enrolment processes" with "enhanced verification and approval". Source: https://www.cyber.gc.ca/en/alerts-advisories/al26-010-cyber-criminals-social-engineering-enabled-compromise-enterprise-saas-environments

**Case study.** The best-known group using this playbook is the one security researchers call Scattered Spider. Two of its members were sentenced to 5.5 years in July 2026 for the 2024 attack on Transport for London. Public incidents that reporting links to helpdesk social engineering of this kind: MGM Resorts (2023); Clorox (2023 — *alleged*: the description comes from Clorox's lawsuit against its IT vendor Cognizant and is not a proven finding); Marks & Spencer and Co-op (2025). Only public reporting is cited here; nothing in this portfolio reproduces attacker tooling.

The attack chain and which project defends each step: [docs/STORY.md](docs/STORY.md).

## Status

**In progress (as of Oct 22, 2026).** Merged so far: H00 (hub calibration), T1-S01 (1E scaffold), T2-S01 (2E generator and test data; the sealed hunt dataset is still to come), T3-S01 (3E scaffold and trial runbook), T4-S01 (4E landing-zone files). Each row below copies its track README; the verify reports are linked. Building runs from D0 (Oct 22, 2026) to a hard stop on Nov 5, 2026 at 4:00 PM KST. Schedule: [docs/MASTER-RUN-SHEET.md](docs/MASTER-RUN-SHEET.md).

Status words used everywhere in this portfolio: `Planned` → `In progress (session IDs)` → `Built` → `Verified` (verify report linked) → `Cut` (moved to after Nov 5). The table below is updated at sessions H01 and H99 by copying each track's own README; if this table and a track README ever disagree, the track README is right.

## The twelve projects

| Track | Level | Project | Repo | Status |
|---|---|---|---|---|
| 1 · Helpdesk (CompTIA A+) | Easy | 1E Front Desk Casebook — caller-verification SOP, 10 tickets, KB articles in English and Korean (`1e-front-desk-casebook/`) | [td-1-helpdesk](https://github.com/DK1051/td-1-helpdesk) | In progress (T1-S01) · [verify report](https://github.com/DK1051/td-1-helpdesk/blob/main/docs/verify/T1-S01.md) |
| 1 · Helpdesk (CompTIA A+) | Hard | 1H Verified Reset Service — a reset API that enforces callback, one-time code and manager approval in order (`1h-verified-reset/`) | [td-1-helpdesk](https://github.com/DK1051/td-1-helpdesk) | Planned |
| 1 · Helpdesk (CompTIA A+) | Hard + AI | 1A Helpdesk Bot Stress Test — an AI helpdesk assistant tested against scripted social-engineering calls (`1a-bot-stress-test/`) | [td-1-helpdesk](https://github.com/DK1051/td-1-helpdesk) | Planned |
| 2 · SOC (CompTIA Security+) | Easy | 2E Blind Hunt — hunt five hidden takeovers in 14 days of generated sign-in logs, graded against a sealed answer key (`2e-blind-hunt/`) | [td-2-soc](https://github.com/DK1051/td-2-soc) | In progress (T2-S01; hunt data waits for step 8) · [verify report](https://github.com/DK1051/td-2-soc/blob/main/docs/verify/T2-S01.md) |
| 2 · SOC (CompTIA Security+) | Hard | 2H Takeover Detection Pack — KQL detections with a test harness on the Kusto emulator (`2h-detection-pack/`) | [td-2-soc](https://github.com/DK1051/td-2-soc) | Planned |
| 2 · SOC (CompTIA Security+) | Hard + AI | 2A Injection-Proof Triage — an AI alert-triage assistant measured against prompt-injection attempts (`2a-triage/`) | [td-2-soc](https://github.com/DK1051/td-2-soc) | Planned |
| 3 · IAM (Microsoft SC-300) | Easy | 3E Anti-Takeover Tenant — a Microsoft Entra trial tenant hardened against reset abuse, mapped to Canadian guidance (`3e-anti-takeover-tenant/`) | [td-3-iam](https://github.com/DK1051/td-3-iam) | Scaffolded — Eojin is configuring the tenant · [verify report](https://github.com/DK1051/td-3-iam/blob/main/docs/verify/T3-S01.md) |
| 3 · IAM (Microsoft SC-300) | Hard | 3H Lifecycle for People and Service Accounts — joiner/mover/leaver engine with attestation and separation-of-duties rules (`3h-lifecycle/`) | [td-3-iam](https://github.com/DK1051/td-3-iam) | Planned |
| 3 · IAM (Microsoft SC-300) | Hard + AI | 3A Agent Passport — an AI assistant that can propose access changes but never grant them (`3a-agent-passport/`) | [td-3-iam](https://github.com/DK1051/td-3-iam) | Planned — first project to cut if time or credit runs short |
| 4 · Cloud (Microsoft AZ-104) | Easy | 4E Canada-Only Landing Zone — Azure policies, a least-privilege role and budget alerts (`4e-canada-landing-zone/`) | [td-4-cloud](https://github.com/DK1051/td-4-cloud) | Built (Claude's work verified) · [verify report](https://github.com/DK1051/td-4-cloud/blob/main/docs/verify/T4-S01.md) |
| 4 · Cloud (Microsoft AZ-104) | Hard | 4H Secretless Deploy — deployments from GitHub Actions with no stored cloud secrets, plus "cannot-do" tests (`4h-secretless-deploy/`) | [td-4-cloud](https://github.com/DK1051/td-4-cloud) | Planned |
| 4 · Cloud (Microsoft AZ-104) | Hard + AI | 4A Containment Runbook Copilot — an AI that drafts dry-run containment steps, scored against my answer keys (`4a-containment-copilot/`) | [td-4-cloud](https://github.com/DK1051/td-4-cloud) | Planned |

## How AI was used

I direct; Claude builds; nothing counts until it is checked. Every repo carries the same `CLAUDE.md` rules and four helper roles (subagents):

- **Director** (Claude Opus 5.5, the main session): plans each session, splits the work, integrates and decides.
- **Builder** (Claude Sonnet 5.5): writes code, tests, CI workflows and docs.
- **Chores** (Claude Haiku 5.5): mechanical work — fixtures, formatting, templates, link checks.
- **Verifier** (Claude Opus 5.5): checks every finished session against the brief's acceptance criteria and writes a report. It never edits.
- **Red team** (Claude Fable 5.1): blunt design reviews before each AI build and the final gate on every README claim. It is never given attack content.

My part is the human work the AI cannot honestly do for me: solving the helpdesk tickets, writing the knowledge-base articles, writing every attack script and injection string used in testing, hunting through the logs and committing my labels before the answer key is unsealed, configuring the tenant, writing the containment answer keys from Microsoft documentation, and sitting the "class" sessions where I explain each project back and get graded.

**The honesty rule.** Everything is checked: a project is marked `Verified` only when its verify report says so, and I can explain and rebuild every piece — the class transcripts are where I prove it. `AI-USE.md` in each repo lists, per project, what Claude did (and which model) and what I did.

## How to verify my work

- **Verify reports** — `docs/verify/<session>.md` in each repo: one line per acceptance criterion with PASS / FAIL / NEEDS-EOJIN and the evidence (test output, file paths).
- **Class transcripts** — `docs/learning/<session>.md`: my answers to ten "why" questions per project, graded honestly, plus one live code change I drove.
- **Commit history** — one branch and one pull request per session (`t1-s02-…`, `h01-…`); each PR description says what changed.
- **Costs and caveats** — `COSTS.md` logs the AI credit spent per session; `docs/CAVEATS.md` logs what went wrong and what I changed because of it.

## The repos

| Repo | What it holds |
|---|---|
| [takeover-defense](https://github.com/DK1051/takeover-defense) | This hub: story, index, schedule, shared rules |
| [td-1-helpdesk](https://github.com/DK1051/td-1-helpdesk) | Track 1 · Helpdesk (CompTIA A+): stop the reset at the front door |
| [td-2-soc](https://github.com/DK1051/td-2-soc) | Track 2 · SOC (CompTIA Security+): catch the takeover the helpdesk missed |
| [td-3-iam](https://github.com/DK1051/td-3-iam) | Track 3 · IAM (Microsoft SC-300): make a stolen reset worthless |
| [td-4-cloud](https://github.com/DK1051/td-4-cloud) | Track 4 · Cloud (Microsoft AZ-104): contain the blast radius in Azure |

## Contact

TODO: LinkedIn URL
