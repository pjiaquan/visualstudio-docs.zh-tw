---
title: "sort 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "sort"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Sort 方法"
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# sort 方法 (陣列) (JavaScript)
將 `Array` 排序。  
  
## 語法  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## 參數  
 `arrayObj`  
 必要項。  任意 `Array` 物件。  
  
 `sortFunction`  
 選擇項。  用來決定元素順序的函式名稱。  如果省略，項目會依 ASCII 字元遞增順序排序。  
  
## 傳回值  
 排序過的陣列。  
  
## 備註  
 `sort` 方法會就地排序 `Array` 物件，在執行時並不會建立新的 `Array` 物件。  
  
 如果您在 `sortFunction` 引數中提供函式，此函式必須傳回下列其中一個值︰  
  
-   如果所傳遞的第一個引數小於第二個引數，則傳回一個負值。  
  
-   如果兩個引數相等，則傳回零。  
  
-   如果第一個引數大於第二個引數，則傳回一個正值。  
  
## 範例  
 下列範例示範如何使用 `sort` 方法。  
  
```javascript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]