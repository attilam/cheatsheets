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
  Lock camera to view menu - to move camera with 3d vp commands  

`Ctrl+Alt+NumPad0` - move active camera to current viewport  

`Z` - toggle wireframe mode  

`Shift+Space` & `Ctrl+UpArrow` & `Ctrl+DownArrow` - Toggle Maximize for active view

## Selection

`Shift+A` - Add Menu  

`F6` - View operator panel for current tool as popup  

`tab` - toggle object/edit mode  

`A` - toggle selection  

`Shift+G` - Select Grouped Menu  
`Ctrl+G` - create new Group  
`Ctrl+Shift+G` - add all objects to active object's group  

`Alt+RMB` - select edge/face loop (after 1 item already selected)  

`C` - circle (brush) selection, scrollwheel to set brush size  
`B` - box select  
`Ctrl+LMB` - freeform (lasso) select  

`L` - select linked (cumulative)  
`Ctrl+L` - select all connected  
`Shift+G` - select similar  

`H` - hide selected  
`Shift+H` - set restrict view (hide others)  
`Alt+H` - clear restrict view  

`X` - delete/dissolve  
  -> in object mode doesn't delete children! use outliner menu!  
  -> also try Limited Dissolve to decimate polygons by angle  
`Ctrl+X` - Dissolve Selected  

`M` - Move to Layer Menu

## Transformation

`Ctrl+space` - Toggle 3D manipulator (Pie)  
  -> `Shift+LMB Drag` - on a manipulator axis transforms on perpendicular plane to axis  
`Alt+space` - Transformation Orientation Menu  

`G` - grab/move  
  -> `G` - again to "edge slide" vertices!  
`R` - rotate (press twice for trackball rotation)  
`S` - scale  
  -> `X,Y,Z` - constrain to single axis  
  -> `Shift+X,Y,Z` - add constraint axis to transform on a plane  
    -> double tap axis keys to toggle local/global  
    -> type in numbers to specify exact transformation along selected axis

### Pivot

`Alt+.` - Active Element  
`Ctrl+.` - Individual Origins  
`Ctrl+,` - Median Point  
`,` - Bounding Box  
`.` - 3D Cursor  

`Alt+,` - Manipulate Center Point  

`Alt+G/R/S` - reset translation/rotation/scale  
`Ctrl+A` - Apply transform (T/R/S)  

`Ctrl+P` - set parent (select child, then parent, then `Ctrl+P`)  
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

`E` - extrude, extend curve (bezier, path, etc)  
  - MUST undo if canceling to clean up the shit it leaves behind  
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

`I` - insert keyframe menu (mouse over context sensitive)  
`Alt+A` - play/pause animation  
`Shift+left/right` - go to beginning/end of animation  
`T` - set keyframe interpolation mode

## Useful Keyboard Shortcuts

`Shift+R` - repeat previous command  

`Shift+NumPad /` - edit linked library (addon)  

`Ctrl+2` - add subdiv modifier with detail set to 2  

`Shift+D` - duplicate object  
`Alt+D` - instantiate object  
`Ctrl+L` - make links (to e.g. material)  
`Shift+Ctrl+Alt+C` - set origin  

`P` - Separate part of the object into a new one  

`V` - set handle type (for curve controls, and animation keyframes)  
`Alt+C` - toggle cyclic (for curves)  
`Alt+C` - Convert to (mesh/curves, in object mode)  

`F12` - Render  

`Ctrl+Shift+RMB` - (Compositing) Connect selected node to viewer

## Misc stuff

- Objects are transforms that reference Data blocks (mesh, materials, etc)
  - the same Data can be referenced by multiple Objects (i.e. instantiating)
  - Data with 0-references gets deleted upon save/reopen
  - add a Fake User to keep 0-ref Data (via the F button in properties)

- use the Edge Split modifier to smooth object via angle (i.e. "smoothing groups"/faceting)
- or use Auto Smooth on the data tab of the selected object

- use the Skin modifier to quickly build organic models, similarly to zbrush
  - in a mesh object extrude points (`Ctrl+LMB`) to build skinned branching structures
  - press `Ctrl+A` to scale vertices (i.e. skin thickness)
- select 2 vertices and use 'Select Vertex Path' (`W` menu) to select all the edges between them (cool to mark UV seams for example)
- the border of the camera view is selectable like any object, transform tools work on it!

- In the Compositing Node editor create a Viewer node, enable background image, and connect any node's output to it via `Ctrl+Shift+RMB`

- Solving Addon Troubles
  - duplicate addons: start blender in terminal, open the Addons panel, it'll show the paths
  - missing addons: uncheck addon, save user prefs to make it disappear

- use Select -> Select All by Trait -> Loose Geometry to help clean up your models

- Make use of the fact that you can type in numbers for interactive transform tool
  - e.g. s z 0 to flatten something in Z, or r y 90 to rotate 90º in y

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


## Addons

- Blender Cloud (for sync)

- Enhanced 3D Cursor
  - https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/3D_interaction/Enhanced_3D_Cursor
  - `F10` - place cursor
  - `LMB Drag` to move 3D cursor along faces
  - Hold `Ctrl` to snap to vertices
  - Hold `Shift` to snap to center of faces

- LoopTools (builtin)
  - https://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Modeling/LoopTools
  - very handy modelling tools in the `W` menu

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
  - lotsa useful node workflow enhancements

- Pie Menus Official (builtin)
  - `Z` - Shading
  - `Q` - View Directions
  - `.` - Pivot
  - `Tab+Shift+Ctrl` - Snapping

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
