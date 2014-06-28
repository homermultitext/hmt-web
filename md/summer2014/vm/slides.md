
# Slides presentations from citedown #



Your editorial repository includes a directory named `writing` and a directory named `converted`.  Any files you create in the `writing` folder with names ending in `.md` are assumed to be markdown files with URNs for scholarly citation.    You can convert those files to generic markdown with all references to URNs turned into URLs with the command

    bash convertcd.sh

You will then find two copies of each file in the `converted` folder:  a generic markdown file you can use with any software that supports markdown, and an html file you can view in a web browser.
