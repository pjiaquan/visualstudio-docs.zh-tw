---
title: "IDebugProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2"
helpviewer_keywords: 
  - "IDebugProgram2 介面"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示在處理程序中執行的程式。  
  
## 語法  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 和自訂的連接埠提供者實作這個介面表示處理程序中的程式。  工作階段偵錯管理員 \(SDM\) 也會實作這個介面來提供資訊給[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。  
  
## 呼叫者的備忘稿  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件會傳回這個介面的新程式。  此介面也做為參數的多個介面上的許多方法。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProgram2`。  
  
|方法|描述|  
|--------|--------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|列舉此程式中正在執行的執行緒。|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|取得程式的名稱。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|取得此程式正在執行中處理序。|  
|[結束](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|結束這個程式。|  
|[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|將附加至這個程式。|  
|[CanDetach](../Topic/IDebugProgram2::CanDetach.md)|判斷偵錯引擎 \(DE\) 可以中斷程式。|  
|[中斷連結](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|中斷偵錯工具，這個程式的連結。|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|取得這個程式的全域唯一識別項。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|取得設計程式的屬性。|  
|[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|會繼續執行此程式從停止的狀態。  會清除任何先前的執行狀態。|  
|[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|會繼續執行此程式從停止的狀態。  會保留任何先前的執行狀態。|  
|[逐步執行](../../../extensibility/debugger/reference/idebugprogram2-step.md)|執行一個步驟。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|此程式停止執行下一個要求的時間它的執行緒執行程式碼的其中一個。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|取得名稱和執行這個程式的偵錯引擎 \(DE\) 的識別項。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|列舉指定的位置，在原始程式檔中的程式碼內容。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|取得這個程式的記憶體位元組。|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|取得這個程式 」 或 「 此程式的組件的反組譯碼資料流。|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|列舉此程式已載入並且正在執行的模組。|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|取得這個程式的 \[編輯後繼續 \(ENC\) 的更新。<br /><br /> 自訂的偵錯引擎不會實作這個方法 \(應該永遠傳回`E_NOTIMPL`\)。|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|列舉此程式的程式碼路徑。|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|寫入檔案傾印。|  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 備註  
 程式已經在特定的執行階段架構中，執行，而 \[處理程序由一或多個程式所組成的執行緒容器。  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [下一步](../Topic/IEnumDebugPrograms2::Next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)