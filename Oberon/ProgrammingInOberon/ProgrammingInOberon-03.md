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















        

        
        

