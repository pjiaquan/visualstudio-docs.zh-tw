---
title: "撰寫 JavaScript 程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "程式碼, JavaScript 語法"
  - "註解, JavaScript 程式碼"
  - "JavaScript 程式碼"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 撰寫 JavaScript 程式碼
就像許多其他程式語言一樣，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會組織成陳述式，也就是由相關陳述式和註解集合組成的區塊。  您可以在陳述式中使用變數、字串、數字和運算式。  
  
## 陳述式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式是陳述式的集合。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式會結合運算式，結合的方式可讓它們執行一個完整的工作。  
  
 陳述式是由一個或多個運算式、關鍵字或運算子 \(符號\) 所組成。  一般而言，陳述式會在單行撰寫，不過也可以在兩行或多行上撰寫。  此外，兩個或多個陳述式可以在同一行撰寫，只需用分號加以分隔。  一般而言，每個新的一行都是以新的陳述式當做開頭。  明確結束陳述式是很好的作法。  您可利用分號 \(;\) 執行此動作，這就是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式結束字元。  
  
 以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式的兩個範例。  \/\/ 字元之後的句子是「*註解*」\(Comment\)，也就是程式中的說明性備註。  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 以大括號 \({}\) 括住的一組 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式稱為一個「*區塊*」\(Block\)。  分組為區塊的陳述式通常被視為單一陳述式。  這表示在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 預期使用單一陳述式的大多數地方都可以使用區塊。  明顯的例外狀況包括 **for** 和 `while` 迴圈的標頭。  請注意，區塊內的單一陳述式是以分號結束，但是區塊本身並非如此。  
  
 一般來說，區塊會用於函式和條件中。  請注意，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 與 C\+\+ 和部分其他語言不同，它不會將區塊視為新範圍，只有函式會建立新範圍。  
  
 在下列範例中，`else` 子句包含一個區塊，此區塊是由大括號括住的兩個陳述式所組成。  此區塊被視為單一陳述式。  此外，函式本身是由大括號括住的陳述式區塊所組成。  函式底下的陳述式在區塊外面，因此不屬於函式定義的一部分。  
  
```javascript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## 註解  
 單行 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 註解是以一對正斜線 \(\/\/\) 為首。  以下是單行註解的範例。  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 多行 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 註解以一個正斜線和星號 \(\/\*\) 開始，並以相反的順序 \(\*\/\) 結束。  
  
```javascript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  如果您要在一個多行註解中嵌入另一個多行註解，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會以非預期的方式來解譯最後產生的多行註解。  標記所嵌入之多行註解結尾的 \*\/ 符號會被解譯為整個多行註解的結尾。  這表示，緊接在內嵌多行註解後面的文字將不會標記為註解，而是會被解譯為 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式碼，而且將會產生語法錯誤。  
  
 我們建議您將所有的註解寫成單行註解區塊，  這樣稍後您便能將含有多行註解的大量程式碼區段標記為註解。  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## 指派與等號比較  
 等號 \(\=\) 會在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 陳述式中用來指派值給變數：這就是指派運算子。  \= 運算子的左方運算元一定是 Lvalue。  Lvalues 的範例如下：  
  
-   變數、  
  
-   陣列元素、  
  
-   物件屬性。  
  
 \= 運算子右邊的運算元一定是 Rvalue。  Rvalue 可以是任何型別的任意值，包括運算式的值。  以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 指派陳述式的範例。  
  
```javascript  
var anInteger = 3;  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 編譯器會將這個陳述式解譯為如下意義：「指派 3 的值給變數 **anInteger**」或是「**anInteger** 接受 3 的值」。  
  
 請務必了解 \= 運算子 \(指派\) 和 \=\= 運算子 \(等號比較\) 之間的差異。  當您要比較兩個值來查明兩者是否相同時，請使用兩個等號 \(\=\=\)。  這部分會在[控制程式流程](../javascript/controlling-program-flow-javascript.md)中詳細討論。  
  
## 運算式  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 運算式值可以是任何有效的 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 型別 \- 數字、字串、物件等等。  最簡單的運算式是常值。  以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 常值運算式的一些範例。  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 較複雜的運算式可能會包含變數、函式呼叫和其他運算式。  您可以使用運算子來結合運算式，以建立複雜的運算式。  運算子範例如下：`+` \(加法\)、`-` \(減法\)、`*` \(乘法\) 和 `/` \(除法\)。  
  
 以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 複雜運算式的一些範例。  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```