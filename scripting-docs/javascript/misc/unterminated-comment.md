---
title: "未結束的註解 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 未結束的註解
您已開始多行註解區塊，但是並未適當結束此區塊。  多行註解會以 "\/\*" 組合做為開始，並且以相反順序的 "\*\/" 組合做為結束。  以下是一個範例：  
  
```javascript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### 若要更正這個錯誤  
  
-   請務必以 "\*\/" 結束多行註解。  
  
## 請參閱  
 [註解陳述式](../../javascript/reference/comment-statements-javascript.md)