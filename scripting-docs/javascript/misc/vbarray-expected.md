---
title: "必須是 VBArray | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5013"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 必須是 VBArray
您提供的物件不是 Visual Basic safeArray，但是必須是 Visual Basic safeArray。  
  
```  
new VBArray(safeArray);  
```  
  
 VBArray 是唯讀的，而且無法直接建立。  safeArray 引數是 VBArray 值，而且必須已取得 VBArray 值，然後才能傳遞給 `VBArray` 建構函式。  只能從現有的 ActiveX 或其他物件擷取值來完成這項作業。  
  
### 若要更正這個錯誤  
  
-   請務必只能將 **VBArray** 物件傳遞給 **VBArray** 建構函式。  
  
## 請參閱  
 [VBArray 物件](../../javascript/reference/vbarray-object-javascript.md)   
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)