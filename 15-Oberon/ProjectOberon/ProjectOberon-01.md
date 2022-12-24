# Project Oberon

## The Design of an Operating System, a Compiler, and a Computer 

## Revised Edition 2013 

Niklaus Wirth 
Jürg Gutknecht 

ISBN 0-201-54428-8 


## Preface

This  book  presents  the  results  of  Project  Oberon,  namely  an  entire  software  environment  for  a  modern  workstation.  The  project  was  undertaken  by  the  authors  in  the  years  1986-89,  and  its  primary  goal  was  to  design  and  implement  an  entire  system  from  scratch,  and  to  structure  it  in  such  a  way  that  it  can  be described,  explained,  and understood  as  a  whole.  In  order  to  become  confronted with all aspects, problems, design decisions and details, the authors not only conceived but also programmed the entire system described in this book, and more. 

本書介紹了 Project Oberon 的成果，即一個完整的軟件環境現代工作站。該項目由作者於 1986-89 年承擔，其主要目標是從頭開始設計和實施整個系統，並將其構建為可以作為一個整體來描述、解釋和理解的方式。為了成為面對方方面面、問題、設計決策和細節，作者不僅構思並編寫了本書中描述的整個系統，等等。

Although  there  exist  numerous  books  explaining  principles  and  structures  of  operating  systems,  there is a lack of descriptions of systems actually implemented and used. We wished not only to give  advice  on  how  a  system  might  be  built,  but  to  demonstrate  how  one  was  built.  Program listings therefore play a key role in this text, because they alone contain the ultimate explanations. The  choice  of  a  suitable  formalism  therefore  assumed  great  importance,  and  we  designed  the  language  Oberon  as  not  only  an  effective  vehicle  for  implementation,  but  also  as  a  publication  medium  for  algorithms  in  the  spirit  in  which  Algol  60  had  been  created  three  decades  ago.  Because  of  its  structure,  the  language  Oberon  is  equally  well  suited  to  exhibit  global,  modular  structures of programmed systems. 

儘管有許多解釋操作系統原理和結構的書籍，缺乏對實際實施和使用的系統的描述。我們不僅希望就如何構建系統提供建議，但要演示系統是如何構建的。程序因此，列表在本文中起著關鍵作用，因為它們本身就包含了最終的解釋。因此，選擇合適的形式主義非常重要，我們設計了Oberon 語言不僅是實施的有效工具，而且還是出版物算法的媒介本著三十年前創建 Algol 60 的精神。由於其結構，Oberon 語言同樣非常適合展示全局的、模塊化的程序化系統的結構。

In spite of the small number of man-years spent on realizing the Oberon System, and in spite of its compactness letting its description fit a single book, it is not an academic toy, but rather a versatile workstation  system  that  has  found  many  satisfied  and  even  enthusiastic  users  in  academia  and  industry.  The  core  system  described  here,  consisting  of  storage,  file,  display,  text,  and  viewer  managers,  of  program  loader  and  device  drivers,  draws  its  major  power  from  a  suitably  chosen,  flexible  set  of  basic  facilities  and,  most  importantly,  of  their  effective  extensibility  in  many  directions  and  for  many  applications.  The  extensibility  is  particularly  enhanced  by  the  language  Oberon  on  the  one,  and  by  the  efficiency  of  the  basic  core  on  the  other  hand.  It  is  rooted  in  the  application  of  the  object-oriented  paradigm  which  is  employed  wherever  extensibility  appears  advantageous. 

儘管花在實現 Oberon 系統上的人年數很少，儘管它的緊湊性讓它的描述適合一本書，它不是學術玩具，而是多才多藝的工作站系統，在學術界和行業。這裡描述的核心系統，由存儲、文件、顯示、文本和查看器組成程序加載器和設備驅動程序的管理器從適當選擇的、一套靈活的基本設施，最重要的是，它們在許多方面的有效擴展性方向和許多應用程序。語言特別增強了可擴展性一方面是 Oberon，另一方面是基本核心的效率。它植根於在可擴展性出現的任何地方都採用面向對象範例的應用有利。

In addition to the core system, we describe in full detail the compiler for the language Oberon and a  graphics  system,  which  both  may  be  regarded  as  applications.  The  former  reveals  how  a  compact  compiler  is  designed  to  achieve  both  fast  compilation  and  efficient,  dense  code.  The  latter  stands  as  an  example  of  extensible  design  based  on  object-oriented  techniques,  and  it  shows  how  a  proper  integration  with  an  existing  text  system  is  possible.  Another  addition  to  the  core system is a network module allowing many workstations to be interconnected. We also show how the Oberon System serves conveniently as the basis for a multi-server station, accommodating a file distribution, a printing, and an electronic-mail facility. 

除了核心系統，我們還詳細描述了 Oberon 語言的編譯器和一個圖形系統，這兩者都可以看作是應用程序。前者揭示瞭如何緊湊型編譯器旨在實現快速編譯和高效、密集的代碼。這後者是基於面向對象技術的可擴展設計的一個例子，它展示了與現有文本系統的正確集成是如何成為可能的。的另一個補充核心系統是一個網絡模塊，允許許多工作站互連。我們還展示Oberon 系統如何方便地作為多服務器站的基礎，提供文件分發、打印和電子郵件功能。

Compactness  and  regular  structure,  and  due  attention  to  efficient  implementation  of  important  details  appear  to  be  the  key  to  economical  software  engineering.  With  the  Oberon  System,  we  wish to refute Reiser's Law, which has been confirmed by virtually all recent releases of operating systems: In spite of great leaps forward, hardware is becoming faster more slowly than software is becoming slower. The Oberon System has required a tiny fraction of the manpower demanded for the  construction  of  widely-used  commercial  operating  systems,  and  a  small  fraction  of  their  demands on computing power and storage capacity, while providing equal power and flexibility to the  user,  albeit  without  certain  bells  and  whistles.  The  reader  is  invited  to  study  how  this  was  possible. 

緊湊和規則的結構，並適當注意重要的有效實施細節似乎是經濟軟件工程的關鍵。有了 Oberon 系統，我們希望反駁 Reiser 定律，幾乎所有最近發布的操作系統都證實了這一點系統：儘管有了很大的飛躍，但硬件的速度比軟件的速度要慢得多變慢。 Oberon 系統只需要一小部分人力廣泛使用的商業操作系統的構建，以及它們的一小部分對計算能力和存儲容量的要求，同時提供同等的能力和靈活性用戶，儘管沒有某些附加功能。請讀者研究這是怎麼回事可能的。

But  most  importantly,  we  hope  to  present  a  worth-while  case  study  of  a  substantial  piece  of  programming in the large for the benefit of all those who are eager to learn from the experiences of others. 

但最重要的是，我們希望提出一個有價值的案例研究為了所有渴望從經驗中學習的人的利益而進行大規模編程別人的。

We wish to thank the many anonymous contributors of suggestions, advice, and encouragement. In particular we wish to thank our colleagues H. Mössenböck and B. Sanders and our associates at the Institut für Computersysteme for reading all or parts of the draft of this book. We are grateful to  M.  Brandis,  R.  Crelier,  A.  Disteli,  M.  Franz,  and  J.  Templ  for  their  work  in  porting  the  Oberon  

我們要感謝許多匿名貢獻者的建議、建議和鼓勵。我們要特別感謝我們的同事 H. Mössenböck 和 B. Sanders 以及我們的同事在 Institut für Computersysteme 閱讀本書的全部或部分草稿。我們很感激感謝 M. Brandis、R. Crelier、A. Disteli、M. Franz 和 J. Templ 在移植 Oberon 方面所做的工作
 
System  successfully  to  various  commercially  available  computers,  and  thus  making  the  study  of  this  book  more  worth-while  for  many  readers.  And  we  gratefully  acknowledge  the  contribution  of  our  school,  ETH,  for  providing  the  environment  and  support  which  made  it  possible  for  us  to  pursue and complete this project. 

系統成功地應用於各種商用計算機，從而使研究這本書更值得許多讀者閱讀。我們非常感謝我們的學校 ETH 提供了環境和支持，使我們能夠追求並完成這個項目。

Zürich, February 1992 
N.W. and J.G.

## Preface to the 2013 edition 

Comments about  plans  to  prepare  a second  edition  to  this  book varied widely.  Some  felt  that  this  book  is  outdated,  that  nobody  is  interested  in  a  system  of  this  kind  any  longer.  "Why  bother"?  Others felt that there is an urgent need for this type of text, which explains an entire system in detail rather than merely proposing strategies and approaches. "By all means"!. Very  much  has  changed  in  these  last  30  years.  But  even  without  this  change,  it  would  be  preposterous  to  propose  and  construct  a  system  competing  with  existing,  worldwide  "standards".  Indeed, very few people would be interested in using it. The community at large seems to be stuck with these gigantic software systems, and helpless against their complexity, their peculiarities, and their occasional unreliability.

關於準備本書第二版的計劃的評論五花八門。有人認為這這本書已經過時了，沒人再對這種系統感興趣了。 “何苦”？其他人覺得迫切需要這種類型的文本，它詳細解釋了整個系統而不僅僅是提出戰略和方法。 “無論如何”！在過去的 30 年裡發生了很大的變化。但即使沒有這種變化，它也會提出和構建一個與現有的全球“標準”競爭的系統是荒謬的。事實上，很少有人會對使用它感興趣。整個社區似乎陷入困境面對這些龐大的軟件系統，卻無力應對它們的複雜性、特性和他們偶爾的不可靠性。

But  surely  new  systems  will  emerge,  perhaps  for  different,  limited  purposes,  allowing  for  smaller  systems. One wonders where their designers will study and learn their trade. There is little technical literature,  and  my  conclusion  is  that  understanding  is  generally  gained  by  doing,  that  is,  "on  the  job".  However,  this  is  a  tedious  and  suboptimal  way  to  learn.  Whereas  sciences  are  governed  by  principles  and  laws  to  be  learned  and  understood,  in  engineering  experience  and  practice  are  indispensable. Does Computer Science teach laws that hold for (almost) ever? More than any other field of engineering, it would be predestined to be based on rigorous mathematical principles. Yet, its core hardly is. Instead, one must rely on experience, that is, on studying sound examples.  

但肯定會出現新的系統，也許是為了不同的、有限的目的，允許更小的系統。人們想知道他們的設計師將在哪裡學習和學習他們的行業。技術含量不高文學，我的結論是，理解通常是通過做來獲得的，也就是說，“在工作”。然而，這是一種乏味且次優的學習方式。而科學是由在工程經驗和實踐中需要學習和理解的原理和規律是必不可少。計算機科學是否教授（幾乎）永遠適用的法則？超過任何其他工程領域，它注定要基於嚴格的數學原理。然而，它的核心幾乎不是。相反，必須依靠經驗，即依靠研究可靠的例子。

The main purpose of and the driving force behind this project is to provide a single book that serves as an example of a system that exists, is in actual use, and is explained in all detail. This task drove home the insight that it is hard to design a powerful and reliable system, but even much harder to make  it  so  simple  and  clear  that  it  can  be  studied  and  fully  understood.  Above  everything  else,  it  requires a stern concentration on what is essential, and the will to leave out the rest, all the popular "bells and whistles". 

這個項目的主要目的和背後的驅動力是提供一本書來服務作為一個存在的系統的例子，在實際使用中，並進行了詳細的解釋。這個任務驅使深入了解設計一個強大而可靠的系統是很困難的，但更難的是使它簡單明了，可以研究和充分理解。最重要的是，它需要嚴格專注於最重要的事情，並願意放棄其餘的一切，所有流行的“鐘聲和口哨聲”。

Recently,  a  growing number  of people has  become  interested  in designing  new,  smaller  systems.  The vast complexity of popular operating systems makes them not only obscure, but also provides opportunities for "back doors". They allow external agents to introduce spies and devils unnoticed by the user, making the system attackable and corruptible. The only safe remedy is to build a safe system anew from scratch. 

最近，越來越多的人開始對設計新的、更小的系統感興趣。流行操作系統的巨大復雜性不僅使它們晦澀難懂，而且還提供了“後門”的機會。他們允許外部代理人在不被注意的情況下引入間諜和魔鬼由用戶，使系統易受攻擊和損壞。唯一安全的補救措施是建立一個安全的系統從頭開始

Turning now to a practical aspect: The largest chapter of the 1992 edition of this book dealt with the compiler translating Oberon programs into code for the NS32032 processor. This processor is now neither available nor is its architecture recommendable. Instead of writing a new compiler for some other commercially available architecture, I decided to design my own in order to extend the desire for simplicity and regularity to the hardware. The ultimate benefit of this decision is not only that the software, but also the hardware of the Oberon System is described completely and rigorously. The processor is called RISC. The hardware modules are decribed exclusively in the language Verilog. 

現在轉向實踐方面：本書 1992 年版中最大的一章涉及編譯器將 Oberon 程序翻譯成適用於 NS32032 處理器的代碼。這個處理器現在既不可用也不推薦其架構。而不是為某些人編寫新的編譯器其他商用架構，我決定設計自己的架構以擴展願望為了硬件的簡單性和規律性。這一決定的最終好處不僅在於軟件，以及 Oberon 系統的硬件都得到了完整而嚴格的描述。這處理器稱為 RISC。硬件模塊僅使用 Verilog 語言進行描述。

The decision for a new processor was expedited by the possibility to implement it, that is, to make it concrete and available. This is due to the advent of programmable gate arrays (FPGA), allowing to turn a design into a real, functioning processor on a single chip. As a result, the described system can  be  realized  using  a  low-cost  development  board.  This  board,  Xilinx  Spartan-3  by  Digilent,  features a 1-MByte static memory, which easily accommodates the entire Oberon System, incuding its compiler. It is shown, together with a display, a keyboard and a mouse in the photo below. The board is visible in the lower, right corner. 

實施它的可能性加快了對新處理器的決定，也就是說，使它具體的和可用的。這是由於可編程門陣列 (FPGA) 的出現，允許在單個芯片上將設計轉變為真正的功能處理器。結果，所描述的系統可以使用低成本的開發板來實現。這個板，Digilent 的 Xilinx Spartan-3，具有 1 兆字節的靜態內存，可輕鬆容納整個 Oberon 系統，包括它的編譯器。它與顯示器、鍵盤和鼠標一起顯示在下面的照片中。這板在右下角可見。

The  decision  to  develop  our  own  processor  required  that  the  chapters  on  the  compiler  and  the  linking  loader  had  to  be  completely  rewritten.  However,  it  also  provided  the  welcome  chance  to  improve their clarity considerably. The new processor indeed allowed to simplify and straighten out the entire compiler. 

開發我們自己的處理器的決定需要關於編譯器和鏈接加載程序必須完全重寫。然而，它也提供了一個受歡迎的機會大大提高他們的清晰度。新處理器確實允許簡化和理順整個編譯器。

For a description of a system to be comprehensible, the key element is the notation, formalism, or language  in  which  it  is  defined.  Algol  60,  published  50  years  ago,  was  proposed  as  a  publication  language,  as  a  formalism  in  which  algorithms  could  be  defined  without  reference  to  particular  computers,  or  to  any  mechanism  at  all.  This  was  a  great  goal,  but  so  far  it  was  hardly  achieved.  Yet, it emphasized the importance of abstraction to be achieved by a notation with a mathematically rigorous foundation. At least, Algol was the first language based on a formally defined syntax. Algol was the result of the early recognition that programs must never be written just to feed computers, but always to be understood and to be instructive to people. 

為了使系統的描述易於理解，關鍵要素是符號、形式主義或定義它的語言。 50年前出版的Algol 60，被提議作為出版物語言，作為一種形式主義，在這種形式主義中，可以在不參考特定的情況下定義算法計算機，或任何機制。這是一個偉大的目標，但到目前為止還很難實現。然而，它強調了通過具有數學意義的符號來實現抽象的重要性嚴謹的基礎。至少，Algol 是第一種基於正式定義語法的語言。Algol是早期認識到程序絕不能僅僅為了餵養計算機而編寫的結果，但總是要被人們理解和啟發。

In  all  my  past  work,  I  have  tried  to  design  a  successor  to  Algol,  that  improves  its  rigor  and  at  the  same  time  extends  its  applicability  from  numerical  algorithms  to  software  systems.  From  a  long  sequence,  starting  with  Algol,  through  Pascal,  Modula,  and  Oberon,  we  have  come  closer  to  this  goal than ever before, and closer than any other language in existence. The key lay in a continued struggle for sensible simplification. 

在我過去的所有工作中，我都試圖設計一個 Algol 的繼任者，它提高了它的嚴謹性和同時將其適用性從數值算法擴展到軟件系統。從長序列，從 Algol 開始，通過 Pascal、Modula 和 Oberon，我們已經接近這個比以往任何時候都更接近目標，比現有的任何其他語言都更接近目標。關鍵在於持續為合理的簡化而奮鬥。

The  Oberon  language,  defined  in  1988,  underwent  a  revision  in  2007,  mostly  discarding  features  that were either duplications or not essential. Adaptation of the system's source code to the revised language was, besides the change of processor, the second important reason for numerous, local changes in this text. We summarize the various deletions of features: 

1988 年定義的 Oberon 語言在 2007 年進行了一次修訂，主要捨棄了一些特性那要么是重複的，要么不是必需的。使系統的源代碼適應修訂版除了處理器的變化之外，語言是許多地方的第二個重要原因此文本的更改。我們總結了特徵的各種刪除：

1. The data types LONGINT, SHORTINT, and LONGREAL have been discarded, and with them the concept of type inclusion. 
2. The LOOP and EXIT statements (repetitions with multiple exit points) have been discarded. 
3. The WITH statement (regional type guard) has been discarded.
4. The RETURN statement has been discarded and is now syntactically merged with the ending of function procedure declarations. 
5. Objects declared in a procedure P are not accessible within a procedure Q that is itself local to P. That is, objects must be either strictly local or global in order to be accessible. 
6. Assignments to imported variables are not permitted  (read-only export). 
7. Forward procedure declarations have been discarded. 

1. 數據類型 LONGINT、SHORTINT 和 LONGREAL 已被丟棄，並且與它們一起類型包含的概念。
2. LOOP 和 EXIT 語句（具有多個退出點的重複）已被丟棄。
3. WITH 語句（區域類型保護）已被丟棄。
4. RETURN 語句已被丟棄，現在在句法上與結尾合併函數過程聲明。
5. 在過程 P 中聲明的對象在過程 Q 中不可訪問，該過程本身對於 P 是本地的。也就是說，對象必須是嚴格本地的或全局的才能被訪問。
6. 不允許對導入的變量賦值（只讀導出）。
7. 向前過程聲明已被丟棄。

In  contrast  to  these removals,  there  is a  single  addition  (made  in 2012):  The  data  type  BYTE  has  been  added.  Its  values  are  integers  x  satisfying    0  ≤  x  <  256.  This  addition  prevents  the  frequent  abuse of the type CHAR. The type BYTE is mainly used for elements of arrays and records in low-level modules in order to economise the use of memory. 

與這些刪除相比，有一個添加（2012 年製作）：數據類型 BYTE 具有已添加。它的值是滿足 0 ≤ x < 256 的整數 x。這種加法防止了頻繁的濫用 CHAR 類型。 BYTE 類型主要用於數組元素和低級記錄模塊，以節省內存的使用。

In spite of these two reasons for changes -- one at the highest level, the language, the other at the lowest,  the  hardware  --  the  remainder  of  the  book  proved  to  be  pretty  stable  and  still  valid.  It  has  been my desire to present the system essentially as it existed 25 years ago, without embellishments.  The  chapters  3  -  5  on  tasking,  the  display  and  the  text,  originally  written  by  J.  Gutknecht,  have  been  carried  over  virtually  unchanged.  Significant  changes,  however,  were  necessary mainly in the descriptions of device drivers for keyboard and mouse. They now use the PS-2  interface  standard.  The  disk  has  been  replaced  by  a  single  SD-card  (flash  memory)  with  a  standard  SPI  interface.  The  interface  to  the  net  no  longer  uses  the  RS-485  interface,  but  is  also  based on the SPI standard. The chapters on the compiler and the linker are completely new. 

儘管有這兩個改變的原因——一個在最高層，語言，另一個在最低的是硬件——本書的其餘部分被證明是相當穩定且仍然有效的。它有我的願望是從本質上呈現 25 年前存在的系統，而不點綴。關於任務分配、顯示和文本的第 3 - 5 章，最初由 J.Gutknecht，幾乎沒有改變。然而，重大變化是必要的主要是在鍵盤和鼠標的設備驅動程序的描述中。他們現在使用PS-2接口標準。磁盤已被單個 SD 卡（閃存）取代標準SPI接口。網絡接口不再使用 RS-485 接口，而是基於SPI標準。關於編譯器和鏈接器的章節是全新的。

Mostly thanks to the regularity of the RISC instruction set, the size of the compiler could be reduced significantly.  It  now  measures  less  than  2900  lines  of  program  and  compiles  itself  in  about  3 seconds, which is proof of its efficiency. The entire system compiles itself in less than 10 seconds. 

主要歸功於 RISC 指令集的規律性，可以減少編譯器的大小顯著地。它現在測量不到 2900 行程序並在大約 3 秒鐘內自行編譯，這是其效率的證明。整個系統在不到 10 秒的時間內自行編譯。

Considered  extravagant  and  hardly  necessary  only  years  ago,  run-time  checks  are  generated  automatically. In particular, they cover index range checks and access to NIL-pointers. Due to their efficiency they hardly affect run-time speed, but are a great benefit to programmers. 

僅在幾年前被認為是奢侈且幾乎沒有必要的，生成運行時檢查自動地。特別是，它們涵蓋了索引範圍檢查和對 NIL 指針的訪問。由於他們的efficiency 它們幾乎不影響運行時的速度，但是對程序員有很大的好處。

A  welcome consequence of  the simplifications of  language  and  processor  is  the  fact  that  all  parts that had been written in assembler code in 1992  -- and therefore were not included in the book -- have now been expressed in Oberon as well. Vindicating my perennial efforts to obtain a high-level language which is powerful and flexible, and also efficient enough to express parts such as device drivers and raster operations, this was the necessary and final step to make this book comprehensive and complete. 

語言和處理器簡化的一個受歡迎的結果是所有部分那是在 1992 年用彙編代碼編寫的——因此沒有包含在本書中——現在也已在 Oberon 中表達。證明我為獲得高水平的長期努力強大而靈活的語言，並且足夠高效地表達設備等部件驅動程序和光柵操作，這是製作本書的必要和最後一步全面而完整。

### References 

http://www.inf.ethz.ch/personal/wirth/Oberon/Oberon07.Report.pdf 
http://www.inf.ethz.ch/personal/wirth/FPGA-relatedWork/RISC.Arch.pdf 

## Acknowledgements 

I  gratefully  acknowledge  the  valuable  contributions  of  Paul  Reed.  He  designed  the  interfaces  to various  devices,  such  as  the  PS-2  and  SPI,  including  the  SD-card,  acting  as  disk  store.  He suggested  many  improvements  and  simplifications.  He  originally  decisively  suggested  a  re-edition of this book of 30 year ago, and was the key impetus to do all this work. My thanks go to him. 

Niklaus Wirth,  September 2013 

致謝

我非常感謝 Paul Reed 的寶貴貢獻。他設計的接口是各種設備，如 PS-2 和 SPI，包括 SD 卡，充當磁盤存儲。他建議了許多改進和簡化。他本來就果斷建議重版30 年前的這本書，是完成所有這些工作的主要動力。我要感謝他。

Niklaus Wirth，2013 年 9 月

## 1 History and motivation

How could anyone diligently concentrate on his work on an afternoon with such warmth, splendid sunshine, and blue sky. This rhetorical question was one I asked many times while spending a sabbatical leave in California in 1985. Back home everyone would feel compelled to profit from the sunny spells to enjoy life at leisure in the country-side, wandering or engaging in one's favourite sport. But here, every day was like that, and giving in to such temptations would have meant the end of all work. And, had I not chosen this location in the world because of its inviting, enjoyable climate?

如此溫暖、燦爛的午後，誰能專心致志地工作呢？ 陽光，和藍天。這個反問是我花一個小時問過很多次的問題1985 年在加利福尼亞休假。回到家裡，每個人都會覺得有必要從中獲利陽光燦爛的日子可以在鄉村享受悠閒的生活，流浪或從事自己喜歡的事情運動。但是在這裡，每一天都是這樣，屈服於這樣的誘惑就意味著所有工作結束。而且，如果我沒有選擇世界上的這個地方，是因為它誘人、令人愉快氣候？

Fortunately, my work was also enticing, making it easier to buckle down. I had the privilege of sitting in front of the most advanced and powerful workstation anywhere, learning the secrets of perhaps the newest fad in our fast developing trade, pushing colored rectangles from one place of the screen to another. This all had to happen under strict observance of rules imposed by physical laws and by the newest technology. Fortunately, the advanced computer would complain immediately if such a rule was violated, it was a rule checker and acted like your big brother, preventing you from making steps towards disaster. And it did what would have been impossible for oneself, keeping track of thousands of constraints among the thousands of rectangles laid out. This was called computer-aided design. "Aided" is rather a euphemism, but the computer did not complain about the degradation of its role.

幸運的是，我的工作也很誘人，讓我更容易屈服。我有幸坐在任何地方最先進、最強大的工作站前，學習也許是我們快速發展的行業中的最新時尚，從一個地方推出彩色矩形屏幕到另一個。這一切都必須在嚴格遵守物理規則的情況下發生法律和最新技術。幸運的是，先進的計算機會報錯如果違反了這樣的規則，它會立即成為規則檢查器並像你的大哥一樣行事，阻止你走向災難。它做到了對人來說不可能的事自己，跟踪佈置的數千個矩形中的數千個約束。這個被稱為計算機輔助設計。 “輔助”是一種委婉的說法，但計算機卻沒有抱怨其角色的退化。

While my eyes were glued to the colorful display, and while I was confronted with the evidence of my latest inadequacy, in through the always open door stepped my colleague (JG). He also happened to spend a leave from duties at home at the same laboratory, yet his face did not exactly express happiness, but rather frustration. The chocolate bar in his hand did for him what the coffee cup or the pipe does for others, providing temporary relaxation and distraction. It was not the first time he appeared in this mood, and without words I guessed its cause. And the episode would reoccur many times.

當我的眼睛盯著五顏六色的顯示屏時，當我面對著我最近的不足之處是，我的同事 (JG) 踏進了永遠敞開的大門。他還碰巧在同一個實驗室休假在家，但他的臉並沒有完全表達快樂，而不是沮喪。他手裡的巧克力棒對他來說就像咖啡一樣杯子或煙斗對其他人有用，提供暫時的放鬆和分散注意力。這不是第一個有一次他出現這種情緒，我不用言語就猜到了原因。而這一集會重複多次。

His days were not filled with the great fun of rectangle-pushing; he had an assignment. He was charged with the design of a compiler for the same advanced computer. Therefore, he was forced to deal much more closely, if not intimately, with the underlying software system. Its rather frequent failures had to be understood in his case, for he was programming, whereas I was only using it through an application; in short, I was an end-user! These failures had to be understood not for purposes of correction, but in order to find ways to avoid them. How was the necessary insight to be obtained? I realized at this moment that I had so far avoided this question; I had limited familiarization with this novel system to the bare necessities which sufficed for the task on my mind.

他的日子裡並沒有充滿推矩形的樂趣；他有一項任務。他是負責為同一台高級計算機設計編譯器。因此，他被迫與底層軟件系統更密切地（如果不是親密地）打交道。它相當頻繁必須在他的案例中理解失敗，因為他正在編程，而我只是在使用它通過申請；簡而言之，我是最終用戶！必須理解這些失敗，而不是為了糾正的目的，但為了找到避免它們的方法。必要的洞察力如何獲得？這一刻我意識到我到目前為止一直在迴避這個問題；我有限制熟悉這個新系統到足以完成我心目中的任務的基本必需品。

It soon became clear that a study of the system was nearly impossible. Its dimensions were simply awesome, and documentation accordingly sparse. Answers to questions that were momentarily pressing could best be obtained by interviewing the system's designers, who all were in-house. In doing so, we made the shocking discovery that often we could not understand their language. Explanations were fraught with jargon and references to other parts of the system which had remained equally enigmatic to us.

很快就很清楚，對該系統的研究幾乎是不可能的。它的尺寸很簡單太棒了，因此文檔很少。暫時回答的問題最好通過採訪系統的設計師來獲得壓力，他們都是內部人員。在這樣做之後，我們驚奇地發現，我們常常聽不懂他們的語言。解釋充滿了行話和對系統其他部分的引用對我們來說仍然同樣神秘。

So, our frustration-triggered breaks from compiler construction and chip design became devoted to attempts to identify the essence, the foundations of the system's novel aspects. What made it different from conventional operating systems? Which of these concepts were essential, which ones could be improved, simplified, or even discarded? And where were they rooted? Could the system's essence be distilled and extracted, like in a chemical process?

因此，我們從編譯器構造和芯片設計中因挫折而中斷，轉而專注於試圖確定本質，系統新穎方面的基礎。是什麼造就了它與傳統操作系統不同？這些概念中哪些是必不可少的，哪些可以改進、簡化甚至丟棄嗎？他們在哪里扎根？可以系統的本質被蒸餾和提取，就像在化學過程中一樣？

During the ensuing discussions, the idea emerged slowly to undertake our own design. And suddenly it had become concrete. "Crazy" was my first reaction, and "impossible". The sheer amount of work appeared as overwhelming. After all, we both had to carry our share of teaching duties back home. But the thought was implanted and continued to occupy our minds.

在隨後的討論中，慢慢產生了我們自己設計的想法。和突然間它變得具體了。 “瘋了”是我的第一反應，“不可能”。 純粹的大量的工作似乎是壓倒性的。畢竟，我們都必須承擔自己的教學責任回家的任務。但是這個想法被植入並繼續佔據我們的思想。

Sometime thereafter, events back home suggested that I should take over the important course about System Software. As it was the unwritten rule that it should primarily deal with operating system principles, I hesitated. My scruples were easily justified: After all I had never designed such a system nor a part of it. And how can one teach an engineering subject without first-hand experience?

此後的某個時候，國內發生的事件表明我應該接手重要的課程關於系統軟件。因為這是不成文的規定，它應該主要處理操作系統原理，我猶豫了。我的顧慮很容易被證明：畢竟我從來沒有設計過這樣的一個系統，也不是它的一部分。沒有第一手資料，如何教授工程學科經驗？

Impossible? Had we not designed compilers, operating systems, and document editors in small teams? And had I not repeatedly experienced that an inadequate and frustrating program could be programmed from scratch in a fraction of source code used by the original design? Our brain-storming continued, with many intermissions, over several weeks, and certain shapes of a system structure slowly emerged through the haze. After some time, the preposterous decision was made: we would embark on the design of an operating system for our workstation (which happened to be much less powerful than the one used for my rectangle-pushing) from scratch.

不可能的？如果我們沒有設計小型的編譯器、操作系統和文檔編輯器團隊？如果我沒有反復經歷過一個不充分和令人沮喪的程序可能會使用原始設計使用的一小部分源代碼從頭開始編程？我們的大腦——暴風雨持續，有許多間歇，持續數週，並且系統的某些形狀結構在陰霾中緩緩出現。一段時間後，做出了荒謬的決定：我們將著手為我們的工作站設計一個操作系統（碰巧是比用於我的矩形推的那個）從頭開始強大得多。

The primary goal, to personally obtain first-hand experience, and to reach full understanding of every detail, inherently determined our manpower: two part-time programmers. We tentatively set our time-limit for completion to three years. As it later turned out, this had been a good estimate; programming was begun in early 1986, and a first version of the system was released in the fall of 1988.

主要目標，親自獲得第一手經驗，並充分了解每一個細節，都從本質上決定了我們的人手：兩個兼職程序員。我們暫定我們的完成時限為三年。後來證明，這是一個很好的估計。編程於 1986 年初開始，該系統的第一個版本於 2018 年秋季發布1988.

Although the search for an appropriate name for a project is usually a minor problem and often left to chance and whim of the designers, this may be the place to recount how Oberon entered the picture in our case. It happened that around the time of the beginning of our effort, the space probe Voyager made headlines with a series of spectacular pictures taken of the planet Uranus and of its moons, the largest of which is named Oberon. Since its launch I had considered the Voyager project as a singularly well-planned and successful endeavor, and as a small tribute to it I picked the name of its latest object of investigation. There are indeed very few engineering projects whose products perform way beyond expectations and beyond their anticipated lifetime; mostly they fail much earlier, particularly in the domain of software. And, last but not least, we recall that Oberon is famous as the king of elfs.

雖然為項目尋找合適的名稱通常是一個小問題，而且經常被遺忘出於偶然和設計師的心血來潮，這可能是講述 Oberon 如何進入我們案例中的圖片。碰巧在我們開始努力的時候，太空探測器航海者號拍攝了一系列天王星及其周圍壯觀的照片，成為頭條新聞衛星，其中最大的一顆被命名為 Oberon。自推出以來，我一直在考慮 Voyager項目作為一個精心策劃和成功的努力，作為對它的一個小小的致敬，我選擇了其最新調查對象的名稱。確實很少有工程項目產品的性能超出預期並超出其預期壽命；他們大多失敗了更早，特別是在軟件領域。最後但同樣重要的是，我們記得 Oberon 是有名的精靈之王。

The consciously planned shortage of manpower enforced a single, but healthy, guideline: Concentrate on essential functions and omit embellishments that merely cater to established conventions and passing tastes. Of course, the essential core had first to be recognized and crystallized. But the basis had been laid. The ground rule became even more crucial when we decided that the result should be able to be used as teaching material. I remembered C.A.R. Hoare's plea that books should be written presenting actually operational systems rather than half-baked, abstract principles. He had complained in the early 1970s that in our field engineers were told to constantly create new artifacts without being given the chance to study previous works that had proven their worth in the field. How right was he, even to the present day!

有意識地計劃的人力短缺強制執行了一個單一但健康的指導方針：專注於基本功能並省略僅迎合既定功能的裝飾慣例和過時的口味。當然，本質核心必須首先被認可和結晶。但基礎已經奠定。當我們決定結果應該可以用作教材。我記得 C.A.R.Hoare 的請求是，應該編寫書籍來展示實際可操作的系統，而不是半烘焙的抽象原則。他在 20 世紀 70 年代初曾抱怨說，我們的現場工程師被告知要不斷創造新的人工製品，而沒有機會研究以前的作品已經在戰場上證明了自己的價值。直到今天，他是多麼正確！

The emerging goal to publish the result with all its details let the choice of programming language appear in a new light: it became crucial. Modula-2 which we had planned to use, appeared as not quite satisfactory. Firstly, it lacked a facility to express extensibility in an adequate way. And we had put extensibility among the principal properties of the new system. By "adequate" we include machine-independence. Our programs should be expressed in a manner that makes no reference to machine peculiarities and low-level programming facilities, perhaps with the exception of device interfaces, where dependence is inherent.

發布結果及其所有細節的新興目標讓編程語言的選擇以新的眼光出現：它變得至關重要。我們計劃使用的 Modula-2 似乎不是比較滿意。首先，它缺乏以適當方式表達可擴展性的工具。我們有將可擴展性列為新系統的主要屬性。通過“足夠”，我們包括機器獨立性。我們的節目應該以一種沒有參考的方式表達機器特性和低級編程設施，也許除了設備接口，其中依賴是固有的。

Hence, Modula-2 was extended with a feature that is now known as type extension. We also recognized that Modula-2 contained several facilities that we would not need, that do not genuinely contribute to its power of expression, but at the same time increase the complexity of the compiler. But the compiler would not only have to be implemented, but also to be described, studied, and understood. This led to the decision to start from a clean slate also in the domain of language design, and to apply the same principle to it: concentrate on the essential, purge the rest. The new language, which still bears much resemblance to Modula-2, was given the same name as the system: Oberon [1, 2]. In contrast to its ancestor it is terser and, above all, a significant step towards expressing programs on a high level of abstraction without reference to machine-specific features.

因此，Modula-2 被擴展了一個現在稱為類型擴展的特性。我們也認識到 Modula-2 包含一些我們不需要的設施，它們並不真正有助於其表達能力，但同時增加了編譯器的複雜度。但是編譯器不僅要被實現，還要被描述、研究和使用。明白了。這導致決定在語言領域也從頭開始設計，並對其應用相同的原則：專注於本質，清除其餘部分。新的仍然與 Modula-2 非常相似的語言被賦予了與 Modula-2 相同的名稱系統：Oberon [1, 2]。與它的祖先相比，它更簡潔，最重要的是，這是一個重要的步驟在不參考特定於機器的情況下在高抽象層次上表達程序特徵。

We started designing the system in late fall 1985, and programming in early 1986. As a vehicle we used our workstation Lilith and its language Modula-2. First, a cross-compiler was developed, then followed the modules of the inner core together with the necessary testing and down-loading facilities. The development of the display and the text system proceeded simultaneously, without the possibility of testing, of course. We learned how the absence of a debugger, and even more so the absence of a compiler, can contribute to careful programming.

我們於 1985 年秋末開始設計系統，並於 1986 年初開始編程。作為一個載體，我們使用我們的工作站 Lilith 及其語言 Modula-2。首先，開發了一個交叉編譯器，然後遵循內核的模塊以及必要的測試和下載設施。顯示和文本系統的開發同時進行，沒有當然，測試的可能性。我們了解瞭如何缺少調試器，甚至更多沒有編譯器，有助於仔細編程。

Thereafter followed the translation of the compiler into Oberon. This was swiftly done, because the original had been written with anticipation of the later translation. After its availability on the target computer Ceres, together with the operability of the text editing facility, the umbilical cord to Lilith could be cut off. The Oberon System had become real, at least its draft version. This happened around the middle of 1987; its description was published thereafter [3], and a manual and guide followed in 1991 [5].

此後，編譯器將其翻譯成 Oberon。這很快就完成了，因為原文是在期待後來的翻譯的情況下寫的。在目標上可用之後計算機 Ceres，連同文本編輯工具的可操作性，是 Lilith 的臍帶可以被切斷。 Oberon 系統已經成為現實，至少是它的草稿版本。這發生過大約在 1987 年中期；隨後出版了它的描述 [3]，以及一本手冊和指南隨後於1991年[5]。

The system's completion took another year and concentrated on connecting the workstations in a network for file transfer [4], on a central printing facility, and on maintenance tools. The goal of completing the system within three years had been met. The system was introduced in the middle of 1988 to a wider user community, and work on applications could start. A service for electronic mail was developed, a graphics system was added, and various efforts for general document preparation systems proceeded. The display facility was extended to accommodate two screens, including color. At the same time, feedback from experience in its use was incorporated by improving existing parts. Since 1989, Oberon has replaced Modula-2 in our introductory programming courses.

該系統的完成又花了一年時間，並專注於將工作站連接成一個用於文件傳輸 [4] 的網絡、中央打印設施和維護工具。三年內完成該系統已達標。中間介紹了系統1988 年到更廣泛的用戶社區，應用程序的工作可以開始。電子服務開發了郵件，添加了圖形系統，並為通用文檔做出了各種努力準備系統進行。顯示設施被擴展以容納兩個屏幕，包括顏色。同時，其使用經驗的反饋被納入改進現有零件。自 1989 年以來，Oberon 在我們的介紹性產品中取代了 Modula-2編程課程。

### References

1. N. Wirth. The programming language Oberon. Software - Practice and Experience 18, 7, (July 1988) 671-690.
2. M. Reiser and N. Wirth. Programming in Oberon - Steps beyond Pascal and Modula. Addison-Wesley, 1992.
3. N. Wirth and J. Gutknecht. The Oberon System. Software - Practice and Experience, 19, 9 (Sept. 1989), 857-893.
4. N. Wirth. Ceres-Net: A low-cost computer network. Software - Practice and Experience, 20, 1 (Jan. 1990), 13-24.
5. M. Reiser. The Oberon System - User Guide and Programmer's Manual. Addison-Wesley, 1991.