---
title: Working With Blender
kind: article
keywords: blender, howto
created_at: 2013-jul-31 23:58:00
is_draft: true
---

## Navigation/View

`MMB` - Orbit  
  -> `Shift` - Pan  
  -> `Ctrl` - Zoom  

`Num0` - Camera/Scene view  
`Num5` - Persp/Ortho  
`Num1/3/7/9` - different ortho views  
`Num.` - Zoom Extents  
`Num/` - Toggle Global/Local mode ("solo"/"exclusive" mode for edited object)  

`Home` - view camera center (to fill 3d vp with camera clip)  

`Ctrl+Alt+Num0` - move active camera to current viewport view  

`Z` - toggle wireframe mode  
`Shift+Z` - Toggle viewport render mode  

`Shift+Space` & `Ctrl+UpArrow` & `Ctrl+DownArrow` - Toggle Maximize for active view  

Properties Panel (`N`) -> `Lock camera to view` - to move active camera with 3d viewport commands  

## Selection

`Shift+A` - Add Menu  

`F6` - View operator panel for current tool as popup  

`tab` - toggle object/edit mode  

`A` - toggle selection  

`Shift+G` - Select Grouped Menu (e.g. parent, children, same type, color, layer, ...)  
`Ctrl+G` - create new Group  
`Ctrl+Shift+G` - add all objects to active object's group  

`Alt+RMB` - Select Menu (lists of all objects under cursor)

`C` - circle (brush) selection, scrollwheel to set brush size  
`B` - box select  
`Ctrl+LMB` - freeform (lasso) select  

`H` - hide selected  
`Shift+H` - set restrict view (hide others)  
`Alt+H` - clear restrict view  

`X` - delete/dissolve  
  -> in object mode doesn't delete children! use outliner menu!  
  -> also try Limited Dissolve to decimate polygons by angle  
`Ctrl+X` - Dissolve Selected  

`M` - Move to Layer Menu

### Edit mode selection

`Ctrl+RMB` - select vertex/edge/face path (after 1 item already selected)  
`Alt+RMB` - select vertex/edge/face loop (mouse direction to item midpoint decides loop orientation) 

`L` - select linked (cumulative)  
`Ctrl+L` - select all connected  
`Shift+G` - select similar  

## Transformation

`Ctrl+space` - Toggle 3D manipulator (Pie)  
  -> `Shift+LMB Drag` - on a manipulator axis transforms on perpendicular plane to axis  
`Alt+space` - Transformation Orientation Menu  

`G` - grab/move  
  -> `G` - again to "edge slide" vertices!  
`R` - rotate (press twice for trackball rotation)  
`S` - scale  
`Ctrl+M` - mirror  
  -> `X,Y,Z` - constrain to single axis  
  -> `Shift+X,Y,Z` - add constraint axis to transform on a plane  
    -> double tap axis keys to toggle local/global  
    -> type in numbers to specify exact transformation along selected axis  

With a camera selected enter Camera View (`Num0`), and the transform tools can be used to tweak it easily.  

To move/rotate/scale on a plane interactively hold `Shift` while dragging the arrow handle corresponding to the _normal_ of the plane.  

### Pivot

`Alt+.` - Active Element  
`Ctrl+.` - Individual Origins  
`Ctrl+,` - Median Point  
`,` - Bounding Box  
`.` - 3D Cursor  

`Alt+,` - Manipulate Center Point  

`Alt+G/R/S` - reset translation/rotation/scale  
`Ctrl+A` - Apply transform (T/R/S)  

`Ctrl+P` - set parent (select child(ren), then parent, then `Ctrl+P`)  
`Shift+Ctrl+P` - parent without inverse menu  
`Alt+P` - clear parent menu (use it after parenting to clear hidden inverse transform!)

### Snapping

`Ctrl+shift+TAB` - set snap type  
`shit+TAB` - toggle snap  
`Shift+S` - Snap Menu (snaps either selection, or cursor)  
`Ctrl+drag` - force snap

## Object Mode

`Ctrl+B` - sets the render border, `Ctrl+Alt+B` to clear  

`Ctrl+J` - Join Objects  

`L` - Make Local Menu (Linking)  

`Ctrl+A` - Apply Transformation menu

`Alt+C` - Convert Menu (convert between mesh <-> curves)

## Edit Mode

`Ctrl+Tab` - Toggle Verts/Edges/Faces mode

`Ctrl+Num+` & `Ctrl+Num-` - grow/shrink selection

`W` - specials menu (Subdivide, Bevel, Bridge, etc)  
`Ctrl+V` - vertex tools  
`Ctrl+E` - edge tools (e.g.: Mark Sharp, Mark Seam (UV))  
`Ctrl+f` - face tools  
`Alt+M` - Merge Menu  
`U` - UV Mapping Menu  
`Shift+G` - Select Similar Menu

`E` - extrude, extend curve (bezier, path, etc; MUST undo if canceling to clean up geo!)  
`Alt+E` - Extrude Menu (choose region/individual)  
`Ctrl+LMB Click` - Quick Extrude Selection  

`Ctrl+B` - Bevel  
`Ctrl+Shift+B` - Vertex Bevel (handy for making circles inside geom)  

`I` - Inset tool  
  -> `Ctrl` - Depth, `O` - Outset, `B` - Boundary  

`Alt+R` - Spin Tool (i.e. Loft, around cursor)  
`Alt+S` - shrink/fatten, push/scale along normal  

`Y` - Split selection (essentially: cut out, by duplicating vertices)  
`K` - Knife tool  
  -> `Ctrl` - midpoint, `C` - constraint snap, `Shift` - disable constraint  
  -> `E` - start another cut  
`Shift+K` - Select Knife tool (works on selection)  

`J` - connect vertices (creates an edge between two verts, splits faces, "lightning bolt")  
`Ctrl+R` - Loop Cut and Slide Tool  

`F` - Fill (make edge/face / convert to single N-gon; Sort Vertices if needs be)  
`Alt+F` - Fill with triangles

`O` - Proportional Edit mode toggle (for soft selections)  
`Alt+O` - Proportional Editing, connected only

`Ctrl+T` - Triangulate Faces  
`Alt+P` - Poke Faces (subdivide so each quad turns into 4 tris in an X shape)  
`Alt+J` - Convert tri selection to Quads  

`Ctrl+N` - make normals consistent (recalculate normals)  

`Shift+E` - set creasing (for subdiv)  

### UV Editor

`P` - Pin  
`Alt+P` - Unpin  
`Ctrl+P` - Pack Islands  
`W` - Welding Menu  
`V` - Stitch  

`Q` - UV Sculpt Tool (use the Toolshelf `T` to change params)  
  -> `F` - change brush radius, `Shift+F` - change brush strength

## Animation

`I` - insert keyframe (context sensitive: control under mouse is keyframed, or popup if in 3D view)  

`T` - set keyframe interpolation mode  

`Alt+A` - play/pause animation  
`Shift+left/right` - go to first/last frame of animation  

## Node Editor

`Ctrl+T` - Add Texture Mapping nodes to selected node  

`Ctrl+Shift+RMB` (Compositing) - Connect selected node to Viewer node  

## Useful Keyboard Shortcuts

`Shift+R` - repeat previous command  

`Shift+NumPad /` - edit linked library (addon)  

`Ctrl+2` - add subdiv modifier with detail set to 2  

`Shift+D` - duplicate object  
`Alt+D` - instantiate object  
`Ctrl+L` - make links (to e.g. material)  
`Ctrl+Shift+Alt+C` - set origin  

`P` - Separate part of the object into a new one  

`V` - set handle type (for curve controls, and animation keyframes)  
`Alt+C` - toggle cyclic (for curves)  
`Alt+C` - Convert to (mesh/curves, in object mode)  

`F12` - Render  

`E` (w. mouse over a control) - Pick value for control in viewport (e.g. for Depth of Field Distance, etc.)

## Misc stuff

- Objects are transforms that reference Data blocks (mesh, materials, etc)
  - the same Data can be referenced by multiple Objects (i.e. instantiating)
  - Data with 0-references gets deleted upon save/reopen
  - add a Fake User to keep 0-ref Data (via the F button in properties)

- _Hover_ over any control and `Ctrl+C` to copy, or `Ctrl+V` to paste value (even colors!)

- Blender's config file is just a scene file, so a way to migrate settings is to open it in the new Blender version

- use the Edge Split modifier to smooth object via angle (i.e. "smoothing groups"/faceting)
- or use Auto Smooth on the data tab of the selected object

- Make use of the fact that you can type in numbers for interactive transform tool
  - e.g. `S` `Z` `0` to flatten something in Z, or `R` `Y` `90` to rotate 90º in Y

- UV Mapping Menu
  - press Reset, then Follow Active Quads to neatly layout selected faces

- Straighten Edges according to normals
  - select edges (e.g. `ctrl+RMB` for a path)
  - set Transformation Orientation (3D View) to "Normal"
  - set Pivot Center (3D View) to "Individual Origins"
  - press `S` (for scale), and `Z` `Z` (to scale along local Z, i.e. normal direction), then `0` (to scale to 0)

- use the Skin modifier to quickly build organic models, similarly to zbrush
  - in a mesh object extrude points (`Ctrl+LMB`) to build skinned branching structures
  - press `Ctrl+A` to scale vertices (i.e. skin thickness)
- select 2 vertices and use 'Select Vertex Path' (`W` menu) to select all the edges between them (cool to mark UV seams for example)
- the border of the camera view is selectable like any object, transform tools work on it!

- use Select -> Select All by Trait -> Loose Geometry to help clean up your models

- use the `Auto Merge` button in 3D View to automatically merge vertices that are moved together

- Bake AO
  - create a new Image map in the UV/Image Editor
  - go to Edit Mode, in UV Mapping Select Unwrap/Lightmap Pack to create UV if necessary
  - link image to UV in UV/Image Editor by browsing to it at the bottom
  - back in Object Mode go to the World tab to setup AO for rendering
    - enable Ambient Occlusion
    - in Gather set Samples to desired amount to keep noise down
    - in Gather tweak Attenuation and Falloff Strength to adjust AO smoothness
  - on the Render tab open the Bake dropdown
    - set Bake Mode to Ambient Occlusion
    - check Normalized
    - set desired Margin
  - press Bake
  - in UV/Image Editor select Image/Save as Image to save the map

- Dynamic Paint Procedural "Tech" Carving
  - create a model as "canvas" and another as "brush"
  - add Dynamic Paint Modifier to both
  - on the Dynamics tab enable Dynamic Paint with the respectable setting for each
  - on the Canvas object
    - in Dynamic Paint Add Canvas, and set Surface Type to Weight
    - on the Data tab new Vertex Group with the same name as the Dynamic Paint Output
    - add a Mask modifier and use the created vertex group as input (invert if needed)
    - optionally use the Solidify modifier on the result
  - on the Brush object
    - turn off editor and camera visibility
    - use tricks, like Displacement modifier with a procedural texture for more interesting looks

- Solving Addon Troubles
  - duplicate addons: start blender in terminal, open the Addons panel, it'll show the paths
  - missing addons: uncheck addon, save user prefs to make it disappear

## Addons

- Blender Cloud (for sync)
  - `Ctrl+Shift+Alt+A` - Download texture

- Enhanced 3D Cursor
  - https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/3D_interaction/Enhanced_3D_Cursor
  - `F10` - place cursor
  - `LMB Drag` to move 3D cursor along faces
  - Hold `Ctrl` to snap to vertices
  - Hold `Shift` to snap to center of faces

- LoopTools (builtin)
  - https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Modeling/LoopTools
  - very handy modelling tools in the `W` menu
  - Arrange points around selection into a circle
  - Relax, space out loop or path

- BoolTool
  - https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Object/BoolTool
  - interactive boolean modifier
  - `Ctrl+Num+` & `Ctrl+Num-` - bool ops (in object mode)
  - use the `Alt+C` menu on target to convert to regular object (finalizes bool)

- ANT Landscape
  - terrain generator
  - https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Add_Mesh/ANT_Landscape

- Property Chart
  - like Houdini's spreadhseets

- Copy Attributes (builtin)
  - `Ctrl+C` - copy various attributes from one objects to another

- Node Wrangler (builtin)
  - lotsa useful/essential node workflow enhancements

- Pie Menus Official (builtin)
  - `Z` - Shading
  - `Q` - View Directions
  - `.` - Pivot
  - `Tab+Ctrl+Shift` - Snapping

- F2 (builtin)
  - massively enhanced fill polygon function `F`

- Extra Objects (builtin)
  - additional mesh and curve objects (2 addons!)

- HardOps ($15)
  - hard surface modelling to 11
  - https://masterxeon1001.com/

- BoxCutter ($15)
  - easy booleans
  - https://masterxeon1001.com/

- Sprytile
  - https://chemikhazi.itch.io/sprytile
  - `S` - snap 3D cursor to nearest vertex
  - `W` - center view on 3D cursor
  - `1` / `2` - rotate tile cw/ccw 90º
  - `3` / `4` - flip tile in X/Y
  - Hold `Alt` to pick tile in scene

- PBR Materials
  - http://www.3d-wolf.com/materials.html

- BRM-UVTools
  - UV editing in the 3D viewport!
  - https://github.com/leukbaars/BRM-UVTools

- BRM-UVAlignMinMax
  - align selected UVs to selection min/max
  - https://github.com/leukbaars/BRM-UVAlignMinMax

- Yet Another Vertex Normal Editor
  - https://github.com/fedackb/yavne

- TexTools
  - https://blenderartists.org/forum/showthread.php?443182-TexTools-for-Blender

- Texture baking UI for Blender 
  - https://github.com/leukbaars/BRM-BakeUI

### Check these out

- Blendermada
  - online blender material database
  - http://blendermada.com/

- Animation Nodes
  - node-based scripting tool
  - http://blenderartists.org/forum/showthread.php?350296-Addon-Animation-Nodes

- Gaffer Light Manager
  - https://cgcookiemarkets.com/all-products/gaffer-light-manager/

- BLAM Blender Camera Calibration Toolkit
  - http://stuffmatic.com/blam-blender-camera-calibration-toolkit/

- Archimesh

- Tissue
  - http://www.co-de-it.com/wordpress/code/blender-tissue

- Amaranth Tools
  - http://pablovazquez.org/amaranth/

- Batch Operations
  - https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/3D_interaction/BatchOperations

- Easy Lattice
  - http://www.blenderartists.org/forum/showthread.php?290925-Easy-Lattice-editing-addon-you-are-going-to-like-the-way-you-lattice&p=2367593#post2367593

- Extrude and Reshape
  - http://blenderartists.org/forum/showthread.php?376618-Addon-Push-Pull-Face
  - crashes a lot :(

- Ice Tools
  - https://blenderartists.org/forum/showthread.php?343641-Iceking-s-Tools
  - retopology helper
