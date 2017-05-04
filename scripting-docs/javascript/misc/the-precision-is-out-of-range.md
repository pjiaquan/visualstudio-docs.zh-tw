---
title: "整數位數超過範圍 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c16760ac-fc08-49d7-8878-9bc434b3c080
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 整數位數超過範圍
您嘗試將無效的引數傳遞給 **Number.prototype.toPrecision** 函式。  **toPrecision** 的引數必須在 1 到 21 之間 \(包含頭尾\)。  
  
### 若要更正這個錯誤  
  
-   請確定 `toPrecision` 的引數不會太大或太小。  
  
## 請參閱  
 [toPrecision 方法 \(數字\)](../../javascript/reference/toprecision-method-number-javascript.md)