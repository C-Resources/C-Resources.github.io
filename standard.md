# The C Language Standard

The C language is standardised by a joint committee of ISO and IEC.
See [C Standards Committee Home
Page](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n3280.htm) for
more information.

New editions of the standard are produced every few years.  At the
time of writing, the most recent one is C23.

## Reading the Standard

The standard is well written but nevertheless not easy to read.  This
is because when reading any part of it, you need to pay attention to
some complex issues that pervade the standard.  These include sequence
points, the as-if rule, implementation-defined and undefined
bheaviour.  It is also important to distinguish the parts of the
standard that are normative and those which are not (for example the
Rationale).

If you are a C compiler author or a maintainer of an implementation of
the Standard C library (though formally from the point of view of the
Standard these are not separate concepts) then it is well worth
purchasing a copy of the standard. Almost everybody else can get away
with using a draft version which is likely to be close but not
identical.

|Version|Standard|Draft|
|:-|:-|:-|
|C23|[ISO/IEC 9899:2024](https://www.iso.org/standard/82075.html)|[N3220 working draft](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n3220.pdf)|
|C17|[ISO/IEC 9899:2018](https://webstore.iec.ch/en/publication/63478) (no longer sold by ISO)|[N2176, C17 ballot](https://web.archive.org/web/20181230041359if_/http://www.open-std.org/jtc1/sc22/wg14/www/abq/c17_updated_proposed_fdis.pdf)|
|C11|ISO/IEC 9899:2011 (no longer on sale by ISO or IEC). However some USA INCITS documents are essentially identical: [INCITS/ISO/IEC 9899-2012](https://webstore.ansi.org/standards/incits/INCITSISOIEC98992012) \+ [Corrigendum 1](https://webstore.ansi.org/standards/iso/ISOIEC9899Cor12012).|[N1570 Committee Draft](https://www.open-std.org/jtc1/sc22/WG14/www/docs/n1570.pdf)|
|C99|ISO/IEC 9899:1999 (no longer on sale by ISO or UEC). However, some associated standards bodies have it available: [INCITS/ISO/IEC 9899:1999](https://webstore.ansi.org/standards/incits/INCITSISOIEC98991999R2005) \+ Corrigenda [Cor1](https://store.accuristech.com/standards/iso_iec/9899_cor1_2001?product_id=1035925), [Cor2](https://store.accuristech.com/standards/iso_iec/9899_cor2_2004?product_id=1205982), [Cor3](https://store.accuristech.com/standards/iso_iec/9899_cor3_2007?product_id=1527765)|[N1256 Committee Draft](https://www.open-std.org/jtc1/sc22/WG14/www/docs/n1256.pdf)|
|C95|**ISO/IEC 9899:1990/AMD 1:1995** (no longer on sale by ISO or IEC).  |[AMD1 Standard Preview](https://web.archive.org/web/20250629143324/https://cdn.standards.iteh.ai/samples/23909/3713b553291741f7aa531e8de6b28bfe/ISO-IEC-9899-1990-Amd-1-1995.pdf)|
|C90|**ISO/IEC 9899:1990** (no longer on sale by ISO or IEC).   [Available from NSAI](https://shop.standards.ie/en-ie/standards/iso-iec-9899-1990-592351_saig_iso_iso_1356836/) .||
|C89|Identical to C90 except for the frontmatter and section numbering.|[C89 Draft (HTML)](https://web.archive.org/web/20250000000000*/https://port70.net/~nsz/c/c89/c89-draft.html)|


## History of the C Language

There is a first-hand account in Dennis M. Ritchie's paper "[The
Development of the C
Language](https://csapp.cs.cmu.edu/3e/docs/chistory.html)" and
Wikipedia's page on C has a
[History](https://en.wikipedia.org/wiki/C_\(programming_language\)#History)
section.

The [timelne at
cppreference.com](https://en.cppreference.com/w/c/language/history.html)
combines the early history of C and events in the standardisation
process.
