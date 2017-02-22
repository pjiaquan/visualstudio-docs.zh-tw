---
title: "啟動為基礎的附件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯引擎啟動"
  - "偵錯引擎，附加至程式"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 啟動為基礎的附件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

啟動為基礎的附件，程式會自動執行。  裝載該程式的處理序啟動時由 SDM，啟動為基礎的附件將遵循路徑相似之處手動附加檔案的方法。  如需資訊，請參閱[附加至程式](../../extensibility/debugger/attaching-to-the-program.md)。  
  
## 附加的處理程序  
 主要的差別在於之後的事件順序**附加**呼叫，如下所示：  
  
1.  傳送 **IDebugEngineCreateEvent2** SDM 事件物件。  如需詳細資訊，請參閱[傳送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  呼叫`IDebugProgram2::GetProgramId`上的方法 **IDebugProgram2** 介面傳遞至**附加**方法。  
  
3.  傳送 **IDebugProgramCreateEvent2** 事件的物件，以通知 SDM 的局部 **IDebugProgram2** DE 代表程式建立物件。  
  
4.  傳送 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 事件來通知 SDM 會啟動處理程序中建立新的執行緒的物件。  
  
## 請參閱  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)   
 [啟用偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)