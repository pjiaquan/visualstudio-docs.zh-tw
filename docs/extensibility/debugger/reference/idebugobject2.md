---
title: "IDebugObject2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2"
helpviewer_keywords: 
  - "IDebugObject2 介面"
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會提供物件的其他資訊。  
  
## 語法  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## 實作者注意事項  
 運算式評估工具會實作這個介面可提供別名和物件的相關資訊的存取權的支援。  
  
## 呼叫端資訊  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面可以取得此介面使用 [QueryInterface](/visual-cpp/atl/queryinterface)。 此外， [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) 傳回此介面。  
  
## 依照 Vtable 順序的方法  
 除了在方法 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面， `IDebugObject2` 實作下列介面︰  
  
|方法|描述|  
|--------|--------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|取得變數的欄位 （如果有的話），可能會支援這個物件所表示的屬性。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|取得 managed 程式碼物件，代表此物件的值。|  
|[CreateAlias](../Topic/IDebugObject2::CreateAlias.md)|建立此物件的唯一識別碼或傳回現有的別名。|  
|[GetAlias](../Topic/IDebugObject2::GetAlias.md)|取得與這個物件相關聯的別名，如果有的話。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|取得這個物件的型別。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|判斷這個物件是否表示使用者資料。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|判斷是否不再有效的 \[編輯後繼續的狀態。<br /><br /> 自訂運算式評估工具不會實作這個方法 \(它一律會傳回 `E_NOTIMPL`\)。|  
  
## 備註  
 請參閱 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 討論別名。  
  
## 需求  
 標頭︰ ee.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)