Ctrl b = `C-b`

Split into left and right pane: `C-b %`

Split into top and bottom pane: `C-b "`

Switch between panes: `C-b` and arrow keys


Create a new window: `C-b c`

Move to previous and next window: `C-b p` and `C-b n`. Alternatively `C-b #` where # is the window number works.

Use `C-b ,` to rename current window

To enter scroll mode: `C-b [`


## Combining and splitting windows into panes
Say you have the following windows

`[1] 0:file.c  1:gdb- 2:vim  3:bash* `

To combine window 1 into 2 with a vertical setting, do `C-b :` to enter command mode and run

```tmux
join-pane -s 2 -t 1
```

To separate these panes into windows do

```tmux
break-pane
```

To switch between horizontal/vertical layouts with

```tmux
next-layout
```

