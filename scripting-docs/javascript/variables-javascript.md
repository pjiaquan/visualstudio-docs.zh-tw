---
title: "變數 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "區分大小寫, JavaScript 變數名稱"
  - "強制型轉"
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 變數 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的變數都包含值，例如 "hello" 或 5。  當您使用變數時，就是參考變數表示的資料之意，例如 `NumberOfDaysLeft = EndDate – TodaysDate`。  
  
 您可以使用變數來儲存、擷取和操作出現在程式碼中的值。  請嘗試給予變數具有意義的名稱，讓別人不必太費工夫就能了解您的程式碼。  
  
## 宣告變數  
 變數第一次出現在指令碼中，就是在您宣告變數的時候，  這麼做可以在記憶體內設定變數，往後就能在指令碼中參考使用。  您應該先宣告然後再使用變數，  請利用 `var` 關鍵字宣告變數。  
  
```javascript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 如果您未在 `var` 陳述式中初始化變數，變數會自動使用 `undefined` 做為其值。  
  
## 為變數命名  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 是區分大小寫的語言，  這表示 myCounter 與 MYCounter 這兩個變數名稱是不同的。  變數名稱的長度不限。  有效變數名稱的建立規則如下：  
  
-   第一個字元必須是 ASCII 字母 \(大寫或小寫\) 或底線 \(\_\)，  而不能是數字。  
  
-   接下來的字元必須是字母、數字或底線 \(\_\)。  
  
-   變數名稱一定不能是[保留字](../javascript/reference/javascript-reserved-words.md)。  
  
 以下是一些有效變數名稱的範例：  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 以下是一些無效變數名稱的範例：  
  
```javascript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 當您要宣告變數並將它初始化，但是不希望指派給它任何特定值時，請指派 `null` 值。  請參閱下列範例：  
  
```javascript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 如果您宣告變數而未指派其值時，其值為 `undefined`。  請參閱下列範例：  
  
```javascript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 `null` 值與數字 0 的作用相同，而 `undefined` 則與特定值 `NaN` \(不是數字\) 的作用相同。  如果您比較 `null` 值和 `undefined` 值，會發現這兩個值相等。  
  
 您在宣告中可以不使用 `var` 關鍵字來宣告變數，而且也可以指定變數的值，  這種方式稱為隱含宣告。  
  
```javascript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 您不能使用從未宣告過的變數。  
  
```javascript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## 強制型轉  
 與 C\+\+ 這類強型別語言相反，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 並不會嚴格規定型別。  這表示 JavaScript 的變數型別不會預先決定。  相反地，變數的型別就是其值的型別。  這個行為可讓您將值當做是不同的型別來處理。  
  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，您可以針對不同型別的值執行運算，而不會發生例外狀況。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 解譯器會將其中一種資料型別隱含轉換 \(或「*強制型轉*」\(Coerce\)\) 成其他資料型別，然後再執行運算。  字串、數字和布林值的強制型轉規則如下：  
  
-   如果您合併使用數字和字串，數字會強制型轉為字串。  
  
-   如果您合併使用布林值和字串，布林值會強制型轉為字串。  
  
-   如果您合併使用數字和布林值，布林值會強制型轉為數字。  
  
 在下列範例中，將數字加入至字串會產生字串。  
  
```javascript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 為了進行比較，字串會自動轉換成對等的數字。  若要明確地將字串轉換為整數，請使用 [parseInt 函式](../javascript/reference/parseint-function-javascript.md)。  若要明確地將字串轉換為數字，請使用 [parseFloat 函式](../javascript/reference/parsefloat-function-javascript.md)。