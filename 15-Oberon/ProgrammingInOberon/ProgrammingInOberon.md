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

本書是一般編程的介紹，尤其是 Oberon 語言編程的指南。 它主要面向那些已經掌握了一些編程基礎知識並希望以更有條理的方式加深理解的人。 儘管如此，為了有利於初學者，還是增加了一個介紹性的章節，以簡明的形式展示了計算機及其編程的一些基本概念。 因此，該文本也適合作為獨立的教程。 使用的符號是 Oberon，它非常適合結構化方法，並引導學生採用在結構化編程的標題下通常廣為人知的工作風格。

As a manual for programming in Oberon, the text covers (almost) all facilities of this language. Part 1 covers the basic notions of variable, expression, assignment, conditional and repeated statement, and the data structure of the indexable array. Together with Part 2, which introduces the important concept of the procedure or subroutine, it contains essentially the material commonly discussed in introductory programming courses. Part 2 also presents data types and structures and constitutes the core of an advanced course on programming. Part 3 introduces the notion of a module, a concept that is fundamental in the design of large programming systems, and to programming in teams. The two basic notions of files and texts are introduced in the forms of modules containing the operations performed on files and texts. Texts are presented as our standard medium for program input and output.

作為 Oberon 編程手冊，本書（幾乎）涵蓋了該語言的所有功能。 第 1 部分涵蓋變量、表達式、賦值、條件和重複語句的基本概念，以及可索引數組的數據結構。 與介紹過程或子例程的重要概念的第 2 部分一起，它基本上包含入門編程課程中通常討論的材料。 第 2 部分還介紹了數據類型和結構，構成了編程高級課程的核心。 第 3 部分介紹模塊的概念，這是大型編程系統設計和團隊編程的基礎概念。 文件和文本這兩個基本概念以包含對文件和文本執行的操作的模塊的形式介紹。 文本是我們程序輸入和輸出的標準媒介。

The language Oberon, published in 1988, has a long history. It is a descendant of Algol 60 (1960), Pascal (1970), and Modula (1979). Algol 60 [1] was designed by an international committee of 13 scientists, and it was the first language to be specified with a rigorous formalism, a syntax, in machine-independent form. Algol was largely oriented toward numerical algorithms, as were computers at that time. Pascal [2] was the result of an enduring debate about widening the range of application of Algol, and it became widely used, in particular but not only, in education. Modula-2 [3] introduced the concept of modules, the parts of large systems connected by clearly specified interfaces. The module allows to hide details of procedures and variables from its users (clients), and it embodies the principle of information hiding. The language Oberon [4] emerged from the urge to reduce the complexity of programming languages, of Modula in particular. This effortresulted in a remarkably concise language. The extent of Oberon, the number of its features and constructs, is smaller even than that of Pascal. Yet it is considerably more powerful.

1988年發表的Oberon語言歷史悠久。 它是 Algol 60 (1960)、Pascal (1970) 和 Modula (1979) 的後代。 Algol 60 [1] 是由一個由 13 位科學家組成的國際委員會設計的，它是第一種以嚴格的形式主義、語法、獨立於機器的形式被指定的語言。 Algol 主要面向數值算法，當時的計算機也是如此。 Pascal [2] 是關於擴大 Algol 應用範圍的持久爭論的結果，它被廣泛使用，尤其是但不僅限於教育領域。 Modula-2 [3] 引入了模塊的概念，即通過明確指定的接口連接的大型系統的各個部分。 該模塊允許對其用戶（客戶端）隱藏過程和變量的細節，它體現了信息隱藏的原則。 Oberon [4] 語言源於促進降低編程語言複雜性，尤其是 Modula。 這種努力導致了一種非常簡潔的語言。 Oberon 的範圍，其特徵和結構的數量，甚至比 Pascal 還小。 然而，它的功能要強大得多。

The one feature that was added in Oberon was the extensibility of data types (record types). Whereas in strongly types languages, such as Algol, Pascal, and Modula, every constant, variable, or function has a fixed type, recognizable from the program text, Oberon allows to define hierarchies of types, and to determine the actual type of a variable (within the hierarchy) at run-time. This, together with records containing fields of procedural types, is the stem of object-oriented programming. Such records are then called objects, and the procedural fields are called methods. Here, we do not touch upon this subject.

Oberon 中添加的一項功能是數據類型（記錄類型）的可擴展性。 在強類型語言中，例如 Algol、Pascal 和 Modula，每個常量、變量或函數都有一個固定的類型，可以從程序文本中識別出來，而 Oberon 允許定義類型的層次結構，並確定變量的實際類型 （在層次結構中）在運行時。 這與包含過程類型字段的記錄一起，是面向對象編程的主幹。 這樣的記錄稱為對象，過程字段稱為方法。 在這裡，我們不涉及這個主題。

Zürich, 1. October 2004 N.W.

1. P. Naur, Ed. Revised Report on the Algorithmic Language Algol 60. Comp. J. 5, 349-367 (1962), and Comm. ACM, 6 (1963) 1 – 17.
2. N. Wirth. The Programming Language Pascal. Acta Informatica, 1 (1971), 35 – 63.
3. N. Wirth. Programming in Modula-2. Springer-Verlag, 1982. ISBN 0-387-50150-9
4. N. Wirth. The Programming Language Oberon. Software - Practice and Experience, 18, 7, (July 1988), 671- 690.




