---
title: "Object.is 函式 (JavaScript) | Microsoft Docs"
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.is 函式 (JavaScript)
傳回值，這個值表示兩個值是否相同。  
  
## 語法  
  
```javascript  
Object.is(value1, value2)  
```  
  
#### 參數  
 `value1`  
 必要項。  要測試的第一個值。  
  
 `value2`  
 必要項。  要測試的第二個值。  
  
## 傳回值  
 如果值相同，則為 `true`，否則為 `false`。  
  
## 備註  
 與 \=\= 運算子不同， `Object.is` 在測試值時不會強制變更任何類型。  
  
 `Object.is` 所套用的比較類似 \=\=\= 運算子所套用的比較，差異在於 `Object.is` 將 `Number.isNaN` 視為與 `NaN` 相同的值。  它也將 \+0 和 \-0 視為不同的值。  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]