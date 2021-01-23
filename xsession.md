# Trying to understand Display managers in modern desktops
Seems to work fine in Ubuntu 16.04, 18.04 and 20.04 (GDM3)

## Login process

display manager (GDM, KDM, LightDM,...):

    - launches X server
    - manages a graphical login screen

session manager:

    - manages session for the logged-in user
    - launches the clients required by the user
    - manages crashes and stops, and generally user session state.

### Graphic login
```
init or systemd -> display manager (GDM, KDM, LightDM...) which invokes the X server -> X session manager (gnome-session) -> X client(s) (Notion, Sawfish, Xeyes, Gedit, Xscreensaver, Xterm...)
```

### Display manager but no session manager:
```
init -> display manager (which invokes the X server) -> X client(s)
```

### Plain login (no display nor session manager)

The good old way

```
init -> getty/login (=display manager) -> shell -> startx/xinit -> X clients
```

## Display manager configuration
### GDM
GDM looks for sessions in `/usr/share/xsessions`. Those are `.desktop` files.
A session file can either launch a good old X session or a real session manager like gnome-session

#### launch a good old X session with GDM
Add a `good_old_xinit.desktop` file in `/usr/share/xsessions`:

```
[Desktop Entry]
Name=Good old X session
Comment=This session runs ~/.xsession or ~/.Xclients if available
Exec=/usr/libexec/xinit-compat # Or whatever other script you want
Icon=
Type=XSession
```

`xinit-compat` script:
```
#!/bin/sh
for session in ~/.xsession ~/.Xclients /etc/X11/xinit/Xclients ;
do
if [ -f ${session} ] ; then
  exec ${session} 2>&1 >~/.xsession_errors.log
fi
done
```

The `Good old X session` should now be available in GDM login screen.

### XDM
XDM sources `~/.xsession`. So populate whatever clients you want in `~/.xsession` or `~/.Xclients`
