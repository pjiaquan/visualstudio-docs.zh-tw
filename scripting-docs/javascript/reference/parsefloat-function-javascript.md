---
title: "parseFloat 函式 (JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat 方法"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# parseFloat 函式 (JavaScript)
會將字串轉換成浮點數。  
  
## 語法  
  
```  
parseFloat(numString)   
```  
  
## 備註  
 必要的 `numString` 引數是一個包含浮點數的字串。  
  
 `parseFloat` 函式傳回的數值等於 `numString` 中包含的數字。  如果沒有任何的 `numString` 前置詞可成功地剖析為浮點數值，則會傳回 `NaN` \(非數字\)。  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 您可以使用 `isNaN` 函式來測試 `NaN`。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 請參閱  
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt 函式](../../javascript/reference/parseint-function-javascript.md)   
 [String 物件](../../javascript/reference/string-object-javascript.md)