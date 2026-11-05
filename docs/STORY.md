# The story: one attack chain, twelve planned defences

Status (Nov 1, 2026): the four AI projects (1A, 2A, 3A, 4A) were cut after their frameworks were built; their evaluations did not run before Nov 5. See [FINAL-GATE.md](FINAL-GATE.md).

Every project in this portfolio defends one step of the same attack. The chain below is the pattern described in public reporting and in the Canadian Centre for Cyber Security alert AL26-010 (May 1, 2026): attackers "convince support staff to reset MFA or enroll attacker-controlled devices". Nothing here goes beyond what that public reporting describes.

The company in every example is fictional: **Maple Harbour Credit Union**, Toronto, 50 staff, domain `mapleharbour.example`.

## The five steps

| Step | What the attacker does (plain English) | Which project defends it |
|---|---|---|
| 1 · Fake call | Phones the helpdesk pretending to be an employee ("I got a new phone, I'm locked out, my manager needs this report in an hour"). Urgency and a plausible story are the whole technique. | **1E** gives the agent a written verification procedure and ten practice tickets, four of them exactly this call. **1A** was built to run the same kind of scripted calls against an AI helpdesk assistant to measure whether it verifies before it acts (cut: not evaluated before Nov 5). |
| 2 · Reset | The agent resets the password or clears MFA for the caller without proving who they are. | **1H** is a lab reset service that refuses out-of-order steps (it cannot tell whether the agent really made the callback): callback to the number on file, a one-time code from the registered device (read back by the user; the 1H README flags this step as an open question), manager approval for privileged accounts, a temporary password that a maintenance job rotates after 60 minutes (the job is not scheduled yet). **3E** configures the identity tenant so a reset alone is not enough (strong authentication methods, Temporary Access Pass only after verified identity); I am still configuring it. |
| 3 · New MFA device | The attacker enrols their own phone or authenticator as the account's MFA, so future logins look legitimate. | **1H** raises an alert for MFA requests made through the service, or reported to it, within 24 hours of a reset it completed. **2H** detects the sequence "reset → new MFA method" in sign-in and audit logs (tested on fictional fixtures and synthetic data only). **3E** is meant to require phishing-resistant methods for admins so an attacker-enrolled device is worth less (not configured yet). |
| 4 · Takeover | Signs in from a new device and location and starts using the account — reading mail, changing settings, requesting more access. | **2E** is my hunt for that activity in 14 days of logs with five hidden takeovers (data sealed; my hunt is still to do). **2H** turns the hunt into repeatable detections. **2A** was built to test whether an AI triage assistant can be fooled by attacker-written text inside the alerts (cut: not evaluated before Nov 5). **3H** limits what any one account can do (least privilege, quarterly access attestation, separation-of-duties rules). **3A** was built so that an AI assistant with access to the identity system can propose a change but never grant one (cut: not evaluated before Nov 5). |
| 5 · Cloud damage | Uses the stolen identity in the cloud: creates resources in the wrong country, grants itself roles, runs up a bill, or destroys evidence. | **4E** (written; its automatic tests read only files in this repository, not Azure; not yet applied to Azure) is designed to lock the Azure subscription to Canadian regions, require an owner tag, limit the operator role and alert on new role assignments and spending. **4H** is built to deploy from GitHub Actions with no stored cloud password or key for an attacker to steal, and its "cannot-do" tests are written to show what the identity is denied; neither workflow has run against Azure yet. **4A** was built to draft a containment checklist (revoke sessions, remove the new MFA method, remove new roles, preserve evidence) in dry-run form, to be scored against my answer keys (cut: no plans scored before Nov 5). |

## Why each layer matters on its own

A helpdesk that verifies well stops most of these calls, but not all. A detection pack catches what the helpdesk missed, but only after the fact. An identity tenant that demands strong authentication makes a stolen reset much less useful (the aim of 3E, not configured yet). Cloud guardrails limit the damage when everything before them failed. The portfolio is built in that order — helpdesk, SOC, IAM, cloud — because that is also the career path: each track is the layer the next job is responsible for.

## Sources used throughout

- Canadian Centre for Cyber Security, alert AL26-010 (May 1, 2026): https://www.cyber.gc.ca/en/alerts-advisories/al26-010-cyber-criminals-social-engineering-enabled-compromise-enterprise-saas-environments
- Public reporting on the group called Scattered Spider (two members sentenced to 5.5 years in July 2026 for the 2024 Transport for London attack) and on incidents at MGM Resorts (2023), Clorox (2023 — alleged, in Clorox's lawsuit against Cognizant), Marks & Spencer and Co-op (2025). Sources, one per incident:
  - Transport for London (2024), sentencing on 16 July 2026 at Woolwich Crown Court: https://thehackernews.com/2026/07/two-scattered-spider-hackers-get-55.html
  - MGM Resorts (2023): https://www.theregister.com/2023/09/14/caesars_mgm_hacks
  - Clorox (2023, alleged in Clorox's 2025 lawsuit against Cognizant): https://www.theregister.com/2025/07/23/lawsuit_clorox_vs_cognizant/
  - Marks & Spencer and Co-op (2025), Reuters, 6 May 2025, "M&S, Co-op Cyberattackers Duped IT Help Desks into Resetting Passwords": https://www.carriermanagement.com/news/2025/05/06/274918.htm
