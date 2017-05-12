---
title: "Number.isFinite 函式 (數字) (JavaScript) | Microsoft Docs"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Number.isFinite 函式 (數字) (JavaScript)
傳回布林值，表示值是否為有限數值。  
  
## 語法  
  
```  
Number.isFinite(numValue)   
```  
  
## 傳回值  
 如果值為 `NaN`、`+∞` 或 `-∞`，則為 `false`否則為 `true`。  
  
## 備註  
  
## 範例  
  
```javascript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**：[Number 物件](../../javascript/reference/number-object-javascript.md)