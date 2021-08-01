Krub LaTeX Files
================

[Krub](https://fonts.google.com/specimen/Krub) is a sans-serif font available in
six different weights with both an upright and italic variant for those weights.

From the Google Fonts Page (retrieved 2021-08-01):

> Krub is a Thai and Latin text face with a twist. It uses the modern structure
> of Thai's traditional looped letterforms and blends it seamlessly with
> elements taken from the metal type era. It's one of the most popular choices
> among graphic designers who are looking for a less dusty traditional Thai
> typeface.

See: [Google Fonts: About Krub](https://fonts.google.com/specimen/Krub#about)

This package will work in pdfLaTeX and LuaLaTeX. It is not tested in XeLaTeX.

Note that there does not seem to be an "official" 256-bit LaTeX font encoding
for the Thai script, only the T1 encoding is supported with pdfLaTeX. To use the
Thai script, use `fontspec` with one of the modern Unicode LaTeX engines.

This package does not include a style file. It does include a map file and a
font definition file for the T1 encoding.


Special Purpose
---------------

My purpose for this font is strictly to use it when typesetting taxonomical
names. I am not including style files to use this font as either the document
heading font or as the document text font. Map file and a T1 encoding font
definition file are included but style file(s) are not.


Modifications for LaTeX
-----------------------

As distributed from Google Fonts, the font files will not work with `pdflatex`
because they have the `OS/2 Version` set to `4` which the `pdftex` engine used
by `pdflatex` does not like.

To remedy this situation, the fonts were downloaded on 2021-08-01 and modified
in [FontForge](https://fontforge.org/). Two modifications were made:

1. The `Really use typo metrics` option was unchecked (that option causes
   FontForge to always use `OS/2 Version 4` when generating TrueType fonts).
2. The `OS/2 Version` was changed from `4` to `3`.

No other changes to Krub were made in FontForge.

The resulting `.sfd` files are located within the following directory:

    texmf-tree/source/krub/

The resulting `.ttf` files are located within the following directory:

    texmf-tree/fonts/truetype/googlefonts/krub/

Both the `.sfd` and `.ttf` files fall under the SIL Open Font License (OFL)
version 1.1 as packaged in the original font download.

A copy of that file accompanies both the `.sfd` and `.ttf` files.


### Typo Metrics Note

It appears that sometime early in the 21st century, some Microsoft software
started ignoring ascenders and decenders in the font itself, using Microsoft's
own `winAscent` and `winDescent` under certain conditions.

It appears that the `typo metrics` options instructs that software not to do
that but instead follow the instructions in the font as the font designer
intended.

As such you may not want to install the TTF fonts in this git on a Windows
system for use outside of LaTeX---instead just use Google Fonts download as
system fonts on a Windows system---assuming you *want* Krub as a system font.

The same issue *may* exist with Microsoft software running on macOS---using the
Google Fonts version *may* be better on macOS too if using as a system font and
you use some Microsoft software. I do not know.

On GNU/Linux systems as far as I know the option is meaningless. There should
be no difference between how the TTF fonts here render versus the Google Fonts
versions in any software on a GNU/Linux system. Also for non-Microsoft software
on macOS and Windows I suspect the option is meaningless.

Leave it to a behemoth capitalist company to change how a font behaves in such
a way that for font designers to get the original behavior, they have to select
a new option that requires changing other meta-data that then causes the font
not to work with some software. Capitalist idiots.

In fairness I could be wrong about what the `typo metrics` option does. That
option does seem to require that `OS/2 Version 4` be specified---which is why
FontForge will automatically set that version when exporting to `.ttf` if that
option is checked---and it does seem related to Microsoft rendering engines.

### ePub Note

Apparently some versions of Adobe Digital Edition also choke with `OS/2 Version
4` so if you want to embed this font in an ePub---you probably should embed the
TTF versions I have here rather than from Google Fonts. Otherwise it might work
just fine for you but not work at all for someone else with a different ePub
viewer that uses an older version of ADE.


Metric Files
------------

The Adobe Font Metric files were generated using the `ttf2afm` program using
the following option flag:

    -e T1-WGL4.enc

The resulting `.afm` files are located within the following directory:

    texmf-tree/fonts/afm/googlefonts/krub/

The TeX Font Metric files were generated using the `afm2tfm` program using the
following option flag:

    -T T1-WGL4.enc

The resulting `.tfm` files are located within the following directory:

    texmf-tree/fonts/afm/googlefonts/krub/

It is my understanding that in most countries, font metric files are not subject
to copyright and therefore not subject to the font license. However, if that is
not the case in your country, the Adobe Font Metric files and the TeX Font
Metric files would fall under the same SIL OFL that the Krub font files fall
under.


Map File
--------

A single font map file for the `pdftex` engine is provided at:

    texmf-tree/fonts/map/pdftex/googlefonts/krub.map

The map file does cover all twelve faces (six weights, bold and italic).

I do not know if other font map files for other engines are needed. If you are
packaging this font for CTAN or you wish to use this font with a different
LaTeX engine, please consult a LaTeX guru if you---like me---also do not know.

I believe that some LaTeX engines (like `dvips`) do not work with TrueType
fonts. If interested in packaging this font for use with `dvips` you *probably*
have to convert it to a Type 1 font first.

I recommend against doing so unless you *really* know what you are doing and
there *really* is a genuine need.

I consider the map file too generic to be subject to copyright but if a license
must be applied to it---then Creative Commons CC0 would apply. That license is
equivalent to Public Domain.


Font Driver Files
-----------------

A font driver files for one TeX Encoding is provided:

1. `texmf-tree/tex/latex/krub/t1krub.fd`

The font definitions file does not include shape definitions for the
extra-light, light, or normal weights. It uses the Medium weight as the LaTeX
normal weight, the SemiBold weight as the LaTeX bold weight, and the Bold weight
as the LaTeX extra bold weight.

With my special purpose, what the font defines as the normal weight was too thin
to use with TeX Gyre Termes but what the font defines as Medium was just right.


Install
-------

These instructions are for TeXLive 2021 but should work on older and newer
versions and should work in *most* LaTeX distributions (MiKTeX, MacTeX, PCTeX,
et cetera) but I have not tried.

Find your `TEXMF-LOCAL` tree. Consult your LaTeX documentation. On my system
where TeXLive is installed within `/usr/local/texlive` the directory for my
`TEXMF-LOCAL` is

    /usr/local/texlive/texmf-local

If your TeXLive is packaged by a GNU/Linux distribution, ask in your distro
support forum if you do not know where it is.

Make sure you are a user account with permission to modify your LaTeX install.

Within your `TEXMF-LOCAL` tree install the files from the `texmf-tree`
directory in this git using the same directory hierarchy. You do not need the
`texmf-tree/source/` files and you *probably* do not need the
`texmf-fonts/afm/` files. However it does not hurt for both to be installed and
they could be useful down the road.

After the files are in place, then run the following commands:

    mktexlsr && updmap-sys --enable Map=krub.map

Congratulations, the Krub font is now available to your `pdftex` engine
(e.g. by using `pdflatex`).
