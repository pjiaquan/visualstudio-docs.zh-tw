---
title: "toString 方法 (陣列) | Microsoft Docs"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toString 方法 (陣列)
傳回陣列的字串表示。  
  
## 語法  
  
```  
  
array.toString()  
```  
  
## 參數  
 `array`  
 必要項。  要表示為字串的陣列。  
  
## 傳回值  
 陣列的字串表示。  
  
## 備註  
 `Array` 的元素會轉換為字串。  產生的字串是串連的，並以逗號分隔。  
  
## 範例  
 以下範例說明如何搭配陣列使用 **toString** 方法。  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]