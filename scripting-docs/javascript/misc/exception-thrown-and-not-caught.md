---
title: "發生例外狀況而且未攔截 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 發生例外狀況而且未攔截
您已在程式碼中包含 `throw` 陳述式，但是它並未包含在 **try** 區塊中，或是沒有關聯的 **catch** 區塊可攔截錯誤。  例外狀況會使用 **throw** 陳述式從 **try** 區塊內擲回，而且會使用 **catch** 陳述式在 **try** 區塊之外攔截到。  
  
### 若要更正這個錯誤  
  
-   請將可擲回例外狀況的程式碼放在 **try** 區塊內，並確定有對應的 **catch** 區塊。  
  
-   確定您的 catch 陳述式會預期正確格式的例外狀況。  
  
-   如果重新擲回例外狀況，請確定有另一個對應的 catch 陳述式。  
  
## 請參閱  
 [Error 物件](../../javascript/reference/error-object-javascript.md)   
 [throw 陳述式](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)