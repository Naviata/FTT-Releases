[← Guide](../GUIDE.md)

# Forester

Fills ground you mark out with trees, bushes, rocks and clutter, at a spacing that respects each
model's real size, keeping off slopes and out of the water.

![Forester](forester.jpg)

## Marking the ground

The tools sit down the left of the map. Anything you mark is shown in green.

| Tool | How |
|---|---|
| **Area** | Click corner by corner. **Shift+click** starts a second, separate area. |
| **Brush** | Drag to paint ground in. **Brush size** appears beside the button. |
| **Rub out** | Drag to take painted ground back out. Its own size, wider than the brush. |
| **Circle** / **Rectangle** | Press at the middle and drag out. |
| **Bin** | Clears everything marked. |

**Ctrl+right-click** removes the last point, **Ctrl+Z** undoes the last stroke, and a drawn area can
have one corner removed by right-clicking the dot itself. One wood can be several areas; they are
filled together, and the count and hectares are shown under the map.

## The species mix

The right-hand column is the model library; the box at its foot is the mix.

- **Plant packs** — ready-made mixes filtered to what your project actually has: Norway spruce,
  European broadleaf, pine, larch, summer, winter, late fall, undergrowth. A pack with fewer than
  twelve variants in your libraries is left out, because it plants the same model over and over.
- **Search the library** and press **Add to mix** for anything else. Weights are normalised, so
  three entries at any numbers give the same result as 33/33/33.
- Drag the splitter above the mix to make it taller.

## Mix settings

| Setting | What it does |
|---|---|
| **Spacing (m)** | How far apart objects are thrown. The floor under everything else. |
| **Max slope (°)** | Nothing is planted on ground steeper than this. Default 35°. |
| **Seed** | Makes a generation repeatable. **Re-roll** changes it. |
| **Keep footprints apart** | Uses each model's measured size, so a big oak takes the room it needs and a shrub does not. |
| **Keep out of the water** | Drops anything below sea level. |
| **Randomise rotation** | Spins every placement through a full turn, overriding what the template asks for. |
| **Randomise scale** | Varies size between **Smallest** and **Largest** (10–200%). Off, each model keeps the range its template was authored with. |
| **Add to what is already there** | Keeps clear of what is already in the preview *and* of the objects in your imported layers, so a second wood does not land on the first. |
| **Lay on the ground slope** | *Per model* — each template decides (the default). *Upright* — everything stands straight. *Lay flat* — everything lies along the ground, for rocks and clutter. |
| **Ground surfaces** | A list of the surfaces in `layers.cfg` with the share of the map each covers. Tick one to keep objects off it — for example no trees on concrete. |

## Generating and exporting

**Generate** fills every marked area at once. Objects are drawn at the size of the model they stand
for, so the wood reads as a wood rather than a field of identical dots.

Not right? Change a setting and press Generate again, or **Re-roll** for a different throw of the
same settings. To thin it by hand, use **Pick** (drag a box, Ctrl-click to add) and **Rub out** from
the map tools, with **Ctrl+Z** to undo.

**Export to TerrainBuilder** writes the object list. Put it in your terrain's `shapefiles` folder and
import it as a layer.

## Saved areas

**Save area** keeps the shape *and* the mix that filled it in your project. Reopening it restores
both, so a wood can be adjusted next week and generated again. A saved area whose models your
project no longer has is listed as unreadable rather than silently dropped.

## If nothing appears

Almost always the slope limit or the water: the default refuses anything steeper than 35° or below
sea level. The line under Generate says which limit did the rejecting.
