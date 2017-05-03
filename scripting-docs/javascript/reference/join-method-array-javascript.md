---
title: "join 方法 (陣列) (JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join 方法"
  - "串連字串，join 方法"
  - "陣列 [Visual Studio]，聯結"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# join 方法 (陣列) (JavaScript)
會加入以指定的分隔符號字串所分隔之陣列的所有元素。  
  
## 語法  
  
```  
  
arrayObj.join([separator])   
```  
  
## 參數  
 `arrayObj`  
 必要項。  `Array` 物件。  
  
 `separator`  
 選擇項。  在產生的 `String` 中，用來分隔陣列各個元素的字串。  若予以省略，陣列元素會用逗號來分隔。  
  
## 備註  
 如果陣列中有任何元素為 **undefined** 或是 `null`，該元素將被視為空字串。  
  
## 範例  
 以下範例說明如何使用 **join** 方法。  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)