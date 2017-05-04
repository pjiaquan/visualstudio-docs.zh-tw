---
title: "資料類型 (JavaScript) | Microsoft Docs"
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
  - "Boolean 資料類型, 支援的資料類型"
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# 資料類型 (JavaScript)
在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中有三個主要資料類型、兩個複合資料類型和兩個特殊資料類型。  
  
## 主要資料類型  
 主要 \(基本\) 資料類型如下：  
  
-   字串  
  
-   數字  
  
-   Boolean  
  
## 複合資料類型  
 複合 \(參考\) 資料類型如下：  
  
-   物件  
  
-   陣列  
  
## 特殊資料類型  
 特殊資料類型如下：  
  
-   Null  
  
-   未定義  
  
## 字串資料類型  
 字串值是一串零個以上的 Unicode 字元 \(字母、數字和標點符號\)。  您可使用字串資料類型來表示 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的文字。  您可以用一對單引號或雙引號括住字串常數，將其加入至指令碼中。  雙引號可以包含在由單引號包圍的字串內，而單引號可以包含在由雙引號包圍的字串內。  以下是字串的範例：  
  
```javascript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 請注意，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 並沒有表示單一字元的類型。  若要在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中表示單一字元，您可以建立只包含一個字元的字串。  包含零字元 \(""\) 的字串是一個空字串 \(長度為零\)。  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 提供可包含在字串中的逸出序列 \(Escape Sequence\)，用來建立無法直接輸入的字元。  例如，`\t` 表示定位字元。  如需詳細資訊，請參閱 [特殊字元](../javascript/advanced/special-characters-javascript.md)。  
  
## Number 資料類型  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，整數和浮點值之間沒有任何差異，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 數字可以是整數或浮點值 \(在內部，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會將所有數字表示為浮點值\)。  
  
### 整數值  
 整數值可以是正整數、負整數和 0。  整數可以用基底 10 \(十進位\)、基底 16 \(十六進位\) 和基底 8 \(八進位\) 來表示。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的大部分數字都是以十進位撰寫。  
  
 您可使用 "0x" \(零和 x&#124;X\) 做為前置字元來表示十六進位 \("hex"\) 的整數。  它們只能包含 0 到 9 的數字，以及字母 A 到 F \(大寫或小寫\)。  字母 A 到 F 用來代表以 10 為基底的 10 到 15 的單一數字。  也就是說，0xF 等於 15，而 0x10 等於 16。  
  
 您可用 "0" \(零\) 做為前置字元來表示八進位的整數。  它們只能包含 0 到 7 的數字。  前置字元為 "0" 且包含數字 "8" 和 \(或\) "9" 的數字會解譯為十進位的數字。  
  
 十六進位和八進位的數字都可以是負數，但是不能有小數部分，而且不能以科學 \(指數\) 標記法撰寫。  
  
> [!NOTE]
>  從 [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)] 開始，[parseInt 函式](../javascript/reference/parseint-function-javascript.md)不會將具有前置 "0" 的字串視為八進位。  當您不使用 `parseInt` 函式時，前置 "0" 的字串仍然可以解譯為八進位。  
  
### 浮點值  
 浮點值可以是含有小數部分的整數。  此外，它們也能以科學標記法來表示；  也就是說，大寫或小寫的 "e" 會用來表示「10 的乘冪」。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 使用數值表示法的八位元組 IEEE 754 浮點數標準來表示數字。  這表示，您可以撰寫大到 1.79769x10<sup>308</sup> 及小到 5x10<sup>-324</sup> 的數字。  包含小數點而且在小數點前面有單一 "0" 的數字會解譯為十進位浮點數。  
  
 請注意，以 "0x" 或 "00" 開頭而且包含小數點的數字，會產生錯誤。  以下是 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 數字的一些範例。  
  
|數字|描述|相等的十進位數|  
|--------|--------|-------------|  
|.0001、0.0001、1e\-4、1.0e\-4|四個相等的浮點數字。|0.0001|  
|3.45e2|浮點數值。|345|  
|45|整數。|45|  
|0378|整數。  雖然它看起來像八進位的數字 \(它以零為首\)，但 8 不是一個有效的八進位數，所以這個數字被視為十進位數。|378|  
|0377|八進位整數。  請注意，雖然看起來只比上個數字少一，但實際值大不相同。|255|  
|0.0001|浮點數字。  即使這個數以零為首，它並不是八進位的數字，因為它有一個小數點。|0.0001|  
|00.0001|這是一個錯誤。  兩個前置零將數字標記為八進位，但是十進位元件中不允許有八進位。|N\/A \(編譯器錯誤\)|  
|0Xff|十六進位整數。|255|  
|0x37CF|十六進位整數。|14287|  
|0x3e7|十六進位整數。  請注意，'e' 不能視為乘冪。|999|  
|0x3.45e2|這是一個錯誤。  十六進位數字不可以有小數部分。|N\/A \(編譯器錯誤\)|  
  
 此外，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 也包含具有特殊值的數字。  這些是：  
  
-   NaN \(非數字\)。  在針對不適當的資料執行算術運算時使用，例如字串或未定義的值  
  
-   正無限大。  當正數太大而無法在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中表示時使用。  
  
-   負無限大。  當負數太大而無法在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中表示時使用。  
  
-   正零和負零。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 會區分正零和負零。  
  
## 布林資料類型  
 雖然字串和數值資料類型實際上可以有無限個不同的值，但布林值資料類型只能有兩種值。  它們是常值 `true` 和 `false`。  布林值為真假值：這會指定條件是否為 true。  
  
 您在指令碼中所做的比較永遠會產生布林值結果。  假設有以下 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式碼行。  
  
```javascript  
y = (x == 2000);  
```  
  
 在這裡，變數 `x` 的值是和數字 2000 進行比較。  如果是，比較的結果就是布林值 **true**，這個值會指派給變數 `y`。  如果 `x` 不等於 2000，則比較的結果會是布林值 `false`。  
  
 布林值在控制結構中特別有用。  下列程式碼會將建立布林值的比較作業與使用它的陳述式直接結合在一起。  請考慮下列 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 程式碼範例。  
  
```javascript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 如果布林值為 `true` \(`z = z + 1`\)，則 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的 `if/else` 陳述式會執行一個動作。如果布林值為 `false` \(`x = x + 1`\)，則執行另一個動作。  
  
 您可以使用任何運算式做為比較運算式。  評估為 0、null、未定義或空字串的任何運算式都會解譯為 `false`。  評估為任何其他值的運算式會解譯為 `true`。  例如，您可以使用如下的運算式：  
  
```javascript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 請注意，上述程式碼行不會檢查 `x` 是否等於 `y + z`，因為只有使用單一等號 \(指派運算子\)。  相反地，以上程式碼會將 `y + z` 的值指派給變數 `x`，然後檢查整個運算式的結果 \(`x` 的值\) 是否為零。  若要檢查 `x` 是否等於 `y + z`，您需要使用下列程式碼。  
  
```javascript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 如需比較的詳細資訊，請參閱[控制程式流程](../javascript/controlling-program-flow-javascript.md)。  
  
## null 資料類型  
 `null` 資料類型在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中只有一個值：null。  此 `null` 關鍵字不能當做函式或變數的名稱。  
  
 含有 `null` 的變數不包含有效的 Number、String、Boolean、Array 或 Object。  您可以藉由指定 `null` 值來清除變數的內容 \(不需刪除變數\)。  
  
 請注意，在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，`null` 不同於 0 \(在 C 和 C\+\+ 中則相同\)。  同時請注意，[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的 `typeof` 運算子會將 `null` 值回報為 `Object` 類型，而不是 `null` 類型。  這種可能造成混淆的行為是為了保持回溯相容性。  
  
## 未定義的資料類型  
 當您使用不存在的物件屬性，或已宣告但從未指派任何值的變數時，會傳回 `undefined` 值。  
  
 雖然可以將變更的類型與字串 "undefined" 比較，檢查其類型是否為 `undefined`，但是您可以將變數與 `undefined` 進行比較，檢查變數是否存在。  下列範例顯示如何判斷變數 `x` 已宣告：  
  
```javascript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 您也可以將未定義的值與 `null` 進行比較。  如果屬性 `someObject.prop` 為 `null`，或屬性 `someObject.prop` 不存在，則這個比較結果是 `true`。  
  
```javascript  
someObject.prop == null;  
```  
  
 若要檢查物件屬性是否存在，您可以使用 **in** 運算子：  
  
```javascript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## 請參閱  
 [物件和陣列](../javascript/objects-and-arrays-javascript.md)   
 [typeof 運算子](../javascript/reference/typeof-operator-decrementjavascript.md)