---
title: "filter 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "陣列 [JavaScript], filter 方法"
  - "filter 方法 [JavaScript]"
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# filter 方法 (陣列) (JavaScript)
傳回符合回呼函式中指定之條件的陣列元素。  
  
## 語法  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`array1`|必要項。  陣列物件。|  
|`callbackfn`|必要項。  最多接受三個引數的函式。  `filter` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次。|  
|`thisArg`|選擇項。  `this` 關鍵字可在 `callbackfn` 函式中參考的物件。  如果省略 `thisArg`，則 `this` 的值就是 `undefined`。|  
  
## 傳回值  
 新陣列，其中包含回呼函式針對來源陣列傳回 `true` 的所有元素。  如果回呼函式針對 `array1` 的所有元素都傳回 `false`，新陣列的長度就是 0。  
  
## 例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 `filter` 方法會針對陣列中的每個元素各呼叫 `callbackfn` 函式一次 \(以遞增索引順序\)。  回呼函式會略過陣列中遺漏的元素。  
  
 除了陣列物件之外，任何具有 `length` 屬性且具有數值索引屬性名稱的物件都可以使用 `filter` 方法。  
  
## 回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(value, index, array1)`  
  
 您最多可以使用三個參數宣告回呼函式。  
  
 下表列出回呼函式參數。  
  
|回呼引數|定義|  
|----------|--------|  
|`value`|陣列元素的值。|  
|`index`|陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## 修改陣列物件  
 `filter` 方法不會直接修改原始陣列，但是回呼函式可以修改。  下表顯示啟動 `filter` 方法後修改陣列物件的結果。  
  
|`filter` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|------------------------|-------------------|  
|在超出陣列原始長度的位置加入元素。|否。|  
|加入的元素會填補至陣列中有遺漏元素的位置。|是 \(如果該索引尚未傳遞至回呼函式的話\)。|  
|元素已變更。|是 \(如果該元素尚未傳遞至回呼函式的話\)。|  
|從陣列中刪除元素。|否 \(除非該元素已傳遞至回呼函式\)。|  
  
## 範例  
 下列範例示範如何使用 `filter` 方法。  
  
```javascript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## 範例  
 在下列範例中，`callbackfn` 引數包含回呼函式的程式碼。  
  
```javascript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## 範例  
 下列範例會顯示 `window` DOM 物件中開頭字母為 "css" 的屬性名稱。  
  
```javascript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## 範例  
 下列範例示範如何使用 `thisArg` 引數指定 `this` 關鍵字可參考的物件。  
  
```javascript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## 範例  
 除了陣列之外，`filter` 方法還適用於字串。  下列範例顯示如何執行這項工作。  
  
```javascript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)   
 [map 方法 \(陣列\)](../../javascript/reference/map-method-array-javascript.md)   
 [forEach 方法 \(陣列\)](../../javascript/reference/foreach-method-array-javascript.md)