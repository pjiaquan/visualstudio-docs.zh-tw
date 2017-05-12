---
title: "keys 方法 (陣列) (JavaScript) | Microsoft Docs"
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# keys 方法 (陣列) (JavaScript)
傳回迭代器，它會傳回陣列的索引值。  
  
## 語法  
  
```  
arrayObj.keys();  
```  
  
#### 參數  
 `arrayObj`  
 必要項。  陣列物件。  
  
## 備註  
  
## 範例  
 下列範例會顯示如何取得陣列的機碼值。  
  
```javascript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]