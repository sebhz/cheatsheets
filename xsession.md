# Trying to understand Display managers in modern desktops
Seems to work fine in Ubuntu 16.04, 18.04 and 20.04 (GDM3)

## Login process

[Display manager](https://en.wikipedia.org/wiki/X_display_manager) (GDM, KDM, LightDM, XDM...):

    - launches X server,
    - manages a graphical login screen,
    - upon login, launches X clients (including possibly session manager),

[Session manager](https://en.wikipedia.org/wiki/X_session_manager) (gnome-session, xfce4-session, XSM...):

    - manages session for the logged-in user,
    - launches the clients required by the user,
    - manages crashes and stops, and generally user session state.

### Graphical login
```
init or systemd -> display manager (GDM, KDM, LightDM...) which invokes the X server -> X session manager (gnome-session) -> X clients (Notion, Sawfish, Xeyes, Gedit, Xscreensaver, Xterm...)
```

### Display manager but no session manager:
```
init -> display manager (which invokes the X server) -> X clients
```

### Plain login (no display nor session manager)

The good old way

```
init -> getty/login (=display manager) -> shell -> startx/xinit -> X clients
```

## Display manager configuration

### GDM3 (default for Ubuntu)
GDM3 looks for sessions in `/usr/share/xsessions`. Those are Freedesktop (a.k.a X dev group, or xdg) `.desktop` files.

GDM3 will present the user with a list of sessions, each one corresponding to an entry in `/usr/share/xsessions`. When the user logs in, the `gdm-x-session` script will source the `/etc/gdm3/Xsession` script, passing it the `Exec` entry in the session `.desktop` file.

`/etc/gdm3/Xsession` script will perform some inits, source the `/etc/X11/xinit/xinitrc.d/*` scripts, then source all scripts in `/etc/X11/Xsession.d`. It will then do some more actions if its argument is `default` - which is weird, since we should never return from the last `Xsession.d` script.

If the argument to `/etc/gdm3/Xsession` is `default` or is not an executable on the user path, some script in `/etc/X11/Xsession.d` will source the user `.xsession` file. If it is an executable on the path, it will be executed.

#### Launch a good old X session with GDM
There are two ways:

##### Using default session (launch ~/.xession)
Add a `xinit.desktop` file in `/usr/share/xsessions`:
```
[Desktop Entry]
Name=Good old X session
Comment=This session runs ~/.xsession if available
Exec=default
Icon=
Type=Application
```

The `Good old X session` should now be available in GDM login screen. Populate the clients in `~/.xsession` ending with the window manager.

##### Using a window manager or session manager
This is the way the package managers of most distro do it. For example using `dwm` window manager.

Add a `dwm.desktop` file in `/usr/share/xsessions`:
```
[Desktop Entry]
Name=dwm session
Comment=Runs dwm as session manager
Exec=dwm
Icon=
Type=Application
```

Then add as many entries as needed in `/etc/X11/Xsession.d` for clients to source by default. `dwm` will be run last (window manager).

## Starting session manager default clients

Modern session managers (at least gnome-session), will parse the `.desktop` files, in the `/etc/xdg/autostart` directory to launch default clients. Some distro packages add their `.desktop` files there.

One can use an external program like `dex` to parse those files by adding the following command in the `.xsession` file, if this is the approach used:

`dex --autostart --environment <my_wm_name>`

This will parse and execute the autostart files applying to your wm (e.g. probably anything that does not require Gnome or KDE).

The command above will also parse `.desktop` files in `~/.config/xdg/autostart`. This can be used to leave only the `dex` invocation to the `.xession` file. Or even to get completely rid of the `.xsession` file if the WM can exec external commands at startup - like `i3` for example.

Adding the `dex` command in a script in `/etc/X11/Xsession.d` will make the autostart files be executed twice in case a real session manager is used. Need to guard against this by checking the scripts argument.

