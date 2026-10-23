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
    "suffixes": ["Fox", "Wizard"],
    "blockedNumbers": ["69", "88", "420", "666", "14", "187"],
    "suffixEmoji": { "Fox": "🦊" }
  },
  "avatar": {
    "emoji": ["🦊", "🐼", "🧙"]
  }
}
```

### Fields

- `version`: bumped whenever the data changes.

**`games`**
- The list people pick from when creating a session and when adding to My Games. The search box filters it as they type.
- Names are cleaned, deduplicated and sorted alphabetically, so the order you write them in doesn't matter.

**`username.prefixes`**
- The first word of a display name, such as `Brave`.
- Each must be letters only (no spaces, digits or symbols) and at most 13 characters. Entries that fail are dropped silently.

**`username.suffixes`**
- The second word, such as `Fox`. Same rules as prefixes.
- A name is prefix + suffix + an optional number of up to 3 digits, like `BraveFox42`.

**`username.blockedNumbers`**
- Digit strings that can't appear in a name's number. It blocks any number that contains one, so `69` also blocks 169 and 690.
- If your hosted file leaves this key out, the app uses its built-in list (69, 88, 420, 666, 14, 187). If you include it, your list replaces the built-in one entirely, so include every number you want blocked.

**`username.suffixEmoji`**
- Maps a suffix to a picture for the Shuffle button, e.g. `"Fox": "🦊"`.
- An entry only counts if that emoji is also in `avatar.emoji`. A suffix with no entry, or with an emoji the picker doesn't offer, gets a random emoji from the list.

**`avatar.emoji`**
- The profile picture options. The order in the file is the order in the grid, so it isn't sorted.
- Each entry must be exactly one emoji. Letters, digits and two emoji in one entry are dropped.

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
