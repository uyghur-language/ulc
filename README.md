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

**UKIJ Tuz Basma** is the default. Your choice sets the Uyghur text *and* the
interface, so the page reads as one typeface; only the display headings keep
their own face (Instrument Serif).

| Font | Style |
| --- | --- |
| UKIJ Tuz Basma | Body text, the default |
| UKIJ Tuz Kitab | Body text, wider |
| UKIJ Basma Qara | Heavier, compact |
| UKIJ Tuz Gezit | Newspaper |
| Noto Naskh Arabic | Naskh |

The UKIJ faces are [self-hosted](fonts/) as subset WOFF2, so they work on any
device rather than only where the desktop fonts happen to be installed. Each
ships in regular *and* bold, since a face that sets the interface needs a real
bold for the 600-weight labels instead of a synthesized one.

Loading stays lazy. A default visit downloads only Tuz Basma's two weights,
66 KB, which are preloaded. Picking another face costs its two weights;
opening the settings sheet loads the regular of each, because the picker
previews every face in itself.

See [fonts/README.md](fonts/README.md) for attribution, how the subsets were
built, and the one glyph that had to be excluded. The fonts are free from
[ukij.org](http://www.ukij.org) and are not covered by this repository's
license.

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

When `h` or `q` is taken by خ or چ, the orphaned letter is reached through the
digraph `hh` or `qh`. The Yengi Yeziq letters `ⱨ` and `ⱪ` are always accepted
for ھ and ق, whichever convention is selected.

`x` cannot stand for both خ and ش, so choosing it for one moves the other to
its alternative. And when خ takes `h` while ش keeps `sh`, nothing else claims
`x`, so it is accepted for ش as well — otherwise it would fall through as a
literal Latin letter.

Every one of the twelve selectable combinations reaches all 32 letters and
round-trips cleanly.

## License

The converter is Apache 2.0 — see [LICENSE](LICENSE). The bundled UKIJ fonts
are the work of the Uyghur Computer Science Association and carry their own
terms; see [fonts/README.md](fonts/README.md).
