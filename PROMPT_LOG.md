# Prompt Log — Team Neon Pulse — FixFirst (CivicLens)
_Event: Tech Habba, Prompt to Product, Acharya — 21 Nov 2026, 4-hour window_

| # | Tool | Prompt / Purpose | Outcome |
|---|------|------------------|---------|
| 1 | Muse | Read Participant Guide + Rules PDFs, extract problem statement, 5 required features, judging rubric (100 marks) and submission penalties | CivicLens spec + rubric checklist |
| 2 | Muse | "100+ people, same problem — what will everyone build, and what novel angle wins Innovation 20/20?" | Rejected generic form+chatbot; chose Duplicate Clustering + Vulnerable-Zone Escalation + HazardEye Photo + Explainable Priority Score |
| 3 | Muse | Design triage logic: 6 categories, BBMP/BWSSB/BESCOM department mapping, severity rules incl. live-wire-near-school = Critical | Category/dept/severity engine spec |
| 4 | Muse | Build single-file prototype: multilingual (EN/Kannada/Hindi script detection + transliteration keywords), photo upload, priority-sorted officer dashboard | Working index.html, all 5 features |
| 5 | Muse | Add 1-click judge demos + seeded duplicate cluster so merging is visible in a 2-minute demo | 3 demo buttons, dashboard stats (duplicates merged, time saved) |
| 6 | Muse | Test triage on 7 cases (critical wire, Kannada garbage, pothole, water leak, tree, drainage, streetlight) and check breakdown sums | Found Critical scored only 75 and streetlight-dark missed High — fixed danger bonus (Critical = 90, breakdown sums exactly) and 'dark' keyword |
| 7 | Muse | Review a rubric analysis warning against "obvious chatbot/wrapper" solutions; audit FixFirst against its 5 suggestions (duplicates, vague handling, multilingual, explainable severity, officer loop) | Already covered 3/5 fully; 2 gaps found: vague-complaint handling and SLA/escalation were only partial |
| 8 | Muse | Add vague-complaint handling: if no category keywords / ≤3 words / generic "road bad", ask 3 clarifying follow-ups with 1-tap detail chips instead of guessing a category | Tested: "road bad" → flagged vague, detailed pothole & Kannada complaints → NOT flagged |
| 9 | Muse | Add officer-side loop: SLA per severity (Critical 4h, High 24h, Medium 3d, Low 7d) + auto-escalation note to Ward Engineer at half-SLA with citizen status update | SLA chip on every ticket; escalation line on Critical/High; Critical case re-tested: 90/100, SLA 4 hrs |
| 10 | Muse | Push prototype to public GitHub repo (arya123-sudo/fixfirst-civiclens, created by Arya in event window) with README in event window | This repository |

_Full unedited AI chat history is submitted separately via share link as required — not edited or deleted._
