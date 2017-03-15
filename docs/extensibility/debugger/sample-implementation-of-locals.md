---
title: "範例實作的區域變數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，本機變數"
  - "運算式評估、 本機變數"
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 範例實作的區域變數
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 以下是 Visual Studio 如何取得方法的區域變數的運算式評估工具 \(EE\) 的概觀:  
  
1.  Visual Studio 偵錯引擎 \(DE\) 會呼叫 [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 取得 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件，代表堆疊框架，包括區域變數的所有屬性。  
  
2.  `IDebugStackFrame2::GetDebugProperty` 呼叫 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 取得物件，描述在其中發生中斷點的方法。 DE 提供符號提供者 \([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)\)、 地址 \([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)\)，並繫結器 \([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\)。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` 呼叫 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) 與所提供 `IDebugAddress` 物件來取得 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 代表包含指定之的位址的方法。  
  
4.  `IDebugContainerField` 介面針對查詢 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 介面。 這是此介面，可用來存取方法的區域變數。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` 具現化類別 \(稱為 `CFieldProperty` 範例中\) 來實作 `IDebugProperty2` 介面，以代表方法的區域變數。`IDebugMethodField` 物件會置於這 `CFieldProperty` 物件連同 `IDebugSymbolProvider`, ，`IDebugAddress` 和 `IDebugBinder` 物件。  
  
6.  當 `CFieldProperty` 物件初始化， [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) 上稱為 `IDebugMethodField` 物件來取得 [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) 結構，其中包含可顯示資訊的方法本身。  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` 傳回 `CFieldProperty` 物件做為 `IDebugProperty2` 物件。  
  
8.  Visual Studio 呼叫 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 傳回 `IDebugProperty2` 物件與篩選 `guidFilterLocalsPlusArgs`。 這會傳回 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 物件，其中包含方法的區域變數。 這個列舉型別填入藉由呼叫 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 和 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)。  
  
9. Visual Studio 呼叫 [下一步](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 取得 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 每個本機的結構。 此結構包含一個指向 `IDebugProperty2` 本機介面。  
  
10. Visual Studio 呼叫 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 的每個本機取得區域的名稱、 值和型別。 這是顯示在資訊 **區域變數** 視窗。  
  
## 本章節內容  
 [實作 GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 描述實作 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)。  
  
 [列舉的區域變數](../../extensibility/debugger/enumerating-locals.md)  
 描述如何偵錯引擎 \(DE\) 會呼叫列舉本機變數或引數。  
  
 [取得本機屬性](../../extensibility/debugger/getting-local-properties.md)  
 描述 DE 如何取得名稱、 類型和值的一個或多個區域變數的呼叫。  
  
 [取得本機值](../../extensibility/debugger/getting-local-values.md)  
 討論取得本機需要評估內容所指定的繫結器物件的服務。  
  
 [評估 \[區域變數\]](../../extensibility/debugger/evaluating-locals.md)  
 說明如何評估區域變數。  
  
## 相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供 DE 呼叫運算式評估工具 \(EE\) 時，會傳遞的引數。  
  
 [MyCEE Sample](http://msdn.microsoft.com/zh-tw/624a018b-9179-402f-9d48-3aec87b48f4f)  
 示範建立 MyC 語言的運算式評估工具的其中一個實作方法。  
  
## 請參閱  
 [顯示 \[區域變數\]](../../extensibility/debugger/displaying-locals.md)