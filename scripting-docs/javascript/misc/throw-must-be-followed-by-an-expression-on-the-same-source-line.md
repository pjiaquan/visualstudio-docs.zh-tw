---
title: "throw 必須接著一運算式，且於同一行程式碼 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# throw 必須接著一運算式，且於同一行程式碼
您使用了 `throw` 關鍵字，但並未在相同原始程式行的此關鍵字後面加上運算式。  `throw` 陳述式包含兩個部分：`throw` 關鍵字，後面緊接著要擲回的運算式。  例如：  
  
```javascript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 您不能分割這兩個元件。  
  
### 若要更正這個錯誤  
  
-   請確定 `throw` 關鍵字及要擲回的運算式出現在同一行。  
  
## 請參閱  
 [Error 物件](../../javascript/reference/error-object-javascript.md)   
 [throw 陳述式](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)