---
title: "IDebugStackFrame2 | Microsoft Docs"
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
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "IDebugStackFrame2 介面"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示在特定執行緒的呼叫堆疊中的單一的堆疊框架。  
  
## 語法  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## 實作器注意事項  
 偵錯引擎 \(DE\) 會實作這個介面表示堆疊框架。  
  
## 呼叫者的備忘稿  
 呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)擷取[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面。  呼叫[下一步](../Topic/IEnumDebugFrameInfo2::Next.md)擷取[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構，其中包含`IDebugStackFrame2`介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugStackFrame2`。  
  
|方法|描述|  
|--------|--------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|取得此堆疊框架中的程式碼內容。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|取得此堆疊框架中的文件內容。|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|取得堆疊框架的名稱。|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|取得堆疊框架的描述。|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|取得電腦相關表示法的堆疊框架相關聯的實體位址範圍。|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|取得評估內容進行目前的內容中的運算式評估為堆疊框架和執行緒。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|取得與堆疊框架相關聯的語言。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|取得與堆疊框架相關的屬性描述。|  
|[EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)|建立列舉值的堆疊框架的屬性。|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|取得與堆疊框架相關聯的執行緒。|  
  
## 備註  
 只有在偵錯程式已停止於中斷點 \(可能因使用者設定中斷點或例外狀況\) 時，會取得這個介面。  從這個介面，可取得運算式內容，來評估運算式、 可傳回的暫存器的清單，或取得與檢查呼叫堆疊。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)