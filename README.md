# GameTimeJSON

Static JSON data files for GameTime. There is no code in this repo, only data that apps can fetch or import.

## Files

### `games.json`

A list of popular multiplayer games.

```json
{
  "version": 2,
  "games": ["Apex Legends", "Fortnite", "Minecraft"]
}
```

- `version`: bumped whenever the data changes.
- `games`: game titles, sorted alphabetically (case-insensitive), no duplicates.

### `username.json`

Safe, friendly word lists that users can combine into a username, such as `Brave` + `Panda` = `BravePanda`.

```json
{
  "version": 1,
  "prefixes": ["Brave", "Cosmic"],
  "suffixes": ["Panda", "Wizard"]
}
```

- `prefixes` and `suffixes`: 20 words each, sorted alphabetically.

## Usage

Fetch the raw file from GitHub:

```
https://raw.githubusercontent.com/founding5067/GameTimeJSON/main/games.json
https://raw.githubusercontent.com/founding5067/GameTimeJSON/main/username.json
```

## Disclaimer

The game titles in `games.json` are just a plain list of names. I don't own, make, or claim any of these games, and this project isn't affiliated with, endorsed by, or sponsored by any of their developers or publishers. All game names and trademarks belong to their respective owners.

## Contributing

`.github/CODEOWNERS` makes @founding5067 the owner of every file, so changes need their review.

When editing a list:
- Keep it sorted and free of duplicates.
- Keep entries family-friendly, since users see them.
- Bump `version` in the file you changed.
- Check the file still parses: `python3 -m json.tool games.json`
