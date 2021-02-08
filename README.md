# Clairvo

Clairvo is a proof-of-concept font that uses OpenType Layout to implement the number system developed by Cistercian monks in the 13th Century. The number system records each number from 1–9999 as a unique sign based on encoding units, tens, hundreds, and thousands in quadrants: top-right, top-left, bottom-right, and bottom-left respectively. The Clairvo font uses OpenType glyph substitution to handle mirroring of the shapes in each quadrant, but relies mostly on contextual GPOS anchors to shift the glyphs around the quadrants. This means that all 9999 numbers can be represented my a minimal number of glyphs.

![](https://github.com/TiroTypeworks/Clairvo/blob/main/graphics/ClairvoSM.png)

____

### Build process

The Clairvo build uses a slightly modified version of the Tiro Library build, which outputs fonts in CFF and TTF OpenType formats, along with WOFF2 and WOFF webfont versions of the same. The Clairvo font does not contain glyphs that tthautohint expects to find in a font, so the portion of the build process that applies ttfautohint has been disabled.

Design source : .vfj (FontLab 7 json)

OpenType Layout source : .vtp (MS VOLT project)

Build source for outlines, spacing, font info : .ufo (Unified Font Object)

Build source for OpenType Layout : input.ttf

*The Clairvo font uses GSUB lookup subtable structures that are not correctly supported in Adobe’s .fea code compilers. The OpenType Layout for this project is done in Microsoft’s Visual OpenType Layout Tool* (*VOLT*) *and the compiled GDEF, GPOS, and GSUB tables are grabbed from the .input.ttf font during the build process. The OTL can be edited by importing the .vtp project file into the .input.ttf file in VOLT, but note that the font should be ‘shiped’ from VOLT to remove internal source references in the OTL tables before building the fonts. Edits to the OTL should be saved by exporting a fresh .vtp file from VOLT.*

From the top level, Clairvo folder:

```
# Create a new virtualenv
python3 -m venv venv
# Activate env
source venv/bin/activate
# Install dependencies
pip install -r requirements.txt
```

For subsequent use (presuming the requirements have not changed), only the second of those steps will be required.

Run the build script indicating the YAML configuration file:

`$ python tools/tirobuild.py clairvo.yml`

