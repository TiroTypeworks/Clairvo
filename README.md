# Clairvo

Clairvo is a proof-of-concept font that uses OpenType Layout to implement the number system developed by Cistercian monks in the 13th Century. The number system records each number from 1–9999 as a unique sign based on encoding units, tens, hundreds, and thousands in quadrants: top-right, top-left, bottom-right, and bottom-left respectively. The Clairvo font uses OpenType glyph substitution to handle mirroring of the shapes in each quadrant, but relies mostly on contextual GPOS anchors to shift the glyphs around the quadrants. This means that all 9999 numbers can be represented my a minimal number of glyphs.

**3 January 2021** : Initial commit; repo will be tidied up and proper build documentation added in the next couple of days; OpenType Layout for this project uses techniques not tested in non-VOLT build stream, so initial fonts use compiled OTL tables from input.ttf

