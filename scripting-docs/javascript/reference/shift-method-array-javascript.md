---
title: "shift 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "shift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "shift 方法"
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# shift 方法 (陣列) (JavaScript)
移除陣列的第一個元素，然後將它傳回。  
  
## 語法  
  
```  
  
arrayObj.shift( )  
```  
  
#### 參數  
 必要的 `arrayObj` 參考是 `Array` 物件。  
  
## 傳回值  
 傳回從陣列中移除的元素。  
  
## 備註  
 在下列程式碼中，說明了如何使用 `shift` 方法。  
  
```javascript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [unshift 方法 \(陣列\)](../../javascript/reference/unshift-method-array-javascript.md)