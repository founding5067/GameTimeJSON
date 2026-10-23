# GameTimeJSON

A static JSON data file for GameTime. There is no code in this repo, only data that apps can fetch or import.

## Files

### `gametime.json`

```json
{
  "version": 1,
  "games": ["Apex Legends", "Fortnite", "Minecraft"],
  "username": {
    "prefixes": ["Brave", "Cosmic"],
    "suffixes": ["Panda", "Wizard"]
  }
}
```

- `version`: bumped whenever the data changes.
- `games`: popular multiplayer game titles, sorted alphabetically (case-insensitive), no duplicates.
- `username.prefixes` and `username.suffixes`: safe, friendly words (20 each, sorted) that users can combine into a username, such as `Brave` + `Panda` = `BravePanda`.

## Usage

Fetch the raw file from GitHub:

```
https://raw.githubusercontent.com/founding5067/GameTimeJSON/main/gametime.json
```

## Disclaimer

The game titles in `gametime.json` are just a plain list of names. I don't own, make, or claim any of these games, and this project isn't affiliated with, endorsed by, or sponsored by any of their developers or publishers. All game names and trademarks belong to their respective owners.

## Contributing

`.github/CODEOWNERS` makes @founding5067 the owner of every file, so changes need their review.

When editing a list:
- Keep it sorted and free of duplicates.
- Keep entries family-friendly, since users see them.
- Bump `version` when the data changes.
- Check the file still parses: `python3 -m json.tool gametime.json`
