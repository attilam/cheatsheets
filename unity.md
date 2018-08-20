---
title: Working With Unity
kind: cheatsheet
keywords: [code, cheatsheet]
created_at: 2015-may-27 13:24:00
---

## Useful Keyboard Shortcuts

`Z` - Pivot mode toggle (Pivot/Center)  
`X` - Rotation pivot toggle (Global/Local)  

## Alignment and Snapping

- Edit-> Snap Settings menu to change snapping  

`CMD+LMB Drag` - Transform with snapping  
`CMD+Shift+LMB Drag` - Transform: snap to target surface normal, Rotate: look at point on target surface  

`CMD+Alt+F` - Move object to view  
`CMD+Shift+F` - Align object to view  

`V` - held when Transform tool is active: snap to vertex  
  - Hold `V` -> `LMB Drag` from active object's vertex to target object's vertex  

`FF` or `Shift+F` - lock camera to GameObject  

## Misc

- Quickly access Editor.log and Player.log using the console's top-right dropdown menu.
- After a crash go to the "Temp/__Backupscenes" folder, it contains 0.backup, a copy of your scene when you last hit Play

## Code

- Use `[SerializeField]` with a private members to create params only changed by artists.
- avoid the use of `Update()` if you can. use coroutines, or events, or other solutions
- use the profiler!
- You can make icons for your custom ScriptableObjects: put "ClassName Icon.png" in a folder called Gizmos
- use the default keyword to have Vecotr3, etc params as defaults  
e.g. `void Thing(Vector2 pos = default(Vector2)) { }`

### mix editor code into component's file

``` csharp
#if UNITY_EDITOR
using UnityEditor;
#endif

// ...

	// Destroying objects if using ExecuteInEditMode
	void OnDisable() {
#if UNITY_EDITOR
		if (!Application.isPlaying) {
			DestroyImmediate(rt);
		} else {
			Destroy(rt);
		}
#else
		Destroy(rt);
#endif
	}

#if UNITY_EDITOR
[UnityEditor.CustomEditor(typeof(MyClass))]
public class MyClassEditor : UnityEditor.Editor {
	public override void OnInspectorGUI() {
		DrawDefaultInspector();

		// ...
	}
}
#endif
```

### Create quick and dirty editor scripts using ExecuteInEditMode

``` csharp
[ExecuteInEditMode]
public class QuickAndDirty : MonoBehaviour {
	public bool doIt = false;

	void Update() {
		if (doIt) {
			doIt = false;

			// do the things (like renaming objects or whatever)
		}
	}
}
```

## Articles and Videos

http://www.gamasutra.com/blogs/SarahHerzog/20151125/260053/Creating_an_Animating_Loading_Screen_in_Unity_5.php

realistic set of stacked pile of objects
https://www.youtube.com/watch?v=PJBPCnuaqIo
