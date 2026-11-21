# FixFirst — CivicLens AI Triage
**Team Neon Pulse | Tech Habba | Prompt to Product | Acharya Institute of Technology**

**Team Leader:** Rohan P (1AY25CD403)  
**Members:** Arya Yaligar (1AY24AI012, GitHub: arya123-sudo), Shiva Prasad (1AY24CD051)

> One Issue. One Ticket. Fixed First — Where It Matters Most.

## Problem — CivicLens
Citizens report potholes, garbage, broken streetlights, water leaks and fallen trees via apps/WhatsApp/social media. Municipal bodies get thousands of reports — many vague, many duplicates, many misrouted — so urgent issues get buried.

**Required:** unstructured complaint (text + optional photo, English/regional language) → structured, prioritised, correctly routed ticket + priority-sorted officer dashboard.

## Our Unique Angle (Why we are different from 100+ teams)
Most teams build a form → AI label → list. FixFirst solves the *real* triage failures:

1. **Duplicate Cluster Engine** — Same pothole reported 12 times becomes 1 master ticket, not 12 buried tickets. Community count boosts priority and saves officer time (shown live in dashboard: "Duplicates Merged" + "Hours Saved").
2. **Vulnerable-Zone Escalation** — A hazard near a School/Hospital is automatically more severe than the same hazard in an empty area. Context-aware severity, not keyword-only.
3. **HazardEye Photo Verification** — Photo attached = verified credibility (+10 priority). Officers act on proof.
4. **Explainable Priority Score 0–100** — Every ticket shows its breakdown: Severity (0-40) + Zone (8-20) + Community (0-20) + Photo (0/10) + Urgency (15). No black box — officers can defend the order to citizens/councillors.

## Features (All 5 Required + Extras)
- [x] 1. Free-text complaint in English / Kannada / Hindi (auto language detection, Kannada & Devanagari script support) + optional photo upload with preview
- [x] 2. Classification: Roads, Waste, Water, Electricity, Trees, Drainage (keyword engine in 3 languages + transliteration)
- [x] 3. Severity: Low / Medium / High / Critical with one-line reason (e.g. exposed live wire near school = Critical)
- [x] 4. Routing: Roads→BBMP Roads, Waste→BBMP SWM, Water→BWSSB, Electricity→BESCOM, Trees→BBMP Forest Cell, Drainage→BBMP Storm Water Drain
- [x] 5. Officer Dashboard sorted by Priority Score, filters by category/severity, status workflow Open→Assigned→Resolved
- [x] Extra: Duplicate detection & merging, Priority breakdown, Crew Route button, Stats (Critical count, duplicates merged, time saved), 1-click judge demos
- [x] Extra: **Vague-complaint handling** — "road bad" is NOT guessed; AI asks 3 clarifying follow-ups with 1-tap detail chips
- [x] Extra: **SLA + auto-escalation** — Critical 4h / High 24h / Medium 3d / Low 7d; Critical & High escalate to Ward Engineer at half-SLA with citizen status update

## How to Run
No install, no backend, no API key — works offline for a bulletproof live demo.
```
Open index.html in any browser
# OR
python3 -m http.server 8000  → http://localhost:8000
```
## Demo Flow (2 minutes)
1. Click **⚡ LIVE WIRE Near School** → Submit → Critical, BESCOM, Priority ~95
2. Click **🇮🇳 KANNADA Garbage** → Submit → Language detected Kannada, Waste, BBMP SWM
3. Click **🔁 DUPLICATE Same Pothole** → Submit → "DUPLICATE DETECTED — Merged into CL-2026-1042, priority boosted" — this is the wow moment
4. Scroll dashboard — tickets re-sort by priority, explain breakdown

## Tech
Single-file HTML/CSS/JS prototype (intentionally dependency-free for 4-hour reliability), rule-based triage engine designed from LLM prompting iterations, Git versioned during event.

## AI Tools Used
Muse / ChatGPT-class GenAI for ideation, triage logic design, code generation & iteration — full prompt log in PROMPT_LOG.md, full chat history submitted separately as required.

## Limitations & Next Steps
- Prototype triage is rule-based for demo reliability; production would call Gemini/GPT Vision for photo hazard detection & free-text understanding
- Location is ward/landmark selection; production adds GPS + GIS proximity auto-detection
- Scale: ward → city → state, WhatsApp bot intake, SLA timers & auto-escalation, officer mobile app

## Team — Neon Pulse
- Rohan P — Team Leader — 1AY25CD403
- Arya Yaligar — 1AY24AI012 — GitHub: arya123-sudo
- Shiva Prasad — 1AY24CD051
_GitHub IDs for Rohan & Shiva to be added when shared._
