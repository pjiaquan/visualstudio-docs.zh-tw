---
title: "直接附加程式 | Microsoft Docs"
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
  - "偵錯引擎，附加至程式"
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 直接附加程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

要偵錯程式已經在一般執行的處理序中的使用者會遵循此程序：  
  
1.  在 IDE 中，選擇**偵錯的處理程序** 指令從 **工具**功能表。  
  
     \[**處理序**\] 對話方塊便會顯示。  
  
2.  選擇處理程序，然後按一下**附加** \] 按鈕。  
  
     **附加至處理序**會出現對話方塊，列出安裝在電腦上所有偵錯引擎 \(DEs\)。  
  
3.  指定要用來偵錯選取的處理序，然後按一下 \[DEs **確定**。  
  
 偵錯封裝啟動偵錯工作階段，並傳遞給它的 DEs 的清單。  偵錯工作階段傳遞此清單中，連同回呼函式，以選取的處理序，並詢問該處理程序，以列舉其執行中的程式。  
  
 以程式設計的方式，在回應使用者要求時，偵錯封裝會具現化工作階段偵錯管理員 \(SDM\)，並將清單中選取的 DEs 傳遞給它。  清單中，連同偵錯封裝傳遞 SDM  [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 介面。  偵錯封裝傳遞至選取的處理序 DEs 的清單，藉由呼叫 [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)。  SDM 會呼叫 [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 上的連接埠列舉處理序中執行的程式。  
  
 從這一刻起，每個偵錯引擎附加到某個程式，就像所述[附加之後啟動](../../extensibility/debugger/attaching-after-a-launch.md)，有兩個例外。  
  
 為了提高效率，使每個 DE 具有一組程式將會加入至群組會實作與 SDM 共用地址空間的 DEs。  如此一來，  [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 呼叫 [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) ，並將它附加至程式的陣列。  
  
 第二個例外狀況是傳送的是，附加到正在執行的程式啟動事件不通常包含進入點的事件。  
  
## 請參閱  
 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)