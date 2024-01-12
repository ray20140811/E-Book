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















        

        
        

