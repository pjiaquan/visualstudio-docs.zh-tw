---
title: "some 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "陣列 [JavaScript], some 方法"
  - "some 方法 [JavaScript]"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# some 方法 (陣列) (JavaScript)
判斷指定的回呼函式是否會針對陣列的任何元素傳回 `true`。  
  
## 語法  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`array1`|必要項。  陣列物件。|  
|`callbackfn`|必要項。  最多接受三個引數的函式。  `some` 方法會針對 `array1` 中的每個元素呼叫 `callbackfn` 函式，直到 `callbackfn` 傳回 `true` 或此陣列的結尾為止。|  
|`thisArg`|選擇項。  `this` 關鍵字可在 `callbackfn` 函式中參考的物件。  如果省略 `thisArg`，則 `this` 的值就是 `undefined`。|  
  
## 傳回值  
 如果 `callbackfn` 函式針對任何陣列元素傳回 `true` 則為 `true`，否則為 `false`。  
  
## 例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 `some` 方法會在每個陣列元素上呼叫 `callbackfn` 函式 \(以遞增索引順序\)，直到 `callbackfn` 函式傳回 `true` 為止。  如果找到造成 `callbackfn` 傳回 `true` 的元素，則 `some` 方法會立即傳回 `true`。  如果回呼不會在任何元素上傳回 `true`，則 `some` 方法會傳回 `false`。  
  
 回呼函式會略過陣列中遺漏的元素。  
  
 除了陣列物件之外，任何具有 `length` 屬性且具有數值索引屬性名稱的物件都可以使用 `some` 方法。  
  
> [!NOTE]
>  您可以使用 [every 方法 \(陣列\)](../../javascript/reference/every-method-array-javascript.md) 檢查回呼函式是否會針對陣列中的所有元素傳回 `true`。  
  
## 回呼函式語法  
 回呼函式的語法如下：  
  
 `function callbackfn(value, index, array1)`  
  
 您最多可以使用三個參數宣告回呼函式。  
  
 下表列出回呼函式參數。  
  
|回呼參數|定義|  
|----------|--------|  
|`value`|陣列元素的值。|  
|`index`|陣列元素的數值索引。|  
|`array1`|包含元素的陣列物件。|  
  
## 修改陣列物件  
 您可以透過回呼函式修改陣列物件。  
  
 下表描述在 `some` 方法啟動後修改陣列物件的結果。  
  
|`some` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|----------------------|-------------------|  
|在超出陣列原始長度的位置加入元素。|否。|  
|加入的元素會填補至陣列中有遺漏元素的位置。|是 \(如果該索引尚未傳遞至回呼函式的話\)。|  
|元素已變更。|是 \(如果該元素尚未傳遞至回呼函式的話\)。|  
|從陣列中刪除元素。|否 \(除非該元素已傳遞至回呼函式\)。|  
  
## 範例  
 下列範例使用 `some` 方法來查明陣列中是否有任何元素為偶數。  
  
```javascript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## 範例  
 下列範例示範如何使用 `thisArg` 參數，此參數會指定 `this` 關鍵字可參照的物件。  它會檢查陣列中是否有任何數字超出傳遞之物件所提供的範圍  
  
```javascript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [every 方法 \(陣列\)](../../javascript/reference/every-method-array-javascript.md)   
 [filter 方法 \(陣列\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map 方法 \(陣列\)](../../javascript/reference/map-method-array-javascript.md)