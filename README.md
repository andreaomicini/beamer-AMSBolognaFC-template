# beamer-AMSBolognaFC-template

![AMSBolognaFC Beamer template logo](logo/amsbolognafc-template-full.svg)

> A ready-to-use presentation skeleton for the
> [AMSBolognaFC Beamer style](https://github.com/andreaomicini/beamer-AMSBolognaFC)

## author

* Andrea Omicini

## requirements

* A TeX distribution providing `pdflatex`, `latexmk` and `bibtex` (TeX Live).

The style itself needs no separate installation: the `.style` submodule pins the
release this template was built against, and the symbolic links in the repository
root reach it.

## usage

Clone the repository **with its submodule**, since the style is pulled in that way:

```bash
git clone --recurse-submodules https://github.com/andreaomicini/beamer-AMSBolognaFC-template.git
```

If you have already cloned without `--recurse-submodules`:

```bash
git submodule update --init .style
```

Then edit `AMSBolognaFC-template.tex` and build it as usual, e.g.

```bash
latexmk -pdf AMSBolognaFC-template.tex
```

The most recent build of the template is attached to every
[release](https://github.com/andreaomicini/beamer-AMSBolognaFC-template/releases).

### the `apice` option

The template's preamble enables the style's `apice` option:

```latex
\documentclass[presentation,cesena,apice]{beamer}\mode<presentation>{\usetheme{AMSBolognaFC}}
```

With it, an `apice` field in a BibTeX entry is displayed as a small `APICe`
marker linking to the corresponding page of the
[APICe](https://apice.unibo.it/) XWiki:

```bibtex
@manual{bibtex-patashnik88,
    ...
    apice = {BibtexPatashnik88},
}
```

Drop the option and nothing else has to change: `\apicepubpar` is still defined,
but expands to nothing, so the same `.bib` and the same slides keep working
with the markers simply absent.

The template's own slides demonstrate the option, and the bibliography shows
the marker in place.

### the `bologna` and `cesena` options

These select the seal that watermarks every slide, in the lower-right corner and
cropped by the page edge. `bologna` selects the seal of the *Alma Mater Studiorum*
as a whole, `cesena` the seal of the *Campus di Cesena*:

```latex
\documentclass[presentation,bologna]{beamer}\mode<presentation>{\usetheme{AMSBolognaFC}}
\documentclass[presentation,cesena]{beamer}\mode<presentation>{\usetheme{AMSBolognaFC}}
```

The two are told apart by the border — solid for the Campus, an outline for the
Ateneo — which is what an eye in the Alma Mater reads first.

**Neither option, no seal.** Since style 1.8 the watermark is not the default: a
deck has to claim a seal out loud, and one that claims neither is simply bare.
The seals are institutional marks, so this is what anyone not belonging — or no
longer, or not yet belonging — to the Alma Mater should do, and the style is
theirs to use unchanged in every other respect.

This template passes `cesena`, so its slides carry the Campus seal.

## relation to beamer-AMSUniBo-template

[beamer-AMSUniBo-template](https://github.com/andreaomicini/beamer-AMSUniBo-template)
is this template with the AMSUniBo style in place of the AMSBolognaFC one. Since
1.8 the two have the same frames and demonstrate the same features; what differs
is the palette, which the `Colours` frame documents, and the faces.

Since 1.10 the template follows style 1.11, where the commands take their colour
from the surface they land on. The `Surfaces` frame states the rule — the
`block` and `alertblock` headers are dark, all else light — and the doubled
form of a command is the same command, smaller and quieter. `One Command, Every
Surface` prints the same source line in the text and in every header and body.
The `Citations` frame shows `\ccite` on a dark header, on the example one and
in running text, with its optional note, as in `\ccite[p.~42]{key}`;
`\cccite` is now the same command. `Alert & Emphasis` shows `\alert` and
`\emph` in a header, and `\aalert` as the quiet alert.

## structure

The style itself lives in the `.style` submodule, which tracks the `main`
branch of [beamer-AMSBolognaFC](https://github.com/andreaomicini/beamer-AMSBolognaFC).
The style files in the repository root are symbolic links into `.style`, so
there is exactly one copy of each file.

To move the template onto a newer style release:

```bash
git submodule update --remote .style
git add .style
git commit -m "Update style submodule"
```

## versioning

The template version is declared in `AMSBolognaFC-template.tex` as
`\templatemajor` / `\templateminor` / `\templatepatch`, giving
`Major.Minor[.Patch]`. `\templatepatch` is optional: comment it out to release
as `Major.Minor`.

Releases are tagged `Major.Minor[.Patch]-<UTC time-stamp>`, with the time-stamp
appended automatically by the CI at release time.

The template is versioned independently of the style: it changes sometimes
together with the style and sometimes on its own.

## licence

The template is released into the public domain under
[CC0 1.0 Universal](LICENSE). Use it, adapt it and build on it freely, with no
obligation to credit or to carry any notice into your own presentations.

This applies to the template itself. The style files reached through the
`.style` submodule are covered by their own licence — the
[LaTeX Project Public License](https://github.com/andreaomicini/beamer-AMSBolognaFC/blob/main/LICENSE),
version 1.3c or later — and `apalike-AMS.bst` remains subject to Oren
Patashnik's terms.
