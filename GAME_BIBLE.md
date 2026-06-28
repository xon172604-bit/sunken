# SUNKEN CITY — Game Bible (story, assets, areas, lore)

> Working title: **FLATLINE**. Genre: first-person underwater survival-horror.
> Core: a **blind shark** hunts your **heartbeat**; manage **air**; descend through
> a flooded dream; the only way out is to **stop fighting and flatline**.

## The one-sentence truth (the twist the whole game hides)
You are a man **drowning right now**. Everything you play is the last dream of an
oxygen-starved brain. The "sunken city" is stitched from your memories. The shark
is your own death. Your **air** is the life left in your lungs. Every door you open,
every level you go *deeper*, you are **sinking, not escaping**. You cannot outswim it.
The only ending is the chair: **let your heart stop**, stop struggling, and finally
let go — and you wake (or pass) in peace.

## The three throughlines
1. **The Shark** = death/panic. Blind, hears your heartbeat. Grows bolder as you sink.
2. **The Radio** = the narrator. A waterlogged radio crackling fragments — flood
   broadcasts at first, then your own voice, then hers, then a flatline tone.
3. **The Girl** (sitting_girl) = the person you're reaching for. Always seated, always
   just out of reach, never speaks. The emotional payoff is at the chair.

---

## ASSET → IN-GAME ROLE (every downloaded asset has a job)

### Environments (each is its OWN scene/area, loaded one at a time — the GPU rule)
| Asset folder | In-game name | Role in the story |
|---|---|---|
| cyberpunk_city | **The Drowned Street** | Opening. Wake submerged in neon ruin. |
| tunnel | **The Tunnel** | Flooded road tunnel; shark gauntlet; load-corridor between areas. |
| japan_cyberpunk | **Neon Alley** | Deeper district; memory starts leaking in. |
| abandoned_house | **Home** | Memory: your house. Regret. |
| bathroom | **The Bath** | Memory: where the drowning is literal. Highest water. |
| warehouse | **The Warehouse** | Memory: where "the accident" happened. |
| haunted_parish | **The Church** | Memory: guilt/funeral. The Girl prays here. |
| abandoned_building | **The Tower** | The descent; the dream decays. |
| lofts | **The Apartments** | Optional descent floor. |
| terem | **The Cabin** | Surreal childhood/dream fragment. |
| debris | **The Collapse** | Choked, broken room near the end. |
| industrial_pack | (set dressing) | Industrial props across tunnel/warehouse. |
| smoking_room | **The Old Room** | FINALE. The chair. Flatline ending. |
| ship_clouds | (ending vista) | The ferry — closing dream imagery. |
| death_earth | (ending vista / skybox) | The shore / the void you wake to. |
| glider | (ending red herring) | "Fly away" — the escape that isn't. |

### Interactables / props
| Asset | In-game name | Job / interaction |
|---|---|---|
| generator, generator2 | **Generator** | Restore power (objective; unlocks doors/lights). |
| locker, locker2, closet | **Locker / Closet** | Hide — breaks the shark's hearing. Loot some. |
| valve, vent_valve | **Valve** | Turn to drain water / open a gate (task). |
| key, key_tag | **Key / Keycard** | Open locked doors. key_tag carries a lore tag. |
| flashlight, torch | **Flashlight / Torch** | Pickup light source; battery drains. |
| radio | **Radio** | Narrator device + loud zone that MASKS your heartbeat. |
| barrels, barrels_cloth | **Barrel** | Floating debris / cover. |
| crates, wooden_crates, asian_crates | **Crate** | Debris; some are lootable containers. |
| pipe_box, pipe_shelf | **Shelf / Pipe** | Loot shelves; industrial dressing. |
| cars, police_cars, zhiguli_cars | **Car wreck** | Half-sunk floating wrecks; cover; some loot. |
| stop_sign | **Street sign** | Street dressing. |
| skateboard | **Skateboard** | Tiny memory prop (childhood) — a note hook. |
| sitting_girl | **The Girl** | Apparition; appears seated, fades when approached. |
| great_white_shark | **The Shark** | The monster. |

---

## AREA FLOW (the descent)
1. **Drowned Street** → restore power + find keycard → open flood bulkhead → Tunnel
2. **Tunnel** → torch on, valves to drain/open the gate, dodge the shark → Neon Alley
3. **Neon Alley** → find the key into the Memory Rooms hub
4. **Memory Rooms** (Home / Bath / Warehouse / Church) → collect 4 **memory fragments**
5. **The Tower / Collapse** (descent, dream breaking, flood fastest) → final key
6. **The Old Room** → the chair → **flatline** → shark dissolves → ending vistas

Air gets scarcer each area (you're running out of life). The shark gets bolder.

---

## LORE TEXTS (notes / radio — drip the story)
- **Street note (on a floating car):** "They said go to high ground. There is no high
  ground. The water came up through the drains, through the walls, through me."
- **Radio, Street:** "...all residents evacuate the lower districts... repeat... the
  barrier has failed..." (static)
- **Tunnel graffiti:** "DON'T MAKE A SOUND. IT HEARS YOU."
- **Home note:** "I told her the boat was safe. I told her I'd hold on. I let go."
- **Bath note:** "The water's warm. If I just stop kicking, it stops hurting."
- **Warehouse note:** "Shift log — valve 3 jammed. Tank overflowed at 02:14. Two unaccounted."
- **Church note:** "Forgive me. I came up and she didn't."
- **key_tag:** a luggage tag: "RETURN TO — (the ink has run)."
- **Radio, final:** your own voice: "...stop swimming. Let your heart go quiet. Come up."
  then a flat tone.
- **Ending card (chair):** "you gasp awake / coughing seawater on a grey shore /
  the flooded city, the shark — the last dream of a drowning man."

---

## MECHANICS (built ✓ / to build ▢)
- ✓ Heartbeat as master variable; blind shark hears it; calm/sprint/panic.
- ✓ Air drain by depth; drown death; rising flood; locker hide; mask zone; electric water.
- ✓ Flatline finale (chair) + shark dissolve + true-ending screen.
- ▢ Persistent inventory + collected lore in GameManager (survive area changes).
- ▢ Area-transition portals (change_scene) gated by items.
- ▢ Readable notes → HUD lore panel; area title cards on entry.
- ▢ Radio device (lore subtitles / audio) doubling as a mask zone.
- ▢ The Girl apparition (appears, fades when approached).
- ▢ world_env auto-collision for walkable scanned environments.
- ▢ Memory-fragment collectibles gating the ending.

## BUILD ORDER
1. Framework: persistent inventory, portals, notes, title cards, world_env collision.
2. Build **Drowned Street** (cyberpunk_city) as the first real playable area + props.
3. Build **Tunnel** + transition. 4. Memory rooms. 5. Descent. 6. Wire the ending vistas.
Each environment: import → measure tris/textures → downscale if heavy → collision → light/fog → place props/interactables/lore → portal in/out → headless-verify.
