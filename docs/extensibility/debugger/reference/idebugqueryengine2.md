---
title: "IDebugQueryEngine2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: cdf774a97ef3b1d0bfeec0be8482d2c116806885
ms.lasthandoff: 04/05/2017

---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
這個介面可讓偵錯管理員 (SDM) 擷取介面，表示偵錯引擎 (DE) 的工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作此介面上實作的最常見的 DE 介面的物件 (例如[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)， [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)，和[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) 才能允許存取[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) DE 本身的介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](/cpp/atl/queryinterface)典型的 DE 介面，以取得此介面上。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugQueryEngine2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|取得自訂偵錯引擎 (DE) 介面。|  
  
## <a name="remarks"></a>備註  
 通常會實作這個介面中實作的物件[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面以支援因果排序逐步執行函式; 亦即時偵錯工具會跳離函式，要執行的下一個函式可能不會在堆疊上的前一個函式，但另一個執行緒中的函式完全。 如需 「 原因 」 的定義，請參閱[Visual Studio 偵錯工具詞彙](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)。  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
