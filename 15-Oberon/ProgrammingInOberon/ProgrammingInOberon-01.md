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

# Part 1

## 1. Introduction

Although this manual assumes that its reader is already familiar with the basic notions of computer and programming, it may be appropriate to start out with the explanation of some concepts and their terminology. We recognize that - with rare exceptions - programs are written - more appropriately: designed - with the purpose of being interpreted by a computer. The computer then performs a process, i.e. a sequence of actions, according to the specifications given by that program. The process is also called a computation.

儘管本手冊假定其讀者已經熟悉計算機和編程的基本概念，但從解釋一些概念及其術語開始可能是合適的。 我們認識到——除了極少數例外——程序是為了被計算機解釋而編寫的——更恰當地說：設計的。 然後計算機根據該程序給出的規範執行一個過程，即一系列動作。 該過程也稱為計算。

The program itself is a text. Since it specifies a usually fairly complex process, and must do so with utmost precision and care for all details, the meaning of this text must be specified very precisely. Such precision requires an exact formalism. This formalism has become known as a language. We adopt this name, although a language is normally spoken and much less precisely defined. Our purpose here is to learn the formalism or language Oberon. It has a long tradition among programming languages. Its ancestor was Algol 60, followed by Pascal and Modula-2.

程序本身就是一個文本。 由於它指定了一個通常相當複雜的過程，並且必須非常精確地執行並註意所有細節，因此必須非常準確地指定此文本的含義。 這種精確性需要精確的形式主義。 這種形式主義已經成為一種語言。 我們採用這個名稱，儘管通常使用一種語言並且定義不那麼準確。 我們在這裡的目的是學習形式主義或語言 Oberon。 它在編程語言中有著悠久的傳統。 它的祖先是 Algol 60，之後是 Pascal 和 Modula-2。

A program usually specifies a process that causes its interpreter, i.e. the computer, to read data (the so-called input) from some sources and to vary its subsequent actions according to the accepted data. This implies that a program does not only specify a (single) process, but an entire - usually unbounded - class of computations. We have to ensure that these processes act according to the given specifications (or should we say expectations?) in all cases of this class. Whereas we could verify that this specification is met in the case of a single computation, this is impossible in the general case, because the class of all permitted processes is much too large. The conscientious programmer ensures the correctness of his program by careful design and analysis. Careful design is the essence of professional programming.

一個程序通常指定一個過程，使它的解釋器，即計算機，從某些來源讀取數據（所謂的輸入），並根據接受的數據改變其後續操作。 這意味著程序不僅指定一個（單個）進程，而且指定整個（通常是無界的）計算類。 我們必須確保這些過程在此類的所有情況下都按照給定的規範（或者我們應該說期望？）行事。 雖然我們可以驗證在單個計算的情況下是否滿足此規範，但在一般情況下這是不可能的，因為所有允許的進程的類別太大了。 認真的程序員通過仔細的設計和分析來確保他的程序的正確性。 精心設計是專業編程的精髓。

The task of designing a program is further complicated by the fact that the program not only must describe an entire class of computations, but often should also be interpreted (executed) by different interpreters (computers). At earlier times, this required the manual transcription of the program from its source form into different computer codes, taking into account their various characteristics and limitations. The difficulties have been drastically reduced, albeit not eliminated, by the creation of high level languages with formal definitions and the construction of automatic translators converting the program into the codes of the various computers.

設計程序的任務更加複雜，因為程序不僅必須描述整個計算類，而且通常還應該由不同的解釋器（計算機）解釋（執行）。 在早期，這需要將程序從其源形式手動轉錄為不同的計算機代碼，同時考慮到它們的各種特性和局限性。 通過創建具有正式定義的高級語言和構建將程序轉換為各種計算機代碼的自動翻譯器，困難已經大大減少，儘管沒有消除。

In principle, the formal language should be defined in an abstract, perhaps axiomatic fashion without reference to an actual computer or interpretation mechanism. If this were achieved, the programmer would have to understand the formal language only. However, such generality is costly and often restrictive, and in many cases the programmer should still know the principal characteristics of his computer(s). Nevertheless, the qualified programmer will make as little reference to specific computer characteristics as possible and rely exclusively on the rules of the formal language in order to keep his program general and portable. The language Oberon assists in this task by confining computer dependencies to specific objects, by allowing to encapsulate them in specific, small parts of a program text.

原則上，形式語言應該以抽象的方式定義，也許是公理化的方式，而不參考實際的計算機或解釋機制。 如果實現了這一點，程序員將只需要理解形式語言。 然而，這種普遍性代價高昂且通常具有限制性，在許多情況下，程序員仍應了解其計算機的主要特性。 然而，合格的程序員將盡可能少地參考特定的計算機特性，而完全依賴形式語言的規則，以保持其程序的通用性和可移植性。 Oberon 語言通過將計算機依賴性限制在特定對像上，允許將它們封裝在程序文本的特定小部分中來協助完成此任務。

From the foregoing it follows that a translation process lies between the program's formulation and its interpretation. This process is called a compilation, because it condenses the program's source text into a cryptic computer code. The quality of this compilation may be crucial to the efficiency of the program's ultimate interpretation. We stress the fact that there may be many compilers for a given language (even for the same computer). Some may be more efficient than others. We recognize that efficiency is a characteristic of implementations rather than the language. It therefore is important to distinguish between the concepts of language and implementation.

從前面可以看出，在程序的製定和解釋之間存在一個翻譯過程。 這個過程稱為編譯，因為它將程序的源文本壓縮成神秘的計算機代碼。 這種編譯的質量可能對程序最終解釋的效率至關重要。 我們強調一個事實，即對於給定的語言（即使對於同一台計算機）可能有許多編譯器。 有些可能比其他的更有效率。 我們認識到效率是實現的一個特徵，而不是語言。 因此，區分語言和實現的概念很重要。

We summarize:
- A program is a piece of text.
- The program specifies computations or processes.
- A process is performed by an interpreter, usually a computer, interpreting (executing) the program.
- The meaning of the program is specified by a formalism called programming language.
- A program specifies a class of computations, the input data acting as parameter of each individual process.
- Prior to its execution, a program text is translated into computer code by a compiler. This process is called a compilation.

我們總結：
- 程序是一段文本。
- 該程序指定計算或過程。
- 一個過程由解釋器執行，通常是計算機解釋（執行）程序。
- 程序的含義由稱為編程語言的形式主義指定。
- 程序指定一類計算，輸入數據充當每個單獨過程的參數。
- 在執行之前，程序文本由編譯器翻譯成計算機代碼。 這個過程稱為編譯。

Program design includes ensuring that all members of this class of computations act according to specification. This is done by careful analytic verification and by selective empirical testing of characteristic cases.

程序設計包括確保此類計算的所有成員都按照規范進行操作。 這是通過仔細的分析驗證和對典型案例的選擇性經驗測試來完成的。

Programs should refrain from making reference to characteristics of specific interpreters (computers) whenever possible. Only the lack of such reference ensures that their meaning can be derived from rules of the language.

程序應盡可能避免引用特定解釋器（計算機）的特性。 只有缺乏這樣的參考才能確保它們的含義可以從語言規則中推導出來。

A compiler is a program translating programs from their source form to specific computer codes. Programs need to be compiled before they are executed. Programming in the wider sense not only includes the formulation of the program, but also the concrete preparation of the text, its compilation, correction of errors, so-called debugging, and the planning of tests. The modern programmer uses many tools for these tasks, including text editors, compilers, and debuggers. He also has to be familiar with the environment of these components. We shall not describe these aspects, but concentrate on the language Oberon.

編譯器是將程序從其源形式轉換為特定計算機代碼的程序。 程序在執行前需要編譯。 廣義的編程不僅包括程序的製定，還包括文本的具體準備、編寫、錯誤更正、所謂的調試和測試計劃。 現代程序員使用許多工具來完成這些任務，包括文本編輯器、編譯器和調試器。 他還必須熟悉這些組件的環境。 我們不會描述這些方面，而是集中討論 Oberon 語言。

