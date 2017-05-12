---
title: "reduce 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "陣列 [JavaScript], reduce 方法"
  - "callback 函式, reduce 方法 [JavaScript]"
  - "reduce 方法 [JavaScript]"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# reduce 方法 (陣列) (JavaScript)
針對陣列中的所有元素呼叫指定的回呼函式。  回呼函式的傳回值即為累加結果，這個傳回值會做為下一個呼叫的引數提供給回呼函式。  
  
## 語法  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`array1`|必要項。  陣列物件。|  
|`callbackfn`|必要項。  最多接受四個引數的函式。  `reduce` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。|  
|`initialValue`|選擇項。  如果指定 `initialValue`，累加運算時便會以這個值當做運算的初始值。  也就是說，第一次呼叫 `callbackfn` 函式時，會提供這個值 \(而不是陣列值\) 當做引數。|  
  
## 傳回值  
 最後一次呼叫回呼函式所傳回的累加結果。  
  
## 例外狀況  
 下列其中一項條件成立時，就會擲回 `TypeError` 例外狀況：  
  
-   `callbackfn` 引數不是函式物件。  
  
-   陣列沒有任何元素，而且也未提供 `initialValue`。  
  
## 備註  
 如果有提供 `initialValue`，`reduce` 方法會針對陣列中的每個存在元素，依遞增索引順序各呼叫 `callbackfn` 函式一次；  如果未提供 `initialValue`，`reduce` 方法則會從第二個元素開始，針對每個元素呼叫 `callbackfn` 函式。  
  
 回呼函式的傳回值會在下一次呼叫回呼函式時提供當做 `previousValue` 引數，  因此最後一次呼叫回呼函式的傳回值會是 `reduce` 方法的傳回值。  
  
 回呼函式會略過陣列中遺漏的元素。  
  
> [!NOTE]
>  [reduceRight 方法 \(陣列\)](../../javascript/reference/reduceright-method-array-javascript.md) 會依遞減索引順序處理元素。  
  
## 回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 您最多可以使用四個參數宣告回呼函式。  
  
 下表列出回呼函式參數。  
  
|回呼引數|定義|  
|----------|--------|  
|`previousValue`|上次呼叫回呼函式所傳回的值。  如果將 `initialValue` 提供給 `reduce` 方法，當第一次呼叫函式時 `previousValue` 會是 `initialValue`。|  
|`currentValue`|目前陣列元素的值。|  
|`currentIndex`|目前陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## 第一次呼叫回呼函式  
 第一次呼叫回呼函式時，當做引數提供的值取決於 `reduce` 方法是否有 `initialValue` 引數。  
  
 如果有為 reduce 方法提供 `initialValue`：  
  
-   `previousValue` 引數為 `initialValue`。  
  
-   `currentValue` 引數是陣列中第一個存在元素的值。  
  
 如果未提供 `initialValue`：  
  
-   `previousValue` 引數是陣列中第一個存在元素的值。  
  
-   `currentValue` 引數是陣列中第二個存在元素的值。  
  
## 修改陣列物件  
 您可以透過回呼函式修改陣列物件。  
  
 下表顯示啟動 `reduce` 方法後修改陣列物件的結果。  
  
|`reduce` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|------------------------|-------------------|  
|在超出陣列原始長度的位置加入元素。|否。|  
|加入的元素會填補至陣列中有遺漏元素的位置。|是 \(如果該索引尚未傳遞至回呼函式的話\)。|  
|元素已變更。|是 \(如果該元素尚未傳遞至回呼函式的話\)。|  
|從陣列中刪除元素。|否 \(除非該元素已傳遞至回呼函式\)。|  
  
## 範例  
 下列範例會將陣列值串連成字串，而其中每個值之間會以 "::" 區隔。  由於未提供任何初始值給 `reduce` 方法，所以第一次呼叫回呼函式時，`previousValue` 引數為 "abc" 且 `currentValue` 引數為 "def"。  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## 範例  
 下列範例會將陣列的值四捨五入之後進行累加。  呼叫 `reduce` 方法時，初始值為 0。  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## 範例  
 下列範例會使用陣列的值搭配回呼函式計算傳回值的總和，  而回呼函式中會使用 `currentIndex` 和 `array1` 參數。  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## 範例  
 在下列範例中取得的陣列，只會包含其他陣列內介於 1 到 10 之間的值。  範例中提供給 `reduce` 方法的初始值是空陣列。  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [reduceRight 方法 \(陣列\)](../../javascript/reference/reduceright-method-array-javascript.md)