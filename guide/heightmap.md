[← Guide](../GUIDE.md)

# Edit heightmap

Roads, rivers and buildings need the ground shaped under them: a river needs a channel, a road a
level strip, a house a flat pad. FTT works that out as you lay them and writes it into your
heightmap when you ask.

![Edit heightmap](heightmap.jpg)

## What asks for ground

| Tool | What it asks for |
|---|---|
| **Streams** | With **Carve a channel** on, a bed cut to the **water width** and **depth** you set, always running downhill. |
| **Roads** | With **Shape the ground under the road** on, the road's width plus a **shoulder** held level, banked back to the ground around. Each road piece is tilted to the road's own grade. |
| **Town Planner** | With **Level the ground under buildings** on, a flat pad under each building, with a **margin** round it. |
| **Bridges** | The ground under a bridge is kept below its deck. |

Nothing is written until you press **Write heightmap**. Until then it is a list of changes.

## The popup

**Edit heightmap** sits beside Export on Roads, Streams, Train tracks, Powerlines and the Town
Planner.

| | |
|---|---|
| **The list** | Every change asked of the ground, one row per press of Lay. |
| **Write heightmap** | Writes them all into your heightmap. The first time, the original is copied into an `FTT backup` folder beside it. |
| **Remove** | Takes the chosen change off the list. |
| **Put the original back** | Writes the heightmap as it was before FTT touched it. |
| **Open folder** | Opens the folder with the heightmap and the backup. |

FTT always works from the original, so writing twice never cuts a river deeper.

## Then in TerrainBuilder

1. Import the heightmap again.
2. Export the objects from FTT **after** writing, and import those — pieces are set on the shaped
   ground.
3. Build and look in Buldozer.

FTT never deletes a backup. Keep the newest one: it is what **Put the original back** uses.
