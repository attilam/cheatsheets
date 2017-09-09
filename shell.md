---
title: Working in the Shell
kind: article
keywords: shell, howto
created_at: 2015-jun-16 08:15:00
is_draft: true
---

## Handy Shortcuts

`man readline` for more  

`Ctrl+L` - clear screen  

`Ctrl+U` - delete whole line  

`Ctrl+K` - delete until end of line  

`Alt+F` - move forward 1 word  
`Alt+B` - move backward 1 word  

## History

`Ctrl+R` - search history  

## tmux

Use it!

`Ctrl+B` - Hotkey (before all shortcuts, like in emacs)  

`?` - Help  

`"` - Split vertically  
`%` - Split horizontally  

## grep

```shell
$ asar list app.asar | grep -v "^/node" # every line NOT (-v) starting with (^) "/node"
```