# Uyghur ↔ Latin Uyghur Converter

Converts text between the Uyghur Arabic script (كونا يېزىق) and Latin Uyghur
(يېڭى يېزىق). A single static page — no build step, no dependencies.

**Live:** https://anwarmamat.github.io/uyghur/ulc/

## Features

- Both directions, with automatic RTL/LTR handling on each field
- On-screen Uyghur keyboard for entering Arabic-script text
- Alphabet chart reflecting your current letter mappings
- Selectable letter mappings for ئە, خ, چ and ش, remembered per device
- Copy to clipboard, and a shareable link that carries the input text

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

Apache 2.0 — see [LICENSE](LICENSE).
