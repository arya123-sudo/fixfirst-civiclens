# Write-up — FixFirst (CivicLens) — Team Neon Pulse
Rohan P (Leader, 1AY25CD403) • Arya Yaligar (1AY24AI012) • Shiva Prasad (1AY24CD051) — Acharya Institute of Technology

## Problem Interpretation
Municipal bodies drown in unstructured citizen complaints. The failure is not collection — it is triage: duplicates create fake workload, misrouting wastes days, and FIFO ordering buries life-threatening issues under minor ones. Both users matter: the citizen (file in 30 seconds, in their language, get a trackable ticket) and the officer (open a dashboard and know, defensibly, what to fix first).

## Approach
FixFirst turns free text/photo into a structured ticket in <2s: language detection (English/Kannada/Hindi) → category classification (Roads/Waste/Water/Electricity/Trees/Drainage) → context-aware severity (keywords + vulnerable-zone proximity: school/hospital escalates) → department routing (BBMP Roads/SWM/Forest/SWD, BWSSB, BESCOM) → Explainable Priority Score 0–100 (Severity + Zone + Community + Photo + Urgency, breakdown shown per ticket).

**Original elements:** (1) Duplicate Cluster Engine — token-similarity + same category/location merges repeat reports into one master ticket and raises its priority by community count; (2) Vulnerable-Zone Escalation; (3) photo credibility boost (+10 for a photo as a presence signal — Vision-API hazard detection is the production step, not claimed here); (4) fully explainable scoring.

## Architecture
Single-file HTML/CSS/JS, no backend — chosen deliberately for demo reliability in a 4-hour event. Triage engine is a deterministic rule/keyword system in 3 languages, designed and iterated via GenAI prompting (see PROMPT_LOG.md). Verified by automated tests on 7 representative complaints: category & department 7/7 correct, Critical case scores 90/100 with breakdown summing exactly, duplicate pair similarity 0.60 correctly merged.

## AI Tools Used
Muse (ideation, architecture, code generation, testing) — full chat history submitted. Team verified all AI output manually and by running test cases; fixes in Prompt #6 are examples of critical review.

## Limitations
Runtime triage is a deterministic rule/keyword engine by design (offline demo reliability), built and iterated with GenAI during the event; an optional live-LLM verification call is included (hybrid pattern) but the demo never depends on it. Production: LLM + Vision model as primary, this engine as fallback; ward/landmark chosen from a list (production: GPS/GIS auto-proximity); no persistent backend (production: database, SLA timers, WhatsApp intake, officer mobile app).

## Credits
Google Fonts (Inter, Noto Sans Kannada) — open license. No external code, data or assets copied; all code written during the event window (see commit history).
