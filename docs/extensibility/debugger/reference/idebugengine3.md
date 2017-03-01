---
title: "IDebugEngine3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 15
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 293517b87b57e905e5807fa9e3f07a47d4cead4c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine3"></a>IDebugEngine3
表示控制項的一個或多個模組的偵錯一個偵錯引擎 (DE)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 實作這個介面是由自訂 DE （如果它支援符號） 來啟用 JustMyCode 狀態。 DE 必須實作這個介面，如果它支援符號和 JustMyCode。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是由工作階段偵錯管理員 (SDM) 傳遞至使用者選項用於載入符號的位置上呼叫。 它也稱為具現化時，設定引擎的 GUID （此 GUID 根據來自引擎註冊期間的度量）。 SDM 也會呼叫此介面設定 JustMyCode 狀態，並設定指定的狀態，偵錯工具已知的所有例外狀況。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自方法[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)、`IDebugEngine3`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|設定 DE 會用來搜尋偵錯符號的路徑。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|載入所有尚未有載入其符號的模組的符號。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|告訴 DE JustMyCode 資訊。|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|從度量設定 DE GUID。|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|設定指定的狀態目前未完成的所有例外狀況。|  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
