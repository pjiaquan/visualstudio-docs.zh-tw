---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

切換圖形診斷 *HUD* \(平視顯示\) 覆疊的開啟或關閉。  
  
## 語法  
  
```cpp  
void ToggleHUD();  
```  
  
## 備註  
 在執行圖形診斷的應用程式中，圖形診斷 HUD 顯示於左上角。  其顯示與應用程式和圖形擷取相關的執行階段資訊，以及呼叫 [AddMessage](../debugger/addmessage.md) 成員函式時所加入的訊息。  
  
 若要切換 HUD，您不需要主動地擷取圖形資訊，它可以透過 `VsgDbg` 類別的一個個體執行切換，不過不需要先呼叫 [Init](../debugger/init.md) 成員函式。