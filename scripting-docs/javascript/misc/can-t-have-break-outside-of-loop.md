---
title: "迴圈外不可以有 &#39;break&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 迴圈外不可以有 &#39;break&#39;
您嘗試在迴圈外使用 **break** 關鍵字。  **break** 關鍵字是用來結束迴圈或 `switch` 陳述式，  因此必須將它內嵌在迴圈或 `switch` 陳述式的主體中。  不過，您可以在 break 關鍵字之後使用**標籤**。  
  
```  
break labelname;  
```  
  
 當您使用巢狀迴圈或 `switch` 陳述式並必須中斷最內層以外的迴圈時，只需要透過 **break** 關鍵字並搭配標籤名稱即可達成。  
  
### 若要更正這個錯誤  
  
-   確保您是在封閉迴圈或 switch 陳述式內部使用 **break** 關鍵字。  
  
## 請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)