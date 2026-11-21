# Prompt Log — Team Neon Pulse — CivicLens — AI Triage for Citizen Complaints
_Event: Tech Habba, Prompt to Product, Acharya — 21 Nov 2026, 4-hour window_

**How we worked:** Team Neon Pulse designed and built CivicLens hands-on in the event window, using Muse as a GenAI assistant for ideation support, code drafting and iteration. Every AI output was reviewed, corrected and live-tested by the team before it was accepted — nothing was taken as-is.

**Team contributions**
- **Rohan P (Team Leader)** — solution & feature ideas (Incident Fusion bands, vulnerable-zone escalation), presentation deck, testing
- **Arya Yaligar** — prototype implementation & integration (triage engine, photo, map, geo-tag features), testing
- **Shiva Prasad** — testing of demo flows & edge cases, demo video recording
- **Muse (GenAI tool)** — assisted ideation, drafted code & content from team prompts, iteration support

| # | Tool | Prompt / Purpose | Outcome |
|---|------|------------------|---------|
| 1 | Muse | Read the Participant Guide + Rules PDFs; extract the problem statement, 5 required features, judging rubric and penalties | Team spec + rubric checklist; verified by the team against the PDFs |
| 2 | Muse | "100+ teams get the same problem — what will everyone build, and what novel angle wins Innovation?" | Generic form+chatbot rejected by the team; Rohan's direction adopted: duplicate clustering + vulnerable-zone escalation + explainable priority |
| 3 | Muse | Design the triage logic: 6 categories, BBMP / BWSSB / BESCOM department mapping, severity rules (live wire near school = Critical) | Engine spec; department mapping validated by the team for Bengaluru |
| 4 | Muse | Draft the single-file prototype v1: complaint form → triage result → officer dashboard | Arya implemented & integrated it; team ran the first demo cases and listed corrections |
| 5 | Muse | Add Incident Fusion: score every new report vs open Incidents (Location 30 + Category 15 + Semantic 40 + Time 15); 75+ auto-merge, 50–74 human Review Queue, Critical bypasses fusion | Implemented; Shiva tested merge / review / new-incident cases live until all three behaved correctly |
| 6 | Muse | Make it citizen-first: in-website photo capture + upload, Photo Evidence Check, Track Your Complaint by ticket ID | Implemented from team feedback; tested with a 10 MB phone photo and a wrong ticket ID |
| 7 | Muse | Add exact-location map pinning and geo-tagged photos that show the place name in words, not just coordinates | Implemented; team verified at the Acharya campus spot — pin and photo stamp showed the correct place name |
| 8 | Muse | Redesign clean & simple — white interface, Home / Report / Dashboard / Track sections with dropdowns (team direction) | UI rebuilt; full demo flow re-tested by all three members |
| 9 | Muse | Fix what live testing exposed: remove-photo option, step-by-step guidance when device location fails, visible geo stamp on the photo | Each fix re-verified in a real browser by the team before acceptance |
| 10 | Muse | Rename the product FixFirst → CivicLens — AI Triage for Citizen Complaints across app, deck, README and write-up | Renamed everywhere; repo URL deliberately kept so the live demo link never breaks |
| 11 | Muse | Assemble the submission pack: pitch deck, write-up, prompt log, prototype screenshots | Deck by Rohan; write-up & log compiled from the team's records; Shiva recorded the demo video from the team's script |
