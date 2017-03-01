---
title: "IDebugManagedObject |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
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
ms.openlocfilehash: d991b417a054073918cd92bfb097926e3e1d49a2
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此介面可讓運算式評估工具 (EE) 值的類別執行個體上呼叫屬性或方法 (例如， `System.Decimal`)，並設定其值，而不需呼叫[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)正在偵錯的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 運算式評估工具會實作這個介面來代表 managed 程式碼的物件，例如的變數。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 若要取得此介面，呼叫[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)上[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)代表實值類別的執行個體。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自方法[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)、`IDebugManagedObject`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|傳回代表 managed 程式碼物件，並且可以從任何適當 managed 程式碼取得介面的介面。|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|將此物件的值設定為指定 managed 程式碼物件的值。|  
  
## <a name="remarks"></a>備註  
 運算式評估工具會使用此介面來剖析樹狀結構中儲存 managed 程式碼的物件。  
  
## <a name="requirements"></a>需求  
 標頭︰ ee.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
