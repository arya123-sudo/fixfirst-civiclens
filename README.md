# CivicLens — AI Triage for Citizen Complaints
**Team Neon Pulse | Tech Habba | Prompt to Product | Acharya Institute of Technology**

**Team Leader:** Rohan P (1AY25CD403, GitHub: rohanp-02)  
**Members:** Arya Yaligar (1AY24AI012, GitHub: arya123-sudo), Shiva Prasad (1AY24CD051, GitHub: shivaprasad938)

> One Issue. One Ticket. Fixed First — Where It Matters Most.

## Problem — CivicLens
Citizens report potholes, garbage, broken streetlights, water leaks and fallen trees via apps/WhatsApp/social media. Municipal bodies get thousands of reports — many vague, many duplicates, many misrouted — so urgent issues get buried.

**Required:** unstructured complaint (text + optional photo, English/regional language) → structured, prioritised, correctly routed ticket + priority-sorted officer dashboard.

## Our Unique Angle (Why we are different from 100+ teams)
Most teams build a form → AI label → list. CivicLens solves the *real* triage failures:

1. **Incident Fusion Engine** — Complaints about the same real-world problem fuse into one **Incident** with supporting reports, scored on 4 signals: Location (30) + Category (15) + Semantic similarity (40) + Time window (15). **75+ auto-merges, 50–74 goes to a human Review Queue, below 50 creates a new Incident** — never a silent wrong merge. Life-safety rule: a Critical hazard always raises its own Incident immediately; fusion never delays it.
2. **Vulnerable-Zone Escalation** — A hazard near a School/Hospital is automatically more severe than the same hazard in an empty area. Context-aware severity, not keyword-only.
3. **Photo Evidence Check** — The moment a photo is attached, an on-device automated check analyses its dimensions, lighting (mean brightness) and sharpness (Laplacian variance), flags low-light / overexposed / blurry evidence on the ticket for the officer, and adds +10 priority. Honest scope: it checks evidence *quality*, not content — detecting the hazard inside the image is the production Vision API step, not claimed here.
4. **Explainable Priority Score 0–100** — Every ticket shows its breakdown: Severity (0-40) + Zone (8-20) + Community (0-20) + Photo (0/10) + Urgency (15). No black box — officers can defend the order to citizens/councillors.

## Features (All 5 Required + Extras)
- [x] 1. Free-text complaint in English / Kannada / Hindi (auto language detection, Kannada & Devanagari script support) + optional photo with preview — **citizen-first 30-second flow**: hero "Report a Problem" button jumps straight to the form, 3-step guidance (Describe → Snap → Submit), and **in-website photo capture** (live camera via getUserMedia with a mobile `capture` fallback) alongside gallery upload. **Exact-location map pinning** (Leaflet + OpenStreetMap): tap-to-pin or one-tap GPS — coordinates ride on the ticket with a view-on-map link so crews reach the exact spot; degrades gracefully offline. **Photos are geo-tagged by default**: taking or attaching a photo automatically stamps it with the device's current location (shown in the Photo Evidence Check and on the ticket), auto-pins the spot if no pin exists, and a **Use My Current Location** button beside the photo buttons lets the citizen set it explicitly
- [x] 2. Classification: Roads, Waste, Water, Electricity, Trees, Drainage (keyword engine in 3 languages + transliteration)
- [x] 3. Severity: Low / Medium / High / Critical with one-line reason (e.g. exposed live wire near school = Critical)
- [x] 4. Routing: Roads→BBMP Roads, Waste→BBMP SWM, Water→BWSSB, Electricity→BESCOM, Trees→BBMP Forest Cell, Drainage→BBMP Storm Water Drain
- [x] 5. Officer Dashboard sorted by Priority Score, filters by category/severity, status workflow Open→Assigned→Resolved
- [x] Extra: Duplicate detection & merging, Priority breakdown, Crew Route button, Stats (Critical count, duplicates merged, time saved), 1-click judge demos
- [x] Extra: **Vague-complaint handling** — "road bad" is NOT guessed; AI asks 3 clarifying follow-ups with 1-tap detail chips
- [x] Extra: **SLA + REAL auto-escalation** — Critical 4h / High 24h / Medium 3d / Low 7d. Every Critical/High ticket carries a live countdown (demo clock compresses half-SLA to 2–4 min; production uses real hours). At zero — or via the 'Simulate half-SLA' button — status flips to ESCALATED → Ward Engineer, citizen notified. Not just a label: a state change you can watch.
- [x] Extra: **Hybrid AI** — deterministic triage engine is the always-on, offline-safe default (designed via GenAI, see Prompt Log); the 'Verify with Live AI (beta)' button additionally calls a live external LLM when the network allows, and openly reports if it is unreachable — the fallback result stands either way.

## How to Run
No install, no backend, no API key — works offline for a bulletproof live demo.
```
Open index.html in any browser
# OR
python3 -m http.server 8000  → http://localhost:8000
```
## Demo Flow (2 minutes)
1. Click **Live Wire Near School** → Submit → NEW Critical Incident, BESCOM, Priority 90 (fusion is bypassed for life-safety — it never waits in a queue)
2. Click **Kannada Garbage** → Submit → Language detected Kannada; Fusion scores it 60/100 vs the existing Dasarahalli garbage Incident (semantic signal is weak across languages) → it lands in the officer **Review Queue** — click *Keep Separate* or *Merge*, a human decides
3. Click **Duplicate Same Pothole** → Submit → Fusion 84/100 → **AUTO-MERGED** into the master Incident, supporting reports +1, priority boosted
4. Click **Vague "Road bad"** → Submit → no guessing: 3 clarifying follow-ups with 1-tap detail chips
5. On any Critical/High ticket, watch the SLA countdown — or click **Simulate half-SLA** to see it flip to ESCALATED live

## Tech
Single-file HTML/CSS/JS prototype, rule-based triage engine designed from LLM prompting iterations, Git versioned during event.
**Next-level design layer (v2):** Three.js particle-cluster background (ThreeUI-style), GSAP + ScrollTrigger choreography, TasteSkill art direction (one palette — warm dark ink + amber; colour spent on severity data; quiet dashboard panels), 21st.dev component patterns (bento grid, shimmer button, number-ticker stats, SVG priority rings). Every enhancement is guarded — if venue WiFi/CDNs fail, animations degrade and the triage engine still works 100% offline.

## AI Tools Used
Muse / ChatGPT-class GenAI for ideation, triage logic design, code generation & iteration — full prompt log in PROMPT_LOG.md, full chat history submitted separately as required.

## Limitations & Next Steps
- Prototype triage is rule-based for demo reliability; production would call Gemini/GPT Vision for photo hazard detection & free-text understanding
- Location is ward/landmark selection; production adds GPS + GIS proximity auto-detection
- Scale: ward → city → state, WhatsApp bot intake, SLA timers & auto-escalation, officer mobile app

## Team — Neon Pulse
- Rohan P — Team Leader — 1AY25CD403 — GitHub: [rohanp-02](https://github.com/rohanp-02)
- Arya Yaligar — 1AY24AI012 — GitHub: [arya123-sudo](https://github.com/arya123-sudo)
- Shiva Prasad — 1AY24CD051 — GitHub: [shivaprasad938](https://github.com/shivaprasad938)
