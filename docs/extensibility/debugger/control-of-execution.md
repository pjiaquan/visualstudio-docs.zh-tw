---
title: "執行的控制權 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [偵錯 SDK]，控制項的執行"
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 執行的控制權
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) 通常傳送下列事件之一做為最後一次啟動事件：  
  
-   進入點事件，如果將附加到新啟動的程式  
  
-   載入完成事件，如果附加至正在執行的程式  
  
 這兩個這些事件會完全停止事件，這表示 DE 等待使用者回應的 IDE。  如需詳細資訊，請參閱[操作模式](../../extensibility/debugger/operational-modes.md)。  
  
## 正在停止事件  
 當停止事件傳送給偵錯工作階段：  
  
1.  包含目前指令指標的執行緒與程式，都可以取得從事件介面。  
  
2.  IDE 會決定目前的原始程式檔和位置，這就會顯示在編輯器中以反白顯示。  
  
3.  偵錯工作階段通常是回應此第一個停止事件藉由呼叫程式的**繼續**方法。  
  
4.  該程式再執行，直到遇到停止條件，這類的方式來點擊的中斷點，當中寫 DE 將中斷點事件傳送至偵錯工作階段。  中斷點事件停止事件，並 DE 再次等待使用者回應。  
  
5.  如果在使用者選擇逐步要事，或是函式，IDE 會提示來呼叫該程式的偵錯工作階段`Step`方法，將它傳遞單位 \(指令、 陳述式或行\) 的步驟，而且步驟的類型 — 也就是是否要逐步執行至、 多於還是超出該函式。  完成此步驟時，DE 便會傳送到偵錯工作階段，也就是停止事件步驟完成的事件。  
  
     \-或\-  
  
     如果在使用者選擇要繼續從目前的指令指標，IDE 會提示來呼叫該程式的偵錯工作階段**執行**方法。  程式會繼續執行，直到發生下一步的停止條件為止。  
  
     \-或\-  
  
     如果偵錯工作階段是要略過特定的停止事件時，偵錯工作階段會呼叫該程式的**繼續**方法。  如果程式逐步執行至、 超過或函式，它遇到的停止條件時，它會繼續步驟。  
  
 以程式設計的方式，當 DE 遇到停止條件時，它會傳送這類停止事件 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 的 「 工作階段偵錯管理員 」 \(SDM\) 為 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 介面。  在 DE 通過 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 和 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 代表的程式，並且包含目前指令指標的執行緒的介面。  SDM 呼叫 [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 以取得最上層堆疊框架和呼叫 [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 以取得目前的指令指標相關聯的文件內容。  此文件內容通常是來源的程式碼檔案名稱、 行和資料行編號。  IDE 會使用這些來反白顯示包含目前指令指標的原始程式碼。  
  
 SDM 通常是回應此第一個停止事件藉由呼叫 [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。  然後會在程式執行，直到它遇到的停止條件，這類的方式來點擊的中斷點，大小寫 DE 會傳送 [IDebugBreakpointEvent2 介面](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ，SDM。  中斷點事件停止事件，並 DE 再次等待使用者回應。  
  
 如果在使用者選擇逐步要事，或是函式，IDE 會提示要呼叫 SDM  [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)，將它傳遞  [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) \(指令、 陳述式或行\) 和 [STEPKIND](../../extensibility/debugger/reference/stepkind.md)，也就是是否要逐步執行至、 多於還是超出該函式。  完成此步驟時，會將傳送 DE  [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) SDM，也就是停止事件的介面。  
  
 如果在使用者選擇要繼續從目前的指令指標，IDE 會要求呼叫 SDM  [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)。  程式會繼續執行，直到發生下一步的停止條件為止。  
  
 如果偵錯封裝要略過特定的停止事件時，偵錯封裝呼叫 SDM，它會呼叫 [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。  如果程式逐步執行至、 超過或函式，它遇到的停止條件時，它會繼續步驟。  這暗示著程式會維護逐步執行的狀態，好讓它知道如何繼續。  
  
 SDM 會呼叫`Step`， **執行**，以及**繼續**是非同步的這表示 SDM 會預期呼叫傳回快速。  如果 DE 傳送 SDM 停止事件之前的相同執行緒上`Step`， **執行**，或**繼續**傳回，SDM 停止回應。  
  
## 請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)