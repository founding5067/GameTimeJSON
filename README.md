# GameTimeJSON

The data file the GameTime app fetches for its game list, username words and avatar emoji. There is no code in this repo, only `gametime.json`.

Raw file:

```
https://raw.githubusercontent.com/founding5067/GameTimeJSON/main/gametime.json
```

## At a glance

| Key | What it holds | Entries |
| --- | --- | --- |
| `version` | Data version number | n/a |
| `games` | Games people can pick from | 103 |
| `username.prefixes` | First word of a display name | 20 |
| `username.suffixes` | Second word of a display name | 22 |
| `username.blockedNumbers` | Digit strings banned from names | 7 |
| `username.suffixEmoji` | Suffix to emoji for the Shuffle button | 22 |
| `avatar.emoji` | Profile picture options | 72 |

## Field reference

### `version`

A number, bumped whenever the data changes.

### `games`

The list people pick from when creating a session and when adding to My Games. The search box filters it as they type.

The app cleans, dedupes and sorts the names alphabetically, so the order in the file doesn't affect what users see.

### `username.prefixes` and `username.suffixes`

The two words of a display name, such as `Brave` and `Fox`. A name is prefix + suffix + an optional number of up to 3 digits, like `BraveFox42`.

Each entry must be letters only (no spaces, digits or symbols) and at most 13 characters. Entries that fail are dropped silently.

### `username.blockedNumbers`

Digit strings that can't appear in a name's number. Any number that contains one is blocked, so `69` also blocks 169 and 690.

If the file leaves this key out, the app uses its own built-in list. If the key is present, your list replaces the built-in one entirely, so include every number you want blocked.

### `username.suffixEmoji`

Maps a suffix to an emoji for the Shuffle button, e.g. `"Fox": "🦊"`.

An entry only counts if that emoji is also in `avatar.emoji`. A suffix with no entry, or with an emoji the picker doesn't offer, gets a random emoji from the list.

### `avatar.emoji`

The profile picture options. The order in the file is the order in the grid.

Each entry must be exactly one emoji. Letters, digits and two emoji in one entry are dropped.

## Editing the data

- Keep `games`, `prefixes` and `suffixes` alphabetical with no duplicates.
- Leave `avatar.emoji` in display order. Don't sort it.
- When you add a suffix, add its `suffixEmoji` entry, and make sure that emoji is in `avatar.emoji`.
- Keep entries family-friendly, since users see them.
- Bump `version`.
- Check the file still parses: `python3 -m json.tool gametime.json > /dev/null`

`.github/CODEOWNERS` makes @founding5067 the owner of every file, so changes need their review.

## Disclaimer

The game titles in `gametime.json` are a plain list of names. I don't own, make or claim any of these games, and this project isn't affiliated with, endorsed by or sponsored by any of their developers or publishers. All game names and trademarks belong to their respective owners.
