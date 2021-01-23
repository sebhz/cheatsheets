# GNU Screen cheat sheet

| Invoking screen ||
| --- | --- |
| Start session | screen -S <_name_> |
| List running sessions | screen -ls |
| Attach to a running session | screen -x |
| Attach to session _name_ | screen -r <_name_> |
| Launch screen in detached mode | screen -d -m |
| Detach a running session | screen -d <_name_> |
| Send command to session | screen -S <_name_> -X <_command_> |
| Rename existing session | screen -S <_name_> -X sessionname <_new\_name_> |


| Leaving screen |||
| --- | --- | --- |
| Detach screen from this terminal. | C-a d, C-a C-d | (detach) |
| Detach and logout. | C-a D D | (pow\_detach) |
| Kill all windows, terminate screen. | C-a \ | (quit) |
| Suspend screen | C-a z, C-a C-z | (suspend) |

| Information / command |||
| --- | --- | --- |
| Show key bindings. | C-a ? | (help) |
| Shows screen license. | C-a , | (license) |
| Display the version and compilation date. | C-a v | (version) |
| Show system information. | C-a t, C-a C-t | (time) |
| Show info about this window. | C-a i, C-a C-i | (info) |
| Enter command line mode. | C-a : | (colon) |

| Clipboard, scrolling, selection |||
| --- | --- | --- |
| Enter copy/scrollback mode. | C-a [, C-a C-[, C-a esc | (copy) |
| Write the contents of the paste buffer | C-a ], C-a C-] | (paste .) |
| Write paste buffer to a file. | C-a > | (writebuf) |
| Reads the screen-exchange file into paste buffer. | C-a < | (readbuf) |
| Removes the file used by C-a < and C-a >. | C-a = | (removebuf) |
| Copy and paste a previous (command) line. | C-a {, C-a } | (history) |

| Terminal |||
| --- | --- | --- |
| Clear the screen. | C-a C | (clear) |
| Toggle flow on, off or auto. | C-a f, C-a C-f | (flow) |
| Toggle current window line-wrap setting | C-a r, C-a C-r | (wrap) |
| Toggles screen visual bell mode. | C-a C-g | (vbell) |
| Toggle 80/132 columns. | C-a W | (width) |
| Reset the virtual terminal | C-a Z | (reset) |
| Write out a `.termcap` file. | C-a . | (dumptermcap) |
| Lock this terminal. | C-a x, C-a C-x | (lockscreen) |

| Window management |||
| --- | --- | --- |
| Create a new window. | C-a c, C-a C-c | (screen) |
| Toggle to the window displayed previously. | C-a C-a | (other) |
| Switch to window number 0 - 9 | C-a _digit_ | (select 0-9) |
| Switch to window number 0 - 9, or the blank window. | C-a - | (select -) |
| Switch to the next window. | C-a n, C-a C-n, C-a Space | (next) |
| Switch to the previous window | C-a p, C-a C-p, C-a Backspace | (prev) |
| Present a selectable list of all windows | C-a ' | (windowlist -b) |
| Show a list of all windows. | C-a w, C-a C-w | (windows) |
| Destroy current window. | C-a k, C-a C-k | (kill) |
| Prompt for a window name or number to switch to. | C-a " | (select) |
| Show the number and title of the current window. | C-a N | (number) |
| Prompt current window name. | C-a A | (title) |
| Resize the window to the current region size. | C-a F | (fit) |

| Split screen |||
| --- | --- | --- |
| Split the current region horizontally | C-a S | (split) |
| Split the current region vertically | C-a | | (split -v) |
| Switch the input focus to the next region. | C-a tab | (focus) |
| Kill the current region. | C-a X | (remove) |
| Delete all regions but the current one. | C-a Q | (only) |

| Special characters |||
| --- | --- | --- |
| Send the command character (C-a) to client | C-a a | (meta) |
| Send a break to window. | C-a b, C-a C-b | (break) |
| Reopen the terminal line and send a break. | C-a B | (pow_break) |
| Send a control-q to the current window. | C-a q, C-a C-q | (xon) |
| Send a control-s to the current window. | C-a s, C-a C-s | (xoff) |
| Enter digraph. | C-a C-v | (digraph) |

| Logging, dumping and monitoring |||
| --- | --- | --- |
| Hardcopy of the current window to the file `hardcopy.n`. | C-a h | (hardcopy) |
| Toggle logging of the current window to `screenlog.n`. | C-a H | (log) |
| Start/stop monitoring the current window for inactivity. | C-a _ | (silence) |
| Toggles monitoring of the current window. | C-a m, C-a C-m, C-a M | (monitor) |

_Version 1.5 – 2018/10/26_
