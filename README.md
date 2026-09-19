# galleon-deck-addons

Add-ons for [galleon-deck](https://github.com/NLMP-DDHS/galleon-deck), the Linux
Stream Deck driver for the Corsair Galleon 100 SD. Each add-on is a ready-made profile,
often with its own themes, auto-switch rule and tools. You can add or remove one with
a single command.

| Add-on | What it is |
|---|---|
| [`star-citizen`](star-citizen/) | 8 pages of flight, combat, power, ops, comms, on-foot and emote keys for Star Citizen 4.x. It includes 7 themes styled on the game's UI, switches to itself while the game has focus, and syncs to your in-game binds. |

## Use

Needs galleon-deck 1.1.0 or newer.

```sh
git clone https://github.com/NLMP-DDHS/galleon-deck-addons
cd galleon-deck-addons
./galleon-addon list                      # what's here and what's installed
./galleon-addon install star-citizen      # install, or upgrade to the version here
./galleon-addon remove star-citizen       # remove again
./galleon-addon run star-citizen sync-binds
```

The first install also links `galleon-addon` into `~/.local/bin`. The running deck
picks up the new profile within a second, with no restart.

- **Upgrading** (`install` again after a `git pull`): replaces the add-on's files and
  keeps the theme you chose for its profile. The old profile is backed up first.
- **Removing:** deletes the add-on's files. It also repoints anything that referred to
  them (your start profile, auto-switch rules, other profiles using its themes), so the
  deck never shows a config error. The profile is backed up to
  `~/.local/state/galleon-deck/addons/backups/`.
- **Clashes:** an install won't overwrite a file that another add-on or you created
  unless you pass `--force`. Even then, it backs the file up first.

## Making an add-on

An add-on is a folder with an `addon.toml`:

```toml
title = "My Game"
version = "1.0.0"
description = "One line for `galleon-addon list`."
requires = "1.1.0"                 # minimum galleon-deck version

[commands]                         # optional: galleon-addon run <addon> <name>
tidy = "tools/tidy"                # a path inside the add-on folder

[hooks]
post_install = ["tidy --quiet"]    # optional: commands run after install/upgrade
```

and any of:

```
profiles/*.toml   → ~/.config/galleon-deck/profiles/
themes/*.toml     → ~/.config/galleon-deck/themes/
images/...        → ~/.config/galleon-deck/addons/<addon>/images/
                    (use them in keys as image = "addons/<addon>/images/x.png")
```

To make the deck switch to your profile when the game has focus, put a rule in the
profile file itself, not in `config.toml`. The rule is then added and removed along
with the add-on:

```toml
auto_switch = [{ class = "^mygame\\.exe$" }]
```

Commands get `GALLEON_DECK_CONFIG` (the config folder) and `GALLEON_ADDON_DIR` in their
environment.

## License

MIT, see [LICENSE](LICENSE). Game names are trademarks of their owners; these add-ons
are not affiliated with them.
