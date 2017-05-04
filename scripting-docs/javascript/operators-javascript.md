---
title: "運算子 (JavaScript) | Microsoft Docs"
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
  - "JavaScript、運算子"
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 運算子 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 擁有完整範圍的運算子，包括算術、邏輯、位元、指派，以及一些其他運算子。  如需說明和範例，請參閱特定運算子的相關主題。  
  
## 計算運算子  
  
|描述|符號|  
|--------|--------|  
|[一元負運算](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
|[遞增](../javascript/reference/increment-and-decrement-operators-javascript.md)|\+\+|  
|[遞減](../javascript/reference/increment-and-decrement-operators-javascript.md)|\-\-|  
|[乘法](../javascript/reference/multiplication-operator-decrement-javascript.md)|\*|  
|[除法](../javascript/reference/division-operator-decrement-javascript.md)|\/|  
|[模數算術](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[加入](../javascript/reference/addition-operator-decrement-javascript.md)|\+|  
|[減法](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
  
## 邏輯運算子  
  
|描述|符號|  
|--------|--------|  
|[邏輯 NOT](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|\!|  
|[小於](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[大於](../javascript/reference/comparison-operators-javascript.md)|\>|  
|[小於或等於](../javascript/reference/comparison-operators-javascript.md)|\<\=|  
|[大於或等於](../javascript/reference/comparison-operators-javascript.md)|\>\=|  
|[相等](../javascript/reference/comparison-operators-javascript.md)|\=\=|  
|[不等於](../javascript/reference/comparison-operators-javascript.md)|\!\=|  
|[邏輯 AND](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[邏輯 OR](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[條件 \(三元\)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[逗號](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[嚴格相等比較](../javascript/reference/comparison-operators-javascript.md)|\=\=\=|  
|[嚴格不等比較](../javascript/reference/comparison-operators-javascript.md)|\!\=\=|  
  
## 位元運算子  
  
|描述|符號|  
|--------|--------|  
|[位元 NOT](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[位元左移](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|\<\<|  
|[位元右移](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|\>\>|  
|[不帶正負號的右移](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|\>\>\>|  
|[位元 AND](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[位元 XOR](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[位元 OR](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## 指派運算子  
  
|描述|符號|  
|--------|--------|  
|[指派](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|\=|  
|[複合指派](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*\= \(例如 \+\= 和 &\=\)|  
  
## 雜項運算子  
  
|描述|符號|  
|--------|--------|  
|[刪除](../javascript/reference/delete-operator-decrementjavascript.md)|刪除|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## 相等和嚴格相等  
 \=\= \(等號比較\) 和 \=\=\= \(嚴格相等比較\) 之間的差異如下：等號比較運算子將會強制轉型不同型別的值，然後再檢查是否相等。  例如，比較字串 "1" 與數字 1 的結果會是 true。  另一方面，嚴格相等比較運算子不會將值強制轉型成不同的型別，所以字串 "1" 與數字 1 的比較結果不會相同。  
  
 基本字串、數字和布林值會根據值來比較。  如果都有相同的值，則它們是相等的。  物件 \(包括 `Array`、`Function`、`String`、**Number**、`Boolean`、**Error**、`Date` 和 `RegExp` 物件\) 是以傳址方式進行比較。  即使這些型別的兩個變數有相同的值，只有當兩者參考完全相同的物件時，它們才是相等的。  
  
 例如：  
  
```javascript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```