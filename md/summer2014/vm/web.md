
# Making web pages from citedown source #

Your repository includes a bash script called `convertcd.sh` that will convert URN references in citedown to live links.  By default, it converts any files in your directory named `writing`, and puts the output in the directory named `converted`.    To run the script with default settings, use

    bash convertcd.sh

You will then find two copies of each file in the `converted` folder:  a generic markdown file you can use with any software that supports markdown, and an html file you can view in a web browser.
