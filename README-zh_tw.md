# 如何寫出無法維護的程式碼

## Ensure a job for life ;-)

**Roedy Green**
 [**Canadian Mind Products**](http://mindprod.com/jgloss/unmain.html)

## 介紹

> _永遠不要歸咎於惡意，這可以解釋成無能。_ - Napoleon

為的是要在Java程式設計的領域創造就業機會，I am passing on these tips from the masters on how to write code that is so difficult to maintain, that the people who come after you will take years to make even the simplest changes. 此外，如果你篤信地遵照這些規則，你甚至能確保你一生的工作，因為除了你以外，沒有人能夠維護這些程式碼。 重申一次，如果你篤信地遵照了**全部地**規則，搞不好連你也沒辦法去維護這些程式碼！

你不必過度參考這些規則。 你的程式碼不應該**看起來**無法維護到讓人絕望，適當**去用**就好。 否則它可能會被重寫或重構。

## 基本原則

> _Quidquid latine dictum sit, altum sonatur._
> _- 無論用拉丁語說什麼，聽起來都很微妙。_

為了挫敗維護的程式設計師，你必須了解他怎麼思考。 他有你龐大的程式，但他沒時間去閱讀全部，更別說是理解了。 他想要快速地找到他要改的地方，然後在沒有產生意外的副作用，趕快修改了事。

程式設計師一次只能夠看一丁點你寫的程式碼，就像是用捲筒衛生紙的捲筒在看一樣。 你要確保他永遠做不到。 你要盡可能地讓他難以找到他正在找的程式碼。 But even more important, you want to make it as awkward as possible for him to safely **ignore** anything.

程式設計師們被約定成俗的慣例給哄騙。 但每隔一段時間，通過巧妙地違反慣例，你就會強迫他用放大鏡閱讀每一行程式碼。

你也許會認為每個語言的特性都會使程式碼難以維護；不然，只有適當地誤用才行。

## 命名

> _"When I use a word," Humpty Dumpty said, in a rather scornful tone, "it means just what I choose it to mean - neither more nor less."_
> - Lewis Carroll -- Through the Looking Glass, Chapter 6

撰寫無法維護程式碼絕大部分的技巧，是命名變數以及方法的藝術。 它們對編譯器完全不重要。 且它們給你超大的空間去利用它們使維護的程式設計師搞得一頭霧水。

#### New Uses For <cite>Names For Baby</cite>

去買一本嬰兒命名的書的副本，然後你永遠不會因為命名變數而感到茫然。 Fred 是一個非常棒的名字，而且非常容易打字。 如果你正在找容易打字的變數名稱，如果你打字用的是 DSK 鍵盤，就試試看 `asdf` 或 `aoeu`。

#### 單一字元的變數名稱

如果你把你的變數取名為 `a`、`b`、`c` ，接著它就會讓簡單的文字編輯器沒辦法搜尋到。 此外，沒有人能夠猜出它們是幹嘛的。 如果有人試圖打破 FØRTRAN 使用 `i`、`j`、`k` 作為索引變數的殊榮，請把它們替換成 `ii`、`jj`、`kk` ，嚴正警吿西班牙宗教裁判所當初對異教徒做得一切（異教徒會被處死，參閱[WiKi](https://zh.wikipedia.org/wiki/%E8%A5%BF%E7%8F%AD%E7%89%99%E5%AE%97%E6%95%99%E8%A3%81%E5%88%A4%E6%89%80)）。

#### 富含創意的拼錯字

如果你必須得用具描述性的變數和函式名稱，就把它們拼錯吧！ 藉由拼錯一些函式和變數的名字，並把其他的拼正確（像是 `SetPintleOpening` 和 `SetPintalClosing` ），我們就可以有效地讓 grep 或 IDE 搜尋技術變無效。 它的效果讓人讚不絕口。 再加入一些國際風味的拼字如 theatres/theaters 差異般的 _tory_ or _tori_ ，會更增添韻味。

#### 抽象一點

在命名函式和變數時，重度地使用像是 _it_ 、 _everything_ 、 _data_ 、 _handle_ 、 _stuff_ 、 _do_ 、 _routine_ 、 _perform_ 和數字，例如： `routineX48` 、 `PerformDataFunction` 、 `DoIt` 、 `HandleStuff` 或是 `do_args_method` 等等的抽象字眼。

#### 糸 宿 田 各 言 吾

使用縮略語來保持程式碼的精簡。 真男人不用解釋這些縮寫，因為他們天生就懂得這些字。 

#### 近義詞替代品

To break the boredom, use a thesaurus to look up as much alternate vocabulary as possible to refer to the same action, e.g. _display_, _show_, _present_. 隱約感受到有些微地差異，但實際上並沒有。 不過，如果有兩個類似的函式之前有關鍵差異，則要一直用相同的詞去描述這兩個函式，例如： _print_ 表示「寫入到一個檔案」和「用墨水在紙上列印」。 在任何情況下，都不要為了特定目的的專案編寫明確定義的語彙表。 這樣是不專業的，因為這違反了結構化設計 _資訊隱藏_ 的原則。 

#### 使用其他語言的複數形式

A VMS script kept track of the "statii" returned from various "Vaxen". Esperanto , [Klingon](http://www.kli.org/) and [Hobbitese](http://www.chriswetherell.com/hobbit) qualify as languages for these purposes. For pseudo-Esperanto pluraloj, add oj. You will be doing your part toward world peace.

#### 字詞的音節第一個字母大寫

隨機地把字詞裏頭一個音節中的第一個字母大寫。 例如： `ComputeRasterHistoGram()` （Histo`G`ram）。

#### 重複使用名稱

在程式語言的規則允許下，把類別、建構子、方法、member variables、參數以及區域變數都給相同的名稱。 在 `{}` 區域內重複使用相同的區域變數名稱，是大加分。 這樣做的目的是為了強迫維護的程式設計師去仔細地檢查每個實例中的區塊範圍。 特別說一下 Java ，可以將普通的方法偽裝成建構子。

#### Åccented Letters

Use accented characters on variable names. E.g.

```c
typedef struct { int i; } ínt;
```

where the second ínt's í is actually i-acute. With only a simple text editor, it's nearly impossible to distinguish the slant of the accent mark.

#### 好好地利用編譯器在命名長度上的限制

如果編譯器只能識別第一個部分的命名，像是每個名稱只能有八個字母，你就可以在後面做豐富的變化，例如： `var_unit_update()` 和 `var_unit_setup()` 。 這樣一來，編譯器會把這兩個函式都當作是 `var_unit` 。

#### 我們的好朋友：底線

用 `_` 和 `__` 作為識別符吧！

#### 混合語言

隨意地穿插兩種語言（人類語言或電腦語言）。 如果你的老闆堅持要你用他的語言，你就告訴他你可以用自己的語言好好地組織好你的想法，抑或是，若不起作用，就宣稱他歧視你的語言，並趁機威脅要告他，好好地賺一筆。

#### ASCII 擴充碼

ASCII 擴充的字符完美地適用於變數名稱，包括了 ß 、 Ð 、以及 ñ 。 它們幾乎無法在簡易的編輯器中直接用鍵盤輸入，除非你用複製/貼上。

#### 用其他語言來命名

以外語辭典作為根本來命名變數。 舉例來說，用德文的 _punkt_ 來表示 _point_ 。 不熟悉德文的維護程序員，將開始一段多元文化的意義之旅。