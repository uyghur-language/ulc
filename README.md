# Uyghur ↔ Latin Uyghur Converter

Converts text between the Uyghur Arabic script (كونا يېزىق) and Latin Uyghur
(يېڭى يېزىق). A single static page — no build step, no dependencies.

**Live:** https://anwarmamat.github.io/uyghur/ulc/

## Features

- Both directions, with automatic RTL/LTR handling on each field
- On-screen Uyghur keyboard for entering Arabic-script text
- Alphabet chart reflecting your current letter mappings
- Selectable Uyghur display font, with live previews
- Selectable letter mappings for ئە, خ, چ and ش, remembered per device
- Copy to clipboard, and a shareable link that carries the input text

### Fonts

Uyghur text can be rendered in Noto Naskh Arabic (the default, from Google
Fonts) or in one of four UKIJ faces, which are the ones Uyghur typesetting
actually uses:

| Font | Style |
| --- | --- |
| UKIJ Tuz Basma | Body text |
| UKIJ Tuz Kitab | Body text, wider |
| UKIJ Basma Qara | Heavier, compact |
| UKIJ Tuz Gezit | Newspaper |

The UKIJ faces are [self-hosted](fonts/) as subset WOFF2, ~25 KB each, so
they work on any device rather than only where the desktop fonts happen to
be installed. Each `@font-face` lists `local()` ahead of the URL, so anyone
who does have them installed renders from disk and downloads nothing.

Loading is lazy. A visitor on the default font fetches no UKIJ file at all;
picking one costs a single ~25 KB request. All four load together only when
the settings sheet is opened, since the picker previews each face in itself.

See [fonts/README.md](fonts/README.md) for attribution and how the subsets
were built. The fonts are free from [ukij.org](http://www.ukij.org) and are
not covered by this repository's license.

## Transliteration notes

Word-initial vowels take a hamza: `ata` → ئاتا. Going the other way, a
word-initial hamza is dropped and a mid-word hamza becomes an apostrophe,
which also serves as an explicit syllable separator on input — `n'ghaq` →
نغاق rather than the ڭھاق you would get from `nghaq`.

`c` is accepted as a shorthand for چ on input, but چ always converts back as
`ch` (or `q`, depending on your setting).

### Letter mappings

The default is ULY (Uyghur Latin Yëziqi). The alternatives follow the older
pinyin-based Yengi Yeziq conventions, which reassign several letters:

| Setting | Default | Alternative |
| --- | --- | --- |
| ئە | `e` → ە, `ë` → ې | `ë` → ە, `e` → ې |
| خ | `x` → خ, `h` → ھ | `h` → خ, `hh` → ھ |
| چ | `ch` → چ, `q` → ق | `q` → چ, `qh` → ق |
| ش | `sh` → ش | `x` → ش |

When `h` or `q` is taken by خ or چ, the orphaned letter is reached through
the digraph `hh` or `qh`; the Yengi Yeziq letters `ⱨ` and `ⱪ` are also
accepted as input. `x` cannot stand for both خ and ش, so choosing it for one
moves the other to its alternative.

## License

The converter is Apache 2.0 — see [LICENSE](LICENSE). The bundled UKIJ fonts
are the work of the Uyghur Computer Science Association and carry their own
terms; see [fonts/README.md](fonts/README.md).
