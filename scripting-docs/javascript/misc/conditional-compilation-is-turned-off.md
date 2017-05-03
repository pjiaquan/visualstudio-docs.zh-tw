---
title: "條件式編譯已經關閉 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 條件式編譯已經關閉
您嘗試使用條件式編譯變數，而未先開啟條件式編譯。  開啟條件式編譯會告知 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 編譯器必須將以 @ 開頭的識別項解譯為條件式編譯變數。  若要執行這項處理，請使用陳述式當做條件式程式碼的開頭：  
  
```  
/*@cc_on @*/  
```  
  
### 若要更正這個錯誤  
  
-   將下列陳述式加入至條件式程式碼的開頭：  
  
    ```javascript  
    /*@cc_on @*/  
    ```  
  
## 請參閱  
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on 陳述式](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if 陳述式](../../javascript/reference/at-if-statement-javascript.md)   
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)