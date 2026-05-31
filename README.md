# ringi

**ringi** is a utility for injecting files back into a source file or archive image.

The injection offset is determined from the filename of the file being injected. This makes it possible to restore modified assets into their original locations after extraction and editing.

## Usage

```text
ringi.exe <options>
```

## Options

| Option                       | Description                                          |
| ---------------------------- | ---------------------------------------------------- |
| `-s <file>`                  | Source file to modify                                |
| `-i <file>`                  | File or file mask to inject (wildcards supported)    |
| `-log <file>`                | Write logs to the specified file                     |
| `-rf`, `--remove-files`      | Remove injected files after successful injection     |
| `--format <format>`          | Filename format: `hex` or `decimal` (default: `hex`) |
| `--override-offset <offset>` | Override the injection offset for a single file      |
| `--override-size <size>`     | Override the injection size for a single file        |
| `-h`, `--help`               | Display help information                             |

## Filename Format

By default, the injection offset is read from the filename.

Examples:

| Filename       | Offset     |
| -------------- | ---------- |
| `0000007F.bik` | `0x7F`     |
| `00010000.png` | `0x10000`  |
| `001A2B3C.wav` | `0x1A2B3C` |

Use `--format decimal` if offsets are stored as decimal values instead of hexadecimal.

The offset can also be overridden manually using the `--override-offset` option.

## Examples

Inject a single file:

```cmd
ringi.exe -s MyArchive.pak -i 0000007F.bik
```

Inject a single file and remove it after successful injection:

```cmd
ringi.exe -s MyArchive.pak -i 0000007F.bik -rf
```

Inject all PNG files from a directory:

```cmd
ringi.exe -s MyArchive.pak -i png\*
```

Inject all PNG files and remove them after successful injection:

```cmd
ringi.exe -s MyArchive.pak -i png\*.png -rf
```

## Support the Project

[![Support on Patreon](https://c5.patreon.com/external/logo/become_a_patron_button.png)](https://www.patreon.com/Shegorat)

If you find this project useful, consider supporting development on Patreon.
