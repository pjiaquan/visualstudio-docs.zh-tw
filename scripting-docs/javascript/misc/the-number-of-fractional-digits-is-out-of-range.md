---
title: "小數點後數字的數目超過範圍 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5026"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 小數點後數字的數目超過範圍
您嘗試將無效的引數傳遞給 **Number.prototype.toExponential** 函式。  函式 **toExponential\(\)** 的引數必須介於 0 與 20 之間 \(包含頭尾\)。  
  
### 若要更正這個錯誤  
  
-   請確定 **toExponential\(\)** 的引數不會太大或太小。  
  
## 請參閱  
 [toExponential 方法 \(數字\)](../../javascript/reference/toexponential-method-number-javascript.md)