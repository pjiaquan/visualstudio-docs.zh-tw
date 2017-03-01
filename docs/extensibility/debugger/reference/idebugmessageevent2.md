---
title: "IDebugMessageEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 12
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
偵錯引擎 (DE) 會使用此介面將訊息傳送至 Visual Studio 需要使用者回應。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 會實作這個介面來傳送訊息至 Visual Studio 需要使用者回應。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
 這個介面的實作必須進行通訊的 Visual Studio 呼叫[{1>responsemanager](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) DE 到。 例如，做法是使用訊息張貼至 DE 訊息處理的執行緒，或實作這個介面的物件可以保存 DE 的參考，與回應傳遞至回撥 DE `IDebugMessageEvent2::SetResponse`。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並傳送這個事件物件需要回應對使用者顯示一則訊息。 此事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)附加至偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugMessageEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|取得要顯示的訊息。|  
|[{1>responsemanager](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|設定回應，如果有，從訊息方塊。|  
  
## <a name="remarks"></a>備註  
 如果需要使用者的特定回應特定訊息 DE 會使用此介面。 比方說，如果 DE 取得 「 拒絕存取 」 訊息，嘗試從遠端附加至程式之後，DE 會傳送特定訊息至 Visual Studio 中`IDebugMessageEvent2`事件與訊息方塊樣式`MB_RETRYCANCEL`。 這可讓使用者重試或取消在附加作業。  
  
 DE 指定如何遵循的慣例，Win32 函式來處理此訊息會`MessageBox`(請參閱[AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)如需詳細資訊)。  
  
 使用[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)介面將訊息傳送至 Visual Studio 不需要使用者回應。  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
