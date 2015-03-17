Reverse engineer a part of the Boost Graph Library.

# Introduction #

Reverse engineer a part of the Boost Graph Library.

You must not use new, delete, malloc(), free(), or std::allocator. All memory management must be handled by STL containers.

You also must produce a UML class diagram of the relationships between all of your classes. You can either do this by hand or by using any UML editor of your choice.


# Program Details #

Graphs are mathematical abstractions that are useful for solving many types of problems in computer science. Consequently, these abstractions must also be represented in computer programs. A standardized generic interface for traversing graphs is of utmost importance to encourage reuse of graph algorithms and data structures. Part of the Boost Graph Library is a generic interface that allows access to a graph's structure, but hides the details of the implementation. This is an “open” interface in the sense that any graph library that implements this interface will be interoperable with the BGL generic algorithms and with other algorithms that also use this interface. The BGL provides some general purpose graph classes that conform to this interface, but they are not meant to be the “only” graph classes; there certainly will be other graph classes that are better for certain situations. We believe that the main contribution of the The BGL is the formulation of this interface.