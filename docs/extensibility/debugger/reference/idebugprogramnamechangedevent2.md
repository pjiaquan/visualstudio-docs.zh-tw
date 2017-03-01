---
title: "IDebugProgramNameChangedEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 6
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
ms.openlocfilehash: d0032971225d25b054cd66ee500800de4bcd7b97
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
程式的名稱變更時傳送從偵錯引擎 (DE) 工作階段偵錯管理員 (SDM)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 會實作這個介面來報告程式的名稱已變更。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 使用 SDM [QueryInterface](/visual-cpp/atl/queryinterface)存取**IDebugEvent2**介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並傳送這個事件来報告的物件名稱變更的程式。 DE 傳送這個事件使用[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到偵錯程式時，會將 SDM 所提供的回呼函式。 自訂連接埠供應商會傳送這個事件，使用我的介面。  
  
## <a name="requirements"></a>需求  
 標頭︰ Msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll
