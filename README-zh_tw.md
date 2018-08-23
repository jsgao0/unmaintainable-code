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