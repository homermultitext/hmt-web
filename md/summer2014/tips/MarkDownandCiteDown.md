# Basic Markdown and Citedown #

## Basic Formatting in Markdown ##

Headings are identified with ‘#.’ Subheadings are created with successive numbers of ‘#’ so on this page

    ##Basic Formatting in Markdown##

is a subheading of

    #Basic Markdown and Citedown#

New paragraphs are formatted by including a blank line between two paragraphs. 

You can also format for emphasis using a single asterisk.   Emphasize a title like the *Iliad* like this:

    *Iliad*

Two asterisks indicate **strong** emphasis, e.g.,

    **strong** emphasis


Bulleted lists are created by starting a line with a hyphen:

    - Item One
    - Item Two

will produce

> - Item One
> - Item Two

Sublists are created by indenting four (4) spaces, e.g.

    - Item Three
        - Sublist item one
        - Sublist item two

yields 


> - Item Three
> 	- Subitems can be created by tabbing in
> 	- Subitem Two 

You can create numbered lists by starting a line with a number -- *any* number -- followed by a period.  So

    1. A
    2. B

produces 

> 1. A
> 2. B


and 

    1. A
    1. B
   
identically produces

> 1. A
> 1. B
 

Markdown also allows you to identify references to urls with square brackets and a colon.

    [1]: http://www.homermultitext.org

defines a reference named `1` to  the site `http://www.homermultitext.org`.  A markdown converter will know these are link references and not display them in the final version.  To attach this link to some text, surround the text with square brackets, followed by the reference identifier.  E.g.,

    Hey, check out [Homer Multitext][1].

would produce

>Hey, check out [Homer Multitext][1].

[1]: http://www.homermultitext.org



## Basic References in Citedown ##

Citedown extends markdown so that you can link and embed URN references.   You can do this with any type of URN, whether cited objects (CITE URNs) or canonical text references (CTS URNs).   Define an identifier for a URN using the same notation as for URL identifiers, e.g., 

If I wanted to link you to piece of evidence to explore at your leisure, I could encode it like this: 

    [2]: urn:cite:hmt:vaimg.VA100VN-0603@0.1842,0.8197,0.1572,0.0909

Then use curly brackets instead of square brackets to identify text linked to this URN, e.g.,

    Hey, go look at this {awesome reference}[2].

You can quote (embed) the reference instead of citing (linking to) the reference by preceding the link with an exclamation point:

    Hey, I want you to see this !{awesome reference}[2].

The HMT virtual machine includes a converter that will generate fully linked markdown from citedown.  You can then user any generic markdown tool to generate web pages, slideshows or pdfs.


