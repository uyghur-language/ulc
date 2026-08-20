# Bundled Uyghur fonts

Four UKIJ faces, self-hosted so the font picker works for every visitor
rather than only for people who have them installed on their desktop.

| File | Family | Size |
| --- | --- | --- |
| `UKIJTuzBasma.woff2` | UKIJ Tuz Basma | 26 KB |
| `UKIJTuzKitab.woff2` | UKIJ Tuz Kitab | 27 KB |
| `UKIJBasmaQara.woff2` | UKIJ Basma Qara | 22 KB |
| `UKIJTuzGezit.woff2` | UKIJ Tuz Gezit | 26 KB |

## Attribution

Created by the **Uyghur Computer Science Association** (UKIJ,
<http://www.ukij.org>), designed by Tursunjan Sultan. The embedded copyright
notice reads "Free distributed and all rights reserved"; the OpenType
embedding permission bits are *Installable* (`fsType` 0) for Tuz Basma, Tuz
Kitab and Tuz Gezit, and *Editable* (`fsType` 8, marked LGPL) for Basma
Qara — all of which permit web embedding.

These fonts are **not** covered by this repository's Apache 2.0 LICENSE,
which applies to the converter's own code.

## How these were produced

Converted from the original TrueType releases with `fontTools`: subset to
the ranges the page can display, then compressed to WOFF2.

```
pyftsubset UKIJTuzB.ttf \
  --unicodes=U+0020-00FF,U+0131,U+0152-0153,U+02BB-02BC,\
U+0600-06FF,U+0750-077F,U+FB50-FDFF,U+FE70-FEFF,\
U+200C-200F,U+2018-201E,U+2026,U+2039-203A,U+2C60-2C7F \
  --layout-features='*' --no-hinting --desubroutinize \
  --flavor=woff2 --output-file=UKIJTuzBasma.woff2
```

`--layout-features='*'` is load-bearing: it keeps the GSUB tables that drive
Arabic joining. The Arabic presentation-form ranges (`FB50-FDFF`,
`FE70-FEFF`) are kept for the same reason — these are 2004-era fonts that
map contextual forms through cmap.

Dropping the unused Cyrillic and symbol coverage took the set from 307 KB to
100 KB. Output was verified pixel-identical to the originals: the same
Uyghur and Latin strings rendered in both, screenshotted, and compared —
zero differing subpixels.
