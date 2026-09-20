### What's in it

The first release of the SWTOR add-on: eight pages built around the quickbars, plus
targeting, interface and world keys, and seven themes drawn from the game's factions.

- **Quickbars under your thumbs.** A page each for the main bar, quickbars 2 and 3, and
  the **companion** bar — one key per slot, twelve to a page.
- **It knows what the game actually binds.** SWTOR binds the main bar (`1`–`=`) and the
  companion bar (`Ctrl+1`–`Ctrl+=`) and leaves quickbars 2–6 with no keys at all, so
  those two pages arrive dim with the chords they expect written in. Bind them in
  Preferences → Key Bindings → Quickbar, then `galleon-addon run swtor bars --bound 2,3`.
- **It follows your interface.** SWTOR keeps keybinds on its servers, so no add-on can
  read them — but it keeps your *interface layout* on disk. `swtor-bars` reads the GUI
  profile your character is using and dims every key whose quickbar is switched off or
  whose slot is past the end of the bar. It runs on install and on **SYNC BARS**.
- **Seven themes:** `swtor-holo` (the default), `swtor-republic`, `swtor-empire`,
  `swtor-jedi`, `swtor-sith`, `swtor-mando` and `swtor-cantina`.
- **Auto-switch:** the profile carries its own rule, matching both the Steam build and
  a non-Steam install. The launcher is left alone.
