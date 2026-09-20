### What's new

Switching to this profile now plays a glitch on the deck: the profile's logo tears
into view while its keys resolve out of the interference, the logo holds for a beat,
and the normal screen returns. That's galleon-deck 1.1.0's profile-switch animation,
so it applies to every profile — this release documents how to use it here.

- **Use the RSI logo.** The package ships no Star Citizen artwork: the logos are
  Cloud Imperium's trademarks. Take `RSI_WHITE.png` (or `STARCITIZEN_WHITE.png`) from
  CIG's Fan Kit, put it in `~/.config/galleon-deck/logos/`, and pick it under
  **Look → Profile logo** in the Galleon Deck app, or set `logo = "logos/rsi-white.png"`
  in the profile. The README walks through it. Without a logo, the profile's name is
  used instead, and nothing else changes.
- Your logo and theme now survive upgrading the add-on.
- The animation is tunable in the app's Settings (speed, how long the logo holds) and
  can be switched off; any key or dial cuts it short.

The keys, themes and bind sync are unchanged from 1.0.1.
