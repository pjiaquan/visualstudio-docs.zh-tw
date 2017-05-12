---
title: "reduceRight 方法 (陣列) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "陣列 [JavaScript], reduceRight 方法"
  - "reduceRight 方法 [JavaScript]"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# reduceRight 方法 (陣列) (JavaScript)
針對陣列中的所有元素呼叫指定的回呼函式 \(以遞減順序\)。  回呼函式的傳回值即為累加結果，這個傳回值會做為下一個呼叫的引數提供給回呼函式。  
  
## 語法  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`array1`|必要項。  陣列物件。|  
|`callbackfn`|必要項。  最多接受四個引數的函式。  `reduceRight` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。|  
|`initialValue`|選擇項。  如果指定 `initialValue`，累加運算時便會以這個值當做運算的初始值。  也就是說，第一次呼叫 `callbackfn` 函式時，會提供這個值 \(而不是陣列值\) 當做引數。|  
  
## 傳回值  
 包含從最後一次呼叫回呼函式算起之累計結果的物件。  
  
## 例外狀況  
 下列其中一項條件成立時，就會擲回 `TypeError` 例外狀況：  
  
-   `callbackfn` 引數不是函式物件。  
  
-   陣列沒有任何元素，而且也未提供 `initialValue`。  
  
## 備註  
 如果有提供 `initialValue`，`reduceRight` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次 \(以遞減索引順序\)。  如果未提供 `initialValue`，`reduceRight` 方法會從倒數第二個元素開始在每個元素上呼叫 `callbackfn` 函式 \(以遞減順序索引\)。  
  
 回呼函式的傳回值會在下一次呼叫回呼函式時提供當做 `previousValue` 引數，  最後一次呼叫回呼函式的傳回值是 `reduceRight` 方法的傳回值。  
  
 回呼函式會略過陣列中遺漏的元素。  
  
 若要以遞增索引順序累計結果，請使用 [reduce 方法 \(陣列\)](../../javascript/reference/reduce-method-array-javascript.md)。  
  
## 回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 您最多可以使用四個參數宣告回呼函式。  
  
 下表列出回呼函式參數。  
  
|回呼引數|定義|  
|----------|--------|  
|`previousValue`|上次呼叫回呼函式所傳回的值。  如果將 `initialValue` 提供給 `reduceRight` 方法，當第一次呼叫函式時 `previousValue` 會是 `initialValue`。|  
|`currentValue`|目前陣列元素的值。|  
|`currentIndex`|目前陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## 第一次呼叫回呼函式  
 當第一次呼叫回呼函式時，當做引數提供的值取決於 `reduceRight` 方法是否有 `initialValue` 引數。  
  
 如果將 `initialValue` 提供給 `reduceRight` 方法：  
  
-   `previousValue` 引數為 `initialValue`。  
  
-   `currentValue` 引數是陣列中存在之最後一個元素的值。  
  
 如果未提供 `initialValue`：  
  
-   `previousValue` 引數是陣列中存在之最後一個元素的值。  
  
-   `currentValue` 引數是陣列中存在之倒數第二個元素的值。  
  
## 修改陣列物件  
 您可以透過回呼函式修改陣列物件。  
  
 下表描述在 `reduceRight` 方法啟動後修改陣列物件的結果。  
  
|`reduceRight` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|-----------------------------|-------------------|  
|在超出陣列原始長度的位置加入元素。|否。|  
|加入的元素會填補至陣列中有遺漏元素的位置。|是 \(如果該索引尚未傳遞至回呼函式的話\)。|  
|元素已變更。|是 \(如果該元素尚未傳遞至回呼函式的話\)。|  
|從陣列中刪除元素。|否 \(除非該元素已傳遞至回呼函式\)。|  
  
## 範例  
 下列範例會將陣列值串連成字串，而其中每個值之間會以 "::" 區隔。  因為不會將任何初始值提供給 `reduceRight` 方法，所以第一次呼叫回呼函式時，`previousValue` 引數為 456 且 `currentValue` 引數為 123。  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## 範例  
 下列範例會尋找陣列元素的平方總和。  呼叫 `reduceRight` 方法時，初始值為 0。  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## 範例  
 下列範例會取得值介於 1 和 10 之間的陣列元素。  提供給 `reduceRight` 方法的初始值是空的陣列。  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## 範例  
 `reduceRight` 方法可以套用至字串。  下列範例示範如何使用這個方法來反轉字串中的字元。  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [reduce 方法 \(陣列\)](../../javascript/reference/reduce-method-array-javascript.md)