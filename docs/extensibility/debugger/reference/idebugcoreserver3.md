---
title: "IDebugCoreServer3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
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
ms.openlocfilehash: caa07706e507bb6f6b8aa84404eab5e67579be5b
ms.lasthandoff: 04/05/2017

---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
這個介面可讓的伺服器處理序正在執行中的相關資訊的存取。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 實作此介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)獲得從這個介面[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面。 呼叫[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)也可以傳回此介面。 這個介面是最常使用自訂連接埠供應商所啟動的伺服器 （本機或遠端） 上的應用程式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了上[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面，這個介面會實作下列方法︰  
  
|方法|說明|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|擷取伺服器的名稱。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|擷取伺服器名稱的易記版本|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|會告知這些處理序啟動時，會自動附加至處理序特定的偵錯引擎。|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|會自動附加動作失敗時，請擷取特定的錯誤碼。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|在伺服器上建立偵錯引擎執行的個體。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|擷取指出伺服器是否與呼叫端在相同電腦上的旗標。|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|擷取值，指出用來與伺服器通訊的通訊協定。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|停用所有自動都附加此伺服器所知的所有偵錯引擎設定。|  
  
## <a name="remarks"></a>備註  
 自訂連接埠供應商收到[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面上呼叫[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。 `IDebugCoreServer3`介面可透過該介面。  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
