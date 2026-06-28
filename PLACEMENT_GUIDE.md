# SUNKEN CITY — Placement Guide (what everything is + how to place it)

You place objects, I do mechanics. This is the reference for every prop scene in
`scenes/props/` — drag it into an area, set its position, done. Properties you can
tweak are in the **Inspector** (right panel) when the node is selected.

> GOLDEN RULES
> - **Interactables** (press E) must sit on/near the floor, in open reachable space.
>   The player's "press E" ray only reaches ~2.6 m and can't go through walls.
> - **Floaters** ignore their Y — they snap to the water surface. Only X/Z matter.
> - Don't bury props inside building walls (they vanish / block you).
> - The **chair goes ONLY in the Old Room** (it's the ending).

---

## INTERACTABLES (player presses E)
| Prop scene | What it is | Job in the game | Place it... |
|---|---|---|---|
| `generator.tscn`, `generator2.tscn` | Generator | Press E → restores **power** (completes the area's `power` objective). Powered doors won't open without it. | On the floor, reachable. Pair with a door that `requires_objective="power"`. |
| `keycard.tscn` | Keycard | Press E → adds **keycard** item + completes `keycard`. | On a surface/floor. Needed by doors with `requires_item="keycard"`. |
| `flashlight_pickup.tscn` | Flashlight | Press E → grants `flashlight` item. | Early in a level. |
| `valve.tscn` | Valve wheel | Press E → completes its `objective_id` (default `"drain"`). Used to open drained gates. | Near a gate. Set `objective_id` to match the gate's `requires_objective`. |
| `note.tscn` | Readable note | Press E → shows lore text. Can also grant an item + complete an objective. | Anywhere readable. **Inspector:** set `title`, `body`, `grants_item`, `completes_objective`. The "memory" notes use `completes_objective="fragment"`. |
| `key_tag.tscn` | Luggage tag | Readable lore (same as note). | Story spots. |
| `radio.tscn` | Radio | Press E → plays broadcasts (lore). **Also masks your heartbeat** nearby, so the shark can't hear you while you stand by it. | At a choke point as a "safe" tool. **Inspector:** edit `broadcasts`. |
| `locker.tscn`, `locker2.tscn`, `closet.tscn` | Hide spot | Press E → hide inside (shark goes deaf to you); E again to leave. | Against walls, near danger / along shark routes. |
| `air_vent.tscn` | Air pocket | Press E → refills your air once, then it's spent. | In deep/long underwater stretches where air runs low. |
| `chair.tscn` | **The flatline chair** | Press E → sit → hold **C** → heart hits zero → **you win** (ending). | **Old Room ONLY.** One per game. |

## DECOR & COVER (no interaction — atmosphere + physical blocking)
| Prop | What it is | Place it... |
|---|---|---|
| `crate.tscn`, `wooden_crates.tscn`, `asian_crates.tscn` | Crates | On the floor as cover/clutter. |
| `pipe_box.tscn`, `pipe_shelf.tscn`, `industrial_pack.tscn` | Industrial dressing | Warehouse/tunnel walls + floor. |
| `stop_sign.tscn` | Street sign | Streets (district). |
| `skateboard.tscn` | Childhood memory prop | Home / a quiet corner. |
| `torch.tscn` | **Lit wall torch** (gives warm light) | On walls in dark areas — adds light + atmosphere. Great for the church. |

## FLOATERS (bob on the water — set only X/Z, they ride the surface)
| Prop | What it is |
|---|---|
| `barrel.tscn`, `barrels_cloth.tscn` | Floating barrels |
| `car.tscn`, `police_car.tscn`, `zhiguli_car.tscn` | Half-sunk floating car wrecks |

## STORY / SPECIAL
| Prop | What it is | Place it... |
|---|---|---|
| `girl.tscn` | The figure you reach for. Appears at a distance, **vanishes when you get close.** | At a distance the player will walk toward. One per memory area. |
| `ship_clouds.tscn` | The **ferry** (ending vista) | Old Room only — far/high. Hidden until the flatline reveal. |
| `death_earth.tscn` | The **blue earth** (ending vista) | Old Room only — far/high. |
| `terem.tscn` | Distant tower (ending vista) | Old Room only — far. |

---

## THE MECHANICS (so your placements make sense)
- **AIR** drains while your head is underwater; refills above water or at an **air vent**. → put air vents in long deep swims.
- **HEARTBEAT** rises from low air / sprint (Shift) / panic; **the shark hears it.** Hold **C** (still) to calm it down.
- **SHARK** is blind — it hunts by heartbeat. It now **stalks toward you whenever you're exposed**; you lose it only by **hiding** (locker/closet) or standing in a **mask zone** (radio). → place hide spots + radios along its routes as the player's escape tools.
- **FLOOD** rises over time (anti-camping). Tune per area on the **AreaConfig** node: `start_water` (starting height) + `flood_rate` (units/sec it rises).
- **FLASHLIGHT** = F key, battery drains. Dark areas (the tunnel) force its use.
- **DOORS / PORTALS** (`area_portal.gd`): open only when their `requires_objective` and/or `requires_item` are met, then load `target_scene`. → always place the thing that completes the requirement somewhere reachable in the same area.

## AREA SETUP (the `AreaConfig` node in each area)
Set these in the Inspector:
- `area_name`, `flavor` — the title card shown on entry.
- `objective_ids` + `objective_texts` — the to-do list (parallel arrays).
- `start_water`, `flood_rate` — the flood for this area.
A portal/door in the area should `requires_objective` one of these ids, completed by a generator/valve/note/pickup you place.

## CURRENT AREA FLOW (edit portal `target_scene` to re-route)
Drowned District → Tunnel → Home → Church → Warehouse → Tower → Old Room (ending).

## TUNNEL NOTE (just rebuilt)
The tunnel env was offset down so its road sits at the play floor; it's **dark
(flashlight only)**, starts with shallow water that **rises**, and the shark
stalks. Its props (valve/vents/notes) are at old heights — **reposition them onto
the new road level** as you see fit.
