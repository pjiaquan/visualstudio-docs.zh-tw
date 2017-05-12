---
title: "IDebugApplication 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication 介面"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplication 介面
公開非遠端偵錯方法提供語言引擎和主應用程式使用。  
  
 除了繼承自 `IRemoteDebugApplication` 的方法之外，`IDebugApplication` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|設定應用程式的名稱。|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|告知同處理序偵錯管理員以語言引擎在單一步驟模式會傳回給呼叫端。|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|使指定的字串是由偵錯工具 IDE 中顯示。|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|如果還沒有附加，啟動偵錯工具預設 IDE 並附加偵錯工作階段之間的這個應用程式。|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|導致目前的執行緒封鎖並傳送中斷點的通知至偵錯工具 IDE。|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|這會導致應用程式釋放所有的參考和輸入了非現用狀態。|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|傳回應用程式之目前中斷旗標。|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|會傳回執行緒與目前的執行緒。|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|提供對指定同步處理非同步存取偵錯作業。|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|將堆疊框架列舉值提供者加入至應用程式。|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|從應用程式移除堆疊框架列舉值提供者。|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|判斷目前執行中的執行緒是偵錯工具執行緒。|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|為呼叫端提供一種機制。在偵錯工具執行緒上執行程式碼。|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|建立與特定文件提供者的新應用程式節點。|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|引發泛型事件至偵錯工具的 `IApplicationDebugger` 介面。|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|導致目前的執行緒封鎖並傳送錯誤的通知至偵錯工具 IDE。|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|判斷 Just\-In\-Time \(JIT\) 偵錯工具是否已註冊。|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|判斷某個 JIT 偵錯工具是否登錄自動偵錯沉默寡言的主機。|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|若要將全域運算式內容提供者加入至應用程式。|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|從應用程式移除全域運算式內容提供者。|