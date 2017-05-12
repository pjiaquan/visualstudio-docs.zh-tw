---
title: "delete 運算子 (JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "陣列項目，刪除"
  - "屬性，刪除"
  - "delete 運算子"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# delete 運算子 (JavaScript)
刪除物件中的屬性或是移除陣列中的元素。  
  
## 語法  
  
```  
delete expression  
```  
  
## 備註  
 `expression` 引數是通常會產生屬性名稱或陣列元素的有效 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 運算式。  
  
 如果 `expression` 的結果為物件，則在 `expression` 中所指定的屬性便會存在，而且此物件也不允許刪除該屬性，最後會傳回 `false`。  
  
 在所有其他的情況下，則一律傳回 `true`。  
  
## 範例  
 下列範例示範如何從陣列中移除元素。  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## 範例  
 下列範例示範如何從物件中刪除屬性。  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)