---
title: "IDebugArrayObject2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: 10
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
ms.openlocfilehash: 35f267fc6b7cecd252119e1b8edc2557decf6483
ms.lasthandoff: 02/22/2017

---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示 managed 的陣列物件，並可讓運算式評估工具 (EE) 來判斷陣列的基底的索引 （下限）。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 這是由 managed 偵錯引擎 (DE) 實作。  
  
## <a name="methods"></a>方法  
 除了在方法[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)介面，這個介面會實作下列方法︰  
  
|方法|說明|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|擷取指定陣列中的維度數目的每個索引的基底的索引 （下限）。|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|判斷陣列是否具有定義的基底索引 （下限）。|  
  
## <a name="remarks"></a>備註  
 運算式評估工具會使用這個介面，代表剖析樹狀結構中的 managed 的陣列。  
  
## <a name="requirements"></a>需求  
 標頭︰ Ee.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll
