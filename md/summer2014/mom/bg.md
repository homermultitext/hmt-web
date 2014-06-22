# HMT-MOM: background #


HMT-MOM attempts to do two related jobs:

1. test every aspect of our editing that can be tested automatically
2. where we need to supplement automated testing with human review, automatically create differnt views of our data to ensure  that human review of content is never simply a second repetition of the same error-prone process

MOM uses the `citemgr` library (<https://github.com/cite-architecture/citemgr>) to validate  relations of the CITE architecture's generic Digital Scholarly Editions model.  In this model, each citable unit of text is explicitly related to a physical surface preserving the text;  both text and physical artifact are explicitly related to documentary visual evidence.    The `citemgr` library verifies the consistency of URNs documenting all sides of that triangle of relations.

In accordance with this model, all editing and verification for the HMT project proceed by physical unit:  the physical surface that preserves a text, whether that is a page of a codex, a panel or face of an inscribed stone, or  single column of a long papyrus scroll (try [this view of the Bankes papyrus][bankes] to see how many columns could fill a single scroll).

To the generic validation of the Digital Scholarly Editions model, MOM adds further tests that are specific to the content or editorial policy of the Homer Multitext project.  To see what tests are covered in each version of MOM released since 2014, see [this page](versions.html).


[bankes]: http://beta.hpcc.uh.edu/tomcat/hmtdigital/images?request=GetIIPMooViewer&urn=urn:cite:hmt:bmpap114.Pap114_pano
