---
title: "valueOf 方法 (陣列) | Microsoft Docs"
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf 方法 (陣列)
傳回指定之物件的基本值。  
  
## 語法  
  
```  
  
array.valueOf()  
```  
  
#### 參數  
 這個方法沒有參數。  
  
## 傳回值  
 傳回陣列執行個體。  
  
## 備註  
 在下列範例中，具現化的陣列物件與這個方法的傳回值相同。  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]