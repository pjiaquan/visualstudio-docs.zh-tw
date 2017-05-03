---
title: "必須是 &#39;catch&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 必須是 &#39;catch&#39;
您使用了例外狀況處理 **try** 區塊，但並未撰寫關聯的 **catch** 陳述式。  例外狀況處理機制會要求將可能失敗的程式碼以及在例外狀況發生時不應該執行的程式碼，一起包裝在 **try** 區塊內。  使用 **throw** 陳述式從 **try** 區塊擲回例外狀況，並利用一個或多個 **catch** 陳述式在 **try** 區塊之外攔截例外狀況。  
  
### 若要更正這個錯誤  
  
-   加入相關聯的 **catch** 區塊。  
  
-   請嘗試使用 **finally** 區塊，而不是 **catch** 區塊。  
  
## 請參閱  
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 物件](../../javascript/reference/error-object-javascript.md)