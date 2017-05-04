---
title: "every 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "陣列 [JavaScript], every 方法"
  - "every 方法"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# every 方法 (陣列) (JavaScript)
判斷陣列中的所有成員是否符合所指定的測試。  
  
## 語法  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`array1`|必要項。  陣列物件。|  
|`callbackfn`|必要項。  最多接受三個引數的函式。  `every` 方法會針對 `array1` 中的每個元素呼叫 `callbackfn` 函式，直到 `callbackfn` 傳回 `false` 或此陣列的結尾為止。|  
|`thisArg`|選擇項。  `this` 關鍵字可在 `callbackfn` 函式中參考的物件。  如果省略 `thisArg`，則 `this` 的值就是 `undefined`。|  
  
## 傳回值  
 如果 `callbackfn` 函式針對所有陣列元素傳回 `true` 則為 `true`，否則為 `false`。  如果陣列沒有任何元素，`every` 方法會傳回 `true`。  
  
## 例外狀況  
 如果 `callbackfn` 引數不是函式物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 `every` 方法會在每個陣列元素上呼叫 `callbackfn` 函式一次 \(以遞增索引順序\)，直到 `callbackfn` 函式傳回 `false` 為止。  如果找到造成 `callbackfn` 傳回 `false` 的元素，則 `every` 方法會立即傳回 `false`。  否則，`every` 方法會傳回 `true`。  
  
 回呼函式會略過陣列中遺漏的元素。  
  
 除了陣列物件之外，任何具有 `length` 屬性且具有數值索引屬性名稱的物件都可以使用 `every` 方法。  
  
> [!NOTE]
>  您可以使用 [some 方法 \(陣列\)](../../javascript/reference/some-method-array-javascript.md) 檢查回呼函式是否會針對陣列中的任何元素傳回 `true`。  
  
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
  
 下表描述在 `every` 方法啟動後修改陣列物件的結果。  
  
|`every` 方法啟動後的狀況。|元素是否會傳遞至回呼函式？|  
|-----------------------|-------------------|  
|在超出陣列原始長度的位置加入元素。|否。|  
|加入的元素會填補至陣列中有遺漏元素的位置。|是 \(如果該索引尚未傳遞至回呼函式的話\)。|  
|元素已變更。|是 \(如果該元素尚未傳遞至回呼函式的話\)。|  
|從陣列中刪除元素。|否 \(除非該元素已傳遞至回呼函式\)。|  
  
## 範例  
 在下列範例中，說明了如何使用 `every` 方法。  
  
```javascript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## 範例  
 下列範例示範如何使用 `thisArg` 引數指定 `this` 關鍵字可參考的物件。  
  
```javascript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [some 方法 \(陣列\)](../../javascript/reference/some-method-array-javascript.md)   
 [filter 方法 \(陣列\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)