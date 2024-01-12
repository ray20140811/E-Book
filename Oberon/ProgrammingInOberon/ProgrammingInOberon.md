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

## 2. A First Example

Let us follow the steps of development of a simple program and thereby explain some of the fundamental concepts of programming and of the basic facilities of Oberon. The task shall be, given two natural numbers x and y, to compute their greatest common divisor (gcd). The mathematical knowledge needed for this problem is the following:

讓我們按照簡單程序的開發步驟來解釋一些編程的基本概念和 Oberon 的基本功能。 任務是給定兩個自然數 x 和 y，計算它們的最大公約數 (gcd)。 這個問題需要的數學知識如下：

1. if x equals y, x (or y) is the desired result
2. the gcd of two numbers remains unchanged, if we replace the larger number by the difference of the numbers, i.e. subtract the smaller number form the larger one.

1. 如果x等於y，x（或y）就是想要的結果
2. 兩個數的gcd保持不變，如果我們用數的差代替較大的數，即從較大的數中減去較小的數。

Expressed in mathematical terms, these rules take the form

用數學術語表示，這些規則採用以下形式

1. gcd(x, x) = x
2. if x > y, gcd(x, y) = gcd(x-y, y)

The basic recipe, the so-called algorithm, is then the following: Change the numbers x and y according to rule 2 such that their difference decreases. Repeat this until they are equal. Rule 2 guarantees that the changes are such that gcd(x,y) always remains the same, and rule 1 guarantees that we finally find the result.

基本方法，即所謂的算法，如下所示： 根據規則 2 更改數字 x 和 y，使它們的差值減小。 重複此操作直到它們相等。 規則 2 保證 gcd(x,y) 始終保持不變，規則 1 保證我們最終找到結果。

Now we must put these recommendations into terms of Oberon. A first attempt leads to the following sketch. Note that the symbol # means "unequal".

現在我們必須將這些建議放入 Oberon 中。 第一次嘗試導致以下草圖。 請注意，符號# 表示“不相等”。

    WHILE x # y DO
        "apply rule 2, reducing the difference and maintaining x > 0 and y > 0"
    END

The sentence within quotes is plain English. The second version refines the first version by replacing the English by formal terms:

引號內的句子是簡單的英語。 第二個版本通過用正式術語替換英語來完善第一個版本：

    WHILE x # y DO
        IF x > y THEN x := x-y ELSE y := y-x END
    END

This piece of text is not yet a complete program, but it shows already the essential characteristic of a structured programming language. Version 1 is a statement, and this statement contains another, subordinate statement (within quotes). In version 2 this is elaborated, and yet further subordinate statements emerge (expressing the replacement of a value x by another value x-y). This hierarchy of statements expresses the underlying structure of the algorithm. It becomes explicit due to the structure of the language, allowing the nesting of components of a program. It is therefore important to know the language's structure (syntax) in full detail. Textually we express nesting or subordination by appropriate indentation. Although this is not required by the rules of the language, it helps in the understanding of a text very considerably.

這段文字還不是一個完整的程序，但它已經顯示出結構化程序設計語言的本質特徵。 版本 1 是一個語句，這個語句包含另一個從屬語句（在引號內）。 在版本 2 中對此進行了詳細說明，並且出現了更多的從屬語句（表示將值 x 替換為另一個值 x-y）。 這種語句層次結構表達了算法的底層結構。 由於語言的結構，它變得明確，允許嵌套程序的組件。 因此，全面了解語言的結構（語法）非常重要。 在文字上，我們通過適當的縮進來表達嵌套或從屬關係。 雖然這不是語言規則所要求的，但它對理解文本有很大幫助。

Reflecting an algorithm's inherent structure by the textual structure of the program is a key idea of structured programming. It is virtually impossible to recognise the meaning of a program when its structure is removed, such as done by a compiler when producing computer code. And we should keep in mind that a program is worthless, unless it exists in some form in which a human can understand it and gain confidence in its design.

通過程序的文本結構來反映算法的內在結構是結構化編程的一個關鍵思想。 當程序的結構被移除時，幾乎不可能識別程序的含義，例如編譯器在生成計算機代碼時所做的。 我們應該記住，一個程序是沒有價值的，除非它以某種形式存在，人類可以理解它並對它的設計有信心。

We now proceed towards the goal of producing a complete program from the above fragment. We realize that we need to specify an action that assigns initial values to the variables x and y, as well as an action that makes the result visible. For this purpose we should actually know about a computer's facilities to communicate with its user. Since we do not wish to refer to a specific machinery, and particularly not in such a frequent and important case as the generation of output, we introduce abstractions of such communication facilities. These facilities are not directly part of the language, but are procedures declared in some (library) modules, to which all programs have access. We postulate read and write procedures as shown in the following example, and will assume that data are thus read from a keyboard and written on a display.

我們現在朝著從上述片段生成完整程序的目標前進。 我們意識到我們需要指定一個將初始值賦給變量 x 和 y 的動作，以及一個使結果可見的動作。 為此，我們實際上應該了解計算機與其用戶通信的設施。 由於我們不希望提及特定的機器，尤其是在輸出生成這樣頻繁且重要的情況下，我們引入了此類通信設施的抽象概念。 這些設施不直接是語言的一部分，而是在某些（庫）模塊中聲明的過程，所有程序都可以訪問這些過程。 我們假定讀取和寫入過程如下面的示例所示，並假設數據是這樣從鍵盤讀取並寫入顯示器的。

    Texts.Scan(S); x := S.i;
    Texts.Scan(S); y := S.i;
    WHILE x # y DO
        IF x > y THEN x := x-y ELSE y := y-x END
    END;
    Texts.WriteInt(W, x, 6)

The procedure Scan scans an input text and reads a (non-negative) integer (S.i). The procedure WriteInt outputs an integer as specified by its first parameter (x). The second parameter (6) indicates the number of digits available for the representation of this value in the output text. Both procedures are taken from the imported (library) module Texts, and they use a locally declared scanner S and a globally declared writer W, connecting to an input source (the text following the command) and output sink (the Log text) imported from the environment Oberon. Details are explained in Chapter 22 of this tutorial.

Scan 過程掃描輸入文本並讀取一個（非負）整數 (S.i)。 過程 WriteInt 輸出一個由其第一個參數 (x) 指定的整數。 第二個參數 (6) 指示可用於在輸出文本中表示此值的位數。 這兩個程序都取自導入的（庫）模塊文本，它們使用本地聲明的掃描器 S 和全局聲明的寫入器 W，從輸入的輸入源（命令後的文本）和輸出接收器（日誌文本） 連接到Oberon環境。 詳細信息在本教程的第 22 章中進行了解釋。

In the next and final version we complete our text such that it becomes a genuine Oberon text:

在下一個也是最終版本中，我們完成了文本，使其成為真正的 Oberon 文本：

        PROCEDURE Gcd*;
            VAR x, y: INTEGER; S: Texts.Scanner;
        BEGIN Texts.OpenScanner(S, Oberon.Par.text, Oberon.Par.pos);
            Texts.Scan(S); x := S.i; Texts.WriteString(W, " x ="); Texts.WriteInt(W, x, 6);
            Texts.Scan(S); y := S.i; Texts.WriteString(W, " y ="); Texts.WriteInt(W, y, 6);
            WHILE x # y DO
                IF x > y THEN x := x-y ELSE y := y-x END
            END;
            Texts.WriteString(W, " gcd ="); Texts.WriteInt(W, x, 6); Texts.WriteLn(W);
            Texts.Append(Oberon.Log, W.buf)
        END Gcd.

The essential additions in this step are declarations. In Oberon, all names of objects occurring in a program, such as variables and constants, have to be declared. A declaration introduces the object's identifier (name), specifies the kind of the object (whether it is a variable, a constant, or something else) and indicates general, invariant properties, such as the type of a variable or the value of a constant.

此步驟中的基本添加是聲明。 在 Oberon 中，必須聲明程序中出現的所有對象名稱，例如變量和常量。 聲明引入對象的標識符（名稱），指定對象的種類（無論是變量、常量還是其他）並指示一般不變的屬性，例如變量的類型或常量的值 .

The entire piece of text is called a procedure, given a name, and has the following format (see also Ch. 10):

整段文本稱為一個過程，給定一個名稱，並具有以下格式（另請參見第 10 章）：

        PROCEDURE name;
            <declarations>
        BEGIN
            <statements>
        END name


In this and the following examples, a particular property of the Oberon system becomes apparent. Whereas in older languages, the notions of program and executable unit were identical, we distinguish carefully between them in Oberon terminology: What used to be called a program is now called a module, a system unit typically incorporating variables and executable statements resident in a system (see also Ch. 19). Compilers accept a module as a compilable unit of text. An executable unit of program we call a procedure. In the Oberon system, any parameterless procedure can be used as a command, if its name is marked with an asterisk. It can be activated by clicking on its name visible anywhere on the display. A module may contain one or several commands. As a consequence, the preceding and following examples of “programs” appear in the form of procedures (commands), and we will always assume that they are embedded in a module importing two service modules Texts and Oberon and containing the declaration of a writer W for output:

在這個例子和下面的例子中，Oberon 系統的一個特殊屬性變得很明顯。 而在較早的語言中，程序和可執行單元的概念是相同的，我們在 Oberon 術語中仔細區分它們：過去稱為程序的現在稱為模塊，一個系統單元通常包含駐留在系統中的變量和可執行語句 （另見第 19 章）。 編譯器接受模塊作為可編譯的文本單元。 我們稱之為程序的可執行程序單元。 在 Oberon 系統中，任何無參數過程都可以用作命令，只要其名稱標有星號即可。 可以通過單擊顯示屏上任何位置可見的名稱來激活它。 一個模塊可能包含一個或多個命令。 因此，“程序”的前後示例以過程（命令）的形式出現，我們將始終假設它們嵌入在一個模塊中，該模塊導入兩個服務模塊 Texts 和 Oberon，並包含編寫器 W 的聲明 對於輸出：


        MODULE Pattern;
         IMPORT Texts, Oberon;
         VAR W: Texts.Writer;
         PROCEDURE command*; (*such as Gcd*)
         BEGIN ... (*using W for output*) ...
            Texts.Append(Oberon.Log, W.buf)
         END command;
        
        BEGIN Texts,OpenWriter(W)
        END Pattern.


A few more comments concerning our Gcd example are in order. As already mentioned, the procedures WriteLn, WriteString, WriteInt and Scan are not part of the language Oberon itself. They are defined in a module called Texts which is presumed to be available. The often encountered modules Texts, Files and Oberon will be defined and explained in Chapter 22 of this book. Here we merely point out that they need to be imported in order to be known in a program. This is done by including the names of these modules in the import list in the importing module’s heading.        

關於我們的 Gcd 示例的更多評論是有序的。 如前所述，過程 WriteLn、WriteString、WriteInt 和 Scan 不是 Oberon 語言本身的一部分。 它們在一個名為 Texts 的模塊中定義，該模塊被認為是可用的。 本書第22章將對經常遇到的模塊Texts、Files和Oberon進行定義和解釋。 這裡我們只是指出它們需要被導入才能在程序中被識別。 這是通過將這些模塊的名稱包含在導入模塊標題的導入列表中來完成的。

The procedure WriteString outputs a string, i.e. a sequence of characters (enclosed in quotes). The procedure WriteLn inserts a line break in the output text. For further explanations we refer to chapters 22.3 and 22.4 of this book:

WriteString 過程輸出一個字符串，即一個字符序列（用引號引起來）。 WriteLn 過程在輸出文本中插入一個換行符。 進一步的解釋我們參考本書的22.3和22.4章：

And this concludes the discussion of our first example. It has been kept quite informal. This is admissible because the goal was to explain an existing program. However, programming is designing, creating new programs. For this purpose, only a precise, formal description of our tool is adequate. In the next chapter, we introduce a formalism for the precise description of correct, "legal" program texts. This formalism makes it possible to determine in a rigorous manner whether a written text meets the language's rules.

這結束了我們第一個例子的討論。 它一直保持非正式。 這是可以接受的，因為目標是解釋現有程序。 然而，編程就是設計、創造新的程序。 為此，僅對我們的工具進行精確、正式的描述就足夠了。 在下一章中，我們將介紹一種用於精確描述正確的、“合法的”程序文本的形式主義。 這種形式主義使得以嚴格的方式確定書面文本是否符合語言規則成為可能。

## 3. A Notation to Describe the Syntax of Oberon

描述 Oberon 語法的符號

A formal language is an infinite set of sequences of symbols. The members of this set are called sentences, and in the case of a programming language these sentences are programs. The symbols are taken from a finite set called the vocabulary. Since the set of programs is infinite, it cannot be enumerated, but is instead defined by rules for their composition. Sequences of symbols that are composed according to these rules are said to be syntactically correct programs; the set of rules is the syntax of the language.

形式語言是一組無限的符號序列。 該集合的成員稱為句子，在編程語言的情況下，這些句子就是程序。 這些符號取自稱為詞彙表的有限集合。 由於程序集是無限的，因此無法枚舉，而是由組合規則定義。 根據這些規則組成的符號序列被稱為句法正確的程序； 規則集是語言的語法。

Programs in a formal language then correspond to grammatically correct sentences of spoken languages. Every sentence has a structure and consists of distinct parts, such as subject, object, and predicate. Similarly, a program consists of parts, called syntactic entities, such as statements, expressions, or declarations. If a construct A consists of B followed by C, i.e. the concatenation BC, then we call B and C syntactic factors and describe A by the syntactic formula

正式語言的程序然後對應於語法正確的口語句子。 每個句子都有一個結構，由不同的部分組成，例如主語、賓語和謂語。 同樣，程序由稱為句法實體的部分組成，例如語句、表達式或聲明。 如果構造 A 由 B 後跟 C 組成，即串聯 BC，則我們稱 B 和 C 為句法因子，並用句法公式描述 A

        A = BC.

If, on the other hand, an A consists of a B or, alternatively, of a C, we call B and C syntactic terms and express A as

另一方面，如果 A 由 B 或 C 組成，我們稱 B 和 C 為句法項，並將 A 表示為

        A = B | C.

Parentheses may be used to group terms and factors. It is noteworthy that here A, B, and C denote syntactic entities of the formal language to be described, whereas the symbols =, | , parentheses, and the period are symbols of the meta-notation describing syntax. The latter are called meta-symbols, and the meta-notation introduced here is called Extended Backus-Naur Formalism (EBNF).

括號可用於對術語和因素進行分組。 值得注意的是，這裡的 A、B 和 C 表示要描述的形式語言的句法實體，而符號 =、| 、括號和句點是描述語法的元符號的符號。 後者稱為元符號，這裡介紹的元符號稱為擴展巴科斯-諾爾形式主義（EBNF）。

In addition to concatenation and choice, EBNF also allows to express option and repetition. If a construct A may be either a B or nothing (empty), this is expressed as

除了串聯和選擇之外，EBNF 還允許表達選項和重複。 如果構造 A 可以是 B 或什麼都不是（空），則表示為

        A = [B].

and if an A consists of the concatenation of any number of Bs (including none), this is denoted by

如果 A 由任意數量的 B（包括無）串聯組成，則表示為

        A = {B}.

This is all there is to EBNF! A few examples show how sets of sentences are defined by EBNF formulas:

這就是 EBNF 的全部！ 一些示例顯示了 EBNF 公式如何定義句子集：

        (A|B)(C|D)      AC AD BC BD
        A[B]C           ABC AC
        A{BA}           A ABA ABABA ABABABA ...
        {A|B}C          C AC BC AAC ABC BBC BAC ...
        
Evidently, EBNF is itself a formal language. If it suits its purpose, it must at least be able to describe itself! In the following definition of EBNF in EBNF, we use the following names for entities:    

顯然，EBNF 本身就是一種形式語言。 如果它適合它的目的，它至少必須能夠描述自己！ 在EBNF中EBNF的以下定義中，我們對實體使用如下名稱：

        statement:      a syntactic equation
        expression:     a list of alternative terms
        term:           a concatenation of factors
        factor:         a single syntactic entity or a parenthesized expression
        
        statement:      句法等式
        expression:     替代術語列表
        term:           一系列因素
        factor:         單個句法實體或帶括號的表達式

The formal definition of EBNF is now given as follows:

現給出EBNF的正式定義如下：

        syntax =     {statement}.
        statement =  identifier "=" expression ".".
        expression = term {"|" term}.
        term =       factor {factor}.
        factor =     identifier | string | "(" expression ")" | "[" expression "]" | "{" expression "}".
        
Identifiers denote syntactic entities; strings are sequences of symbols taken from the defined language's vocabulary. For the denotation of identifiers we adopt the widely used conventions for programming languages, namely:

標識符表示句法實體； 字符串是從已定義語言的詞彙表中提取的符號序列。 對於標識符的表示，我們採用廣泛使用的編程語言約定，即：

*An identifier consists of a sequence of letters and digits, where the first character must be a letter. A string consists of any sequence of characters enclosed by quote marks (or apostrophes).*

*標識符由一系列字母和數字組成，其中第一個字符必須是字母。 字符串由引號（或撇號）括起來的任意字符序列組成。*

A formal statement of these rules in terms of EBNF is given in the subsequent chapter.

後續章節將根據 EBNF 對這些規則進行正式說明。

## 4. Representation of Oberon Programs

The preceding chapter has introduced a formalism, by which the structures of well-formed programs will subsequently be defined. It defines, however, merely the way in which programs are composed as sequences of symbols, in contrast to sequences of characters. This "shortcoming" is quite intentional: the representation of symbols (and thereby programs) in terms of characters is considered too much dependent on individual implementations for the general level of abstraction appropriate for a language definition. The creation of an intermediate level of representation by symbol sequences provides a useful decoupling between language and ultimate program representation. The latter depends on the available character set. As a consequence, we need to postulate a set of rules governing the representation of symbols as character sequences. The symbols of the Oberon vocabulary are divided into the following classes:

前一章介紹了一種形式主義，隨後將通過這種形式主義來定義格式良好的程序的結構。 然而，與字符序列相比，它僅定義了將程序組合為符號序列的方式。 這個“缺點”是有意為之的：用字符表示符號（以及程序）被認為過於依賴於適合語言定義的一般抽象級別的個別實現。 通過符號序列創建中間級別的表示提供了語言和最終程序表示之間有用的解耦。 後者取決於可用的字符集。 因此，我們需要假設一組規則來管理符號作為字符序列的表示。 Oberon 詞彙表的符號分為以下幾類：

    identifiers, numbers, strings, operators and delimiters, and comments.

The rules governing their representation in terms of the standard ISO character set are the following:

根據標準 ISO 字符集管理它們的表示的規則如下：

1. *Identifiers* are sequences of letters and digits. The first character must be a letter. Capital and lower-case letters are considered as distinct.

1. *標識符*是字母和數字的序列。 第一個字符必須是字母。 大寫字母和小寫字母被認為是不同的。

Examples of well-formed identifiers are

格式良好的標識符的例子是

    Alice likely jump BlackBird SR71

Examples of words which are no identifiers are

沒有標識符的單詞示例是

    sound proof     (blank space is not allowed)
    sound-proof     (neither is a hyphen)
    2N              (first character must be a letter)
    Miller's        (no apostrophe allowed)
    
Sometimes an identifier has to be qualified by another identifier; this is expressed by prefixing i with j and a period (j.i); the combined identifier is called a qualified identifier (abbreviated as qualident). Its syntax is

有時一個標識符必須由另一個標識符限定； 這通過在 i 前加 j 和句點 (j.i) 來表示； 組合標識符稱為合格標識符（縮寫為 qualident）。它的語法是

    qualident = {identifier "."} identifier.

2. *Numbers* are either integers or real numbers. The former are denoted by sequences of digits. Numbers must not include any spaces. Real numbers contain a decimal point and a fractional part. In addition, a scale factor may be appended. It is specified by the letter E and an integer which is possibly preceded by a sign. The E is pronounced as "times 10 to the power of".

數字是整數或實數。 前者由數字序列表示。 數字不得包含任何空格。 實數包含小數點和小數部分。 此外，可以附加比例因子。 它由字母 E 和一個前面可能帶有符號的整數指定。 E 發音為“乘以 10 的次方”

Examples of well-formed numbers are

格式正確的數字的例子是

    1981 1 3.25 5.1E3 4.0E-10
    
Examples of character sequences that are not recognized as numbers are

不被識別為數字的字符序列的例子是

    1,5             no comma may appear
    1'000'000       neither may apostrophs
    3.5En           no letters allowed (except the E)
    
The exact rules for forming numbers are given by the following syntax:

形成數字的確切規則由以下語法給出：

    number = integer | real.
    integer = digit {digit}.
    real = digit {digit} "." {digit} [ScaleFactor].
    ScaleFactor = "E" ["+"|"-"] digit {digit}.

Note: Integers are taken as octal numbers, if followed by the letter B, or as hexadecimal numbers if followed by the letter H.

注意：如果整數後跟字母 B，則整數被視為八進制數；如果後跟字母 H，則整數被視為十六進制數。

3. *Strings* are sequences of any characters enclosed in quote marks. In order that the closing quote
is recognized unambiguously, the string itself evidently cannot contain a quote mark.

*字符串*是用引號括起來的任何字符的序列。 為了使閉合引號被明確識別，字符串本身顯然不能包含引號。

Examples of strings are

字符串的例子是

    "no comment"
    "Buck's Corner"

4. Operators and delimiters are either special characters or reserved words. These latter are written in capital letters and must not be used as identifiers. Hence is it advantageous to memorize this short list of words. The operators and delimiters composed of special characters are

運算符和定界符是特殊字符或保留字。 後者以大寫字母書寫，不得用作標識符。 因此，記住這個簡短的單詞列表是有好處的。 由特殊字符組成的運算符和分隔符是


    +       addition, set union                     加法, 聯集
    -       subtraction, set difference             減法, 差集
    *       multiplication, set intersection        乘法, 交集
    /       division, symmetric set difference      除法, 對稱差      
    :=      assignment
    &       logical AND
    ~       logical NOT
    =       equal
    #       unequal
    <       less than
    >       greater than
    <=      less than or equal
    >=      greater than or equal
    ()      parentheses
    []      index brackets                          索引括號
    {}      set braces                              大括號
    (* *)   comment brackets                        註釋括號
    ^       dereferencing operator                  解引用運算符
    , . ; : .. |    punctuation symbols             標點符號

The reserved words are enumerated in the following list; their meaning will be explained throughout the subsequent chapters:

保留字列舉如下； 它們的含義將在後續章節中解釋：

    ARRAY       BEGIN       BY          CASE
    CONST       DIV         DO          ELSE
    ELSIF       END         FALSE       FOR
    IF          IMPORT      IN          IS
    MOD         MODULE      OF          OR
    POINTER     PROCEDURE   RECORD      REPEAT
    RETURN      SET         THEN        TO
    TRUE        TYPE        UNTIL       VAR
    WHILE

It is customary to separate consecutive symbols by a space , i.e. one or several blanks. However, this is mandatory only in those cases where the lack of such a space would merge the two symbols into one. For example, in "IF x = y THEN" spaces are necessary in front of x and after y, but could be omitted around the equal sign.

通常用空格分隔連續的符號，即一個或幾個空格。 但是，只有在缺少這樣的空間會將兩個符號合併為一個的情況下，這才是強制性的。 例如，在“IF x = y THEN”中，x 之前和 y 之後必須有空格，但等號周圍可以省略。

5. Comments may be inserted between any two symbols. They are arbitrary sequences of characters enclosed in the comment brackets (* and *). Comments are skipped by compilers and serve as additional information to the human reader. They may also serve to signal instructions (options) to the compiler.

可以在任意兩個符號之間插入註釋。 它們是包含在註釋括號（* 和 *）中的任意字符序列。 編譯器會跳過註釋，並作為人類讀者的附加信息。 它們還可以用於向編譯器發出指令（選項）。

## 5. Statements and Expressions

The specification of an action is called a statement. Statements can be interpreted (executed), and that interpretation (execution) has an effect. The effect is a transformation of the state of the computation, the state being represented by the collective values of the program's variables. The most elementary action is the assignment of a value to a variable. The assignment statement has the form

動作的規範稱為語句。 語句可以被解釋（執行），並且解釋（執行）產生效果。 效果是計算狀態的轉換，該狀態由程序變量的集體值表示。 最基本的操作是為變量賦值。 賦值語句具有以下形式

    assignment = designator ":=" expression.

and its corresponding action consists of three parts in this sequence:

且其對應的動作由三部分組成:

1. Evaluate the designator designating a variable.
2. Evaluate the expression yielding a value.
3. Replace the value of the variable identified in 1. by the value obtained in 2.

1. 評估指定變量的指示符。
2. 評估產生一個值的表達式。
3. 將 1. 中標識的變量的值替換為 2. 中獲得的值。

Simple examples of assignments are

賦值的簡單例子是

    i := 1
    x := y+z

Here i obtains the value 1, and x the sum of y and z, and the previous values are lost. Evidently, every variable in an expression must previously have been assigned a value. Observe that the following pairs of statements, executed in sequence, do not have the same effect:

這裡i得到的值是1，x是y和z的和，之前的值都丟失了。 顯然，表達式中的每個變量都必須預先分配了一個值。 請注意，按順序執行的以下成對語句不會產生相同的效果：

    i := i+1; j := 2*i
    j := 2*i; i := i+1

Assuming the initial value i = 0, the first pair yields i = 1, j = 2, whereas the second pair yields j = 0. If we wish to exchange the values of variables i and j, the statement sequence

假設初始值 i = 0，第一對產生 i = 1，j = 2，而第二對產生 j = 0。如果我們希望交換變量 i 和 j 的值，語句序列

    i := j; j := i

will not have the desired effect. We must introduce a temporary value holder, say k, and specify the three consecutive assignments

不會有預期的效果。 我們必須引入一個臨時值持有者，比如 k，並指定三個連續的賦值

    k := i; i := j; j := k

An expression is in general composed of several operands and operators. Its evaluation consists of applying the operators to the operands in a prescribed sequence, in general taking the operators from left to right. The operands may be constants, or variables, or functions. (The latter will be explained in a later chapter.) The identification of a variable will, in general, again require the evaluation of a designator. Here we shall confine our presentation to simple variables designated by an identifier. Arithmetic expressions (there exist other expressions too) involve numbers, numeric variables, and arithmetic operators. These include the basic operations of addition (+), subtraction (-), multiplication (*), and division. They will be discussed in detail in the chapter on basic data types. Here it may suffice to mention that the slash (/) is reserved for dividing real numbers, and that for integers we use the operator DIV which truncates the quotient.

一個表達式通常由幾個操作數和運算符組成。 它的評估包括按規定的順序將運算符應用於操作數，通常從左到右採用運算符。 操作數可以是常量、變量或函數。 （後者將在後面的章節中解釋。）通常，變量的識別將再次需要指示符的評估。 在這裡，我們將把我們的介紹限制在由標識符指定的簡單變量上。 算術表達式（也存在其他表達式）涉及數字、數值變量和算術運算符。 其中包括加法 (+)、減法 (-)、乘法 (*) 和除法的基本運算。 它們將在基本數據類型一章中詳細討論。 這裡可能足以提及斜杠 (/) 是為除實數而保留的，對於整數，我們使用截斷商的運算符 DIV。

An expression consists of consecutive terms. The expression

表達式由連續的項組成。 表達方式

    T0 + T1 + ... + Tn

is equivalent to

相當於

    ((T0 + T1) + ...) + Tn

and is syntactically defined by the rules

並且在句法上由規則定義

    SimpleExpression = ["+"|"-"] term {AddOperator term}.
    AddOperator = "+" | "-" | "OR".

Note: for the time being, the reader may consider the syntactic entities expression and SimpleExpression as equivalent. Their difference and the operators OR, AND, and NOT will be explained in the chapter on the data type BOOLEAN.    

注意：暫時，讀者可以認為句法實體表達式和簡單表達式是等價的。 它們的區別以及運算符 OR、AND 和 NOT 將在數據類型 BOOLEAN 的章節中解釋。

Each term similarly consists of factors. The term

每個術語同樣由因素組成。 項

    F0 * F1 * ... * Fn

is equivalent to

相當於

    ((F0 * F1) * ...) * Fn

and is syntactically defined by the rules

並且在句法上由規則定義

    term = factor {MulOperator factor}.
    MulOperator = "*" | "/" | "DIV" | "MOD" | "&".

Each factor is either a constant, a variable, a function, or an expression itself enclosed by parentheses.    

每個因子要麽是常量、變量、函數，要麽是用括號括起來的表達式本身。

Examples of (arithmetic) expressions are

（算術）表達式的例子是

    2*3+4*5             = (2*3)+(4*5)       = 26
    15 DIV 4 * 4        = (15 DIV 4)*4      = 12
    15 DIV (4*4)        = 15 DIV 16         = 0
    2+3*4-5             = 2+(3*4)-5         = 9
    6.25 / 1.25 + 1.5   = 5.0 + 1.5         = 6.5

The syntax of factors, implying that a factor may itself be an expression, is evidently recursive. The general form of designators will be explained later; here it suffices to know that an identifier denoting a variable or a constant is a designator.

factors 的語法暗示一個 factor 本身可能是一個表達式，顯然是遞歸的。 標識符的一般形式將在後面解釋； 在這裡知道表示變量或常量的標識符是指示符就足夠了。

    factor = number | string | set | designator [ActualParameters] | "(" expression ")" | "~" factor.

The rules governing expressions are actually quite simple, and complicated expressions are rarely used. Nevertheless, we must point out a few basic rules that are well worth remembering.

管理表達式的規則其實很簡單，很少使用複雜的表達式。 然而，我們必須指出一些非常值得記住的基本規則。

1. Every variable in an expression must previously have been assigned a value.
2. Two operators must never be written side by side. For instance a * -b is illegal and must be written as a*(-b).
3. The multiplication sign must never be omitted when a multiplication is required. For example, 2n is illegal and must be written as 2*n.
4. MulOperators are binding more strongly than AddOperators.
5. When in doubt about evaluation rules (i.e. precedence of operators), use additional parentheses to clarify. For example, a + b * c may just as well be written as a+(b*c).

1. 表達式中的每個變量都必須預先分配了一個值。
2. 絕不能並排書寫兩個運算符。 例如 a * -b 是非法的，必須寫成 a*(-b)。
3. 當需要乘法時，絕不能省略乘號。 例如2n是非法的，必須寫成2*n。
4. 乘法運算子 的綁定比 加法運算子 更強。
5. 當對評估規則（即運算符的優先級）有疑問時，使用額外的括號來澄清。 例如，a + b * c 也可以寫成 a+(b*c)

The assignment is but one of the possible forms of statements. Other forms will be introduced in the following chapters. We enumerate these forms by the following syntactic definition

賦值只是陳述的可能形式之一。 其他形式將在後面的章節中介紹。 我們通過以下句法定義來枚舉這些形式

    statement = [ assignment | ProcedureCall | IfStatement | WhileStatement | RepeatStatement | ForStatement ].

Several of these forms are structured statements, i.e. some of their components may be statements again. Hence, the definition of statement is, like that of expressions, recursive.

其中一些形式是結構化語句，即它們的某些組件可能又是語句。 因此，語句的定義與表達式的定義一樣，是遞歸的。

The most basic structure is the sequence. A computation is a sequence of actions, where each action is specified by a statement, and is executed after the preceding action is completed. This strict sequentiality in time is an essential assumption of sequential programming. If a statement S1 follows S0, then we indicate this sequentiality by a semicolon

最基本的結構是序列。 計算是一系列動作，其中每個動作由語句指定，並在前一個動作完成後執行。 這種嚴格的時間順序是順序編程的基本假設。 如果語句 S1 跟在 S0 之後，那麼我們用分號表示這種順序性

    S0; S1

This statement separator (not terminator) indicates that the action specified by S0 is to be followed immediately by the action corresponding to S1. A sequence of statements is syntactically defined as

此語句分隔符（不是終止符）表示 S0 指定的操作將緊跟對應於 S1 的操作。 語句序列在句法上定義為

    StatementSequence = statement {";" statement}.

The syntax of statements implies that a statement may consist of no symbols at all. In this case, the statement is said to be empty and evidently denotes the null action. This curiosity among statements has a definite reason: it allows semicolons to be inserted at places where they are actually superfluous, such as at the end of a statement sequence.

語句的語法意味著語句可能根本不包含任何符號。 在這種情況下，該語句被認為是空的並且顯然表示空動作。 語句之間的這種好奇心有一個明確的原因：它允許在實際上多餘的地方插入分號，例如在語句序列的末尾。

## 6. Control Structures

It is a prime characteristic of computers that individual actions can be selected, repeated, or performed conditionally depending on some previously computed results. Hence the sequence of actions performed is not always identical with the sequence of their corresponding statements. The sequence of actions is determined by control structures indicating repetition, selection, or conditional execution of given statements.

計算機的一個主要特徵是可以根據某些先前計算的結果有條件地選擇、重複或執行各個動作。 因此，執行的動作順序並不總是與其相應語句的順序相同。 動作的順序由指示給定語句的重複、選擇或條件執行的控制結構決定。

### 6.1 Repetitive Statements

The most common situation is the repetition of a statement or statement sequence under control of a condition: the repetition continues as long as the condition is met. This is expressed by the while statement. Its syntax is

最常見的情況是在條件控制下重複語句或語句序列：只要滿足條件，重複就會繼續。 這由 while 語句表示。它的語法是

    WhileStatement = "WHILE" expression "DO" StatementSequence "END".





        

        
        

