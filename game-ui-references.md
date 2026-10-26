# Game UI References & Assets

Check this list before starting any game UI design task.
**Rule:** only assets marked ✅ may be copied into this repo. Everything else is reference-only — link to it, never re-upload it.

| Site | Use it for | Can it live in this repo? |
|---|---|---|
| [Kenney](https://kenney.nl/assets) | Free UI packs, icons, buttons, pixel and 3D assets for prototypes | ✅ Yes — CC0 (no attribution required, commercial OK) |
| [Game UI Kits (enotsixlm)](https://enotsixlm.github.io/game-ui-kits/) | Coded component kits in 7 styles (gothic, cyberpunk, Mario, iOS casual, 8-bit pixel…) — copy CSS patterns and tokens | ⚠️ Check the repo's LICENSE file first. If none, link and learn only |
| [Pixlab24](https://pixlab24.com/) | Pixel-art icons, buttons, panels, tilesets | ⚠️ Per-pack licence — check each download page; keep a note of source + licence next to anything added |
| [Interface In Game](https://interfaceingame.com/) | Screenshot library of real game UI, tagged by genre and component (menus, inventory, HUD, popups) | ❌ Reference only — copyrighted game screenshots |
| [GameUI.net](https://www.gameui.net/) | Chinese community: original UI practice works, guofeng / anime / sci-fi styles, tutorials, jobs | ❌ Reference only — designers' own work |
| [Lemoo UI](https://www.lemooui.com/) | Game UI motion: gacha pulls, popups, reward animations, UE/Unity plugin resources | ❌ Reference only — designers' own work |

## How to use with an AI agent
- **Layout / UX patterns:** browse Interface In Game by component first.
- **Visual style direction:** GameUI.net (Asian-market styles) and Game UI Kits (coded styles).
- **Motion:** Lemoo UI.
- **Actual assets for a build:** Kenney first, Pixlab24 second, always recording the licence.

## Folder convention for downloaded assets
```
game-assets/
  kenney/<pack-name>/        # include the pack's License.txt
  pixlab24/<pack-name>/      # include SOURCE.md with URL + licence text
```
