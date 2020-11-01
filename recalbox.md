# Recalbox general
Valid for Recalbox 7.0.x

## Standard buttons layout
```
                X
Select Start  Y   A
                B 
```
## Shortcuts
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
| Add a credit (Arcade)        | Select         |

## Invoking a virtual keyboard in emulator (retroarch-based)
`Start+Y`, then press `Select` to switch to "Mouse mode"

Move with the arrows, type with `B`.

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

## Amstrad CPC

### Changing disks / cassette side

### Specific games

#### Barbarian
Press `Enter` until MODE1 (1P joystick) or MODE2 (1P keyboard) or MODE3 (2P) appears, then `Space` to launch game.

#### Prince of Persia
To jump, use high diagonal.
