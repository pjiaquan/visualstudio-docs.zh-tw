---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將自訂訊息加到圖形診斷 *HUD* \(平視顯示\)。  
  
## 語法  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### 參數  
 `szMessage`  
 要加到HUD的訊息。  
  
## 備註  
 圖形診斷 HUD 在圖形診斷下執行的應用程式顯示於左上角。  顯示與應用程式和圖形擷取相關的執行階段資訊資訊，以及呼叫此函式時所加入的訊息。  
  
 若要將訊息加至 HUD，您不需要有效地擷取圖形資訊；換言之，訊息可透過 `VsgDbg` 類別的執行個體來加入，不用先呼叫 [Init](../debugger/init.md) 成員函式。  訊息僅顯示於 HUD ，不會記錄為圖形記錄檔。