[← Guide](../GUIDE.md)

# Hole Generator

Marks the terrain cells a hole is cut in — for a tunnel, a bunker or anything underground — and
writes them to `holes.cfg`.

![Hole Generator](hole.jpg)

## The two views

| | |
|---|---|
| **2D map** | The satellite map from above, with the cell grid. |
| **3D view** | The same place in 3D, marked cells in red on the real ground, with the objects standing beside them. |

Both mark holes the same way, so you can find the spot from above and check it from the ground.

## Marking

- **Click** the map (or the ground in 3D) to mark a hole at the size and shape below.
- **Pick an area** — drag a block and every cell inside it is marked.
- **Rub out cells** — drag to take single cells back out.
- **Undo last** and **Clear** for the rest; **Ctrl+Z** works as everywhere else.

| Setting | What it does |
|---|---|
| **Group** | The group your marks go into — type a name such as `Dambog` or `Military`. Each group becomes its own class in `holes.cfg`, so letters, digits and underscores only. Left empty it is `Holes`. |
| **Size** | How many cells across each mark is. |
| **Shape** | Square or round. Below four cells the two are the same cells. |
| **Show the cell grid** | The terrain's own grid over the map, with coordinates, thinning as you zoom out. |

The readout under the map gives the cell under the pointer, the world position, and that cell's
bounds in metres — so a number worked out on paper can be checked against the map.

## The grid

**Grid size** and **cell size** are read from the heightfield and can be corrected by hand, because
the two do not always agree with what a terrain really uses (`2048 × 10 m` and `4096 × 5 m` are both
20,480 m, and only one of them matches your cells). The pair is remembered per terrain, and **Take
it from the heightfield** puts them back.

**Jump to cell (X, Z)** centres the map on a cell; **Fit map** frames the whole terrain.

## Shapes as a guide

**Show a shapefile…** draws a `.shp` over the map as an outline — useful for cutting holes where a
GIS layer says. It makes no holes by itself. **Shift them onto the terrain** moves the shapes so
their middle sits on the middle of the terrain, which is a guess: only you know where the data was
meant to land.

## Writing it

**Write the holes** writes `holes.cfg` beside `layers.cfg` — where TerrainBuilder and Buldozer read
it — and adds the one `#include` line to `config.cpp` if it is not already there. Groups already in
the file are read back in, so you can add to them later.

Buldozer re-reads `holes.cfg` on every alt-tab, which is the workflow: mark in FTT, write, alt-tab,
look.

## The HOLES card

Every group is listed with its tile count and whether it is saved, edited or unsaved — with **Go
to** (centres the map, or the camera in 3D), **Rename** and **Remove**. Removing a group is
undoable; writing the file clears the undo history, because the file keeps no trace of a click.
