# Recalbox general
Valid for Recalbox 7.0.x

## Standard buttons layout
```
                X
Select Start  Y   A
                B 
```
## Shortcuts for retroarch-based emulators
See https://recalbox.gitbook.io/documentation/basic-manual/getting-started/during-the-game.

Specific shortcuts

| Function                     | Shortcut       |
| ---                          | ---            |
| Screenshot                   | Hotkey + L1    |
| Save state to current slot   | Hotkey + Y     |
| Load state from current slot | Hotkey + X     |
| Select previous slot         | Hotkey + Up    |
| Select next slot             | Hotkey + Down  |
| Exit an emulator             | Hotkey + Start |
| Reset emulator               | Hotkey + A     |
| Get retroarch menu           | Hotkey + B     |
| Speed up an emulator         | Hotkey + Right |
| Rewind                       | Hotkey + Left  |

### Invoking a virtual keyboard in emulator (retroarch-based)
`Start + Y`, then press `Select` to switch to "Mouse mode"

Move with the arrows, type with `A`.

### Changing disks / cassette side
Use retroarch menu (Hotkey + B) "disk control" menu.

## Pad-to-key
See https://recalbox.gitbook.io/documentation/v/francais/utilisateur-avance/configurations/pad-to-keyboard.

Place a `.p2k.cfg` file in your rom dir (for global map).

Can be overridden by `<rom_name>.p2k.cfg`

Basic example (works great with Amstrad CPC for a majority of games):

```
# dpad to arrow keys
0:up = up
0:down = down
0:right = right
0:left = left

# Retroarch CPC core uses A and B for joystick buttons. Leave them alone.
# button X to SPACE
0:x = space
# button Y to Y key (for Y/N prompts)
0:y = y
# And finally, map START button to ENTER 
0:start = enter
```

# Systems

## Arcade
| Function                     | Shortcut       |
| ---                          | ---            |
| Add a credit (Arcade)        | Select         |

## Amstrad CPC

### Specific games

#### Barbarian
Press `Enter` until MODE1 (1P joystick) or MODE2 (1P keyboard) or MODE3 (2P) appears, then `Space` to launch game.

#### Prince of Persia
To jump, use high diagonal.

## Atari ST
The default emulator is not retroarch, so has different bindings.
See https://recalbox.gitbook.io/documentation/v/francais/emulateurs/ordinosaures/atari-st/libretro-hatari

| Button | Action                                                  |
| ---    | ---                                                     |
| A      | Left click                                              |
| B      | Right click                                             |
| X      | Open emulator interface (useful to change floppy, etc.) |
| Y      | Shift                                                   |
| Select | Toggle between mouse and joystick mode                  |
| R1     | Change mouse sensitivity                                |
| L1     | Virtual keyboard                                        |
| L2     | Status display                                          |

## Amiga

### Specific games

#### Another world
The original game was protected by a codewheel. An online version exists at https://oldgames.sk/codewheel.

## Thomson
Official docs (https://recalbox.gitbook.io/documentation/v/francais/emulateurs/ordinosaures/thomson-t08/theodore) seems outdated.

This is a libretro core, so Hotkey shortcuts will work, but it has specific bindings for virtual keyboard.

| Button | Action                                                           |
| ---    | ---                                                              |
| A      | Joystick button                                                  |
| Select | Open virtual keyboard                                            |
| Y      | Change position of virtual keyboard                              |
| B      | Press key in virtual keyboard (long press leave the key pressed) |
| Start  | Tries and do the right thing to start game                       |


