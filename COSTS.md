# Credit log (cloud-session credit, $250, ends Nov 5 4:59 PM KST)

One line per session. Read the balance from the usage menu before the session starts and again after `wrap`.

Format: `- <date> <ID> | balance before $ | balance after $ | spent $ | cap $ | note`

- 2026-10-22 H00 | balance before $250 | balance after $228 | spent $22 | cap $3 | H00 ran in the same cloud session as T1-S01, T2-S01, T3-S01 and T4-S01, so the usage menu shows one combined number for all five; H00 alone was a small share (file checks + probe, no builder). Fast mode was on for most of the run, which raised the cost.

Calibration note (H00): Combined D0 spend was about $22 against the sum of the five caps ($3 + $5 + $8 + $5 + $5 = $26), so all five sessions finished under their combined cap even with fast mode on. The caps in `docs/MASTER-RUN-SHEET.md` look about right. Keep them, run with fast mode off from D1, and re-check after D1. At ~$22/day the $250 credit would run out before Nov 5, so later days need to average about $15 or less.
