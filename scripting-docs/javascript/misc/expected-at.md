---
title: "必須是 &#39;@&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 必須是 &#39;@&#39;
您嘗試建立變數，此變數要利用 `@set` 陳述式來搭配條件式編譯陳述式使用，但是並未在變數名稱之前放置 **@** 符號。  
  
### 若要更正這個錯誤  
  
-   在變數名稱之前加上 "**@**" 符號。  例如：  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## 請參閱  
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)   
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)