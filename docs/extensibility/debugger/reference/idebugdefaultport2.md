---
title: "IDebugDefaultPort2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
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
ms.openlocfilehash: d048bf55d8a8cb721e8ebf85444e49c3bfa771b9
ms.lasthandoff: 04/05/2017

---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
這個介面會提供數種方法來存取伺服器的連接埠，以及通知功能。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 實作此介面代表存取程式的偵錯連接埠。 如果會處理遠端偵錯自訂連接埠供應商也可以實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 方法的引數[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面會提供此介面。 呼叫[QueryInterface](/cpp/atl/queryinterface)上[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面也可以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了中定義的方法[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)，這個介面會實作下列方法︰  
  
|方法|描述|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|取得從這個連接埠的連接埠通知介面。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|主控這個連接埠的伺服器取得的介面。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|決定是否在本機電腦上執行此連接埠。|  
  
## <a name="remarks"></a>備註  
 名稱"`IDebugDefaultPort2`」 是出入，因為它不代表預設連接埠。 無法呼叫它"IDebugPort3。 」  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
