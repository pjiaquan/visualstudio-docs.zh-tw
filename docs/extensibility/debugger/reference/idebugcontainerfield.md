---
title: "IDebugContainerField |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7cf087725f8cfcb8ba53da739706ededcddb61c4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcontainerfield"></a>IDebugContainerField
這個介面表示的符號或其他符號或類型的容器類型。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者實作的相同物件上實作這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。 此介面也是代表容器的所有介面的基底類別。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 許多介面的許多方法會傳回這個介面。 因為這是所有容器的基底類別，更具特製化的介面可以從這個介面取得使用[QueryInterface](/visual-cpp/atl/queryinterface)。 這類介面包括[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)， [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)， [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)，和[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了在方法[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法︰  
  
|方法|說明|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|建立容器的欄位的列舉值。|  
  
## <a name="remarks"></a>備註  
 陣列 （容器的變數），類別 （如方法和變數的容器） 和方法 （在容器中的參數和區域變數） 都是容器的範例。  
  
## <a name="requirements"></a>需求  
 標頭︰ sh.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
