[← Guide](../GUIDE.md)

# Fences, streams, train tracks and powerlines

Four tools that lay pieces along a line you draw. They share the drawing: click to add points,
double-click to finish, **Ctrl+right-click** to take a point back, **Shift+click** to start a second
line, and the ring, rectangle and line tools for those shapes. One press of **Lay** lays every line
drawn, and **Export to TerrainBuilder** writes the object list.

Each picks what it can offer by reading your models: a piece whose size FTT cannot measure is left
out rather than laid wrongly.

---

## Fences

Panels along the line, posts where pieces meet, and gates.

| Setting | What it does |
|---|---|
| **Posts at the joins** | A post wherever two panels meet. |
| **Post on every turn** | A post on each corner. A fence corner model is square and says nothing about which way it faces, so a post — which has no facing to get wrong — stands there instead. |
| **Run all the way to the last point** | Carries the fence to the end of the line rather than stopping at the last whole panel. |

**Gates** (second tab). Pick the gate, then how often:

| | |
|---|---|
| **Per side** | One gate on each side of what you drew — a square gets four, which is how a compound is built. |
| **Every N panels** | One gate per so many panels, for a long boundary. A run shorter than one interval gets none. |
| **Just one** | Exactly one on the whole run, for a yard or a paddock. |

And where in the stretch: **Random**, drawn from the seed, so a re-roll moves it and the same seed
repeats it; or **Middle**, mid-stretch every time. A gate *replaces* a panel rather than being
inserted, so the fence stays the length you drew.

Gates are found by name (`Wall_Gate_*`), and a pair of leaves is placed as one gate.

---

## Streams

Water laid piece by piece, and still water in a drawn area.

| Setting | What it does |
|---|---|
| **Overlap** | How far each piece is pushed into the one before. 0 butts the models; 6 m butts the water surfaces. Default 1 m. |
| **Height above ground** | Lifts the whole run this far above the terrain. Written at ground level the water is swallowed by the ground, so it starts at 10 m — set it to 0 once the run is where you want it. |
| **Bend margin** | A little extra pull-back at corners so no gap can open on the outside of a bend. |
| **Height step** | Odd and even pieces are nudged apart by this, so no two water surfaces are ever exactly level and cannot z-fight. |
| **Follow the ground** | Tilts each piece to the fall of the ground under its own two ends. A run that climbs is reported rather than laid silently. |

Only straight pieces are used. The curve models are cut to fit particular places on particular maps,
so bends are made by turning straights and overlapping them at the outer corner.

**Pond** (second tab). Draw an area, choose **Pond** (mossy) or **Lake** (clearer), and **Fill with
water**. Tiles are flat and all sit at the height of the ground under the middle of the area, so the
surface is level like real still water. The edge is stepped at the tile size, which is what square
tiles mean.

---

## Train tracks

| Setting | What it does |
|---|---|
| **Overlap** | As for water: how far each piece laps the one before. |
| **Corner radius** | The radius corners are built at. |
| **Straights for corners the kit cannot turn** | A kit with real curve models can only turn what those models turn. Off, a corner outside that is left as drawn and reported. On, it is built from short straights at the radius above. |
| **Tracks** / **Spacing** | Lay more than one track in parallel, this far apart. |

---

## Powerlines

Two different things behind one panel, decided by what you pick:

- **Poles** — walked along the line at a **pole spacing** you set, with **a pole at each end**.
- **High-voltage spans** — pre-assembled hundred-metre spans that chain like road pieces. There is
  nothing to space, so the spacing rows disappear and the panel says why. A tower stands on each
  corner and at the far end.

The turn models are not used: with no mating points, where a turn begins and ends could only be
guessed from a bounding box, and a tower on the corner is exact.
