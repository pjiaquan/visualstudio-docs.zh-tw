---
title: "Boolean 物件 (JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolean 資料類型, Boolean 物件"
  - "Boolean 物件"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Boolean 物件 (JavaScript)
建立一個新的布林值。  
  
## 語法  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## 參數  
 `boolObj`  
 必要項。  指派 `Boolean` 物件的變數名稱。  
  
 `boolValue`  
 選擇項。  新物件的初始布林值。  如果 `boolvalue` 被省略或者為 `false`、0、`null`、`NaN` 或空字串，Boolean 物件的初始值就會是 `false`。  否則，初始值為 `true`。  
  
## 備註  
 `Boolean` 物件是布林資料型別的包裝函式。  每當布林資料型別轉換為 `Boolean` 物件時，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 都會隱含使用 `Boolean` 物件。  
  
 您幾乎不用明確具現化 `Boolean` 物件。  
  
## 屬性  
 下表列出 `Boolean` 物件的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[constructor 屬性](../../javascript/reference/constructor-property-boolean.md)|指定用來建立布林值的函式。|  
|[prototype 屬性](../../javascript/reference/prototype-property-boolean.md)|傳回布林值的原型參考。|  
  
<a name="js56jsobjarraymeth"></a>   
## 方法  
 下表列出 `Boolean` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|[toString 方法](../../javascript/reference/tostring-method-boolean-1.md)|傳回布林值的字串表示。|  
|[valueOf 方法](../../javascript/reference/valueof-method-boolean.md)|取得布林值的參考。|  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]