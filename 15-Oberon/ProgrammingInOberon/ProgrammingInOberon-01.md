# Programming in Oberon

A derivative of Programming in Modula-2 (1982)
        
Niklaus Wirth

## Table of Contents

### [Preface](#Preface)

### Part 1

1. Introduction
2. A First Example
3. A Notation to Describe the Syntax of Oberon
4. Representation of Oberon Programs
5. Statements and Expressions
6. Control Structures
    6.1 Repetitive Statements
    6.2 Conditional Statements
7. Elementary Data Types
    7.1 The Type INTEGER
    7.2 The Type REAL
    7.3 The Type BOOLEAN
    7.4 The Type CHAR
    7.5 The Type SET
8. Constant and Variable Declarations
9. Arrays3

### Part 2
10. Procedures
11. The Concept of Locality
12. Parameters
    12.1 Variable Parameters
    12.2 Value Parameters
    12.3 Open Array Parameters
13. Function Procedures
14. Recursion
15. Type Declarations
16. Record Types
17. Dynamic Data Structures and Pointers
18. Procedure Types27

### Part 3
19. Modules
20. Definitions and Implementations
21. Program Decomposition into Modules
22. The concept of sequence
    22.1. About input and output
    22.2. Files and Riders
    22.3. Texts, Readers and Writers
    22.4. Standard Input and Output42

### Part 4
23. Object-oriented Programming
    23.1. The origins of object-oriented programming
    23.2. Type extensions and inhomogeneous data structures
    23.3. Methods
    23.4. Handlers and Messages

Appendix: Syntax, Keywords, Standard functions


# Preface

This text is an introduction to programming in general, and a guide to programming in the language Oberon in particular. It is primarily oriented towards people who have already acquired some basic knowledge of programming and would like to deepen their understanding in a more structured way. Nevertheless, an introductory chapter is added for the benefit of the beginner, displaying in a concise form some of the fundamental concepts of computers and of programming them. The text is therefore also suitable as a self-contained tutorial. The notation used is Oberon, which lends itself well for a structured approach and leads the student to a working style that has generally become known under the heading of structured programming.

?????????????????????????????????????????? Oberon ???????????????????????? ?????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ???????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????? ?????????????????? Oberon???????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????

As a manual for programming in Oberon, the text covers (almost) all facilities of this language. Part 1 covers the basic notions of variable, expression, assignment, conditional and repeated statement, and the data structure of the indexable array. Together with Part 2, which introduces the important concept of the procedure or subroutine, it contains essentially the material commonly discussed in introductory programming courses. Part 2 also presents data types and structures and constitutes the core of an advanced course on programming. Part 3 introduces the notion of a module, a concept that is fundamental in the design of large programming systems, and to programming in teams. The two basic notions of files and texts are introduced in the forms of modules containing the operations performed on files and texts. Texts are presented as our standard medium for program input and output.

?????? Oberon ????????????????????????????????????????????????????????????????????? ??? 1 ???????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ???????????????????????????????????????????????? 2 ?????????????????????????????????????????????????????????????????????????????? ??? 2 ????????????????????????????????????????????????????????????????????????????????? ??? 3 ????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????????

The language Oberon, published in 1988, has a long history. It is a descendant of Algol 60 (1960), Pascal (1970), and Modula (1979). Algol 60 [1] was designed by an international committee of 13 scientists, and it was the first language to be specified with a rigorous formalism, a syntax, in machine-independent form. Algol was largely oriented toward numerical algorithms, as were computers at that time. Pascal [2] was the result of an enduring debate about widening the range of application of Algol, and it became widely used, in particular but not only, in education. Modula-2 [3] introduced the concept of modules, the parts of large systems connected by clearly specified interfaces. The module allows to hide details of procedures and variables from its users (clients), and it embodies the principle of information hiding. The language Oberon [4] emerged from the urge to reduce the complexity of programming languages, of Modula in particular. This effortresulted in a remarkably concise language. The extent of Oberon, the number of its features and constructs, is smaller even than that of Pascal. Yet it is considerably more powerful.

1988????????????Oberon????????????????????? ?????? Algol 60 (1960)???Pascal (1970) ??? Modula (1979) ???????????? Algol 60 [1] ??????????????? 13 ???????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? Algol ???????????????????????????????????????????????????????????? Pascal [2] ??????????????? Algol ??????????????????????????????????????????????????????????????????????????????????????????????????? Modula-2 [3] ???????????????????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????????????????????????????? Oberon [4] ????????????????????????????????????????????????????????? Modula??? ??????????????????????????????????????????????????? Oberon ??????????????????????????????????????????????????? Pascal ????????? ???????????????????????????????????????

The one feature that was added in Oberon was the extensibility of data types (record types). Whereas in strongly types languages, such as Algol, Pascal, and Modula, every constant, variable, or function has a fixed type, recognizable from the program text, Oberon allows to define hierarchies of types, and to determine the actual type of a variable (within the hierarchy) at run-time. This, together with records containing fields of procedural types, is the stem of object-oriented programming. Such records are then called objects, and the procedural fields are called methods. Here, we do not touch upon this subject.

Oberon ??????????????????????????????????????????????????????????????????????????? ?????????????????????????????? Algol???Pascal ??? Modula????????????????????????????????????????????????????????????????????????????????????????????????????????? Oberon ?????????????????????????????????????????????????????????????????? ??????????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????? ??????????????????????????????????????????

Z??rich, 1. October 2004 N.W.

1. P. Naur, Ed. Revised Report on the Algorithmic Language Algol 60. Comp. J. 5, 349-367 (1962), and Comm. ACM, 6 (1963) 1 ??? 17.
2. N. Wirth. The Programming Language Pascal. Acta Informatica, 1 (1971), 35 ??? 63.
3. N. Wirth. Programming in Modula-2. Springer-Verlag, 1982. ISBN 0-387-50150-9
4. N. Wirth. The Programming Language Oberon. Software - Practice and Experience, 18, 7, (July 1988), 671- 690.

# Part 1

## 1. Introduction

Although this manual assumes that its reader is already familiar with the basic notions of computer and programming, it may be appropriate to start out with the explanation of some concepts and their terminology. We recognize that - with rare exceptions - programs are written - more appropriately: designed - with the purpose of being interpreted by a computer. The computer then performs a process, i.e. a sequence of actions, according to the specifications given by that program. The process is also called a computation.

????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????? ???????????????????????????

The program itself is a text. Since it specifies a usually fairly complex process, and must do so with utmost precision and care for all details, the meaning of this text must be specified very precisely. Such precision requires an exact formalism. This formalism has become known as a language. We adopt this name, although a language is normally spoken and much less precisely defined. Our purpose here is to learn the formalism or language Oberon. It has a long tradition among programming languages. Its ancestor was Algol 60, followed by Pascal and Modula-2.

????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????? ????????????????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????? ?????????????????????????????????????????????????????? Oberon??? ????????????????????????????????????????????? ??????????????? Algol 60???????????? Pascal ??? Modula-2???

A program usually specifies a process that causes its interpreter, i.e. the computer, to read data (the so-called input) from some sources and to vary its subsequent actions according to the accepted data. This implies that a program does not only specify a (single) process, but an entire - usually unbounded - class of computations. We have to ensure that these processes act according to the given specifications (or should we say expectations?) in all cases of this class. Whereas we could verify that this specification is met in the case of a single computation, this is impossible in the general case, because the class of all permitted processes is much too large. The conscientious programmer ensures the correctness of his program by careful design and analysis. Careful design is the essence of professional programming.

?????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????????????????????????????? ?????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ???????????????????????????????????????????????????????????????????????????????????? ???????????????????????????????????????

The task of designing a program is further complicated by the fact that the program not only must describe an entire class of computations, but often should also be interpreted (executed) by different interpreters (computers). At earlier times, this required the manual transcription of the program from its source form into different computer codes, taking into account their various characteristics and limitations. The difficulties have been drastically reduced, albeit not eliminated, by the creation of high level languages with formal definitions and the construction of automatic translators converting the program into the codes of the various computers.

?????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ?????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????

In principle, the formal language should be defined in an abstract, perhaps axiomatic fashion without reference to an actual computer or interpretation mechanism. If this were achieved, the programmer would have to understand the formal language only. However, such generality is costly and often restrictive, and in many cases the programmer should still know the principal characteristics of his computer(s). Nevertheless, the qualified programmer will make as little reference to specific computer characteristics as possible and rely exclusively on the rules of the formal language in order to keep his program general and portable. The language Oberon assists in this task by confining computer dependencies to specific objects, by allowing to encapsulate them in specific, small parts of a program text.

??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? Oberon ????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????

From the foregoing it follows that a translation process lies between the program's formulation and its interpretation. This process is called a compilation, because it condenses the program's source text into a cryptic computer code. The quality of this compilation may be crucial to the efficiency of the program's ultimate interpretation. We stress the fact that there may be many compilers for a given language (even for the same computer). Some may be more efficient than others. We recognize that efficiency is a characteristic of implementations rather than the language. It therefore is important to distinguish between the concepts of language and implementation.

???????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????????????????? ???????????????????????????????????????????????????????????????????????? ?????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????? ?????????????????????????????????????????????????????????????????? ???????????????????????????????????????????????????

We summarize:
- A program is a piece of text.
- The program specifies computations or processes.
- A process is performed by an interpreter, usually a computer, interpreting (executing) the program.
- The meaning of the program is specified by a formalism called programming language.
- A program specifies a class of computations, the input data acting as parameter of each individual process.
- Prior to its execution, a program text is translated into computer code by a compiler. This process is called a compilation.

???????????????
- ????????????????????????
- ?????????????????????????????????
- ??????????????????????????????????????????????????????????????????????????????
- ????????????????????????????????????????????????????????????
- ???????????????????????????????????????????????????????????????????????????
- ????????????????????????????????????????????????????????????????????? ???????????????????????????

Program design includes ensuring that all members of this class of computations act according to specification. This is done by careful analytic verification and by selective empirical testing of characteristic cases.

????????????????????????????????????????????????????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????????

Programs should refrain from making reference to characteristics of specific interpreters (computers) whenever possible. Only the lack of such reference ensures that their meaning can be derived from rules of the language.

???????????????????????????????????????????????????????????????????????? ?????????????????????????????????????????????????????????????????????????????????????????????

A compiler is a program translating programs from their source form to specific computer codes. Programs need to be compiled before they are executed. Programming in the wider sense not only includes the formulation of the program, but also the concrete preparation of the text, its compilation, correction of errors, so-called debugging, and the planning of tests. The modern programmer uses many tools for these tasks, including text editors, compilers, and debuggers. He also has to be familiar with the environment of these components. We shall not describe these aspects, but concentrate on the language Oberon.

?????????????????????????????????????????????????????????????????????????????? ????????????????????????????????? ??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????? ????????????????????????????????????????????????????????????????????????????????????????????????????????? ?????????????????????????????????????????? ??????????????????????????????????????????????????? Oberon ?????????

