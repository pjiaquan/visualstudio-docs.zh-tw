---
title: "Symbol.for 函式 (JavaScript) | Microsoft Docs"
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Symbol.for 函式 (JavaScript)
傳回指定索引鍵的符號；如果索引鍵不存在，則使用新的索引鍵建立新的符號物件。  
  
## 語法  
  
```vb  
Symbol.for(key);  
```  
  
#### 參數  
 `key`  
 必要項。  符號的索引鍵，也可做為描述。  
  
## 備註  
 這個方法會搜尋全域符號登錄中的符號。  如果您將符號序列化為字串，請使用全域符號登錄，以確定特定字串在所有查閱中都會對應到正確符號。  
  
## 範例  
  
```javascript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]