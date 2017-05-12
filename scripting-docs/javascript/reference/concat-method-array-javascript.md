---
title: "concat 方法 (Array) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat 方法 (陣列)"
  - "Concat 方法"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# concat 方法 (Array) (JavaScript)
合併兩個以上的陣列。  
  
## 語法  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## 參數  
 `array1`  
 必要項。  其他陣列所串連的 `Array` 物件。  
  
 `item1,. . ., itemN`  
 選擇項。  要加入至 `array1` 結尾的其他項目。  
  
## 備註  
 `concat` 方法會傳回一個 `Array` 物件，其中包含 `array1` 和任何其他提供項目的串連結果。  
  
 要加入至陣列的項目 \(*item1 itemN*\) 是以從清單中的第一個項目開始的順序加入。  如果其中一個元素本身就是陣列，它的內容會加入至 `array1` 的結尾。  如果此項目不是陣列，它會當做單一陣列元素加入至陣列的結尾。  
  
 來源陣列的元素會複製到結果陣列，如下所示：  
  
-   如果物件是複製自串連到新陣列的任何陣列，物件參考還是會指向相同的物件。  此時新陣列的改變會導致原始陣列的改變，而原始陣列的改變也會導致新陣列的改變。  
  
-   如果有數字或字串值加入至新陣列，只有值會複製過去。  某個陣列中的值如果變更，並不會影響其他陣列中的值。  
  
## 範例  
 下列範例會示範如何搭配陣列使用 `concat` 方法：  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [concat 方法 \(字串\)](../../javascript/reference/concat-method-string-javascript.md)   
 [join 方法 \(陣列\)](../../javascript/reference/join-method-array-javascript.md)