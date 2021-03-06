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

以外語辭典作為根本來命名變數。 舉例來說，用德文的 _punkt_ 來表示 _point_ 。 不熟悉德文的維護程序員，將展開一段多元文化的意義之旅。

#### 用數學命名

選一些變數名稱來偽裝成數學運算子，例如：

```js
openParen = (slash + asterix) / equals;
```

#### 令人困惑的名字

用一些與內含無關的字眼作為變數名稱。 例如：

```js
marypoppins = (superman + starship) / god;
```

This confuses the reader because they have difficulty disassociating the emotional connotations of the words from the logic they're trying to think about.


#### 重新命名與重新利用

這招在 Ada 特別管用，該語言不受標準化的混淆技術給影響。 The people who originally named all the objects and packages you use were morons. 並非要說服他們改變，just use renames and subtypes to rename everything to names of your own devising. 要確保有留下一些舊有名字作參考，讓人覺得是粗心打錯，而實際上是個陷阱。

#### 啥時要用 i

永遠不要用 `i` 作為最內層的迴圈變數。 拿來用在其他用途吧。 大方地把 `i` 用在其他的用途上，尤其是作為非整數的變數，接著把 `n` 拿去作為迴圈索引。

#### Conventions Schmentions

不要遵守 [Sun Java 編碼規範](http://web.archive.org/web/20091003224540/http://java.sun.com/docs/codeconv/)，畢竟， Sun 自己也沒遵守。 幸運地是，編譯器不會因為你違反編碼規範而罷工。 這樣做的目的在於讓變數名稱之間擁有微小的差異。 如果你被逼著遵照大小寫的規範，你仍然可以推翻不明確的含糊地帶，例如：*同時*用 _input**F**ile**n**ame_ 和 _input**f**ile**N**ame_ 。 發明出屬於你自己的絕望又複雜的命名規則，然後幹譙那些沒有遵守的人們。

#### 小寫的 l 和數字的 1 根本就像是兄弟

用小寫的 l 表示長整數常數。 例如： `10l` 比 `10L` 更容易被誤認為是 `101`。 禁止任何能夠清楚分辨 `uvw` 、 `wW` 、 `gq9` 、 `2z` 、 `5s` 、 `il17|!j` 、 `oO08` 、 `` `'" `` 、 `;,.` 、 `m nn rn` 和 `{[()]}` 的字體。 盡量揮灑創意吧！

#### 把全域變數的名稱當做私有變數再利用

在模組 A 宣告一個全域陣列，接著在模組 B 的標頭檔裡面宣告一個同樣名稱的私有變數，這樣一來，就可以讓人以為你在模組 B 裡面正用著全域變數，事實上你一直在用的是相同名稱的私有變數。 不用特別為這個複寫在註解裡面做說明。

#### 回收再利用

用矛盾的方法回收變數，盡可能地混淆命名範圍。 舉例來說，假設你有 `A` 和 `B` 兩個全域變數，以及 `foo` 和 `bar` 兩個函式。 如果你知道 `A` 在正常情況下會被傳到 `foo` ，且 `B` 會被傳到 `bar` ，確保你定義的函式要是 `function foo(B)` 和 `function bar(A)` ，這樣一來，在函式裡面的 `A` 都會是引用 `B` ， `B` 則是一直引用 `A` 。 使用多一點的函式和全域變數時，你可以建立廣大的命名矛盾網路。

#### 回收你的變數

只要規則允許，重新利用已有的變數名稱。 同樣地，為兩個無關的目的使用相同的臨時變數(purporting to save stack slots)。 For a fiendish variant, morph the variable, for example, assign a value to a variable at the top of a very long method, and then somewhere in the middle, change the meaning of the variable in a subtle way, such as converting it from a 0-based coordinate to a 1-based coordinate. Be certain not to document this change in meaning.

#### Cd wrttn wtht vwls s mch trsr

正當在變數或函式名稱中用縮寫時，break the boredom with several variants for the same word, and even spell it out longhand once in while. 這樣有助於擊敗那些使用文字搜尋去理解你程式的部分樣貌的懶惰鬼。 研究一個變體命名的策略，例如：把國際化的 _colour_ 、美式的 _color_ ，以及痞子腔 _kulerz_ 混用。 If you spell out names in full, there is only one possible way to spell each name. 這些對維護的程式設計師來說非常簡單地就能夠記起來。 因為有很多不同的方法去縮寫一個詞，你可以有多個不同的變數都作為同樣顯而易見的目的。 作為額外的好處，維護的程式設計師可能甚至不會注意到它們是單獨的變量。

#### 誤導的名稱

確保每個函式的實作內容都比名稱上來得多一點或少一點。 來個簡單的例子，有個名為 `isValid(x)` 的函式應當有把 `x` 轉成二進制並將結果存入資料庫的功能。

#### 前綴 m_

在 C++ 的世界裡有一種命名規則，就是將 `m_` 作為前綴，加在每個成員前面。 This is supposed to help you tell them apart from methods, so long as you forget that "method" also starts with the letter "m".

#### o_apple obj_apple

在每個類別的每個實例前面加上 "o" 或是 "obj"作為前綴，以顯示你正在思慮著巨大的多型架構。

#### 匈牙利符號

匈牙利符號是原始碼混淆技術中的戰略性核武，用吧！ 由於這種用法玷污了大量的原始碼，沒有什麼比完美計劃好的匈牙利命名攻擊來得更快速打爆維護的程式設計師。 下列的提示將幫助你敗壞匈牙利命名原本的意圖：

 - 在 C++ 和其他語言中，堅持使用 "c" 作為常數，直接強制規定變數裡的常數。

 - Seek out and use Hungarian warts that have meaning in languages other than your current language. 