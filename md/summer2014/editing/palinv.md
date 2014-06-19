# Recording a paleographic sample #

## Rationale ##

We want to collect paleographic observations for two distinct purposes.

1. We want to document the repertory of graphemes that we have transcribed in our edition.  By "grapheme" we mean a single visual symbol that could represent a single letter, a ligature, or an abbreviation.  This corresponds closely to the kind of paleographic notes that might be made, if not necessarily published, in paleographic surveys, although now we can comprehensively publish our observations together with the documentary visual evidence.
2. We also have an unprecendented opportunity to collect paleographic observations for statistical statements about the distribution and use of distinct forms of writing.  For this purpose, it is essential to collect randomly chosen observations. In the summer of 2014, our practice is that, for each page we edit, we want to collect a full set of observations for *one* line of the *Iliad* (the first line on the given page), and for the first twenty graphemes in the main scholia.  (This could conceivably encompass more than one scholion, or it might be only a fraction of the content of a single long scholion.)  


## Method ##

Paleographic observations are citable objects:  we will record them in CITE Collection.   Because we want to know which observations were randomly sampled, and which observations were made because you encountered a previously unrecorded form, we will use two distinct collections.

In your team's editing repository, you should find a file named `paleography.csv` in the `collections` directory which is preformatted for recording your randomly selected observations.  (Be sure you can find this both on github, from a web browser interface, and in your local clone of the repository in your virtual machine.)

Objects in the collection have four properties:  you can see that the `.csv` file is organized in four columns: labelled **Observation**, **TextURN**, **Image**, and **Comments**.

- **Observation** will consist of a unique URN for each observation you record. It will be formatted like this: `urn:cite:op:TEAMCOLLECTION.IDENTIFIER`
- **TextURN** will consist of the urn for the text passage with the specification for the paleographic feature you are observing. You should include the specific text passage (line of the *Iliad* or individual scholion), and a "subreference" identifying an indexed substring within that passage. For example, if you are observing the first alpha on line 55 of Book One in the *Iliad* in the Venetus A, the urn will look like this: urn:cts:greekLit:tlg0012.tlg001.msA:1.55@α. Be sure to include all diacritical marks. If the grapheme is a ligature, include both letters. If this is not the first time you have indexed a particular paleographic feature, note the index of the occurrence in square brackets []. For for instance, if the alpha we cited above was the third alpha, the citation would look like this: urn:cts:greekLit:tlg0012.tlg001.msA:1.55@α[3]
- **Image** will consist of the full URN reference, including the region of interest coordinates, acquired using the image citation tool. In your table, be sure to place this reference  in quotes "..." to protect the commas of the region of interest from being misinterpreted as columns of your table.
- **Comments** will consist of any further notes you have to add on the image you have indexed. This column can be left blank if no comment is necessary.


## Verifying your work ##

We cannot computationally verify your visual indices, but we do want to provide a different method of visually reviewing your index. HMT-MOM includes a task that will create a web page where you can visually survey your index.

Within your editing repository, you should find a shell script called `palview.sh` that you can run within your virtual machine: 

       sh palview.sh

This will create in the hmt-mom build directory a directory called `paleography` with web page called `viewer.html` that you can open in a web browser in your host operating system.
