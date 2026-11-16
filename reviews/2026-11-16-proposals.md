# Proposals — 2026-11-16

**PROPOSED — awaiting Mohamed's approval.** Nothing in `sets/` changes until he approves.

## Summary
| Set | Now | Proposal | Expected (reading only) |
|---|---|---|---|
| 3d-home-tour-from-floor-plan | 6.5 | Superseded by the merged House Tour v2 below | — |
| floor-plan-walkthrough-harsh-critic | 8.2 | **House Tour v2** = this set + best parts of the home-tour set, metric, KSA | ~9 |
| 3d-city-district-flyover | 7.2 | **District Flyover v2** | ~8.8 |

Patterns applied everywhere (from lessons.md):
1. Read back as a table + check totals + "ask, don't guess" + **STOP until I say "confirmed"**.
2. One kind of object per message + "keep everything already built exactly as it is".
3. Self-critique at the end of each build step.
4. Fresh-chat critic with a 9/10 threshold.
5. Metric units, phone/touch and a performance budget from the first build, not at the end.
6. No hype numbers. Prices are placeholders in SAR.

---

# A) House Tour v2 (merged) — 8 prompts
Replaces: floor-plan-walkthrough-harsh-critic v1 (base) + 3d-home-tour-from-floor-plan v1 (style switch, lighting, client screen).
Setup: one chat for building, a second fresh chat for the critic (prompt 5). Upload the plan as PDF or a sharp photo.

## 1/8 · Read the plan — STOP
```
You're an architectural visualizer. Here's a floor plan. Don't build anything yet.
Read it back to me as a table: room name, size in meters (L × W), area in m², doors (count + width), windows (count + width), and which rooms it connects to.
Use only the dimensions printed on the plan. Sum the areas and compare with the total on the plan; show the difference.
Also list: wall thickness you'll use, ceiling height (default 2.8 m if not shown), floor levels and stairs.
List anything unclear as numbered questions. Don't guess.
Stop here and wait until I reply "confirmed".
```

## 2/8 · Build the shell
```
Build the confirmed plan as one HTML file with three.js from a CDN. Shapes in code only, no imported models or images.
This step: walls, floors, ceilings, door openings and windows only — no furniture yet. Exact dimensions from the confirmed table.
Camera: eye level 1.6 m, walls I can't walk through.
Controls from the start: WASD + mouse on laptop, and an on-screen joystick + drag-to-look on phone.
Show the room name when I enter, a minimap with a "you are here" dot, and a button for a top-down dollhouse view with the roof off.
Performance budget: smooth on a mid-range phone — simple materials, one sun light, no heavy real-time shadows.
When done, list every place where the model differs from the table.
```

## 3/8 · Furnish one zone at a time
```
Furnish only [living + dining] in [modern / warm luxury / Najdi contemporary] style. Keep everything already built exactly as it is.
Match these references for floors, cabinets, lighting and colors: [attach photos, renders or moodboard]. They are the bar.
Real furniture sizes, at least 0.9 m clear walkway around everything, doors and windows never blocked.
Then tell me which part looks least real and list anything you couldn't match.
```
Repeat for each zone (kitchen, bedrooms, majlis, baths). After the last zone: "Add a style switch with 3 styles; furniture keeps the same positions."

## 4/8 · Light presets
```
Add three light buttons: Morning, Sunset, Night. Sunset is warm and golden through the windows; Night turns on lamps and ceiling lights with a soft glow.
Smooth transition between them. Keep everything else unchanged and stay inside the phone performance budget.
```

## 5/8 · Harsh critic (NEW CHAT)
```
You're a strict critic. You didn't build this.
For each room I'll send: a screenshot of the 3D scene, the reference it should match (photo, render or moodboard), and its row from the plan table.
For each room: score 1–10 for (a) match to the reference and (b) match to the plan dimensions. Name the single biggest gap and exactly what to change.
A 7 isn't done.
```
Paste the notes back into the build chat. Repeat until every room is 9+ on both scores.

## 6/8 · Renovation preview (optional, for fit-out clients)
```
Make a copy of the house with these changes: [remove the wall between kitchen and living, add an island].
Add a Before / After button and highlight what changed.
Then list what this change involves — load-bearing wall check, plumbing, electrical, HVAC, municipality/Balady permits — as questions for the structural engineer and contractor. Don't present any of it as approval.
```

## 7/8 · Guided tour + client package
```
Add a Start Tour button: the camera walks the order a buyer would, about 90 seconds, pausing in each room with a one-line caption in Arabic and English — what the room is great for, plus its area in m².
At the end, rise to the dollhouse view.
Add a welcome screen with [project name, location, logo] and Start, a floor switch if there's more than one level, and a contact button with [name, WhatsApp].
Then check on a phone-size screen (390 px wide) and a laptop: list anything cut off, too small to tap, or slow, and fix it.
Finally re-check every room against the confirmed table and fix mismatches.
```

## 8/8 · The pitch
```
Write two short messages to [sales manager name] at [developer], who is selling [project] in [city]:
1) WhatsApp (under 60 words) and 2) email (subject under 6 words, body under 120 words), in [Arabic / English].
I built a free 3D walkthrough from one of their plans: [link]. Lead with the link and the benefit — buyers walk the home before it's built.
Offer: a tour for each plan at [price SAR] per plan, ready in [X] working days.
No hype words, no "I hope this finds you well".
Then write my reply if they say it's too expensive (offer one plan as a paid pilot, not a discount).
```

---

# B) District Flyover v2 — 8 prompts
Base: 3d-city-district-flyover v1.

## 1/8 · Plan the district — STOP
```
You're an urban designer. Plan a small [Mediterranean / Eastern Province compound] district I'll build in 3D with three.js.
Give me: a block grid with dimensions in meters, what sits on each block (villas with roof terraces, plaza with fountain, park with pond, landmark tower), roads with crosswalks, and [elevated train loop / boulevard with palms] as the hero piece.
Colors as hex codes, and the 10 details that make it feel lived in.
Also give a performance plan: how many objects, which ones repeat (instancing).
Stop and wait until I reply "confirmed".
```

## 2/8 · The ground
```
Build the confirmed plan in one HTML file with three.js from a CDN. Shapes in code only, no imported models or images.
Ground only: asphalt roads with lane lines and crosswalks, sidewalks with curbs, grass, stone plaza. Soft sun, pale sky.
Orbit controls that work with mouse and touch (pinch to zoom). Smooth on a mid-range phone.
```

## 3/8 · The buildings
```
Add the buildings from the plan: white villas, 2–4 floors, tall windows, balconies with railings, flat roofs with terraces, plants and a water tank; warm light in some windows. Vary height and layout so no two look the same. Use instancing for repeated parts.
Keep everything already built exactly as it is. Then tell me which part looks least real.
```

## 4/8 · Plaza and park life
```
Fill the plaza and park: fountain in a ring of hedges, café tables with umbrellas, benches, street lamps, palms along the roads, pond with rocks and a lit gazebo. Real proportions, spread naturally, not in rows.
Keep the rest unchanged. Then tell me which part looks least real.
```

## 5/8 · The hero piece
```
Add the [elevated train loop on white pillars with one glass-roof station and a 2-car train that stops 3 seconds / landmark boulevard with animated cars].
Keep the rest unchanged and stay inside the phone performance budget.
```

## 6/8 · Flyover
```
Add a Tour button: hide all buttons, fly the camera in 20 seconds — wide from above, down to the fountain, past the cafés, follow the hero piece, rise back to wide. Smooth easing, no sudden turns, then loop.
Also add a 1080×1920 vertical mode for Reels recording.
Test on a phone-size screen and a laptop; list and fix anything slow or cut off.
```

## 7/8 · Harsh critic (NEW CHAT)
```
You're a strict critic. You didn't build this.
I'll send screenshots of the district from 5 angles plus the original plan.
Score each angle 1–10 for realism and match to the plan, name the biggest gap and exactly what to change. A 7 isn't done.
```
Repeat until every angle is 9+.

## 8/8 · The pitch
```
Write a WhatsApp message (under 60 words) and an email (under 120 words) in [Arabic / English] to [sales manager] at [developer], selling [project], a [compound/district] in [city].
I made a free 3D flyover of a district like theirs: [link]. Lead with what buyers get — walking the finished streets before anything is built.
Offer: a 3D flyover of their own project from their plans for [price SAR], ready in [X] working days. No hype words.
Then write my reply if they say it's too expensive.
```

---

## What still blocks a confirmed 9
Reading only can't prove it. One real test per set (even on a small plan) is needed to confirm.
