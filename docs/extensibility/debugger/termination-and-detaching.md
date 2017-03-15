---
title: "終止，並中斷連結 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式終止事件"
  - "偵錯引擎，中斷連結程式"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 終止，並中斷連結
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

以下說明正常結束。  
  
## 討論  
 後 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 介面持續發生，如果不有任何中斷點、 例外狀況及執行階段錯誤，或是要偵錯程式偵錯應用程式中的無限迴圈會執行到完成為止。  這是正常結束。  
  
 您必須傳送 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 實作正常結束。  這需要實作 [IDebugProgramDestroyEvent2::GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md) 方法。  
  
## 請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)