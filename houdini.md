---
title: Working With Houdini
kind: article
keywords: houdini, howto
created_at: 2014-oct-09 23:13:00
is_draft: true
---

## Useful Keyboard Shortcuts

`Shift` after tool shelf button - move object prototype on Y axis  
`CMD+LMB` on tool shelf button - create in origin  
`Q` - repeat tool (add another node of the same type, a MUST for modelling)  

## Viewport

`ESC` - view mode:  
`SPACE` held - quick switch to view mode  
`H` - home  
`A` - frame all  
`G` - frame selected  
`Z` - pick focus point  
`D` - display options  
`Alt+'` - switch between single and multi views (maximize view)  

`W` - wireframe toggle  
`Shift+W` - shaded wireframe toggle  

## Selection

`S` - Select Mode  
`1` - object select  
`2` - point select  
`3` - edge select  
`4` - primitives select  
`5` - vertex select  

`N` - select all  
`A+MMB` - Loop select (have to select another element first, hold `Shift` to add)  
`Shift+L` - select loop  
`Enter` (in viewport) - handle for current tool, if switched away  

`\`` - Reselect for current tool  

## Transform

`T` - Translate  
`R` - Rotate  
`E` - Scale  

`Shift+LMB drag` - precision mode  

## Handles

`M` - Handle Alignment cycle (Object/World/View/Component)  

## Animation

`Up/Down Arrow` - play/pause animation forward/back  
`CMD+Up Arrow` - reset to first frame  
`Alt+LMB` - create keyframe  
`Ctrl+LMB` - delete keyframe  

## Network Editor

`L` - relayout nodes (cleanup)  
`T` - toggle tree view  
`C` - toggle color palette  
`Shift+D` - hide selected nodes  
`Shift+E` - unhide all  
`R` - swap node inputs  
`Shift+C` - create subnet  

## Textfields

`Shift+RMB` - undo edit  
`Ctrl+MMB` - Revert to Defaults  
`Alt+MMB` - Export parameter to type properties  

## Misc

`I` - "dive into" selected node (works in viewport, network, etc!)  
`U` - go up a level (works in viewport, network, etc!)  
`P` - toggle parameter panel within active viewport/editor  

`Ctrl+LMB` drag on slider - snap slider to whole numbers  

`CMD+L` on any navigation bar - enter path manually  

`X` - create Visualize SOP from selected  

## Expressions

`* ^ground*` - everything, but NOT anything that starts with 'ground'  

## Attributes

Right click any SOP and select Spreadsheet to open the Geometry Spreadsheet.  

## VEX

- via http://www.tokeru.com/cgwiki/index.php?title=HoudiniVex  
- via http://nomoreretake.net/en/2015/09/25/houdini-recipewrangle-memo-01/  

### Frequently used attributes

``` VEX
// SOP
@Cd // Point Color
@P // Point Position
@v // Point Velocity
@ptnum // Processed Point Number
@numpt // Total Num of Points
@primnum // Processed prim
@numprim // Total Num of prims
@pscale // Particle Scale
@N // Point Normal

// Time
@Frame // Frame Number
@Time // in seconds?
```

### Attribute Creation

``` VEX
// Types
f@Float = 1.0; // float
i@ID = @ptnum; // int
v@Vec = {0,1,2}; // vector
u@UV = {3, 4}; // vector2
s@Text = "blah"; // string

// Component Access
@P.x = @P.x + rand(@ptnum);
@P.y = anoise(@P.y);
@P.z = fit(@P.z, 0, 5);

@Cd = {1, 0, 0};
@Cd.g = @Cd.g+1;
```

### Geometry

``` VEX
// Add Point
vector pos = {0, 0, 0};
addpoint(geoself(), pos);

// Add Primitive (Line)
int prim = addprim(geoself(), "polyline");
for(int i=0; i<@numpt; i++) {
	addvertex(geoself(), prim, i);
}

// Add Primitive (Face)
int faceNum = 3;

for(int j=0; j<@numpt; j+=faceNum) {
	int prim = addprim(geoself(), "poly"); // or "polyline"
	for(int i=j; i < j+faceNum; i++) {
		addvertex(geoself(), prim, i);
	}
}

// Remove Point
if (@ptnum%5 == 0) {
	removepoint(geoself(), @ptnum);
}

// Remove Primitive
if (@primnum%2 == 1) {
	removeprim(geoself(), @prminum, 1);
}

// Groups (as attribute)
// access as [@group_*], e.g. check as [@group_blah==1]
if (@ptnum < chi('threshold')) {
	i@group_mygroup = 1;
}

if (@ptnum == 10) {
	i@group_mygroup = 0;
}

// Groups
string groupName = "testGroup";

for(int i=0; i<@numpt; i++) {
	if (@P.x<0) {
		setpointgroup(geoself(), groupName, @ptnum, 1, "set");
	}
}
// same for prims, via setprimgroup(...)

// Channels, Parameter Interface
int i = chi("myIntParam");
float f = chf("myFloat");
vector vec = chv("myVector");
//
// Press the connector button on the right of the wrangle
// text editor to auto create parameter interface!
```

Create a new attribute by defining it, with a @ in front: `@foo;`, or even initialize it: `@foo=1;`

Create a vector attrib by prefixing with v: `v@myvec={1,2,3};`, `v@myvec=set(0, @P.x, 1);`

float `f@foo=1.234;`, int `i@foo=1;`, vector `v@vec={1,2,3};`, quaternion `p@quat;`, 3x3 matrix `3@tr;`

Access attribute channels via dot notation: `@Cd.r = sin(@P.x*2);`

Use explicit attribute type with custom attributes, or Houdini will assume float: `@Cd = v@mycolor;`

Automatically create UI controls for channels: `i@myint = chi('myint');`, `f@foo = chramp('myramp', @P.x);`

Some common functions: `fit()`, `rand()`, `sin()`, `cos()`, `radians()`, `length()`, `distance()`

Some common built-in attributes: `@ptnum`, `@numpt`, `@Time`, `@Frame`, `@prminum`, `@numprim`

Use variables instead of attributes to keep things local: `float foo; vector bar; matrix m`

Get values from arbitrary points `vector col = point(0, "Cd", 5);`

Array variable: `int myarray[] = {1,2,3}; int foo = myarray[2];`
Array attribute: `i[]@things = {1,2,3}; int foo = i[]@things[2];`

Examples:

```vex
if (rand(@ptnum) > ch('threshold')) {
	removepoint(0, @ptnum);
}
```

```vex
@d = length(@P);
@P.y = sin(@d*ch('scale')+(ch('speed')*@Time));
```

## OPScript

`commandecho on`  
`opcf` - change folder (like cd)  
`opadd type name` - add node of type, with name (opadd geo myBall)  
`opparm object param value` - set value of param on object (opparm mySphere tx (3.0))  
`opscript -b /obj/someObject > $HIP/scripts/obj/someObject.cmd` - write out an object  
`source $HIP/something.cmd` - load a written out object  

`exhelp` - 'man' style expression help  

## Links

http://www.tokeru.com/cgwiki/index.php?title=Houdini

## Tips

Drag and drop anything onto anything to reference it, it usually works...

Parent by either parent tool, or connecting objects in network editor
Unparent using either parent tool (don't select secondary object), or breaking connection in Network editor (drag from socket to empty space)

When dealing with variables put the name within `{}` when they are in the middle of a string (e.g. `${OS}` instead of `$OS`)

In the Copy SOP use 'Pack geometry before copying' to instance objects instead of copying, and look at the savings!

To "fix" object alignment when using the Copy SOP to copy onto points on an object
  - polygonal objects: add a Point SOP of the target object, select Add Normals ($NY, $NY, $NZ), and Particles/Add Up Vector (0, 1, 0)
  - splines: add a PolyFrame SOP, turn off Normal Name, set Tangent Name to N

To create a "3D grid", create a Box, and add a Points from Volume SOP under it.

In the Attribute SOP use the Local Variable switch to create variables out of attributes, accessible via $ (e.g. `$MYATTRIB`).

Use the Attribute Transfer SOP to create falloffs (Effectors in MoGraph). It is a good idea to create a custom attribute on source/target objects to transfer.

Create a Visualize SOP by pressing `X` to visualize attributes in different ways.

Use an Attribute VOP to create response curves/falloffs in attribute values:
  - use Bind VOP to input the attribute
  - create response curve (e.g. via a Spline Ramp VOP)
  - use Bind Export to output the attribute back to the object

Avoid the Point SOP if possible: it doesn't scale well with high point counts, uses a lot of local variables, and you have to type each expression 3 times always (xyz/rgb). Instead use Point VOPs/wranglers, shaders, particles, anything.

Use the Solver SOP to create persistent/accumulation effects.

Use VEX inside group fields to create impromptu groups: `@P.y<0`. No spaces though, space is used by Houdini to separate group names!
