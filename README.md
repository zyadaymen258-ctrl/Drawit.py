# drawit

**Engineering drawings by code.** Write Python in the editor, and drawit draws the
isometric and orthographic views next to it, then exports a finished sheet
(frame, title block, coloured isometric, section views, dimensions).

Developed by Eng. Ziad Ayman.

## Features
- **Shapes are Python classes**: `Box`, `Cylinder`, `Cone`, `Sphere`, `Tube`, `Torus`,
  `Wedge`, `Prism`, `Extrusion`, `Revolution`, `Plate`, `LBracket`, `Flange`.
  Their parameters are the shape's properties.
- **Operations are methods of the shape**: `cut_hole`, `cut_slot`, `cut_rect`,
  `cut_extrude`, `cut_arc`, `cut_arc_slot`, `cut_function`, `cut_parametric`,
  `cut_surface`, `cut_revolve`, `hollow`, `extrude`, `union`, `intersect`,
  `fillet`, `chamfer`, `move`, `rotate`, `mirror`, `scale`.
- **Cavities of any shape**, including cuts defined by a function `y = f(x)`.
- **2D profiles**: `Circle`, `Rect`, `Ellipse`, `Slot`, `Polygon`, `Sector`,
  `FunctionRegion`, `Parametric`, `Path` and more.
- **Sheet output**: orthographic views, coloured isometric, hatched sections,
  centerlines, automatic dimensions, hidden lines.
- **Export**: PDF, PNG, JPG, SVG, DXF, STL.
- **Editor**: syntax highlighting and code autocomplete.
- **Pure Python** (numpy + Pillow). No CadQuery / OpenCascade required.

## Quick example
```python
from drawit import *

part = Box(40, 30, 10, color="orange")
part.cut_hole(d=6)

sheet = Sheet("My part", size="A4", orientation="landscape", dimensions=True)
sheet.add(part, views=["front", "top", "iso"])