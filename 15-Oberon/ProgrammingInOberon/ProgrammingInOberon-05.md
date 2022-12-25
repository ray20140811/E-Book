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
