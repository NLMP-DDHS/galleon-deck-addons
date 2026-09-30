# Helldivers 2 add-on

A Galleon Deck profile for Helldivers 2: every stratagem on its own key. A key holds
the stratagem menu and taps the code for you, so calling in a 500kg is one press. The
deck switches to this profile while the game has focus and switches back when you
leave it.

Download `helldivers-2-<version>.tar.gz` from the
[releases](https://github.com/NLMP-DDHS/galleon-deck-addons/releases). Then, in the
Galleon Deck app, open **Add-ons** and click **Install from file…**. Or run:

```sh
galleon-addon install ~/Downloads/helldivers-2-1.0.0.tar.gz
```

It needs galleon-deck **1.2.0** or later, the release that added the `sequence` action.

## What you get

- **6 pages** (turn the right dial to change page, press it to go back to **mission**):

  | Page | Keys |
  |---|---|
  | mission | Reinforce, Resupply, SOS Beacon, Hellbomb, Eagle Rearm, SEAF Artillery, Super Earth Flag, Illumination Flare, Upload Data, Seismic Probe, SSSD Delivery, Prospecting Drill |
  | orbital | Precision, Gatling, Airburst, 120mm, 380mm, Walking Barrage, Laser, Railcannon, Napalm Barrage, EMS, Gas, Smoke |
  | eagle | Strafing Run, Airstrike, Cluster Bomb, Napalm, Smoke, 110mm Rocket Pods, 500kg, Rearm, Patriot and Emancipator exosuits |
  | weapons | MG, AMR, Stalwart, EAT, Recoilless, Flamethrower, Autocannon, HMG, Railgun, Spear, Grenade Launcher, Laser Cannon |
  | support | Arc Thrower, Quasar, Commando, Airburst Rocket Launcher, Jump Pack, Supply Pack, Guard Dog, Rover, Ballistic Shield, Shield Generator Pack |
  | defense | MG, Gatling, Autocannon, Rocket, Mortar and EMS Mortar sentries, HMG Emplacement, Tesla Tower, Shield Relay, AP, Incendiary and AT mines |

- **Colours from the game:** red for offensive, blue for supply, green for defensive,
  yellow for mission. The theme, `hd-super-earth`, is hazard yellow on black.
- **Auto-switch:** the profile holds its own rule for the game window, matching the
  Steam build under Proton (`steam_app_553850`) and `helldivers2.exe`.

## Binds

Keys press the game's defaults: hold **Left Ctrl** for the stratagem menu, then
**W A S D** for up, left, down, right. If you've rebound either in game, edit
`~/.config/galleon-deck/profiles/helldivers-2.toml`: change `hold`, or the letters in
each `sequence`.

If the game drops inputs (a code fails only sometimes), raise `step_ms` on the key:
the gap between taps in milliseconds, default 40.

Arrowhead changes a code now and then in a patch. If one stratagem stops working,
check its code in game and fix that key's `sequence`.

## Removing

Click **Remove** on the Add-ons tab, or run `galleon-addon remove helldivers-2`.

This add-on is a fan project, not affiliated with Arrowhead Game Studios or Sony
Interactive Entertainment, and ships no game artwork.
