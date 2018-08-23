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