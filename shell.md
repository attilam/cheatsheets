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

## Directory Stacks


Push a directory onto stack and enter it
```shell
$ pushd /dir/name
```

pop directory off, go back to previous
```shell
$ popd
```

## Text Manipulation

```shell
$ asar list app.asar | grep -v "^/node" # every line NOT (-v) starting with (^) "/node"
```

```shell
$ sort log.csv | uniq > clean.csv
```

```shell
$ grep -E 'Set Flat|Show Panorama' clean.csv > flatpano.csv
```

```shell
$ egrep -o '([TLF][0-9].*){1,3}' clean.csv
```
