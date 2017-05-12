---
title: "new 運算子 (JavaScript) | Microsoft Docs"
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
  - "new_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript 中的 new 運算子"
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# new 運算子 (JavaScript)
建立新的物件。  
  
## 語法  
  
```  
new constructor ([arguments])   
```  
  
## 參數  
 `constructor`  
 必要項。  物件的建構函式。  如果建構函式不含引數，可省略括號。  
  
 `arguments`  
 選擇項。  要傳給新物件之建構函式的任何引數。  
  
## 備註  
 `new` 運算子會執行下列工作：  
  
-   建立不含成員的物件。  
  
-   呼叫該物件的建構函式，並傳遞新建立之物件的指標當做 `this` 指標。  
  
-   接著建構函式會依據傳遞給自己的引數來初始化物件。  
  
 以下範例說明 **new** 運算子的有效使用方式。  
  
```javascript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)