---
title: "IDebugProcessEx2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
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
ms.openlocfilehash: 56483c55810f75042184439be9f0d7bcfb2d6836
ms.lasthandoff: 04/05/2017

---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
這個介面可讓偵錯管理員 (SDM) 通知的處理程序是從處理序中斷連結或附加至工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 自訂連接埠供應商實作此介面上相同的物件做為[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面以︰  
  
-   支援的工作階段連線到處理程序的追蹤  
  
-   支援自動附加跨多個偵錯引擎  
  
 如果選擇自訂連接埠供應商可以實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
  
-   SDM 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugProcess2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProcessEx2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|通知處理程序工作階段現在偵錯程序。|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|通知處理程序工作階段不會再偵錯程序。|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|新增程式節點以進行偵錯引擎的清單。|  
  
## <a name="remarks"></a>備註  
 這個介面是私用 SDM 和處理序之間。  
  
## <a name="requirements"></a>需求  
 標頭︰ Portpriv.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
