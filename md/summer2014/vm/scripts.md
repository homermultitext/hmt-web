# Summary of automated tasks in the HMT VM #

Your editorial repository includes shell scripts that automate several tasks in the HMT VM.

## Paleographic inventory ##

To create a web page where you can visualize the paleographic inventory you created in `collections/paleography.csv`:

    sh palview.sh

The web page is in `hmt-mom/build/paleography/viewer.html`

## Verifying relations of text, image and artifact ##

You can test the consistency of your indexing by running

    sh dse.sh FOLIO-PAGE-URN

This will create a visual inventory of your index in `hmt-mom/build/visualinventory/inventory.xml`.  (**NB**: Chrome's default security settings will not load the javascript file that is used to overlay your indices on an image;  Safari or Firefox will open the file without problems using default settings.)

## XML editing ##

You can run the full HMT-MOM verification suite with this command:

    sh verify.sh FOLIO-PAGE-URN

where `FOLIO-PAGE-URN` is the full URN for a page you have edited and want to validate.

For full details on working with HMT-MOM, see [this page](../mom/index.html).

