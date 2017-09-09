---
title: "Let's learn: Max/MSP"
created_at: 2014-03-27 21:38:32 +0400
keywords: max, msp, jit, gen, cycling74, max4live, live, ableton, howto
kind: article
is_draft: true
---

## Create Objects

`X` - show a list of object types  

`N` - object  
`M` - message  
`I` - integer  
`F` - float  
`L` - live object  
`J` - jit object  
`T` - toggle  
`B` - button  
`C` - comment  
`P` - presentation object  

`ALT+LMB` - (on object) open help for object  

**!!! Numbers: if decimal point exists: float (e.g: 0.), if not: int.**

Use $N to refer use inlet N as param

## Send and Receive

Two nodes for wireless messaging:  
`[send name]` → `[receive name]`, or just `[s name]` → `[r name]`

## Patch cords

Black cords are data lines, yellow cords are audio lines.  
If multiple cords go to an inlet, their values are summed.  

`CMD+SHIFT+Y` - route patch cords  
`ALT+LMB` drag - rect select cords  

## Patch Locking

`CMD+E` - toggle edit mode  
`CMD+LMB` click - toggle lock  
`CMD+LMB` drag - (on object) temporarily toggle lock  

## Presentation Mode (`ALT+CMD+E`)

Select nodes and choose "Add to Presentation" to make them available there.  
**RMB click empty space → Patcher Inspector → Open in Presentation**

## Patchers within Patchers

`CMD+SHIFT+E` - encapsulate selection into a new patcher  
`CMD+2*LMB` - open up a patcher for editing  

`patcher` - creates a subpatcher that can have its own `inlet` and `outlet` objects to route data  

`bpatcher` - can load a saved patcher with its own presentation mode for node GUI  

`poly~ MaxPatName N` - loads subpatcher MaxPatName to enable N voice polyphony  
`thispoly~` within a `poly~` subpatcher can be used to signal if a poly voice is "busy"  
**patch `loadmess target 0` into the first inlet of a `poly~` to send params to inlets of all voices (the target attribute sets voice number, 0 = all)**

Loaded subpatchers have `in N`, `out N`, and also ~ versions to represent inlets and outlets (N is the index)

## Abstractions, Packages and Projects

Save patchers as abstractions so they can be used in Max like standard objects. The folder to save to is ~ **Max 6.1/Packages/ati/patchers/blah.maxpat**. In this case you get a new object that you can place as `ati.blah`.

## Interesting messages

`bondo <num>` - takes `<num>` inputs, packs all of them and forwards them

`target 0` - target voice for `poly~`, 0 means all voices

`drunk 128 12` - random number with steps

`loadmess message` - sends message when the patcher is loaded (double-click to send manually)

`print` - log to Max console.  
`meter~` - signal meter