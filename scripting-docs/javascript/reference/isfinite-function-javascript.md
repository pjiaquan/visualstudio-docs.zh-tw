---
title: "isFinite 函式 (JavaScript) | Microsoft Docs"
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
  - "isFinite"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "有限數字"
  - "isFinite 方法"
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# isFinite 函式 (JavaScript)
判斷所提供的數字是否為有限值。  
  
## 語法  
  
```  
isFinite(number)   
```  
  
## 備註  
 必要的 `number` 引數是任何數值。  
  
 如果 `number` 是 `NaN`、負無限大或正無限大以外的任何值，則 `isFinite` 函式會傳回 `true`。  否則在以上三種情況下，此函式會傳回 **false**。  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 請參閱  
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)