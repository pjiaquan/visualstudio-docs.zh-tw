---
title: "迴圈外不可以有 &#39;continue&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 迴圈外不可以有 &#39;continue&#39;
您嘗試在迴圈外使用 **continue** 陳述式。  **continue** 陳述式只能在以下項目的主體內使用：  
  
-   `do-while` 迴圈、  
  
-   `while` 迴圈、  
  
-   **for** 迴圈、  
  
-   **for\/in** 迴圈。  
  
### 若要更正這個錯誤  
  
-   請確定 **continue** 陳述式有出現在以下項目的主體內：  
  
    -   `do-while` 迴圈、  
  
    -   `while` 迴圈、  
  
    -   **for** 迴圈、  
  
    -   **for\/in** 迴圈。  
  
## 請參閱  
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)