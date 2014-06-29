# An overview of the CTS URN notation #

CTS URNs are part of the CITE architecture. They provide the permanent canonical references to texts or passages of text, and are used by Canonical Text Services (CTS) to identify or retrieve passages of text. 

CTS URNs are a kind of Uniform Resource Name (URN). To quote from [RFC 2141](http://tools.ietf.org/html/rfc2141):

> Uniform Resource Names (URNs) are intended to serve as persistent, location-independent, resource identifiers.

## Semantics of a CTS URN

CTS URNs are citations, and they express the semantics of a "text" according to the OHCO2 model.[^ohco2Note]

[^ohco2Note]: "Ordered Hierarchy of Citation Objects." The original OHCO model defined a "text" as an Ordered Hierarchy of Content Objects; this model broke down due to the (inevitably) overlapping definitions of "content". See [Smith, N., Weaver, G., “Applying Domain Knowledge from Structured Citation Formats to Text and Data Mining: Examples Using the CITE Architecture” _Dartmouth Computer Science Technical Report TR2009-649_ 2009.](http://katahdin.cs.dartmouth.edu/reports/TR2009-649.pdf)

CTS URNs refer to a passage of text in terms of two hierarchies. The first hierarchy identifies a text in a model similar to the conceptual model of the Functional Requirements for Bibliographic Records (FRBR). (For an introduction to FRBR, see this [basic reading list](http://archive.ifla.org/VII/s13/frbr/readings.htm).) Where the conceptual model of FRBR aims to represent bibliographic entries as they are cataloged by librarians, however, CTS URNs aim to model works as they are cited by scholars.

CTS URNs organize works in *text groups*. Text groups have no direct parallel in FRBR, and do not have a predefined semantic range. Instead, they associate works, according to traditional citation practice, in groups with various meanings. The text group may reflect authorship (e.g., a work entitled *The Adventures of Huckleberry Finn* might belong to a group named "Mark Twain"), or may represent some other kind of corpus (e.g., a work numbered 1 belonging to a group named "Federalist Papers", or a work entitled *Κατὰ Λοῦκαν* belonging to a textgroup named "Novum Testamentum"). Within a text group, a CTS URN's work is a conceptual entity, like the FRBR work: it is an abstract idea of the content expressed in all versions of a work, in the original language or in translation.

The work may optionally be identified with increasing specificity as versions (translation or edition), or exemplars (individual physical copies). The CTS URN's version corresponds to the "expression" in the FRBR model, while exemplars correspond to "items" in FRBR parlance. At the "version" level, a text may be an "edition" of the notional "work", that is, a version of the work in the language in which the work was originally composed. A version in any other language is a translation. The CTS URN does not distinguish between editions and translation; they are both expressed by version-level URNs. 

The second hierarchy in a CTS URN refers to a passage expressed in a logical citation scheme. While the nature of this hierarchy depends on the specific work referred to by a CTS URN, many texts will fall into one of a few common citation schemes. Prose works might be cited by chapter and section, or book, chapter and section, for example, or poems might be cited by line, stanza and line, or book and line, for example.

Within the smallest citation unit (such as a paragraph or section for a prose work, or line of verse for a poem), CTS URNs can further specify a span of text with a subreference. Subreferences identify indexed substrings, or a range between an indexed pair of substrings. Because subreferences are inherently language-specific, they are only valid when the work identifier is specified to the level of a version (edition or translation), or exemplar.

##Resolving CTS URNs

By "resolving CTS URNs," we mean specifically the symmetric problems of how we determine what work a CTS URN refers to, and how we determine what URN values to use to refer to a work. (The further question of how to *retrieve* a passage of text referred to by a CTS URN is beyond the scope of the CTS URN's location-independent identifiers.)

These problems are analogous to the familiar problems of resolving internet domain names to numeric addresses, and vice versa, and it is unsurprising that CTS URNs use analogous mechanisms solve them. Like the internet domain name system, CTS URNs must guarantee that the values used to identify a work are globally unique. Like DNS, CTS URNs achieve this by delegating responsibility for managing authoritative registries. Like a top-level DNS server, CTS URNs depend ultimately on a top-level registry listing what further CTS registries are responsible for specific domains. This top-level registry is housed in the Scaife Digital Library, a durable digital repository. (Further links to SDL will be added here when they are available.)

Just as a university or business can manage domain names within its own domain name space, an organization can manage a registry of canonical identifiers for texts within its domain. So the top-level registry assigns the identifier greekLit to a registry maintained at the Center for Hellenic Studies covering ancient Greek transmitted by manuscript copying. Other registries could be added to cover specific collections of epigraphic or papyrological texts.

##Syntax of a CTS URN

URNs always begin with the string `urn:` followed by a protocol identifier. We use the identifier `cts` for our protocol.

Colons separate the top-level elements of a CTS URN: any use of a semicolon as a data value must therefore be escaped. The top-level elements are:

	1.	urn name space (required: always cts)
	2.	cts namespace (required: a value that can be resolved to a unique URI)
	3.	work identifier (required: a value registered in the designated registry)
	4.	passage reference (optional)
	5.	subreference (optional)

The general structure of a CTS URN is therefore

    urn:cts:CTSNAMESPACE:WORK:PASSAGE:SUBREFERENCE?

Periods separate second-level hierarchical components of the work identifier and passage reference.

### CTS namespace

The work citation must include a namespace prefix resolving to a unique URI in the `GetCapabilities` reply of a recognized CTS service.

### Work identifiers

Work identifiers are formatted as dot-separated components representing at least one of 

    textgroup, work, edition | translation, exemplar

Values must be registered with the registry identified by the CTS namespace component.

Example: The namespace Registry identifies the CHS registry of ancient Greek transmitted by manuscript copying with the namespace `greekLit`; the CHS registry in turn identifies the textgroup "Homer" with the ID `tlg0012`and the work *Iliad* with the ID `tlg001`. A URN reference to the *Iliad* would therefore be expressed as 

    urn:cts:greekLit:tlg0012.tlg001
    
### Passage citations

Passage citations may refer either to individual passages or to ranges within a work.

A reference to an individual passage is formatted as dot-separated components representing one or more levels of the citation hierarchy defined in a CTS TextInventory for that work.

A reference to a range is formatted as two passage references separated by a hyphen.

CTS 3 accommodates works with multiple citation schemes. Because different parts of a work might have citation schemes with different depths to their citation hierarchy, it is essential to allow ranges to include references to beginning and end points at different depths in different citation schemes. To avoid ambiguity, each of the two passage references in a range expression must be given fully: implicit context, as is commonly used in informal normal, is not permitted. (E.g., while common informal usage allows expressions like `1.10-20` to mean "lines 10-20 of book 1," a CTS URN would require an passage expression like `1.10-1.20` )

Examples: Extending the previous example, a reference to line 10 of book 1 of the *Iliad* would be 

    urn:cts:greekLit:tlg0012.tlg001:1.10 

A reference to lines 10-20 of the same book would be: 

    urn:cts:greekLit:tlg0012.tlg001:1.10-1.20


### Subreferences

Subreferences identify spans within a single citation unit using indexed substrings. A subreference follows the citation-element, separated by the character `@`.

## Summary

| Namespace Identifier | Namespace Specific String | CTS Namespace | TextGroup | Work | Version | Exemplar | Citation | Subreference |
|----------------------|---------------------------|---------------|-----------|------|---------|----------|----------|---|
| `urn` | `:cts` | `:greekLit` | `:tlg0012` | `.tlg001` | `.msA` | `.thosJeff` | `:1.2` | `@οὐλομένην` |


| Component | Notes |
|---|---|
| `urn:cts:greekLit:tlg0012.tlg001.msA.thosJeff:1.2@οὐλομένην` ||
| `urn` | Namespace Identifier `<NID>`, required by the URN standard. |
| `:cts` | Namespace Specific String `<NSS>`, required by the URN standard, identifies this URN as a CTS URN. |
| `:greekLit` | CTS Namespace. An abbreviation for an identifying authority for some domain of texts.  |
| `:tlg0012` | Textgroup. In this case, the textgroup known as "Homer", which includes the works _Iliad_ and _Odyssey_. `tlg0012` is the identifier asserted by the Center for Hellenic Studies' _First Thousand Years of Greek_ project, abbreviated by the namespace `greekLit`  |
| `.tlg001` | The identifier for the _Iliad_, a notional work, encompassing every edition and translation of that work. |
| `.msAVill` | An identifier for an edition of the Homeric _Iliad_, the version of the Greek text that appears on the Venetus A manuscript, as edited by Gaspar de Villoison, in this case. |
| `.thosJeff` | An identifier for a particular exemplar of the Venetus A edition by Villoison owned by, and annoted by the hand of, Thomas Jefferson. |
| `:1.2` | The citation. The _Iliad_ is canonically cited by Book + Poetic line; this two-level citation hiearchy, then, consists of two values separated by a `.`: Book 1, line 2.[^arbitrary] | 
| `@οὐλομένην` | Subreference. This identifies the string `οὐλομένην` in line 2 of Book 1 of Thomas Jefferson's copy of Villoison's edition of the Homeric _Iliad_.[^subrefs-note] |

[^arbitrary]: N.b. that the values (`1` and `2`) are _arbitrary identifiers_; these just happen to look like numbers, but they do not themselves determine the sequence. An edition of the _Iliad_ might begin with `1.2`, or might have the passage cited as `1.2` being the fight line of the poem. `1.2` could be followed, in a lacunose edition, by `1.6`.

[^subrefs-note]: N.b. A subreference element on a CTS URN, to be valid, must be attached to a CTS URN specific to the **version** level. The precise content of a passage cited at the **work** level is not prescribed.
