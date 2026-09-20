[← Guide](../GUIDE.md)

# Terrain Creation

Seven steps, in the order the work happens. Pick a step on the left and its settings open beside it.

## 1. Mapframe calculator

Terrain size and cell size in; out come the numbers TerrainBuilder's **Mapframe properties** dialog
asks for — grid size, imagery width, landgrid, tiles in a row, overlapped area, satellite segment.

- **Only safe sizes** (on by default) offers the sizes that actually work: powers of two, with a
  grid under 8192. Bohemia's own documentation says an 8192 grid makes TerrainBuilder *"extremely
  unstable"*.
- Turn it off to type anything. A size that is not a power of two is a caution, not an error — 20 km
  is perfectly usable, it just does not divide as cleanly for imagery.
- **Take it from the open project** reads the numbers out of your `.tv4p`.

FTT cannot create the TerrainBuilder project itself: `.tv4p` is a format nothing outside
TerrainBuilder can write safely. It gives you every number to type in, which is the part that is
easy to get wrong.

## 2. Create Terrain Source

Lays down a new terrain from one that already works — the FTT sample, or a terrain you have.

It copies only what a terrain needs (imagery, `layers.cfg`, the legend, both configs, the economy
folder) and renames it through every file: `worldName`, `ceFiles`, the world class, `CfgWorldList`,
the map paths in `layers.cfg`. What it leaves behind is listed with the reason — the sample's
gigabytes of GIS material and exports, and the TerrainBuilder project, which is deliberately not
cloned so your new terrain does not arrive carrying someone else's object layers.

**Dry run** shows every file and every rewrite before anything is written.

## 3. Import rasters from QGIS — *coming soon*

Needs a heightfield writer FTT does not have yet.

## 4. Surfaces and layers.cfg

Every surface your `layers.cfg` declares, with its texture swatch, its legend colour and how much of
the map it covers — beside every colour actually painted in the mask.

- **Compare** cross-references the two: colours in the mask that no surface maps, near misses (a
  colour one value away from a mapped one — the kind of mistake that stays invisible until a surface
  comes out wrong in game), and surfaces mapped but never painted.
- **Add a surface** from the 40 on the work drive: pick it, give it a legend colour, and both the
  texture and material lines are written correctly.
- **Remove** is offered only after a comparison, and refused while the mask still paints that
  surface — removing one that is in use leaves bare ground in game.

`UsedTerrainMaterials` in `config.cpp` is kept in step with what you change.

## 5. CFG editor

The values that name a terrain, over the file itself.

Fields for the world class, `worldName`, `ceFiles`, the description, name, author, url and the map
name and description keys. Focus a field and the file below scrolls to that exact value and
highlights it. Ctrl+F searches, and **What the keys mean** explains each one.

**Check** reads the file against the disk: a `.wrp` that is not there, a CE folder that does not
exist, a `centerPosition` that disagrees with the heightfield. Anything wrong is said under the
field it belongs to rather than in a wall of text at the bottom.

Saving changes only the values you typed and leaves every other byte of the file alone.

## 6. Generate navmesh

Four checks, then the tool:

- `navmeshName` names this terrain's own navmesh, not another map's;
- the `.nm` file is where it says;
- the `.nm` is newer than the `.wrp`;
- the navmesh PBO is in `requiredAddons`.

The first one is not hypothetical: it catches a terrain still pointing at Chernarus's navmesh, which
is what happens when somebody swaps it while testing and forgets. NavMeshGenerator has no command
line, so FTT checks the wiring and opens it.

## 7. Pack to PBO

`FileBank` then `DSSignFile`, with a dry run that prints the exact command lines rather than running
them. Signing is optional and off unless you choose a key.
