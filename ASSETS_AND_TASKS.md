# FLATLINE — Master Asset & Task List (build bible)

Flooded cyberpunk city. A **blind shark** hunts by your **heartbeat**. You manage
**air** (swim up to breathe, but breathing is loud), complete **tasks** to escape,
and the ending flips it: you must **flatline your own heart** to starve the shark.

## How to read this
- **[YOU DOWNLOAD]** = you source the model/sound; I tell you what + where + license.
- **[I CODE]** = I write the behavior/script; no download needed.
- **[BOTH]** = a downloaded asset + my script to make it do something.
- Keep everything **LOW-POLY**. The HD 4400 cannot run heavy/realistic assets in
  real time. Target: simple meshes, small textures, no 4K, no 2M-tri models.

## Hardware budget (hard limits — see device notes)
- No photoreal water/reflections, no the heavy 2.4M-tri cinematic city.
- Stylized + dark + fog hides roughness (same trick that saved the cinematic).
- Prefer CC0 (no credit needed). CC-BY = add to CREDITS.txt (shark is already there).

## Best free sources
- **Models:** kenney.nl (CC0 kits), quaternius.com (CC0 low-poly), poly.pizza,
  Sketchfab (filter *Downloadable* + license), itch.io asset packs.
- **Audio:** freesound.org, Wikimedia Commons, OpenGameArt.org, Pixabay.
- **Textures (if needed):** ambientCG, Poly Haven (both CC0).

---

## PHASE 1 — Make swimming feel like a real game (mostly CODE, no downloads)
- [ ] **[I CODE]** Underwater camera feel — bob/sway while swimming *(started)*.
- [ ] **[I CODE]** Drowning effect — screen darkens + red/blue vignette + blur + muffled audio as air drops; gasp + clear when you surface.
- [ ] **[I CODE]** Underwater tint/fog — blue murk below the water line, clears above.
- [ ] **[I CODE]** Surface splash / breath SFX hooks (sounds added in Phase 4 audio).
- [ ] **[BOTH]** Flashlight / TORCH — model + my code (toggle, cone light, battery drains).
      *Asset:* search "flashlight low poly" on Poly Pizza / Sketchfab (CC0/CC-BY).
- [ ] **[BOTH]** Locker HIDEOUT — model + my code (enter to hide, breaks the shark's
      "line of sound", hold breath to stay quiet). *Asset:* "locker" / "school locker" low poly.

## PHASE 2 — The world (DOWNLOAD-heavy, I place + optimize)
- [ ] **[YOU DOWNLOAD]** Modular building kit — low-poly cyberpunk/city walls, floors, doors.
      *Search:* Kenney "City Kit" / Quaternius "Modular buildings" (CC0).
- [ ] **[YOU DOWNLOAD]** Flooded street props — debris, barrels, crates, pipes, signs, neon.
- [ ] **[YOU DOWNLOAD]** Cars (low-poly, a few variants) — half-submerged, floating.
      *Search:* Kenney "Car Kit" (CC0).
- [ ] **[YOU DOWNLOAD]** Dark stormy skybox / panorama (or I make a dark fog environment in code).
- [ ] **[I CODE]** Lay out a small playable district from the kit (a few streets + buildings).
- [ ] **[I CODE]** Rising flood — water level slowly rises over time (anti-camping).

## PHASE 3 — Items, locks & tasks (BOTH: small models + my scripts)
- [ ] **[BOTH]** KEYS + DRAWERS/CABINETS — find keys, open locked drawers. *Asset:* "drawer" / "cabinet" / "key" low poly.
- [ ] **[BOTH]** Locked DOORS + KEYCARD — open with key/card. *Asset:* "door" + "keycard".
- [ ] **[BOTH]** VALVE / PIPE — turn valves as a task. *Asset:* "valve wheel" low poly.
- [ ] **[BOTH]** GENERATOR — restore power task (unlocks doors / lights). *Asset:* "generator".
- [ ] **[BOTH]** AIR POCKET / AIR SOURCE — refill spots that deplete. *Asset:* "air tank" / "pipe vent".
- [ ] **[I CODE]** Objective system — list of tasks, "escape" unlocks when done.
- [ ] **[I CODE]** Challenge mechanics: electrified water zones, blood-in-water trail (decal),
      loud-zone sound masking, calm-breathing minigame, adrenaline lock.

## PHASE 4 — Audio & atmosphere (DOWNLOAD + my hooks)
- [ ] HAVE already: heartbeat, waves, thunder, rain (in `assets/audio`, more in D:\...\audio).
- [ ] **[YOU DOWNLOAD]** Underwater ambience (muffled rumble), bubbles, gasping/breathing.
- [ ] **[YOU DOWNLOAD]** Shark cues — water rush/whoosh, bite/chomp, low growl/sonar ping.
- [ ] **[YOU DOWNLOAD]** UI/interaction — locker open/close, valve turn, door unlock, alarm, pickup.
- [ ] **[I CODE]** Wire all of these to events (muffle audio underwater, sting on shark-near, etc.).

## PHASE 5 — Shark polish & the ENDING
- [ ] **[I CODE / maybe DOWNLOAD]** More shark behavior — circling, idle drift, fast lunge.
      Note: current shark has only **Swim / Bite / ArmatureAction**. More *animations* would
      need a different rigged shark (download) OR I fake variety via speed/turn behavior in code.
- [ ] **[I CODE]** Shark DISSOLVE/death — dissolve shader + particles when it starves (the ending payoff).
- [ ] **[YOU DOWNLOAD]** Smoking-room chair (LIGHT/low-poly version — the cinematic one is too heavy).
- [ ] **[I CODE]** ENDING: final flooded room → reverse the calm mechanic to flatline your
      own heartbeat to 0 → shark starves & dissolves → gasp, pulled from real water
      (callback to the strangle shot) = it was a drowning man's dream.

---

## Priority / order
1. **Phase 1** now — it's almost all code, needs no downloads, and makes the core *feel* real.
   (You can start sourcing the **torch** + **locker** in parallel.)
2. Then **Phase 2** world once you've grabbed a building/car kit.
3. **Phase 3** tasks → **Phase 4** audio → **Phase 5** ending.

## Download checklist for YOU to start on (Phase 1 + 2 first picks)
- [ ] Flashlight / torch (low poly)
- [ ] Locker (low poly)
- [ ] Low-poly city/building kit (Kenney or Quaternius)
- [ ] Low-poly car kit (Kenney)
Drop them in `assets/models/<name>/` like you did the shark; tell me the folder names and I'll wire them in.
