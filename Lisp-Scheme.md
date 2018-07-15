Reading "Structure and Interpretation of Computer Programs" by Harold Abelson and Gerald Jay Sussman with Julie Sussman, foreword by Alan J. Perlis  
http://www.math.grinnell.edu/~miletijo/m208s15/StructIntCompPrograms.pdf  
Taking some thoughts from the book and making some sort of summary for myself here.  
  
The other important document is this one (not reading it yet):  
https://standards.ieee.org/findstds/standard/1178-1990.html  

- Digital computer vs. mechanical vs. other?
- Since large programs grow from small ones, it is crucial that we develop an arsenal of standard program structures of whose correctness we have become sure — we call them idioms — and learn to combine them into larger structures using organizational techniques of proven value.
- Unlike programs, computers must obey the laws of physics. If they wish to perform rapidly — a few nanoseconds per state change — they must transmit electrons only small distances (at most 11 2 feet).
- Amongthe programs we write, some (but never enough) perform a precise mathematical function such as sorting or finding the maximum of a sequence of numbers, determining primality, or finding the square root. We call such programs algorithms, and a great deal is known of their optimal behavior, particularly with respect to the two important parameters of execution time and data storage requirements. A programmer should acquire good algorithms and idioms. Even though some programs resist precise specifications, it is the responsibility of the programmer to estimate, and always to attempt to improve, their performance.
- [...] and we have rewritten all the program examples to ensure that any Scheme implementation conforming to the IEEE Scheme standard (IEEE 1990) will be able to run the code.
- http://mitpress.mit.edu/sicp provides support for users of this book. This includes programs from the book, sample programming assignments, supplementary materials, and downloadable implementations of the Scheme dialect of Lisp.
- MIT Core Curriculum (GIRs) / common core curriculum: https://mitadmissions.desk.com/customer/portal/articles/1283021-mit-core-curriculum-girs-
- The list, Lisp’s native data structure [...]
- It is better to have 100 functions operate on one data structure than to have 10 functions operate on 10 data structures. As a
result the pyramid [aka. Pascal language] must stand unchanged for a millennium; the organism [aka. Lisp language] must evolve or perish.
- No Lisp program of any size beyond a few lines can be written without being saturated with discretionary functions. Invent
and fit; have fits and reinvent! We toast the Lisp programmer who pens his thoughts within nests of parentheses.





