---
title: "&#39;default&#39; 只可以出現在 &#39;switch&#39; 陳述式中一次 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &#39;default&#39; 只可以出現在 &#39;switch&#39; 陳述式中一次
您嘗試在 switch 陳述式內使用 **default** 陳述式一次以上。  預設案例一定是 switch 陳述式內的最後一個 case 陳述式 \(它是「後續」案例\)。  
  
### 若要更正這個錯誤  
  
-   從您的 `switch` 陳述式移除任何額外的 **default** case 陳述式 \(在您的 switch 陳述式中最多只能使用一個 default case 陳述式\)。  
  
## 請參閱  
 [switch 陳述式](../../javascript/reference/switch-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [JavaScript 保留字](../../javascript/reference/javascript-reserved-words.md)