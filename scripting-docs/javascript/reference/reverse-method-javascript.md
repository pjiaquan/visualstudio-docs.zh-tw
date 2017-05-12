---
title: "reverse 方法 (JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "陣列 [Visual Studio]，反轉元素順序"
  - "reverse 方法"
  - "調換項目"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# reverse 方法 (JavaScript)
反轉 `Array` 中的元素。  
  
## 語法  
  
```  
  
arrayObj.reverse()   
```  
  
## 參數  
 `arrayObj`  
 必要項。  任意 `Array` 物件。  
  
## 傳回值  
 反向的陣列。  
  
## 備註  
 必要的 `arrayObj` 參考是 `Array` 物件。  
  
 `reverse` 方法會就地反轉 `Array` 物件的元素。  在執行時並不會建立新的 `Array` 物件。  
  
 如果此陣列不是連續的，`reverse` 方法會在陣列中建立元素，以填補陣列中的間隙。  每一個這些建立的項目都會有 `undefined` 值。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `reverse` 方法。  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [concat 方法 \(陣列\)](../../javascript/reference/concat-method-array-javascript.md)