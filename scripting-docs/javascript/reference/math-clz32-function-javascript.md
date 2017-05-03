---
title: "Math.clz32 函式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.clz32 函式 (JavaScript)
傳回數字之 32 位元二進位表示法中的前置零位元數。  
  
## 語法  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## 備註  
 如果 `number` 是 0，則結果會是 32。  如果32 位元二進位編碼的最高有效位元 `number` 為 1，結果將會是 0。  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用對象**：[Math 物件](../../javascript/reference/math-object-javascript.md)