# Star Wars: The Old Republic add-on

A Galleon Deck profile for SWTOR 7.x. It puts your quickbars under your thumbs, adds
targeting, interface and world keys, and brings seven themes drawn from the game's
factions. The deck switches to this profile while the game has focus and switches back
when you leave it.

Download `swtor-<version>.tar.gz` from the
[releases](https://github.com/NLMP-DDHS/galleon-deck-addons/releases). Then, in the
Galleon Deck app, open **Add-ons** and click **Install from file…**. Or run:

```sh
galleon-addon install ~/Downloads/swtor-1.0.0.tar.gz
```

## What you get

- **8 pages** (turn the right dial to change page, press it to go back to **bar 1**):
  bar 1 · bar 2 · bar 3 · companion · target · panels · world · look.
- **Auto-switch:** the profile holds its own rule for the game window. It matches the
  Steam build (`steam_app_1286830`) and a non-Steam one (`swtor.exe`). The launcher is
  left alone, so the deck only switches once you're in game.
- **Themes in the game's colours:** keys with cut corners and bright corner ticks, and
  one palette per faction:

  | Theme | Look |
  |---|---|
  | `swtor-holo` (default) | pale blue on black with the UI's gold accent |
  | `swtor-republic` | ochre gold on dark bronze, ivory highlights |
  | `swtor-empire` | cold crimson on black, steel-grey highlights |
  | `swtor-jedi` | a green blade on near-black |
  | `swtor-sith` | molten red on ember black, gold heat |
  | `swtor-mando` | brushed beskar on gunmetal, burnt orange trim |
  | `swtor-cantina` | Nar Shaddaa neon: magenta and signboard teal |

  Choose one on the **look** page, or in the Galleon Deck app. The palettes were picked
  by eye from the game's look. They are not official colours.

## About the binds

**SWTOR keeps your keybinds on its servers.** Nothing on this machine can read them —
your local `settings/Keybindings/` folder stays empty until you deliberately export a
preset. So unlike the Star Citizen add-on, this one can't sync to your binds: the keys
press the game's 7.x **defaults**, and if you've rebound something you change the key in
`~/.config/galleon-deck/profiles/swtor.toml` to match. Every default is listed below.
Upgrading the add-on backs that file up first, so your edits are never lost silently.

### Quickbars 2–6 are not bound out of the box

The game binds the **main** quickbar (`1`–`9`, `0`, `-`, `=`) and the **companion**
quickbar (the same keys with `Ctrl`). Quickbars 2 to 6 ship with *no keys at all* —
all 60 slots read "Not Bound" in Preferences.

So the **bar 2** and **bar 3** pages arrive dim, with the chords they expect already
written in. To light them up:

1. In game, press `Ctrl+P` → **Key Bindings** → **Quickbar**.
2. Bind Quickbar 2 slot *N* to `Alt`+*N*, and Quickbar 3 slot *N* to `Shift`+*N*
   (that's `Alt+1` … `Alt+0`, `Alt+-`, `Alt+=`, and the same with `Shift`). Neither
   chord is used by anything else at defaults.
3. Tell the deck:

   ```sh
   galleon-addon run swtor bars --bound 2,3      # --unbound 3 undoes it
   ```

Prefer different chords? Bind whatever you like in game and edit the `keys = …` values
on those pages to match.

> ⚠️ **Don't assume `Ctrl+1` is quickbar 3.** At defaults `Ctrl`+number is the
> **companion** bar, which is why this add-on gives it a page of its own. Guides that
> show `Ctrl` as quickbar 3 are describing their author's personal setup.

### It follows your interface layout

The half the game *does* keep on disk is your UI layout, and the deck follows it. On
install, and whenever you press **SYNC BARS** on the look page, the add-on reads the
GUI profile your character is using and dims every key whose quickbar is switched off
or whose slot is past the end of the bar:

```sh
galleon-addon run swtor bars                  # --dry-run to preview
```

It finds the game through your Steam libraries or a Wine prefix; pass `--settings-dir`
otherwise, and `--character NAME` to follow a character other than the one you played
last. It never writes to the game folder or the prefix.

A **dim** key still holds its bind — it's just a slot you can't see, or a bar you
haven't bound. The look page carries that mark as a legend.

## Naming your slots

Out of the box a quickbar key shows its slot number, because only you know what sits in
slot 7. To label one, edit the profile and give the key a `label`, an `icon`, or both:

```toml
{ label = "FORCE LEAP", icon = "\U000F046E", keys = "LEFTALT+3", swtor_bar = 2, swtor_slot = 3 },
```

Icons are Material Design Icons codepoints, the same set the rest of the deck uses; the
Galleon Deck app has a picker. Keep `swtor_bar` and `swtor_slot` on the key — that's
what **SYNC BARS** uses to find it. Your labels survive an upgrade.

## Key map (game defaults)

**bar 1** — the main quickbar, bound out of the box.

| Key | Bind | In game |
|---|---|---|
| 1 – 12 | `1` `2` `3` `4` `5` `6` `7` `8` `9` `0` `-` `=` | Main Quickbar Slot 1–12 |

**bar 2** and **bar 3** — quickbars 2 and 3. Unbound by the game; the pages ship dim
expecting `Alt`+slot and `Shift`+slot. Slots 11 and 12 are `-` and `=`.

**companion** — the companion quickbar, bound out of the box.

| Key | Bind | In game |
|---|---|---|
| 1 – 12 | `Ctrl+1` … `Ctrl+0`, `Ctrl+-`, `Ctrl+=` | Companion Quickbar Slot 1–12 |

**target**

| Key | Bind | In game |
|---|---|---|
| NEXT | `Tab` | Target Next Enemy |
| PREV | `Shift+Tab` | Target Previous Enemy |
| FRIEND | `Ctrl+Tab` | Target Next Friend |
| SELF | `F1` | Target Self |
| GROUP 1–4 | `F2` `F3` `F4` `F5` | Target Group Member 1–4 |
| COMPANION | `Shift+F1` | Target Companion |
| FOCUS | `Alt+F` | Set Focus Target |
| ASSIST | `Alt+T` | Acquire Target's Target |
| CENTRE | `Alt+C` | Target Center Screen Enemy |

**panels**

| Key | Bind | In game |
|---|---|---|
| CHARACTER | `C` | Character Sheet |
| INVENTORY | `I` | Inventory |
| ABILITIES | `P` | Abilities |
| MISSIONS | `L` | Mission Log |
| MAP | `M` | Area Map |
| GALAXY | `Shift+M` | Galaxy Map |
| STYLES | `K` | Combat Styles |
| GUILD | `G` | Guild Pane |
| SOCIAL | `O` | Friends Pane |
| LEGACY | `Y` | Legacy Pane |
| COLLECTION | `Ctrl+C` | Collections |
| ACTIVITIES | `Ctrl+G` | Activities / Group Finder |

**world**

| Key | Bind | In game |
|---|---|---|
| COVER | `F` | Take Cover |
| COVER HERE | `Shift+F` | Take Cover in Place |
| SHEATH | `Z` | Sheath / Unsheath Weapon |
| SIT | `X` | Sit |
| FLOURISH | `Ctrl+Z` | Mount Flourish |
| AUTORUN | `Num *` | Toggle Autorun |
| WALK | `Num /` | Toggle Run / Walk |
| HIDE UI | `Alt+Z` | Toggle User Interface |
| COMPANIONS | `N` | Companions & Contacts |
| STRONGHOLD | `U` | Strongholds Management |
| PREFS | `Ctrl+P` | Preferences |
| CHAT | `Enter` | Open Chat |

**look:** one key per theme, **SYNC BARS**, a screenshot key, the `= INACTIVE` legend
key, and back.

The generated **settings** page (brightness, profiles) comes last, as in every profile.

### Things the game doesn't bind at all

Mount, sprint, stealth, quick travel, fleet pass and the rest are **abilities**, not
keybinds: drag them from the Abilities window (`P`) onto a quickbar and the deck reaches
them through that bar's page. `/stuck`, ready checks and emotes are chat commands with
no default key.

## Notes for Proton

SWTOR is ProtonDB Platinum and takes the deck's keystrokes like any other keyboard.
Two things worth knowing:

- **Numpad keys.** `AUTORUN` and `WALK` are `Num *` and `Num /`. The deck turns NumLock
  on for its own virtual keyboard before sending those, so they arrive as numpad keys.
- **`-` and `=`.** Main-bar slots 11 and 12 are the plain, unshifted `-` and `=` of a US
  layout. On another keyboard layout, change those two keys in the profile.
- If a chord like `Ctrl+Tab` or `Alt+Z` never reaches the game, check your compositor
  isn't binding it first — those are the ones window managers tend to claim.

## Removing it

```sh
galleon-addon remove swtor
```

This removes the profile and themes, and any `config.toml` rule that points at them.
Before deleting the profile, it backs it up (with your labels and edits) to
`~/.local/state/galleon-deck/addons/backups/`.

Not affiliated with BioWare, Electronic Arts or Lucasfilm. STAR WARS: The Old Republic
is a trademark of Lucasfilm Entertainment Company Ltd.
