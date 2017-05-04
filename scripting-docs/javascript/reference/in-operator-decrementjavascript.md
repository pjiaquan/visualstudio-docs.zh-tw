---
title: "in 運算子 (JavaScript) | Microsoft Docs"
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
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in 運算子"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# in 運算子 (JavaScript)
測試物件的屬性是否存在。  
  
## 語法  
  
```  
  
result = property in object  
```  
  
## 參數  
 `result`  
 必要項。  任何變數。  
  
 `property`  
 必要項。  評估為字串運算式的運算式。  
  
 `object`  
 必要項。  任何物件。  
  
## 備註  
 `in` 運算子會檢查物件是否有名稱為 `property` 的屬性。  它也會判斷屬性是否為物件的原型鏈結的一部分。  如需物件原型的詳細資訊，請參閱[原型與原型繼承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)。  
  
## 範例  
 下列範例示範如何使用 `in` 運算子：  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)