---
title: "Math.sign 函式 (JavaScript) | Microsoft Docs"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Math.sign 函式 (JavaScript)
傳回數字的正負號，以指出數字為正數、負數或 0。  
  
## 語法  
  
```  
Math.sign(number)  
```  
  
## 備註  
 所需之 `number` 引數是須有正負號的數值運算式。  
  
 傳回值可以是下列其中之一：  
  
-   `NaN`，如果 `number` 是 `NaN`。  
  
-   \-0，如果 `number` 是 −0。  
  
-   \+0，如果 `number` 是 \+0。  
  
-   \-1，如果 `number` 是負值，而且非 −0。  
  
-   \+1，如果 `number` 是正值，而且不是 \+0。  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]