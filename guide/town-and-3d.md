[← Guide](../GUIDE.md)

# Town Planner and 3D View

## Town Planner

Clicks buildings onto the map, turned to line up with the nearest road.

**Placing.** Pick a building from the palette and click the map. **Ctrl+right-click** takes the last
one back. **Pick at random** takes a different building from the palette for each click, from the
**seed** — so a street is not the same house twenty times. Re-roll the seed for a different set.

**Facing.**

| | |
|---|---|
| **Along road** | The long side runs along the road, which is how houses line a street. |
| **Across** | The long side runs across the road, so the building presents its narrow end to it. |
| **Free** | Ignore the road and use the **angle** below. |
| **Flip 180°** | Turns it round. |

Front and back cannot be told apart from a model's shape — DayZ's buildings do not say which way
they face in anything FTT can read — so the flip is offered rather than guessed. About one building
in five is square enough to have no long side at all, and the panel says so rather than pretending.

**What is offered.** A model is a building if it carries a door selection, or if it is named as a
building in `mapgrouppos.xml`. Parts — walls, roofs, balconies — satisfy neither and stay out of the
list.

---

## 3D View

![3D View](fly.jpg)

Flies over your own heightfield, with the satellite map draped over it, water, and every placed
object drawn as a box at its real size. It is a viewer: nothing here changes your terrain.

**Flying.** Mouse to look, the usual keys to move, and the camera never drops below the ground.
Object boxes are drawn near the camera up to a cap you can raise, so a town does not cost a frame.

**Three looks:**

| | |
|---|---|
| **Satellite** | The satellite map over the shaded ground — what the terrain looks like. |
| **Plain** | Grey ground with the shading alone, which is how you read *shape* rather than ground cover. |
| **Mesh** | The triangles themselves. |

The satellite drape is one image over the whole terrain, so it goes soft near the ground — that is
resolution, not a fault. Real models are not drawn: DayZ ships them compressed in a way nothing
outside its own tools can read, so a box at the model's exact size is what the data supports.
