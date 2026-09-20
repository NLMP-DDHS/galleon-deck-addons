# galleon-deck-addons

Add-ons for [galleon-deck](https://github.com/NLMP-DDHS/galleon-deck), the Linux
Stream Deck driver for the Corsair Galleon 100 SD. Each add-on is a ready-made profile,
often with its own themes, auto-switch rule and tools. You can add or remove one with
a single command.

| Add-on | What it is |
|---|---|
| [`star-citizen`](star-citizen/) | 8 pages of flight, combat, power, ops, comms, on-foot and emote keys for Star Citizen 4.x. It includes 7 themes styled on the game's UI, switches to itself while the game has focus, and syncs to your in-game binds. |
| [`swtor`](swtor/) | 8 pages for Star Wars: The Old Republic 7.x: the main, 2nd, 3rd and companion quickbars, plus targeting, interface panels and world keys. It includes 7 themes drawn from the game's factions, switches to itself while the game has focus, and follows the quickbars your interface actually shows. |

## Use

Each add-on is a **separate download**. Take the ones you want and ignore the rest.
They need galleon-deck 1.1.0 or newer, which includes the add-on manager.

1. Download the add-on's `.tar.gz` from the [Releases](https://github.com/NLMP-DDHS/galleon-deck-addons/releases)
   page, e.g. `star-citizen-1.0.0.tar.gz`.
2. In the Galleon Deck app, open the **Add-ons** tab and click **Install from file…**.
   Or from a terminal:

   ```sh
   galleon-addon install ~/Downloads/star-citizen-1.0.0.tar.gz
   ```

The running deck picks up the new profile within a second, with no restart. The
**Add-ons** tab, or `galleon-addon list`, shows what's installed.

- **Upgrading:** install the newer package the same way. It replaces the add-on's
  files and keeps the theme you chose for its profile. The old profile is backed up
  first.
- **Removing:** click **Remove** on the Add-ons tab, or run `galleon-addon remove star-citizen`.
  It deletes the add-on's files. It also repoints anything that referred to them (your
  start profile, auto-switch rules, other profiles using its themes), so the deck never
  shows a config error. The profile is backed up to
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

While working on an add-on, install it straight from its folder with
`galleon-addon install ./my-game`. Or add this repository's folder under the Add-ons
tab's folder button, so everything in it is listed. `galleon-addon pack ./my-game`
builds the package.

### Releasing

Each add-on is released on its own. Bump `version` in its `addon.toml`, then push a tag
named after the add-on and version:

```sh
git tag star-citizen-v1.0.0 && git push origin star-citizen-v1.0.0
```

The [release workflow](.github/workflows/release.yml) packs `star-citizen-1.0.0.tar.gz`
and publishes it as a GitHub release with install instructions.

## License

MIT, see [LICENSE](LICENSE). Game names are trademarks of their owners; these add-ons
are not affiliated with them.
