# Summary of automated tasks in the HMT VM #

Your editorial repository includes shell scripts that automate several tasks in the HMT VM.

## Paleographic inventory ##

To create a web page where you can visualize the paleographic inventory you created in `collections/paleography.csv`:

    sh palview.sh

The web page is in `hmt-mom/build/paleography/viewer.html`


## XML editing ##

You can run the full HMT-MOM verification suite with this command:

    sh verify.sh FOLIO-PAGE-URN

where `FOLIO-PAGE-URN` is the full URN for a page you have edited and want to validate.

For full details on working with HMT-MOM, see [this page](../mom/index.html).


## Writing in citedown ##

Your editorial repository includes a directory named `writing` and a directory named `converted`.  Any files you create in the `writing` folder with names ending in `.md` are assumed to be markdown files with URNs for scholarly citation.    You can convert those files to generic markdown with all references to URNs turned into URLs with the command

    bash convertcd.sh

You will then find two copies of each file in the `converted` folder:  a generic markdown file you can use with any software that supports markdown, and an html file you can view in a web browser.