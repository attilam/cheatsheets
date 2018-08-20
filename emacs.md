---
title: Working With Emacs
kind: cheatsheet
keywords: [code, cheatsheet]
created_at: 2015-jun-03 20:01:00
---

## Basics

`C-x C-c` - Exit Emacs  
`Esc Esc Esc` - get out of a recursive editing level  

`C-h` - Help  
`C-h ?` - Show all help available  
`C-h c <command>` - display short help on a command  
`C-h k <command>` - display documentation for a command  
`C-h f <function>` - display help for a function  
`C-h a <something>` - display apropos for something  

## Moving around

`C-f` - Forward 1 character  
`C-b` - Backward 1 character  

`M-f` - Forward 1 word  
`M-b` - Backward 1 word  

`C-n` - Next line  
`C-p` - Previous line  

`C-a` - Beginning of line  
`C-e` - End of line  

`M-a` - Beginning of sentence  
`M-e` - End of sentence  

`C-v` - Move 1 page down  
`M-v` - Move 1 page up  

`M-<` - Move to beginning of document  
`M->` - Move to end of document  

`C-l` - Align cursor to top/mid/bottom of screen  

`C-/` or `C-_` - Undo  

`C-g` - stop/cancel a command  

`C-u <num> <command>` - Repeat `<command>` (can be text too!) `<num>` times  

## Buffers/Windows

`C-x 1` - 1 window mode (`C-x 2` for 2 window mode)  

`C-h k C-f` - open a new window to show help for the `C-f` command  

`C-x C-b` - List buffers  
`C-x b <buffername>` - jump to a buffer, or create new buffer if not exist  

`C-x o` - Move to the other window  
`C-M-v` - Scroll other window  

`C-x k` - Kill (close) a buffer  

## Clipboard, Killing (Cut), and Yanking (Paste)

"Killing" text is basically the cut function on a clipboard.  

`C-Space` - Start Selection  

`C-d` - like the `Del` key usually  

`M-Backspace` - kill 1 word before  
`M-d` - kill 1 word after  

`C-k` - kill to the end of line  
`M-k` - kill until end of sentence  

`C-w` - kill selection  

`C-y` - "Yank" text, i.e. Paste  
`M-y` - after `C-y` walk clipboard stack backwards  

## File Management

`C-x C-f <filename>` - Find (Open) file in a new buffer  
`C-x C-s` - Save file  
`C-x s` - Save some files with modifications  

## Search

`C-s` - Search forward  
`C-r` - Search backward  

These enter incremental search mode. Repeat the command to search for the next occurrence, press Backspace to "retreat" (prev.)

## Extended commands

`C-x <command>` - some quick command  
`M-x <command>` - execute named command  

Named commands can be space/tab completed.  

`M-x repl s<Return>changed<Return>altered` - replaces all occurrences of "changed" with "altered"  
`M-x recover-file` - recover auto save file  
`M-x text-mode` - switch to plain text editing mode
