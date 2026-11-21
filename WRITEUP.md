# Write-up — CivicLens — AI Triage for Citizen Complaints — Team Neon Pulse
Rohan P (Leader, 1AY25CD403) • Arya Yaligar (1AY24AI012) • Shiva Prasad (1AY24CD051) — Acharya Institute of Technology

## Problem Interpretation
Municipal bodies drown in unstructured citizen complaints. The failure is not collection — it is triage: duplicates create fake workload, misrouting wastes days, and FIFO ordering buries life-threatening issues under minor ones. Both users matter: the citizen (file in 30 seconds, in their language, get a trackable ticket) and the officer (open a dashboard and know, defensibly, what to fix first).

## Approach
CivicLens turns free text/photo into a structured ticket in <2s: language detection (English/Kannada/Hindi) → category classification (Roads/Waste/Water/Electricity/Trees/Drainage) → context-aware severity (keywords + vulnerable-zone proximity: school/hospital escalates) → department routing (BBMP Roads/SWM/Forest/SWD, BWSSB, BESCOM) → Explainable Priority Score 0–100 (Severity + Zone + Community + Photo + Urgency, breakdown shown per ticket).

**Original elements:** (1) Incident Fusion Engine — every new report is scored against open Incidents on location (30), category (15), token/Jaccard semantic similarity (40) and time window (15): 75+ auto-merges as a supporting report and raises priority, 50–74 is queued for a human officer decision, <50 creates a new Incident, and a Critical hazard bypasses fusion entirely so life-safety is never queued; (2) Vulnerable-Zone Escalation; (3) photo credibility boost (+10 for a photo as a presence signal — Vision-API hazard detection is the production step, not claimed here); (4) fully explainable scoring.

## Architecture
Single-file HTML/CSS/JS, no backend — chosen deliberately for demo reliability in a 4-hour event. Triage engine is a deterministic rule/keyword system in 3 languages, designed and iterated via GenAI prompting (see PROMPT_LOG.md). Verified live in a real browser on the canonical cases: Live Wire → Critical / BESCOM / priority 90 with the breakdown summing exactly; Kannada duplicate-candidate → fusion 60 → officer Review Queue; pothole duplicate → fusion 84 → auto-merge with priority boost; vague complaint → clarifying questions instead of a guess.

## AI Tools Used
Muse was used as a GenAI assistant — ideation support, code drafting and iteration — under the team's direction (see Prompt Log). Rohan led solution & feature design and built the presentation deck; Arya implemented and integrated the prototype; Shiva led testing and recorded the demo video. Every AI output was reviewed by the team and verified by running live test cases; the fixes in the prompt log are examples of that critical review.

## Limitations
Runtime triage is a deterministic rule/keyword engine by design (offline demo reliability), built and iterated with GenAI during the event; an optional live-LLM verification call is included (hybrid pattern) but the demo never depends on it. Production: LLM + Vision model as primary, this engine as fallback; ward/landmark chosen from a list (production: GPS/GIS auto-proximity); no persistent backend (production: database, SLA timers, WhatsApp intake, officer mobile app).

## Credits
Map: Leaflet.js (BSD-2-Clause) with map tiles and data © OpenStreetMap contributors (ODbL); place-name lookup: Nominatim (OpenStreetMap Foundation). Animation: GSAP via CDN (guarded — the app works fully without it). Fonts: Google Fonts (Space Grotesk, Inter, Noto Sans Kannada) — open licenses. No external code, data or assets copied into the product; all product code was written during the event window (see commit history).
