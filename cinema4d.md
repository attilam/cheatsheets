---
title: Working With Cinema 4D
kind: article
keywords: cinema4d, howto
created_at: 2015-jun-03 18:38:00
is_draft: true
---

## View

`1` - Pan  
`2` - Zoom  
`3` - Rotate  

Or just use `Alt` + mouse buttons, like in Maya.

## Selection

`H` - Frame Geometry  
`O` - Frame Object  
`S` - Frame Selected part  

`LMB+Scroll Wheel` - Tweak live selection radius  

`Cmd+LMB Drag` - (on scene object) Duplicate Object  

`Alt+G` - Group objects  

## Tools

`E` - Translate  
`R` - Rotate  
`T` - Scale  

`C` - Make Editable  

`M` - modelling menu (emacs-like)  
`V` - radial menu  
`U` - selection/edit menu (emacs-like)  

`D` - Extrude  
`I` - Inner Extrude  

## Rendering

`Cmd+B` - Render Settings  

`Cmd+R` - Render  
`Shift+R` - Render to viewer  

`LMB Double Click` - in material pane to create new material  

## Misc

If view gets screwed up, just select another mode, then back to current. (e.g. persp→parallel→persp)

Hold `Shift` to insert modifiers below objects (by default they are placed in the scene root for some reason).

## Looks & FX (Learn Squared)

### Explosphere

- use Physical Sky (optionally set Composite tag, to hide from camera rays) with reflective objects
- create sphere (icosphere); create MoGraph/PolyFX under it; add a MoGraph/Effectors/Random to PolyFX; set a falloff
- use Atom Array for that cool wireframe look