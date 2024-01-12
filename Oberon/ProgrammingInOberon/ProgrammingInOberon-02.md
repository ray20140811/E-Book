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

