# Making pdfs from citedown

Your editorial repository includes a directory named `writing` and a directory named `converted`. Any files you create in the writing folder with names ending in `.md` are assumed to be markdown files with URNs for scholarly citation. You can convert those files to generic markdown with all references to URNs turned into URLs with the command

    bash convertcd.sh

Your virtual machine includes a very handy converter utility, [pandoc, for converting this generic markdown to multiple formats](http://johnmacfarlane.net/pandoc/).  It also includes an installation of the TeX typesetting system, and 11 fonts from the [Greek Font Society](http://www.greekfontsociety.gr/pages/en_about.html) suitable for use in printing pdfs.



## Shorthand aliases for creating pdfs##

The following aliases provide shorthands for calling `pandoc` using  fonts from the Greek Font Society.  The name of the alias corresponds to one of the fonts you can read about and see specimens of [here](http://www.greekfontsociety.gr/pages/en_typefaces1.html).  

To use one of the aliases, supply the name of the markdown file you want to convert together with pandoc's `-o` option to name the output file.  For example:

    didot -o printable.pdf yourwriting.md

This creates a pdf named `printable.pdf` from a markdown file named `yourwriting.md` using the lovely [GFS Didot Classic typeface](http://www.greekfontsociety.gr/images/Didot%20Specimen.pdf) for the main font.

(Links in the list below are to the GFS specimen sheets for each typeface.)

- [artemisia](http://www.greekfontsociety.gr/images/ArtemisiaSpecimen.pdf)
- [baskerville](http://www.greekfontsociety.gr/images/BaskervilleSpecimen.pdf)
- [bodoni](http://www.greekfontsociety.gr/images/BodoniSpecimen.pdf)
- [complutum](http://www.greekfontsociety.gr/images/ComplutumSpecimen.pdf)
- [didot](http://www.greekfontsociety.gr/images/Didot%20Specimen.pdf)
- [gazis](http://www.greekfontsociety.gr/images/GazisSpecimen.pdf)
- [neohellenic](http://www.greekfontsociety.gr/images/NeoHellenic%20Specimen.pdf)
- [olga](http://www.greekfontsociety.gr/images/OlgaSpecimen.pdf)
- [porson](http://www.greekfontsociety.gr/images/PorsonSpecimen.pdf)
- [solomos](http://www.greekfontsociety.gr/images/SolomosSpecimen.pdf)
- [theokritos](http://www.greekfontsociety.gr/images/TheokritosSpecimen.pdf)