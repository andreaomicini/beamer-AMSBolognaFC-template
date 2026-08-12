# beamer-AMSBolognaFC-template

> A ready-to-use presentation skeleton for the
> [AMSBolognaFC Beamer style](https://github.com/andreaomicini/beamer-AMSBolognaFC)

## author

* Andrea Omicini

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
\documentclass[presentation,apice]{beamer}\mode<presentation>{\usetheme{AMSBolognaFC}}
```

With it, an `apice` field in a BibTeX entry is displayed as a small `(APICe)`
marker linking to the corresponding page of the
[APICe](https://apice.unibo.it/) Wiki:

```bibtex
@manual{bibtex-patashnik88,
    ...
    apice = {BibtexPatashnik88},
}
```

Drop the option and nothing else has to change: `\apicepar` is still defined,
but expands to nothing, so the same `.bib` and the same slides keep working
with the markers simply absent.

The template's own slides demonstrate the option, and the bibliography shows
the marker in place.

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
