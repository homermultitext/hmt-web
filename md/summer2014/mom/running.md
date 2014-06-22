# Running MOM #



Your editing repository includes two shell scripts you can use to verify your editorial work.


## dse.sh ##


`dse.sh` verifies *only* the relations of all the three interlinked components of the Digital Scholarly Editions (DSE) model:  text, artifact and image.  Its syntax is

    bash dse.sh FOLIO-PAGE-URN

where FOLIO-PAGE-URN is the full URN for a manuscript page (e.g., `urn:cite:hmt:msA.12r` cites folio 12 recto of the Venetus A).  `hmt-mom` checks that all DSE relations are correct, and creates the visual inventory of texts indexed to an image. (See [more details about hmt-mom's output](output.html).)  The advantage of using `dse.sh` is that you can test all of your indexing work even before you have begun editing XML.
 

## verify.sh ##

`verify.sh` runs the same tests as `dse.sh`, plus additional tests analyzing the text of your XML edition.  To use `verify.sh`, run


     bash verify.sh FOLIO-PAGE-URN

where `FOLIO-PAGE-URN` is the full URN for a page you have edited and want to validate.

