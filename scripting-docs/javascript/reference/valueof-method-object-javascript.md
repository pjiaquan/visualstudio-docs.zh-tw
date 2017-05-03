---
title: "valueOf 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf 方法"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# valueOf 方法 (Object) (JavaScript)
傳回指定之物件的基本值。  
  
## 語法  
  
```  
  
object.valueOf( )  
```  
  
## 備註  
 必要的 `object` 參考是任何內建 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件。  
  
 每個內建 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件定義的 `valueOf` 方法都不同。  
  
|物件|傳回值|  
|--------|---------|  
|Array|傳回陣列執行個體。|  
|Boolean|布林值。|  
|Date|從 UTC 1970 年 1 月 1 日午夜起算，儲存在物件中的時間值 \(以毫秒為單位\)|  
|函式|函式本身。|  
|Number|數值。|  
|物件|物件本身。  這是預設值。|  
|字串|字串值。|  
  
 **Math** 物件和 `Error` 物件沒有 `valueOf` 方法。  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **適用於**：[Array 物件](../../javascript/reference/array-object-javascript.md)&#124; [Boolean 物件](../../javascript/reference/boolean-object-javascript.md)&#124; [Date 物件](../../javascript/reference/date-object-javascript.md)&#124; [Function 物件](../../javascript/reference/function-object-javascript.md)&#124; [Number 物件](../../javascript/reference/number-object-javascript.md)&#124; [Object 物件](../../javascript/reference/object-object-javascript.md)&#124; [String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [toString 方法 \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)