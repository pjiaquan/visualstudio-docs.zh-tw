---
title: "IDebugProperty2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2"
helpviewer_keywords: 
  - "IDebugProperty2 介面"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示堆疊框架屬性、 程式文件屬性或某些其他屬性。  屬性通常是運算式評估的結果。  
  
> [!NOTE]
>  這種使用方式的 「 屬性 」 不應該混淆與表示類別、 成員變數雖然`IDebugProperty2`可表示這類實體。  
  
## 語法  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來代表特定種類的值。  例如，值可以是數值運算式評估，用於顯示記憶體或暫存器和它們的值清單的記憶體內容的結果。  
  
## 呼叫者的備忘稿  
 呼叫[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)以取得這個介面表示評估的結果。  `IDebugExpression2::EvaluateAsync`傳回這個介面傳送[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) SDM，依序呼叫的介面[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)要擷取其屬性。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)傳回這個介面來提供相關的指令碼文件。  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)傳回這個介面來表示函式的傳回值。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)傳回這個介面來代表不同的屬性，例如名稱或記憶體內容的程式。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)傳回這個介面來代表不同的屬性，例如本機變數的堆疊框架。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugProperty2`。  
  
|方法|描述|  
|--------|--------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|在 \[填滿[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構描述屬性。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|從字串中設定屬性的值。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|從指定的參考值會設定屬性的值。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|列舉屬性的子系。|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|傳回父代屬性。|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|傳回描述最具衍生性屬性的屬性的屬性。|  
|[GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md)|傳回的記憶體位元組組成屬性的值。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|傳回屬性值的記憶體內容。|  
|[GetSize](../Topic/IDebugProperty2::GetSize.md)|會傳回大小而定，以位元組為單位的屬性值。|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|傳回這個屬性值的參考。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|傳回屬性的更多資訊。|  
  
## 備註  
 屬性，以`IDebugProperty2`介面，可視為具有名稱、 類型及地址的值。  更廣泛來說， `IDebugProperty2`可以表示所有包含階層式結構，與父代和子節點。  
  
 屬性是通常是暫時性的從前只只要目前的堆疊框架上，例如項目。  相反地，參考，以在[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面，持續時間，只要值仍將保留在記憶體中。  
  
 可以使用 IDE `IDebugProperty2`介面，以讓使用者瀏覽\]，並在執行階段修改內容。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)