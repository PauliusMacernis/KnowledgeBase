Reading "Structure and Interpretation of Computer Programs" by Harold Abelson and Gerald Jay Sussman with Julie Sussman, foreword by Alan J. Perlis  
http://www.math.grinnell.edu/~miletijo/m208s15/StructIntCompPrograms.pdf  
Taking some thoughts from the book and making some sort of summary for myself here.  
  
The other important document is this one (not reading it yet):  
https://standards.ieee.org/findstds/standard/1178-1990.html  

# Foreword & Preface to the Second Edition & Preface to the First Edition

- Digital computer vs. mechanical vs. other?
- Since large programs grow from small ones, it is crucial that we develop an arsenal of standard program structures of whose correctness we have become sure — we call them idioms — and learn to combine them into larger structures using organizational techniques of proven value.
- Unlike programs, computers must obey the laws of physics. If they wish to perform rapidly — a few nanoseconds per state change — they must transmit electrons only small distances (at most 11 2 feet).
- Amongthe programs we write, some (but never enough) perform a precise mathematical function such as sorting or finding the maximum of a sequence of numbers, determining primality, or finding the square root. We call such programs algorithms, and a great deal is known of their optimal behavior, particularly with respect to the two important parameters of execution time and data storage requirements. A programmer should acquire good algorithms and idioms. Even though some programs resist precise specifications, it is the responsibility of the programmer to estimate, and always to attempt to improve, their performance.
- The list, Lisp’s native data structure [...]
- It is better to have 100 functions operate on one data structure than to have 10 functions operate on 10 data structures. As a
result the pyramid [aka. Pascal language] must stand unchanged for a millennium; the organism [aka. Lisp language] must evolve or perish.
- No Lisp program of any size beyond a few lines can be written without being saturated with discretionary functions. Invent
and fit; have fits and reinvent! We toast the Lisp programmer who pens his thoughts within nests of parentheses.
- [...] and we have rewritten all the program examples to ensure that any Scheme implementation conforming to the IEEE Scheme standard (IEEE 1990) will be able to run the code.
- This edition emphasizes several new themes. The most important of these is the central role played by different approaches to dealing with time in computational models: objects with state, concurrent programming, functional programming, lazy evaluation, and nondeterministic programming. We have included new sections on concurrency and nondeterminism, and we have tried to integrate this theme throughout the book.
- http://mitpress.mit.edu/sicp provides support for users of this book. This includes programs from the book, sample programming assignments, supplementary materials, and downloadable implementations of the Scheme dialect of Lisp.
- MIT Core Curriculum (GIRs) / common core curriculum: https://mitadmissions.desk.com/customer/portal/articles/1283021-mit-core-curriculum-girs-
- First, we want to establish the idea that a computer language is not just a way of getting a computer to perform operations but rather that it is a novel formal medium for expressing ideas about methodology. Thus, programs must be written for people to read, and only incidentally for machines to execute.
- Second, we believe that the essential material to be addressed by a subject at this level is not the syntax of particular programming-language constructs, nor clever algorithms for computing particular functions efficiently, nor even the mathematical analysis of algorithms and the foundations of computing, but rather the techniques used to control the intellectual complexity of
large software systems.
- We control complexity by building abstractions that hide details when appropriate. We control complexity by establishing conventional interfaces that enable us to construct systems by combining standard, well-understood pieces in a “mix and match” way. We control complex ity by establishing new languages for describing a design, each of which emphasizes particular aspects of the design and deemphasizes others.
- Underlying our approach to this subject is our conviction that “computer science” is not a science and that its significance has little to do with computers. The computer revolution is a revolution in the way we think and in the way we express what we think.
- procedural epistemology —the study of the structure of knowledge from an imperative point of view, as opposed to the more declarative point of view taken by classical mathematical subjects. Mathematics provides a framework for dealing precisely with notions of “what is.” Computation provides a framework for dealing precisely with notions of “how to.”
- Lisp-like languages: They have very few ways of forming compound expressions, and almost no syntactic structure. All of the formal properties can be covered in an hour, like the rules of chess. After a short time we forget about syntactic details of the language (because there are none) and get on with the real issues—figuring out what we want to compute, how we will decompose problems into manageable parts, and how we will work on the parts.
- Another advantage of Lisp is that it supports (but does not enforce) more of the large-scale strategies for modular decomposition of programs than any other language we know.
  - We can make procedural and data abstractions, 
  - we can use higher-order functions to capture common patterns of usage,
  - we can model local state using assignment and data mutation, 
  - we can link parts of a program with streams and delayed evaluation, 
  - and we can easily implement embedded languages.
- From Lisp we take the metalinguistic power that derives from the simple syntax, the uniform representation of programs as data objects, and the garbage-collected heap-allocated data. 
- From Algol we take lexical scoping and block structure, which are gifts from the pioneers of programming-language design who were on the Algol committee.
- Marvin Minsky and Seymour Papert formed many of our attitudes about programming and its place in our intellectual lives. To them we owe the understanding that computation provides a means of expression for exploring ideas that would otherwise be too complex to dealwith precisely. They emphasize that a student’s ability to write and modify programs provides a powerful medium in which exploring becomes a natural activity.
- We also strongly agree with Alan Perlis that programming is lots of fun and we had better be careful to support the joy of programming. Part of this joy derives from observing great masters at work.

# Building Abstractions with Procedures
- Well-designed computational systems, like well-designed automobiles or nuclear reactors, are designed in a modular manner, so that the parts can be constructed, replaced, and debugged separately.
- Lisp was invented in the late 1950s as a formalism for reasoning about the use of certain kinds of logical expressions, called recursion equations , as a model for computation. The language was conceived by John McCarthy and is based on his paper “Recursive Functions of Symbolic Expressions and Their Computation by Machine” (McCarthy 1960).
- The Lisp 1 Programmer’s Manual appeared in 1960, and the Lisp 1.5 Programmer’s Manual (McCarthy et al. 1965) was published in 1962. The early history of Lisp is described in McCarthy 1978.
- A Lisp interpreter is a machine that carries out processes described in the Lisp language.
- **Lisp, whose name is an acronym for LISt Processing**, was designed to provide symbol-manipulating capabilities for attacking programming problems such as the symbolic differentiation and integration of algebraic expressions. It included for this purpose new data objects known as atoms and lists, which most strikingly set it apart from all other languages of the period.
- The Lisp dialect used in this book, called Scheme (Steele and Sussman 1975), was invented in 1975 by Guy Lewis Steele Jr. and Gerald Jay Sussman of the MIT Artificial Intelligence Laboratory and later reimplemented for instructional use at MIT. Scheme became an IEEE standard in 1990 (IEEE 1990). The Common Lisp dialect (Steele 1982, Steele 1990) was developed by the Lisp community to combine features from the earlier Lisp dialects to make an industrial standard for Lisp. Common Lisp became an IEEE standard in 1994 (ANSI 1994).
- Although Lisp has not yet overcome its old reputation as hopelessly inefficient, Lisp is now used in many applications where efficiency is not the central concern. For example, Lisp has become a language of choice for operating-system shell languages and for extension languages for editors and computer-aided design systems.
- The most significant of these features is the fact that Lisp descriptions of processes, called procedures , can themselves be represented and manipulated as Lisp data. The importance of this is that there are powerful program-design techniques that rely on the ability to blur the traditional distinction between “passive” data and “active” processes.

## 1.1 The Elements of Programming
- Every powerful language has three mechanisms for combining simple ideas to form more complex ideas:
  - **primitive expressions** , which represent the simplest entities the language is concerned with,
  - **means of combination** , by which compound elements are built from simpler ones, and
  - **means of abstraction** , by which compound elements can be named and manipulated as units.
- In programming, we deal with two kinds of elements: procedures and data. (Later we will discover that they are really not so distinct.). Thus, any powerful programming language should be able to describe primitive data and primitive procedures and should have methods for combining and abstracting procedures and data.

### 1.1.1 Expressions
- One kind of primitive expression you might type is a number. (More precisely, the expression that you type consists of the numerals that represent the number in base 10.)
- science of numerical analysis
- Expressions such as these (for example: `(+ 2.7 10)`, `(/ 10 5)`, `(* 5 99)`, `(- 1000 334)`, `(+ 137 349)`), formed by delimiting a list of expressions within parentheses in order to denote procedure application, are called **combinations** . The leftmost element in the list is called the **operator** , and the other elements are called **operands** . The value of a combination is obtained by **applying the procedure specified by the operator to the arguments that are the values of the operands**.
- The convention of placing the operator to the left of the operands is known as prefix notation , and it may be somewhat confusing at first because it departs significantly from the customary mathematical convention. Prefix notation has several advantages, however. One of them is that it can accommodate procedures that may take an arbitrary number of arguments, as in the following examples: `(+ 21 35 12 7)`, `(* 25 4 12)`. No ambiguity can arise, because the operator is always the leftmost element and the entire combination is delimited by the parentheses.
- A second advantage of prefix notation is that it extends in a straight forward way to allow combinations to be nested , that is, to have combinations whose elements are themselves combinations: `(+ (* 3 5) (- 10 6))`, `(+ (* 3 (+ (* 2 4) (+ 3 5))) (+ (- 10 7) 6))`, we can help ourselves by writing such an expression in the form:
```
(+ (* 3
        (+ (* 2 4)
            (+ 3 5)))
    (+ (- 10 7)
        6))
```
### 1.1.2 Naming and the Environment
- A critical aspect of a programming language is the means it provides for using names to refer to computational objects. We say that the name identifies a variable whose value is the object. In the Scheme dialect of Lisp, we name things with `define`. Typing `(define size 2)` causes the interpreter to associate the value `2` with the name `size`. Once the name `size` has been associated with the number `2`, we can refer to the value `2` by name: `size`
- **Lisp-Scheme has `define` while Clojure has `def`!!!***
- Lisp systems typically provide features to aid the user in formatting expressions. Two especially useful features are:
  - one that automatically indents to the proper pretty-print position whenever a new line is started and 
  - one that highlights the matching left parenthesis whenever a right parenthesis is typed.
- Lisp obeys the convention that every expression has a value. This convention, together with the old reputation of Lisp as an inefficient language, is the source of the quip by Alan Perlis (paraphrasing Oscar Wilde) that “Lisp programmers know the value of everything but the cost of nothing.”
- `(* 5 size)`
- `(define circumference (* 2 pi radius))`
- It should be clear that the possibility of associating values with symbols and later retrieving them means that the interpreter must maintain some sort of memory that keeps track of the name-object pairs. **This memory is called the environment** (**more precisely the global environment** , since we will see later that a **computation may involve a number of different environments**).

### 1.1.3 Evaluating Combinations
- Let us consider that, in evaluating combinations, the interpreter is itself following a procedure.  
To evaluate a combination, do the following:  
  1. Evaluate the subexpressions of the combination.
  2. Apply the procedure that is the value of the leftmost subexpression (the operator) to the arguments that are the values of the other subexpressions (the operands).
- Even this simple rule illustrates some important points about processes in general. First, observe that the first step dictates that in order to accomplish the evaluation process for a combination we must first perform the evaluation process on each element of the combination. Thus, the evaluation rule is recursive in nature; that is, it includes, as one of its steps, the need to invoke the rule itself. **The example to consider**: `(*  (+ 2 (* 4 6))  (+ 3 5 7)  )` ,- requires that the evaluation rule be applied to four different combinations.
- In fact, the “percolate values upward” form of the evaluation rule is an example of a general kind of process known as **tree accumulation**.
- We take care of the primitive cases by stipulating that:
  - the values of numerals are the numbers that they name,
  - the values of built-in operators are the machine instruction sequences that carry out the corresponding operations, and
  - the values of other names are the objects associated with those names in the environment.
- We may regard the second rule as a special case of the third one by stipulating that symbols such as `+` and `*` are also included in the global environment, and are associated with the sequences of machine instructions that are their “values.” The key point to notice is the role of the environment in determining the meaning of the symbols in expressions. In an interactive language such as Lisp, **it is meaningless to speak of the value of an expression such as `(+ x 1)` without specifying any information about the environment that would provide a meaning for the symbol `x` (or even for the symbol `+` )**. The general
notion of the environment as providing a context in which evaluation takes place will play an important role in our understanding of program execution.
- Notice that the evaluation rule given above does not handle definitions. For instance, evaluating `(define x 3)` does not apply `define` to two arguments, one of which is the value of the symbol `x` and the other of which is `3`, since the purpose of the `define` is precisely to associate `x` with a value. (That is, **`(define x 3)` is not a combination.**). Such exceptions to the general evaluation rule are called **special forms**. `define` is the only example of a special form that we have seen so far.
- 





