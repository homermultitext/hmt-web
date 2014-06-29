# The CITE architecture 

The CITE architecture defines a framework for scholarly reference to the unique cultural phenomena that humanists study. It was originally developed for the _Homer Multitext_, a project under the editorship of Casey Dué and Mary Ebbott, sponsored by the Center for Hellenic Studies of Harvard University, Gregory Nagy, Director.

It begins with definitions of two URN formats for citing resources:  the _CTS URN_ for texts, and the _CITE Collection URN_ for citing discrete objects.  URNs are technology-independent, human-readable but machine-parseable identifiers.

The architecture then defines corresponding network services that identify and retrieve objects using CITE URNs.

- The _Canonical Text Service_ uses CTS URNs to identify and retrieve digital representations of texts.
- The _CITE Collection Service_ uses Collection URNs to identify and retrieve digital representations of discrete objects.

In the CITE architecture, URNs also serve to associate objects with each other.  This relation is represented as a typed pairing of URNs, referred to as a _CITE Index_.  Generically, a CITE Index is a graph with nodes representing citable objects, and arcs representing the relation between the two objects; this can be instantiated as a triplet store.  We define a third service, a the CITE Graph service, that delivers nodes in a CITE graph adjacent to a node identified by URN.

The trio of Collections, Indexes and Texts make up the core of the CITE architecture.  The architecture allows further extensions (hence the acronym, CITE).  This web site includes documentation for one extension: the CHS Image Extension defines an extended URN notation for citing regions of interest on images that are uniquely identified by Collection URNs, and a corresponding network service for working with these extended URNs.

